# Wave 1 report

`wave1-report.md` is the report of the first calibration of the strategy library (wave 1: 8 katas, 4 symbols, 1h and 4h, 280 pre-registered cells). Its sha256 is `e91edb41b1c50e4c1f87ebd2c99f6192e09d8c7cdc5574c38aee9f16b042016b`.

## How it was produced

- **The rules came first.** Every rule was fixed before any price was read. The pre-registration's fingerprint is published in `KraidleAI/monark-precommitments` (commit `36c0982`). The katas themselves are specified in `KATA-SPEC.md`, with the conformance vectors in `vectors.json`, in this repository.
- **Four time blocks.** Thresholds and seasonal factors were frozen on the selection block (2024-10-01 to 2025-10-01). Each cell was calibrated once on the calibration block (2025-10-01 to 2026-04-01), then checked on the test block (2026-04-01 to 2026-10-01), which can veto a cell but never tune one.
- **Recomputed independently, blind.** A second team wrote its own implementation from the written definitions only, without reading the code or the results. It recomputed all 280 cells and sealed the fingerprint of its result before any comparison. Every status, k*, rank, bound, threshold and veto is equal. The only differences are in the last binary digit of some floating-point values: one platform's logarithm differs from the other's by one unit in the last place, and the spec did not fix the order of one multiplication. With both aligned, the two registries are identical byte for byte.
- **The same layout whatever the outcome.** Nothing was removed for its result.

## What it says, in one line

276 cells serve calibrated silence, 2 serve a calibrated region, and 2 were vetoed by the test block. The null reading expected 0.19 direction cells to open by chance alone; one opened on calibration and was vetoed on test.

## What it is not

Every item of the report is a reference computation under the stated assumptions of the pre-registration: cost-net values, deflated Sharpe ratios, PBO by combinatorially symmetric cross-validation and the Benjamini-Hochberg list. None of it is a promise of returns.
