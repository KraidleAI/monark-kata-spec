# MONARK gate contract, version 1.1.0

**Version 1.1.0, effective 2026-10-06.** It replaces version 1.0.0. The service switched on that date, and this document was published the same day.

This document defines what the gate speaks:
- the three versioned formats: prediction, coverage verdict, gate decision;
- the request envelope and its parameters;
- the policy table files a verdict refers to, and how to recompute a verdict from them;
- the error bodies and their closed catalogue of codes;
- the output of the `calibrate` tool.

[`KATA-SPEC.md`](../KATA-SPEC.md), at the root of this repository, defines how a kata value is computed. This document does not repeat it; section 9 says what the gate accepts from a kata.

The conformance vectors of this version are in `vectors-1.1.0.json`, next to this file (`contract-1.1.0/vectors-1.1.0.json`). Every value in it was computed by the gate's own code. Section numbers below are the ones the served messages cite.

## 1. Scope

- The gate receives a **prediction** with caller parameters and returns a **gate decision**, which holds a **coverage verdict**.
- MONARK gates a predictor. It does not compute the predictor's value, does not trade, and never calls the tool it gates.
- The server speaks exactly one version. A prediction whose `schema_version` is not `"1.1.0"` is refused with code `schema_version_unsupported` (section 13).
- The attestation formats (`AttestedPrice`, `AttestedFlow`, `AttestedBook`) are not part of this version. They keep `schema_version` `"1.0.0"`.
- The schemas of this version are published in this directory, under `schemas/`: `prediction`, `coverage-verdict`, `gate-decision`, `policy-row` and `tool-error`. The `$id` of each is `https://github.com/KraidleAI/monark-kata-spec/raw/main/contract-1.1.0/schemas/<name>.schema.json`.

## 2. Conventions

- **JSON.** Every format is a closed JSON object: a key not listed for it is refused.
- **Numbers.** Every number the server writes is a finite IEEE-754 binary64 value. A non-finite value is never written.
- **Requests are I-JSON (RFC 7493).**
  - A string with a lone surrogate, anywhere in the request envelope, is refused with HTTP 400 `param_invalid`, unless an earlier check refuses it (a field restricted to printable ASCII is refused by the input schema with `input_invalid`).
  - A number outside binary64 (for example `1e400`) is refused with HTTP 400 `param_invalid`.
  - These two checks run after every other check of the request, so a request that another check refuses keeps that other code. For example, `[1e400]` as calibration scores is refused with `byo_calibration_invalid`.
  - A request with a repeated object key is outside this contract. At this version the server keeps the last value. Do not send one.
- **Canonical writing**, used for every digest in this document:
  - minified JSON, no spaces;
  - every object key is ASCII; a non-ASCII key is refused. Keys are sorted by their bytes (for ASCII keys this is also JavaScript's default string order);
  - numbers written as JavaScript writes them, the shortest round-trip decimal: `0` and `1` without a decimal point, `1e-7` (not `1e-07`), `1e+21`;
  - `-0` is written `0`;
  - strings as `JSON.stringify` writes them; a string with a lone surrogate is refused;
  - an absent optional key is omitted; a key whose value is `null` is written.

  Python's `json.dumps` writes some numbers differently, so it does not conform as is.

  | Value | Canonical writing | sha256 |
  |---|---|---|
  | `{"b":1,"a":[0.1,1e-7,-0]}` | `{"a":[0.1,1e-7,0],"b":1}` | `5f092fcffdb6f012f59af4d9214b9875fc47af0d59a913f2026c7b75a9403e47` |
  | `[0,1,1e21,1.5e-7,123456789012,-2.5]` | `[0,1,1e+21,1.5e-7,123456789012,-2.5]` | `913c0bff13b0654f6fa9ee152b82276480a84a36f63f6469de8398460d9593ab` |
  | `[]` | `[]` | `4f53cda18c2baa0c0354bb5f9a3ecbe5ed12ab4d8e11ba873c2f11161202b945` |
  | `{"\u00e9":1}` (a key that is one non-ASCII letter) | refused: a non-ASCII key | |
  | `["\ud800"]` | refused: a lone surrogate | |

  A request is digested as the server reads it, so `1.0` and `1`, `-0` and `0`, `0.10000000000000001` and `0.1` give the same `request_sha256`. So do two writings of the same envelope with other key orders or spaces.
- **Digests.** A digest is the lowercase hex sha256 of the UTF-8 bytes of a canonical writing.
- **Times.** RFC 3339 date-times, with the grammar of section 3.
- **Decimal strings in policy table files.**
  - `alpha`, `test_delta`, `t1` and `t2` are the shortest round-trip writing of the binary64 number they stand for. A verdict's `alpha` is that number.
  - `miss_bound` (7 decimals), `marginal_alpha` (4 decimals), `runs_level` and `tail_frac` are kept exactly as written, trailing zeros included (for example `tail_frac` `0.90`). Compare them as strings.

## 3. Prediction (`schemas/prediction.schema.json`)

| Field | Type | Rule |
|---|---|---|
| `schema_version` | string | must be `"1.1.0"`, otherwise `schema_version_unsupported`. The schema keeps a version pattern, so that a caller on another version gets this named refusal and not a generic validation error. |
| `task_class` | string, printable ASCII, non-empty | the question asked (section 9 for kata classes) |
| `yhat` | string or number | the predictor's output. The served classes take a number; a caller-supplied calibration in `set` mode takes a label. |
| `predictor_id` | string, printable ASCII, non-empty | the population key. For a kata class, the key without its bucket (section 9). On `liquidation-eligible-coverage` the server derives the stratum key from `yhat` and does not use this field for the lookup; `cell_key` shows the key it used. |
| `produced_at` | string | RFC 3339 date-time, strict (below) |
| `features_digest` | optional, 64 lowercase hex | the digest of the inputs read. **Required on kata classes** (`features_digest_required`). |

**`features_digest`.** The input schema of the HTTP and MCP entry points checks its form. An in-process call that skips the input schema is checked for its presence only, on a kata class; its value is then bound by `request_sha256`.

**`produced_at` grammar:**
- `YYYY-MM-DD`, then `T` or `t`, then `hh:mm:ss` with an optional fraction, then `Z`, `z` or `±hh:mm`;
- a real calendar date (`2024-02-29` is valid, `2026-02-29` is not);
- hours 00 to 23, minutes 00 to 59, seconds 00 to 59, or 60 only when the UTC time is 23:59 (a leap second, counted as the next second);
- offsets at most 23:59.

A value outside this grammar is refused. At the HTTP and MCP entry points, the input schema's `date-time` format refuses some of these values first, with `input_invalid`; the others get `produced_at_invalid`.

An instant more than 300 s after the server's clock is refused with `produced_at_future`; the instant is read to the millisecond, its fraction truncated after three digits. So `…T04:05:00.0004Z` against a clock at `…T04:00:00Z` is accepted. This check, and the kata lateness check of section 9, run at the HTTP and MCP entry points, which read the server clock. An in-process call without a clock gets the grammar check and, on a kata class, the grid check, which reads no clock.

## 4. Request envelope

`{ "prediction": Prediction, "params": Params, "attested"?: AttestedPrice }`.

- `attested` is an `AttestedPrice` in its own 1.0.0 format. No served class has an attestation subject, so every request that carries `attested` is refused with `attested_inconsistent`.
- `params` is described in the service's OpenAPI document. It is not one of the three versioned formats, but the meaning of its fields and the decision order of section 6 belong to the version: changing them gives a new version (section 15).

| Field | Type and range | Meaning |
|---|---|---|
| `alpha` | number in (0, 1) | the target miscoverage. **Required for every class.** |
| `nMin` | integer ≥ 1 | the least number of calibration scores. **Required for every class.** |
| `tau` | number ≥ 0 | the set-size threshold |
| `tauInterval` | number ≥ 0 | the width threshold of an interval region, in the units of the region (section 8) |
| `remainingBudget`, `bFloor` | finite numbers, `bFloor` ≥ 0 | the caller's remaining authorization capacity and its floor (section 6) |
| `intent` | string, number or `null` | the value tested against the region |
| `tool` | non-empty string | the gated tool; echoed, never called |
| `clockOpen` | boolean | whether the caller's decision window is still open |
| `calibration` | optional object | the caller's own scores (below) |

A value out of these ranges is refused with `param_invalid`. A field of the wrong JSON type, or missing, is refused by the input schema of the entry point with `input_invalid`.

**Imposed `alpha` and `nMin`.** Where a class imposes them, the value sent must equal the class's value, otherwise `policy_alpha_mismatch` or `policy_nmin_mismatch`. They are never replaced silently.

| Where | `alpha` | `nMin` |
|---|---|---|
| `liquidation-eligible-coverage`, every stratum | `0.01` | `100` |
| `stable-run-velocity-24h`, the one key with a committed calibration | `0.1` | `50` |
| kata `dir` classes, with or without a row | `0.45` | `6` |
| the other kata classes, with or without a row | `0.01` | `299` |

On `cascade-liquidable-24h`, on the other keys of `stable-run-velocity-24h`, and on a caller-supplied calibration, the caller's values are used.

**`calibration`** (the caller-supplied path): `{scores, mode, candidates?}`.
- `scores`: at most 10000 finite numbers; in `interval` mode none is negative.
- `mode`: `interval` (an additive band around a number `yhat`) or `set` (a set over `candidates`).
- `candidates`, `set` mode only: 1 to 10000 objects `{label, score}`; labels printable ASCII, unique, without `|`; scores finite.
- A malformed calibration is refused with `byo_calibration_invalid` (at the HTTP and MCP entry points, a field of the wrong type or more than 10000 elements is refused first by the input schema, with `input_invalid`); a `yhat` of the wrong type for the mode with `byo_yhat_type`; in `set` mode, a `tau` above the number of candidates minus 1 with `byo_set_tau_cap`.
- A calibration is refused with `byo_overrides_committed` on `btc-dir-15m`, `cascade-liquidable-24h`, `liquidation-eligible-coverage` (any key), and on the committed key of `stable-run-velocity-24h`. Another key of `stable-run-velocity-24h` may bring its own calibration.
- Names that imitate a committed or reserved name are refused: section 13 (`byo_edge_blank`, `byo_lookalike_committed`, `byo_reserved_kata`, `byo_lookalike_confusable`).

## 5. Coverage verdict (`schemas/coverage-verdict.schema.json`)

17 fields are required; `scores` is optional.

| Field | Type | Meaning |
|---|---|---|
| `schema_version` | `"1.1.0"` | constant |
| `task_class` | string | echoed |
| `method` | `"split"`, `"hac-cp"` or `"risk-control"` | how `qhat` is chosen (section 7). The served marginal classes and caller-supplied calibrations use `split`; the kata classes use `risk-control`. No served path uses `hac-cp`. |
| `alpha` | number in (0, 1) | the alpha of the row used. With no row: the class's alpha on a kata class, the imposed value on `liquidation-eligible-coverage`, otherwise the caller's. It is the target miscoverage, not a measured rate. |
| `n_calib` | integer ≥ 0 | the number of calibration scores: the row's `n`, or the number of scores sent on a caller-supplied calibration; 0 when no row applies |
| `region` | object or `null` | the served region; `null` when no region is served |
| `qhat` | number or `null` | the quantile behind `region`; `null` exactly when `region` is `null` |
| `qhat_unit` | `"label"`, `"scale"` or `"score"` | the class's unit (sections 8 and 10), whatever the reason. On a caller-supplied calibration it is fixed by the mode: `label` in `interval` mode, `score` in `set` mode, so one caller `task_class` can carry both units. |
| `scale` | number or `null` | on a class with `qhat_unit` `"scale"`, the sigma_hat sent as `yhat`; otherwise `null` |
| `abstain` | boolean | `true` whenever `region` is `null`, and for every `calib_*` reason |
| `reason` | string | one literal of section 6 |
| `residual` | array of strings | residual assumptions carried from an attestation; empty at this version |
| `scores` | array of numbers, optional | the calibration scores. The server does not send this field at this version. |
| `scores_sha256` | 64 hex | the digest of the calibration scores as one JSON array, in the order of the table file's `order` column (`time` for kata rows and for the stable-run row, `ascending` for the liquidation rows), or in the caller's order for a caller-supplied calibration. With no row, the digest of `[]`. |
| `cell_key` | string or `null` | the key the server looked up in the class's table file, whether or not a row was found; `null` only on a caller-supplied calibration |
| `policy_row_sha256` | 64 hex or `null` | the digest of the row used; `null` when no row applies |
| `policy_table_sha256` | 64 hex or `null` | the digest of the class's table file; `null` only on a caller-supplied calibration |
| `produced_at` | string | the prediction's `produced_at` |

**Region objects:**
- `{ "kind": "set", "labels": [string...], "label_schema": string }`: an intent is in the region if it is a string equal to a listed label.
- `{ "kind": "interval", "lo": number, "hi": number }`: an intent is in the region if it is a number x with lo ≤ x ≤ hi.
- An intent of another type, and `null`, is in no region.

**Couplings**, checked by the server before it sends a verdict:
- `region` is `null` exactly when `qhat` is `null`; then `abstain` is `true` and `reason` is one of the reasons section 6 admits with no region;
- `abstain` is `true` for every `calib_*` reason;
- `scale` is not `null` exactly when `qhat_unit` is `"scale"`;
- a non-null `policy_row_sha256` implies a non-null `cell_key`;
- `cell_key` is `null` exactly when `policy_table_sha256` is `null`;
- when `scores` is present, `scores_sha256` is its digest.

## 6. Gate decision, reasons and decision order

**Gate decision** (`schemas/gate-decision.schema.json`), 9 required fields:

| Field | Meaning |
|---|---|
| `schema_version` | `"1.1.0"` |
| `action` | `commit`, `defer` or `abstain` |
| `allow` | `true` exactly when `action` is `commit` |
| `tool` | `params.tool`, echoed |
| `intent` | `params.intent`, echoed |
| `verdict` | the coverage verdict of section 5 |
| `remaining_budget` | `params.remainingBudget`, echoed |
| `request_sha256` | the sha256 of the canonical writing of the request envelope as the server read it (section 2) |
| `reason` | one literal of the list below |

**Reasons.** One list is used for `verdict.reason` and `decision.reason`. The column "No region" says whether a verdict may carry this reason with `region: null`.

| Reason | No region | Meaning |
|---|---|---|
| `covered` | no | the region is served (verdict); the call commits (decision) |
| `set_too_large` | no | the set has more labels than `tau`. On the decision: the caller's clock is open, action `defer`. |
| `interval_too_wide` | no | the interval is wider than `tauInterval` and the caller's clock is open (action `defer`) |
| `intent_not_in_region` | no | the intent is outside the region; on a caller-supplied set, also an empty set |
| `budget_exhausted` | no | `remainingBudget` is below `bFloor` |
| `clock_expired` | no | the region is too large or too wide and `clockOpen` is false |
| `no_label_schema` | no | in the list; the gate does not produce it at this version |
| `upstream_timeout` | yes | in the list; the server never invents a timeout |
| `attestation_absent`, `attestation_refused`, `binding_broken` | yes | in the list; no served class has an attestation subject, so the gate does not produce them |
| `non_evaluable` | yes | the prediction cannot be evaluated (step 1), a direction lean of exactly 0 (section 9), or a non-finite input to the decision (step 3) |
| `under_calib` | yes | no calibration serves this call: no row for the key, fewer scores than `nMin`, a rank above n, a row with status `under_calib`, an additive band edge that is not finite (section 8), or a liquidation `qhat` of 0 |
| `calib_silence` | yes | the row's calibration is calibrated silence (its status reason is in section 10). On a kata set class the verdict carries `{up, down}`; on a kata band, no region. |
| `calib_vetoed` | yes | a pre-registered forward check vetoed a row that served a region; regions as `calib_silence` |
| `calib_retired` | yes | the row was retired after deployment; regions as `calib_silence` |
| `out_of_support` | yes | the sigma_hat sent is outside the calibration support of the row |
| `region_degenerate` | yes | the calibrated region has zero width, or a kata band has no finite edge (section 8) |

**Decision order.** Steps 1 to 4 apply to every region; then sets and intervals have different orders. The first step that applies wins.

1. The prediction is not evaluable: action `abstain`, reason `non_evaluable`. A prediction is not evaluable when `yhat` is not a finite number, or, on a caller-supplied calibration in `set` mode, when `yhat` is not one of the candidate labels.
2. Timeout: `abstain`, `upstream_timeout`. The server never sets it.
3. A non-finite `remainingBudget`, `bFloor`, `tau`, `tauInterval`, `n_calib` or `nMin`: `abstain`, `non_evaluable`. A request cannot reach this step: a non-finite parameter is refused before with `param_invalid`. The step stays for the decision function called in process.
4. `n_calib` below `nMin`, a verdict without region, or a reason admitted with no region: action `abstain`. The reason is the verdict's when the verdict's reason is admitted with no region, even when `n_calib` is below `nMin`; otherwise it is `under_calib`. A null region under a reason that needs one gives `abstain` `under_calib`, never an error. A `calib_*` cell abstains: it never defers, because waiting does not lift a silence.

Set region:

5. intent not in the set: `abstain`, `intent_not_in_region`;
6. `remainingBudget` below `bFloor`: `abstain`, `budget_exhausted`;
7. more labels than `tau`: `defer` with `set_too_large` if `clockOpen` is true, otherwise `abstain` with `clock_expired`;
8. `commit` with `covered`.

Interval region:

5. lo ≥ hi (a zero-width or inverted region; a served verdict already answers such a region with `region: null` and `region_degenerate`): `abstain`, `region_degenerate`;
6. `remainingBudget` below `bFloor`: `abstain`, `budget_exhausted`;
7. width hi − lo above `tauInterval`: `defer` with `interval_too_wide` if `clockOpen` is true, otherwise `abstain` with `clock_expired`. The width test comes before the intent test;
8. intent not in the interval: `abstain`, `intent_not_in_region`;
9. `commit` with `covered`.

## 7. Methods and ranks

`qhat` is the score at rank p among the n calibration scores sorted ascending.

| `method` | Rank p | Fails closed |
|---|---|---|
| `split` | p = ⌈(n + 1)(1 − a)⌉, computed in exact integers | `under_calib` if n < `nMin` or p > n |
| `risk-control` | p = n − k*, where k* is the largest k ≥ 0 with P(Bin(n, alpha) ≤ k) ≤ test_delta, decided in exact rational arithmetic | `under_calib` if n < n0 (no such k) |
| `hac-cp` | in the enumeration only; no served path uses it | |

**The value a of a split rank.**
- For a caller-supplied calibration and for `calibrate`: a is the decimal that the shortest round-trip writing of the `alpha` received denotes, as JavaScript's `Number.prototype.toString` writes it, exponent included, with no limit on the number of decimals. `0.12345` is read as 12345/100000.
- For a row of a table file: a is the decimal of the row's `alpha` string.

Split rank vectors (n, alpha: p): (9, 0.3: 7); (19, 0.15: 17); (24, 0.44: 14); (9, 0.7: 3); (613, 0.1: 553); (170, 0.01: 170); (9, 0.12345: 9); (10, 1e-7: 11, so `under_calib`). Reading alpha as its exact binary value instead would give 8, 18, 14 and 4 for the first four. That is not the rule.

**Per-calibration values** (`risk-control`, used by the kata classes):
- n0 is the smallest n with (1 − alpha)^n ≤ test_delta: 6 at alpha 0.45, 299 at alpha 0.01, both at test_delta 0.05.
- `miss_bound` U(n, k*, test_delta) is the one-sided Clopper-Pearson upper bound: the alpha at which P(Bin(n, alpha) ≤ k*) = test_delta, rounded up to the next multiple of 10^-7 and written with 7 decimals.
- The test_delta of a recalibration attempt j (1 to 4) is the base value divided by 2^(j − 1): `0.05`, `0.025`, `0.0125`, `0.00625`.

| alpha | n | k* | p | `miss_bound` |
|---|---|---|---|---|
| 0.45 | 6 | 0 | 6 | `0.3930378` |
| 0.45 | 20 | 4 | 16 | `0.4010282` |
| 0.45 | 100 | 36 | 64 | `0.4463429` |
| 0.01 | 299 | 0 | 299 | `0.0099692` |
| 0.01 | 500 | 1 | 499 | `0.0094523` |
| 0.01 | 1000 | 4 | 996 | `0.0091300` |

## 8. Units and regions

| `qhat_unit` | Score | Region served |
|---|---|---|
| `label` | in the units of the label | an additive band [lo, hi] around `yhat` (`stable-run-velocity-24h`, caller `interval` mode, and `cascade-liquidable-24h`, which has no row), or an upper bound [0, hi] (`liquidation-eligible-coverage`) |
| `scale` | fl(label / sigma_hat), one binary64 division | the band [0, h*], in label units (kata band classes) |
| `score` | an abstract score | a set of labels (kata `dir` classes; caller `set` mode) |

**Additive band.** The edges are taken from the score test:
- hi is the largest double x with fl(x − yhat) ≤ qhat;
- lo is the smallest double x with fl(yhat − x) ≤ qhat;
- both are found by bisection on the bit patterns of the doubles.

If yhat − qhat or yhat + qhat is not finite, no band is served: `under_calib`. If lo = hi, no band is served: `region_degenerate`.

| yhat | qhat | lo | hi |
|---|---|---|---|
| 1 | 1 | -1.1102230246251565e-16 (that is −2^-53, where yhat − qhat = 0) | 2 |
| 0.0001 | 0.00013119228083333334 | -0.00003119228083333335 | 0.00023119228083333336 |
| 0.1 | 0 | no band: `region_degenerate` | |
| 1.7e308 | 1e307 | no band: `under_calib` | |

**Upper bound** (`liquidation-eligible-coverage`). The score is max(y − yhat, 0). The region is [0, yhat + qhat]. At this version `yhat` and `qhat` are integers, and the server checks when it builds the table that the largest `yhat` of the stratum plus `qhat` is at most 2^53, so the sum is exact. A `qhat` of 0 serves no region: `under_calib`.

**h\*** (kata band classes) is the largest double h ≥ 0 with fl(h / sigma_hat) ≤ qhat.
- Correctly rounded division is monotone in the numerator for a fixed sigma_hat > 0. So x ≤ h* holds exactly when fl(x / sigma_hat) ≤ qhat, double for double.
- A bisection on the bit patterns of the non-negative doubles finds h*.
- When MAX_VALUE itself passes, there is no finite edge. When h* is 0, the band has zero width. Both serve no region, with `region_degenerate`.

| qhat | sigma_hat | h* |
|---|---|---|
| 1 | 0.0123 | 0.0123 |
| 2.5 | 0.0137 | 0.03425 |
| 0.7 | 0.003 | 0.0021 |
| 6.752248630174e-311 | 1.0124145746231078e28 | 6.836074924667226e-283 |
| 5e-324 | 1e300 | 7.410984687618697e-24 |
| 0 | 1e300 | 2.470328229206233e-24 |
| 1e300 | 1e10 | no finite edge |

On a kata band class, `intent` and `tauInterval` are in the label units of the class, which `KATA-SPEC.md` and its pre-registration define, and the width compared with `tauInterval` is h*.

**Sets.** A label is in the region when its score is at most `qhat`. On a kata `dir` class the region is `{side}` with `qhat` 0, or `{up, down}` with `qhat` 1 (section 9).

## 9. Kata classes on the gate

**The gate abstains on every well-formed kata call at this version.** No kata table holds a row, so the gate serves no region and makes no coverage statement on a kata class. A well-formed call answers `under_calib`, or `non_evaluable` for a lean of exactly 0 on a `dir` class. A malformed call is a named HTTP 400.

- **Class names** follow `<sym>-<family>-<h>`. The pattern `^[a-z0-9]{2,10}-(dir|range|mae-down|mae-up)-(15m|1h|4h|24h)$`, compared without ASCII case, is reserved against caller-supplied names, as is the key prefix `kata:` (section 13). A class is served only if it has a table file. A reserved name without one answers `task_class_unknown`. `btc-dir-15m` is retired and answers `task_class_retired`.
- **Class registry.** The 32 served kata classes, each with its own table file (section 10):

| Classes | `region_rule` | `qhat_unit` | `method` | `alpha` | `test_delta` | `n_min` (n0) | `h_ms` | `label_schema` |
|---|---|---|---|---|---|---|---|---|
| `{btc,eth,bnb,sol}-dir-{1h,4h}` | `sign-set` | `score` | `risk-control` | `0.45` | `0.05` | 6 | 3600000 or 14400000 | `up\|down` |
| `{btc,eth,bnb,sol}-{range,mae-down,mae-up}-{1h,4h}` | `scaled-band` | `scale` | `risk-control` | `0.01` | `0.05` | 299 | 3600000 or 14400000 | `null` |

**Request contract.** A kata call first passes the checks every call passes:
- the parameter ranges;
- `schema_version`;
- the `produced_at` grammar and future check;
- the guards of a caller-supplied calibration (a kata class name with a calibration is a reserved name: `byo_reserved_kata`);
- `attested`.

Then, in this order, the first failing check answers:
1. **grid**: on the fields of the `produced_at` string, the seconds are `00`, every fraction digit is `0`, and the instant (offset applied) is a multiple of the class horizon; otherwise `produced_at_off_grid`. So `…T04:00:00.0004Z` and `…T23:59:60Z` are off grid;
2. **lateness**: a call received more than 300 s after `produced_at` is refused with `produced_at_stale`. The 300 s is the same clock tolerance as `produced_at_future`. A class whose horizon is shorter than 1 h needs its own value, set by a dated revision before it is served;
3. `yhat` is a number, otherwise `yhat_type_mismatch`;
4. `features_digest` is present, otherwise `features_digest_required`;
5. **key**: `predictor_id` follows the grammar below, otherwise `kata_key_invalid`;
6. **domain**: on a `dir` class, a lean in [−1, 1]; on a band class, a finite sigma_hat > 0; otherwise `kata_yhat_domain`;
7. `alpha` equals the class's value, otherwise `policy_alpha_mismatch`, also when no row applies;
8. `nMin` equals the class's n0, otherwise `policy_nmin_mismatch`, also when no row applies;
9. on a `dir` class, `tau` is at most 1, otherwise `policy_tau_cap`.

A lean of exactly 0 answers `non_evaluable` only after all these checks.

**Key grammar** (grammar only): `kata:<kataId>@<venue>/<SYMBOL>/<h>`.
- `kata:` is exact, in lower case.
- `kataId` and `venue`: 1 to 64 characters, `^[a-z0-9]+(-[a-z0-9]+)*$`.
- `SYMBOL`: 2 to 20 of `A-Z` and `0-9`, starting with the class's symbol in upper case.
- `<h>`: the class's horizon.
- No bucket and no other segment.

The gate checks the grammar only. A kata or a venue that has no row gives a key with no row, which answers `under_calib`. A `SYMBOL` that only starts with the class's symbol (for example `BTCDOMUSDT` on a `btc-…` class) is accepted, and has no row.

**The key looked up** (`cell_key`) is derived by the server from `yhat`:
- a band class: `<predictor_id>/b0`;
- a `dir` class with a lean of exactly 0: `<predictor_id>`, and no row is looked up;
- a `dir` class otherwise: the side is `up` for a lean > 0 and `down` for a lean < 0. The thresholds are those of the first current row of that side, in the order of the table file. With m = |lean|, compared to the binary64 numbers `Number(t1)` and `Number(t2)`: `b1` if m ≤ t1, `b2` if t1 < m ≤ t2, `b3` if m > t2. The key is `<predictor_id>/<side>-b<k>`. When the side has no current row, the key is `<predictor_id>/<side>`; at this version every `dir` call with a non-zero lean gets this key.

The thresholds are compared as binary64 numbers, not as exact decimals. [`KATA-SPEC.md`](../KATA-SPEC.md) section 5, "compare |m| to the number they denote", is read this way by the gate: a threshold string is the shortest round-trip writing of a double, and the number it denotes is that double. The table below is the vector that fixes this reading. With thresholds `0.1` and `0.2`, whose doubles lie above those decimals:

| m | 0.05 | 0.1 | next double above 0.1 | 0.2 | next double above 0.2 | 1 |
|---|---|---|---|---|---|---|
| bucket | `b1` | `b1` | `b2` | `b2` | `b3` | `b3` |

**What the gate does not check.** It does not recompute the kata value and does not check the bars behind `features_digest`. `KATA-SPEC.md` sections 2 and 5 describe the pure kata function: a scale value that is not strictly positive, and a lean outside [−1, 1], non-finite or 0, are `non_evaluable` there. A conforming kata does not output those values. If one is sent, the refusals above are the gate's answers, and a lean of 0 answers `non_evaluable`.

**Rows, for when a kata table holds one.** No kata row is served at this version, and the server refuses to load a kata table file that holds a row. The reading below is stated so that the published table format has one meaning:
- on a `dir` class, a row with status `region` serves `{side}` with `qhat` 0, and the verdict follows the set rule: `abstain` true and reason `set_too_large` when 1 > `tau`, otherwise `covered`. Rows with status `silence`, `vetoed` or `retired` serve `{up, down}` with `qhat` 1 and their `calib_*` reason. A row with status `under_calib` serves no region, with `under_calib`;
- on a band class, a sigma_hat outside [`calib_support.min`, `calib_support.max`] answers `out_of_support`; otherwise a row with status `region` serves [0, h*], and a row with another status serves no region, with its reason.

## 10. Policy table files (`class-policy-v2`, `schemas/policy-row.schema.json`)

There is **one table file per served `task_class`**: `policy/<task_class>.json` in this directory (`contract-1.1.0/policy/<task_class>.json` from the root of the repository). A table file is the JSON object `{ "row_format": "class-policy-v2", "class": ClassEntry, "rows": [PolicyRow...] }`. Its bytes are its canonical writing, so its sha256 is the `policy_table_sha256` the server sends. A new table file of one class does not change the digest of another class.

**What the published files hold at this version.** There are 35 table files:
- the 32 kata classes, with no row;
- `cascade-liquidable-24h`, with no row;
- `stable-run-velocity-24h`, with one row: its committed key, n 613, `order` `time`;
- `liquidation-eligible-coverage`, with one row: stratum s0, n 170, `order` `ascending`.

The two rows carry no array of scores: they carry n, `alpha`, `p_served`, `marginal_alpha`, the one score `qhat`, `scores_sha256`, `source` and `text`. The 35 digests are listed in `vectors-1.1.0.json` (`served_tables`).

**Short 0/1 sequences.** The digest of a 0/1 sequence of 30 points or fewer can be inverted by trying every sequence. **No published table file carries a row of 30 points or fewer**, so none carries the digest of a 0/1 sequence of 30 points or fewer. At this version this holds because the only rows are the two above: their n is 613 and 170, above 30, and neither score sequence is a 0/1 sequence (each holds values other than 0 and 1). The synthetic tables of `vectors-1.1.0.json` hold no row of 30 points or fewer either. Kata rows, whose sequences can be 0/1 sequences, are not published. The server has no check of its own for this rule. The tool that writes the published table files refuses any row of 30 points or fewer. A revision that publishes kata rows says how it keeps the rule.

**ClassEntry**, 16 keys, all present:

| Key | Type |
|---|---|
| `task_class` | string |
| `region_kind` | `set` or `interval` |
| `region_rule` | `sign-set`, `scaled-band`, `additive-band` or `upper-bound` |
| `qhat_unit` | `label`, `scale` or `score` |
| `statement` | `per-calibration` or `marginal` |
| `method` | `risk-control` or `split` |
| `alpha`, `test_delta` | decimal string or `null` (`null` when the class does not impose it) |
| `n_min` | integer ≥ 1 or `null` |
| `h_ms` | integer ≥ 1 or `null` (the horizon in ms) |
| `grid` | boolean |
| `cell_key_rule` | `kata-bucket`, `committed-key` or `liq-stratum` |
| `cell_key_base` | string or `null` (the liquidation base key) |
| `strata_cuts` | strictly increasing integers ≥ 1, or `null` |
| `label_schema` | string or `null` |
| `text` | the text served when no current row holds the key looked up (section 12) |

The class entries of the three marginal classes:

| `task_class` | `region_rule` | `cell_key_rule` | `alpha` | `n_min` | `strata_cuts` |
|---|---|---|---|---|---|
| `stable-run-velocity-24h` | `additive-band` | `committed-key` | `null` | `null` | `null` |
| `cascade-liquidable-24h` | `additive-band` | `committed-key` | `null` | `null` | `null` |
| `liquidation-eligible-coverage` | `upper-bound` | `liq-stratum` | `0.01` | 100 | `[200000000000, 10000000000000, 100000000000000]` |

All three have `region_kind` `interval`, `qhat_unit` `label`, `statement` `marginal`, `method` `split`, `test_delta`, `h_ms` and `label_schema` `null`, and `grid` false. The liquidation amounts are in units of 10^-8. The stratum k of `yhat` is the number of cuts that are ≤ `yhat`: k = 0 below the first cut, 3 at or above the last. For example, 199999999999 is in s0, 200000000000 in s1, 10000000000000 in s2 and 100000000000000 in s3.

**PolicyRow**, 60 keys, all present. A column that does not apply is `null`, never omitted. The list is closed; a change of it needs a new `row_format`.

| Group | Columns and types |
|---|---|
| identity | `row_format` (`class-policy-v2`), `task_class`, `cell_key` (strings), `region_rule` (as ClassEntry), `current` (boolean) |
| kata | `kata_id` (string), `w` (integer ≥ 1), `venue`, `symbol` (strings), `horizon` (`15m`, `1h`, `4h`, `24h`), `side` (`up`, `down`), `bucket` (`up-b1`, `up-b2`, `up-b3`, `down-b1`, `down-b2`, `down-b3`, `b0`), `thresholds` (`{t1, t2}`, decimal strings) |
| scale | `scale_table` (`{kind, values, sha256}`: `kind` `hour-of-week` or `us-profile`, `values` numbers > 0 or `null`, `sha256` the digest of `values`), `calib_support` (`{min, max}`, numbers > 0), `fit_sha256` (64 hex) |
| statement | `statement` (as ClassEntry), `alpha` (string `^0\.[0-9]{0,3}[1-9]$`), `test_delta` (decimal string), `calib_attempt` (integer 1 to 4), `calib_cause` (string), `calib_parent` (`none` or 64 hex), `epoch` (integer ≥ 1), `bound_on` (`commit` or `region`), `tau_cap` (1), `n_min` (integer ≥ 1) |
| calibration | `n` (integer ≥ 0), `k_star` (integer ≥ 0), `p_served` (integer ≥ 1), `k_obs`, `misses` (integers ≥ 0), `qhat` (number), `miss_bound` (`^0\.[0-9]{7}$`), `marginal_alpha` (`^0\.[0-9]{4}$`), `aux_seq` (`label` or `score`) |
| dependence checks | `runs_miss`, `runs_aux` (`pass`, `reject`, `empty`), `tail_frac`, `runs_level` (strings), `tail_m`, `tail_a` (integers ≥ 0), `tail_tail_num` (decimal integer string), `tail_tail_den` (decimal integer string ≥ 1), `miss_adj_a` (integer ≥ 0), `miss_adj_tail_num`, `miss_adj_tail_den` (as the tail pair) |
| forward checks | `test`, `bridge`, `fwd` (each `{k_test, n_test, u_test}`: `k_test` integer ≥ 0 or `null`, `n_test` integer ≥ 0, `u_test` `1` or `^0\.[0-9]{7}$` or `null`), `vetoes` (`{test, bridge, fwd}`: `test` boolean, the others boolean or `null`) |
| status | `status` (`region`, `silence`, `vetoed`, `under_calib`, `retired`), `status_reason` (string), `retire` (`{cause, k_test, n_test, u_test}`) |
| digests | `scores_sha256` (64 hex, not null), `aux_sha256`, `series_sha256` (64 hex), `order` (`time` or `ascending`, not null), `source` (`{registry_file, registry_sha256, trial_id, wave, generator}`, not null), `recompute` (`{verifier, scores_sha256, report_sha256}`) |
| text | `text` (string, not null): the text served with this row |

Every integer is a safe integer. `test` holds the first forward block of a row's wave; `bridge` and `fwd` hold the two further forward blocks of a wave 2 row and are `null` on a wave 1 row. Each tail is kept as two unreduced integer strings, because its denominator can exceed 2^53.

**Columns of a `marginal` row** (stable-run, liquidation), a closed list. A marginal row may set only these 20 columns: `row_format`, `task_class`, `cell_key`, `region_rule`, `current`, `statement`, `alpha`, `calib_attempt`, `n_min`, `n`, `p_served`, `qhat`, `marginal_alpha`, `status`, `status_reason`, `retire`, `scores_sha256`, `order`, `source` and `text`. Every other column is `null`, and `p_served`, `qhat` and `marginal_alpha` are not `null`. The server rebuilds each marginal row from the scores it holds and refuses a table whose rows differ:
- n is the number of scores;
- `p_served` is the split rank of section 7, and `qhat` is the score at that rank;
- `marginal_alpha` is (n + 1 − p) / (n + 1), rounded up at 4 decimals;
- `scores_sha256` is taken in the declared `order`.

**Schema and admission.** `schemas/policy-row.schema.json` states what holds for one key alone: type, nullability, enumeration, pattern and integer bounds. A file valid against the schema is not always admitted. The server also holds these rules, a closed list:
- a decimal string is the shortest round-trip writing (so `-0` and `0.10000000000000001` match the schema's pattern and are refused);
- `strata_cuts` is strictly increasing;
- `scale_table.sha256` is the digest of `scale_table.values`;
- `vetoes` and the forward blocks are both set or both `null`, for `test`, `bridge` and `fwd`;
- `retire` is set exactly on a row with status `retired`;
- a tail numerator comes with its denominator;
- `side` is the first part of `bucket` (`null` with `b0`);
- `miss_bound` and `bound_on` are both set or both `null`, and set only on a row with status `region`;
- `tau_cap` is set exactly on a `sign-set` row, which has no `scale_table` and no `calib_support`;
- the closed column list of a marginal row, above;
- the file rules: every row has the class's `task_class`; rows are sorted by `task_class`, then `cell_key`, then `calib_attempt`, and this key is unique; at most one row per `cell_key` is current;
- the canonical writing (no lone surrogate, no non-ASCII key).

**Status reasons** of a kata row, a closed list:
- `` (empty) on a row with status `region`;
- `empty bucket` and `n <n> below n0 <n0>` on a row with status `under_calib`;
- `misses <m> above k* <k>`, `dependence check rejects`, `auxiliary sequence constant (fails closed)` (wave 1) and `tail sequence constant (fails closed)` (wave 2) on a row with status `silence`;
- `vetoed: <block>` on a row with status `vetoed`, where `<block>` is `test`, `bridge` or `fwd`;
- `retired: <cause>` on a row with status `retired`.

The two marginal rows have status `region` and an empty `status_reason`.

**Buckets of a direction side.** A side with thresholds has three current rows, `b1`, `b2` and `b3`, with the same thresholds. A bucket that is structurally empty (equal thresholds) is still a row, with status `under_calib` and reason `empty bucket`. A table that omits a bucket of such a side is refused. A side without thresholds has no row.

**Recalibrations.** Rows are added, superseded and retired only by new table files, published in a new directory of this repository that the release notes name. A file already published is never rewritten.
- Per cell, the attempts are 1 to k without a gap.
- The `calib_parent` of attempt 1 is `none`.
- The `calib_parent` of attempt j ≥ 2 is the digest of the canonical writing of row j − 1 as it is written in the table, with `current` false. The form the server served (`current` true) is refused. So the parent's form, and its digest, are fixed once a child exists.
- A child keeps the kata cell and the factor table of its parent.
- Only the last attempt is current.
- A row retired without a successor stays current, with status `retired`.

**Publication.** A file published in this repository under a versioned directory is never withdrawn and never rewritten. A new `row_format` value, with a dated revision of this document, is required to change the row format. It does not change `schema_version` by itself, but a change of meaning of a verdict field does (section 15).

## 11. Recomputing a verdict

Given a gate decision and the request you sent:

1. **Request.** The sha256 of the canonical writing of your request envelope equals `decision.request_sha256` (section 2).
2. **Table.** Take the published table file of `verdict.task_class` whose digest equals `verdict.policy_table_sha256`. Skip this step on a caller-supplied calibration (`cell_key` and `policy_table_sha256` are `null`).
3. **Key.** Derive the key the server looked up; it equals `verdict.cell_key`:
   - kata: section 9;
   - `stable-run-velocity-24h` and `cascade-liquidable-24h`: your `predictor_id`;
   - `liquidation-eligible-coverage`: `class.cell_key_base` of the table file, followed by `/s<k>`, with k the stratum of `yhat` (section 10). Your `predictor_id` is not used.
4. **Row.** Look for the row with this `cell_key` and `current` true.
   - **No row:**
     - expect `region` `null`, `qhat` `null`, `abstain` true, `policy_row_sha256` `null`, `n_calib` 0, and `scores_sha256` the digest of `[]`;
     - expect `method` and `qhat_unit` from the class entry, and `alpha` as section 5 says;
     - expect `scale` = `yhat` on a kata band class, otherwise `null`;
     - expect the reason `under_calib`, or `non_evaluable` for a lean of exactly 0 on a kata `dir` class.
   - **A row:**
     - its digest equals `verdict.policy_row_sha256`;
     - `alpha` = the number `row.alpha` writes;
     - `n_calib` = `row.n` and `scores_sha256` = `row.scores_sha256`;
     - `method` is `risk-control` when `statement` is `per-calibration`, else `split`.
5. **Region.**
   - `additive-band` (stable-run): the band of section 8 from `yhat` and `row.qhat`.
   - `upper-bound` (liquidation): [0, `yhat` + `row.qhat`].
   - `sign-set` and `scaled-band` (kata): section 9. No kata row is served at this version.
6. **Decision.** Apply section 6 with your `params`.

**Vectors.** `vectors-1.1.0.json` gives, under `http`, the full request, the server clock and the response of each case. The names of the recomputation cases are:
- `stable_run_row`, `stable_run_other_key_no_row`;
- `liquidation_row_s0`, `liquidation_no_row_s1`;
- `kata_dir_no_row`, `kata_dir_down_no_row`, `kata_dir_zero_lean`, `kata_band_no_row`;
- `byo_interval`.

Under `synthetic_kata`, it applies steps 4 to 6 to two synthetic kata tables, which are not served. They show the computation, not a served answer. Among them, `set_region_row_tau_0_5_clock_open` is a set row with `tau` 0.5: the verdict has `abstain` true and reason `set_too_large`, and the decision is `defer`.

For example, `kata_dir_no_row`:
- the request: `task_class` `btc-dir-1h`, `predictor_id` `kata:vote4-v1@example/BTCUSDT/1h`, `yhat` 0.3, `produced_at` `2026-10-06T04:00:00Z`, `alpha` 0.45, `nMin` 6, received 60 s after `produced_at`;
- the answer: `action` `abstain`, `reason` `under_calib`, `cell_key` `kata:vote4-v1@example/BTCUSDT/1h/up`, `method` `risk-control`, `qhat_unit` `score`, `n_calib` 0, `policy_row_sha256` `null`, `policy_table_sha256` `c04ae2921430968857350fd2fa663d0931f92c1a9bfeb595a7d341d3a02cc6e1`, the digest of the published `policy/btc-dir-1h.json`.

**What this does not recompute.** On a kata row, `qhat`, `k_obs`, `misses` and the dependence checks depend on calibration scores that are neither published nor held by the server. They are bound by `scores_sha256` and `aux_sha256`. Before a kata row can be served, it must pass the server's import check:
- it recomputes from the row's counts `k_star`, `p_served`, `n_min`, `marginal_alpha`, `miss_bound`, the test_delta of the attempt, the forward vetoes and the wave 2 tails;
- it compares the row to the projection of its pinned registry file;
- it requires a `recompute` block bound to the row's `scores_sha256`, from a verifier other than the generator;
- it refuses a row that does not match.

The two marginal rows are rebuilt by the server from the scores it holds (section 10).

## 12. What a verdict states

- **`marginal`** (method `split`; the stable-run and liquidation rows, and caller-supplied calibrations). Split conformal coverage is a statement in expectation over the calibration draw, and it holds only under exchangeability. The served text of each class says what is assumed:
  - the stable-run text says that exchangeability is not assumed and that no coverage is measured;
  - the liquidation text says that the bound comes from one recorded episode, and that no coverage is claimed on any other event.
- **`per-calibration`** (method `risk-control`). This is the statement kind of the kata classes. No kata row is served at this version: **the gate makes no coverage statement on a kata class**, and it abstains on every well-formed kata call (section 9).
- **`alpha`** is the target miscoverage of the row or of the caller. It is not a measured rate.
- **The served text.** A decision comes with a text content (`content` on MCP and on the HTTP mirror), which is not inside the decision object:
  - on a served class, the text begins with the `text` of the current row that holds `verdict.cell_key`, or, when there is none, with the `text` of the class entry. The table digest binds that text;
  - so on `liquidation-eligible-coverage`, strata s1 to s3 carry the class text, and only s0 carries the text of its row;
  - on a caller-supplied calibration, the text begins with the fixed text of the caller-supplied path;
  - the rest of the content restates fields of the decision. It is not part of this contract.

## 13. Errors

**HTTP 400 body** (`schemas/tool-error.schema.json`, its root): one of three closed objects, told apart by `error`:
- `{error: "tool_error", operation, message, code}`, with `code` one of the 29 codes of the catalogue other than `input_invalid`, `json_invalid` and `output_invalid`;
- `{error: "invalid_input", operation, message, code: "input_invalid", issues}`: the body fails the input schema. The form of the elements of `issues` is not part of the contract;
- `{error: "invalid_json", operation, message, code: "json_invalid"}`: the body is not JSON.

**HTTP 500 body** (`$defs/InternalError` of the same schema): `{error: "internal_error", operation, code?: "output_invalid"}`. `output_invalid` means that the server refused to send an output that fails its own output schema.

**Outside the catalogue**, these bodies carry no `code`:
- 403 (`invalid_origin`), 404 (`not_found`, `unknown_operation`), 405 (`method_not_allowed`) and 413 (`payload_too_large`);
- a 500 whose body has no `code`.

**MCP.** An error raised by a tool returns `isError: true`, the message as first content, and the code in `_meta["monarkgate.tech/error_code"]`. Input-schema validation errors and JSON-RPC parse errors carry no code.

**Catalogue** (32 codes, in their order):

| Code | Refusal |
|---|---|
| `param_invalid` | a gate parameter out of its range (section 4), or a request that is not I-JSON (section 2) |
| `schema_version_unsupported` | `prediction.schema_version` is not `"1.1.0"`. The message names the version the gate speaks and where this specification is published. |
| `byo_calibration_invalid` | a malformed caller-supplied calibration |
| `byo_yhat_type` | `yhat` does not have the type of the calibration mode |
| `byo_set_tau_cap` | `set` mode: `tau` above the number of candidates minus 1 |
| `yhat_type_mismatch` | `yhat` is not a number on a served class |
| `liq_yhat_domain` | the liquidation `yhat` is not a non-negative safe integer |
| `attested_inconsistent` | an `attested` object was sent; no served class has an attestation subject |
| `task_class_unknown` | the class is not served and no calibration was supplied |
| `byo_overrides_committed` | a calibration sent on a committed class or key (section 4) |
| `byo_edge_blank` | a caller class or key that starts or ends with a blank |
| `byo_lookalike_committed` | a caller class or key equal to a committed one without ASCII case |
| `byo_reserved_kata` | a caller class in the reserved kata pattern (section 9), or a caller key starting with `kata:`, both compared without ASCII case (`btc-dir-15m` with a calibration keeps `byo_overrides_committed`, section 4) |
| `byo_lookalike_confusable` | a caller class or key that equals a committed or reserved name once ASCII confusables are folded |
| `produced_at_invalid` | `produced_at` is not strict RFC 3339 (section 3) |
| `produced_at_future` | `produced_at` more than 300 s after the server clock |
| `output_invalid` | (HTTP 500) the server refused its own output |
| `policy_alpha_mismatch`, `policy_nmin_mismatch` | `alpha` or `nMin` differs from the value the class imposes (section 4) |
| `task_class_retired` | the class is retired (`btc-dir-15m`); the name stays reserved |
| `attest_refused`, `calibrate_input_invalid`, `cascade_input_invalid` | the refusals of the tools `attest`, `calibrate` and `cascade` |
| `ukemi_predict_input_invalid` | the refusal of a tool that is not served at this version |
| `input_invalid`, `json_invalid` | the body fails the input schema, or is not JSON |
| `kata_key_invalid` | `predictor_id` is not a kata key without bucket for this class (section 9) |
| `kata_yhat_domain` | a kata `yhat` outside its domain (section 9) |
| `features_digest_required` | a kata call without `features_digest` |
| `policy_tau_cap` | `tau` above 1 on a kata `dir` class |
| `produced_at_off_grid` | a kata `produced_at` not on the class horizon grid (section 9) |
| `produced_at_stale` | a kata call received more than 300 s after `produced_at` (section 9) |

**Rules:**
- A code is never renamed, removed or reused for another refusal. New codes are added only by a dated revision of this document.
- A consumer must treat an unknown code as a refusal of its request, including a consumer that validates with an older copy of the schema.
- The message text is not part of the contract.
- When a request is invalid on two points, which code is returned is not part of the contract.

## 14. The `calibrate` tool

`calibrate` takes `{scores, alpha, nMin}` and returns `{qhat, n, alpha, method, scores_sha256, label, reason}`.
- `scores`: at most 10000 finite numbers; `alpha` in (0, 1); `nMin` an integer ≥ 1. A value out of these ranges is refused with `calibrate_input_invalid`, a score outside binary64 included. At the HTTP and MCP entry points, a value of the wrong type or more than 10000 scores is refused first by the input schema, with `input_invalid`.
- `method` is always `split`. `n` and `alpha` are echoed.
- `scores_sha256` has the definition of section 5, over the scores in the order sent, computed by the same function as the verdict's.
- `qhat` is the score at the split rank of section 7, the same rank the gate uses on a caller-supplied calibration; `reason` is then `null`. When n < `nMin` or the rank exceeds n, `qhat` is `null` and `reason` is `under_calib`.
- **Audit loop.** Send the same scores, in the same order, with the same `alpha` and `nMin`, to `calibrate` and to `gate` with a `calibration`. The loop closes when `verdict.scores_sha256`, `verdict.alpha` and `verdict.qhat` equal the `calibrate` values, or when both answer `under_calib`. A reordered array gives another digest: it is a mismatch, not another calibration.

Vector (cases `calibrate`, `calibrate_reordered` and `byo_interval` of `vectors-1.1.0.json`):
- scores `[0.5,0.1,0.9,0.3,1,0.7,0.2,0.8,0.4,0.6]`, `alpha` 0.1, `nMin` 5: `qhat` 1, `n` 10, `scores_sha256` `4c8d845ee8f80e0a108be93e0dc43b7e0dfd379fcf5b2e9f36b146c33b3849c6`;
- the gate verdict on the same scores in `interval` mode has the same three values;
- the reversed array gives `scores_sha256` `0fb22b1f46e8b57352f1cd3bd70a21178ede5d661bbfc2240764f2dfbe5f3e7e`, with the same `qhat`.

## 15. Versioning and notice

- `schema_version` covers the prediction, the verdict and the decision together. The server accepts and produces exactly one version.
- Any change to the set of valid prediction, coverage verdict or gate decision documents, to the meaning of a field (a `params` field included), or to the decision order of section 6 gives a new version. The previous version is then refused with `schema_version_unsupported`. The error body (`tool-error.schema.json`) and the table format (`policy-row.schema.json`) are not versioned by `schema_version`: a dated revision may extend the `code` enumeration (section 13), and a table format change needs a new `row_format` (section 10).
- In this project the middle number counts format revisions: 1.1.0 is not a semantic-versioning "compatible" release, and a 1.0.0 consumer refuses it.
- **Notice of this version.** Version 1.1.0 had no notice period. It was published in this repository on its effective date, 2026-10-06, in one release with the service switch. Its release notes are also the notes of release `v0.9.0` of the public mirror, https://github.com/KraidleAI/Monark. From that date, the refusal message of version 1.0.0 names the version spoken and where this document is published. This document is `contract-1.1.0/CONTRACT.md` of https://github.com/KraidleAI/monark-kata-spec.
- Without a version change, a dated revision of this document may:
  - add error codes;
  - add, supersede or retire policy table rows, and add classes, by new table files published in a new directory of this repository (a file under `contract-1.1.0/` is never rewritten);
  - clarify text.

## 16. Changes from 1.0.0

- `schema_version` is `"1.1.0"` in all three formats. 1.0.0 is refused.
- `method` gains `risk-control`.
- Reasons gain `calib_silence`, `calib_vetoed`, `calib_retired`, `out_of_support` and `region_degenerate`. A zero-width additive band now answers `region_degenerate` instead of `under_calib`.
- `region` may be `null` (no region served). In 1.0.0 an empty set region stood for "no region".
- New required verdict fields: `qhat_unit`, `scale`, `cell_key`, `policy_row_sha256`, `policy_table_sha256`.
- `calib_digest` is removed and replaced by `scores_sha256`. The old field hashed the sorted binary64 scores; the new one is the digest of the canonical writing of the scores in the declared order. The name changed because the definition changed.
- `calibrate` returns `scores_sha256` instead of `set_digest`, and the audit loop compares three values (section 14).
- The split rank is computed in exact integers from the decimal alpha. For some (n, alpha) pairs the served quantile moves by one rank: for n 24 and alpha 0.44 the rank is 14, where 1.0.0 served 15.
- Additive band edges are taken from the score test (section 8).
- The decision gains `request_sha256`.
- Requests must be I-JSON: a lone surrogate or a number outside binary64 is refused with `param_invalid` (section 2).
- Every HTTP 400 body carries a `code` from the catalogue of section 13.
- The reserved class pattern widens to `^[a-z0-9]{2,10}-(dir|range|mae-down|mae-up)-(15m|1h|4h|24h)$`, compared without ASCII case (section 9).
- The 32 kata classes are served from their table files, which hold no row: the gate abstains on every well-formed kata call (section 9).
- `KATA-SPEC.md` is unchanged. Its pure functions are as before; the gate's answers to out-of-domain values are those of section 9 here.
