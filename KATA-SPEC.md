# Kata specification, wave 1

A kata is a frozen strategy: a pure, deterministic function of a fixed window of closed bars. MONARK calibrates each kata per cell and gates the calls an agent makes with it. MONARK does not run the kata; the agent does. This document lets an agent compute the same value MONARK calibrated, and check it against the conformance vectors.

**Version 2026-10-02.** It replaces the version of 2026-10-01. Section 4 now writes the order of the operations in the EWMA term, which the first version left open. Section 6 adds two decisions to the `random_walk` case and the `ewma_association` cases, so there are now 333 checks instead of 317. No kata value changes: the code already computed this order, and every value stored in the first version is unchanged.

Source of the rules: the strategy library pre-registration (ADR 0005 v3.1, sha256 `b011e4de3c1b2644af03d15db5992ea964c896a0255e59f7fe4f810736e27b60`, fingerprint posted in the public repository `KraidleAI/monark-precommitments`, commit `36c0982`). The labels (close(t), the path moves, the drop rules) are defined there and in the plan of this part; a caller needs only the sections below.

## 1. Bars and the decision time

- Times are integer milliseconds UTC. Bars are built from 15-minute candles: 4 per 1h bar, 16 per 4h bar, aligned on multiples of the horizon since the epoch.
- A bar covers [start, start + h). Open is the first candle's open, close the last candle's close, high the maximum high, low the minimum low, volume and taker-buy volume the sums, added from the oldest candle to the newest.
- A bar with a missing candle is absent. It is never interpolated.
- At decision time t (a multiple of h), a kata reads the W bars that end at or before t. The last one covers [t - h, t). A bar still forming at t is never read.
- A window with an absent bar gives `non_evaluable`.

**The bytes read (`features_digest`).** The sha256 of the UTF-8 text of one JSON array holding, for each bar of the window from the oldest, the array `[start, open, high, low, close, volume, takerBuyBase]`. Numbers are written as JavaScript writes them: shortest round-trip decimal, integers without a decimal point, no spaces. Example: one bar `[[1759276800000,100,101.5,99,100.25,12,0.5]]`, sha256 `2564e5c6b056f611767a3a864e3794ca0f80e7dde8c275842ddc9a9f73166426`.

## 2. Arithmetic

- IEEE-754 double precision. Every sum runs from the oldest bar to the newest, including the EWMA weight normalizer.
- A window of W bars holds W - 1 one-bar log returns, r_i = ln(close_i / close_(i-1)).
- Standard deviations are sample standard deviations (divide by n - 1).
- `clip` bounds a value to [-1, 1]. Any zero denominator gives `non_evaluable`.
- A direction lean of exactly 0, or a non-finite one, is `non_evaluable` (no view).
- A scale value that is not strictly positive is `non_evaluable`.

## 3. Direction katas (lean m in [-1, 1])

| Id | W | Value |
|---|---|---|
| `trend-ema-v1` | 200 | m = clip((EMA20 - EMA100) / (5 x ATR14)). EMA of span s: k = 2 / (s + 1), seeded with the mean of the first s closes of the window, then `e = k * c + (1 - k) * e` over the remaining closes. ATR14 = mean of the last 14 true ranges, TR_i = max(high_i - low_i, abs(high_i - close_(i-1)), abs(low_i - close_(i-1))). |
| `tsmom-v1` | 25 | m = clip(R24 / (2 x sd24 x sqrt(24))), R24 = ln(close_last / close_first), sd24 = standard deviation of the 24 one-bar log returns. |
| `meanrev-z-v1` | 20 | z = (close_last - mean of the 20 closes) / standard deviation of the 20 closes; m = clip(-z / 2). |
| `takerflow-v1` | 24 | s = (sum of taker-buy base volume) / (sum of base volume); m = clip((s - 0.5) / 0.05). |
| `vote4-v1` | 200 | the mean of the four leans above, each computed on its own trailing W bars and summed in this order; `non_evaluable` if any of the four is. |

## 4. Scale katas (sigma_raw > 0)

| Id | W | Value |
|---|---|---|
| `ewma-vol-hw-v1` | 101 bars (100 returns) | sigma_raw = sqrt(sum of w_i r_i^2), w_i = 0.94^i / sum_j 0.94^j with i = 0 for the most recent return, each weight normalized before use. Each term is computed as `(w_i * r_i) * r_i`: the weight times the return, then times the return, left to right. The other order, `w_i * (r_i * r_i)`, can differ in the last bit. |
| `realized-vol-hw-v1` | 49 bars (48 returns) | sigma_raw = root mean square of the 48 returns. |
| `parkinson-hw-v1` | 48 bars | sigma_raw = sqrt(mean of ln(high / low)^2 / (4 ln 2)). |

**The hour-of-week factor.** The served scale is sigma_hat = sigma_raw x f(slot of t).
- Slot 0 is Monday 00:00 UTC. At 1h there are 168 slots (24 x weekday + hour); at 4h there are 42 (the 1h slot divided by 4, rounded down).
- f is frozen per (kata, symbol, horizon) on the selection block and published with the cells that use it; the range cell and the two path cells of `ewma-vol-hw-v1` share one table. f(slot) is the root mean square of r / sigma_raw over that block's decisions in the slot.
- A slot without a factor gives `non_evaluable`.

## 5. Buckets of a direction lean

- Each cell is keyed by side (up for m > 0, down for m < 0) and strength tercile of |m|.
- The thresholds t1 and t2 of each side are published as decimal strings, written as section 1 writes numbers (JavaScript's shortest round-trip writing: `0.00001`, `1.5e-7`). Compare |m| to the number they denote:
  - `b1`: |m| <= t1;
  - `b2`: t1 < |m| <= t2;
  - `b3`: |m| > t2.
- A side without thresholds is `under_calib`. A lean outside [-1, 1], non-finite or 0 is `non_evaluable`.
- How thresholds are frozen (needed only to reproduce the vector checks): on the selection block, per side, the |m| of the evaluable leans in [-1, 1] sorted ascending, n values; t1 is the value at rank ceil(n / 3) and t2 at rank ceil(2n / 3), 1-based; below 3 values the side has no thresholds. Ties are possible (for example many leans clipped at 1): then t1 or t2 can equal the next one and a bucket is structurally empty, which shows as `under_calib`.
- Factors (needed only to reproduce the vector checks): samples with sigma_raw not > 0 or a non-finite r are skipped; the sums run in the order the samples are given.
- Example key: `kata:vote4-v1@<venue>/BTCUSDT/1h/up-b3`, where the venue of each cell is published with the cell. Scale cells use the bucket `b0`.
- A cell is identified by the pair (task class, key). The range class and the two path classes use the same scale kata, so their keys coincide and only the task class tells them apart.

## 6. Conformance vectors

`vectors.json` holds synthetic bars only, never a recorded candle: seeded random walks and hand-built edge cases (flat prices with zero volume, a steady trend). It also holds bucket and factor cases.
- `kata_cases[].bars` are arrays `[start, open, high, low, close, volume, takerBuyBase]`.
- For each decision, `end` is the number of bars available, and the window of a kata is `bars[end - W : end]`.
- `digests` gives the `features_digest` of three windows, `factors` and `factors_4h` hour-of-week tables at 1h and 4h.
- `ewma_association` gives two windows of `random_walk` (ends 107 and 122) on which the two orders of the EWMA term give different doubles. `value` is the order of section 4, and `other_association` is the other order. They are compared bit for bit, not within the tolerance below, because within 1e-12 the two orders cannot be told apart. A recomputation that wants to match the reference to the bit can use them to check which order it runs.
- **Conformance contract.** An implementation conforms when every value is within a relative 1e-12 of the reference value (absolute 1e-15 near zero), every string (thresholds, buckets, `non_evaluable`, digests) is equal, and every number written into the digest bytes is written as section 1 says.
- **Bit identity is not promised across platforms.** The natural logarithm of two standard libraries can differ by one unit in the last place on some inputs (measured by MONARK's review on one host: 5 256 of 1 000 000 ratios in [0.95, 1.05] between Node v24.15.0 and Python 3.14.5 on Windows 10), so two correct implementations can differ in the last bit of a lean or a scale.
- **Near a bucket edge.** A lean within 1e-12 relative of a published threshold can fall in the neighbouring bucket on another platform. MONARK derives the bucket from the `yhat` the caller sends, so the caller is served the cell of the value it actually computed.
- **Measured, not promised.** The reference code (Node v24.21.0) and an independent implementation (Python 3.11) agree bit for bit on all 333 checks of these vectors (Python 3.11 for the first 317, Python 3.11.15 for this version). The independent implementation was written from the pre-registration and the plan by a separate instance instructed not to read the reference code; this is declared by its author, and the instruction is recorded in the plan. The `ewma_association` lines were added to it in this version by the author of the reference code, who had read it.

## 7. What a kata value is not

A lean is a direction and a strength computed from past bars. It is not a statement about the next move. The statement comes only from MONARK's calibration of the cell, and it holds only for calls whose value is the kata's output on the window named by the call's `features_digest`.
