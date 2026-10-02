# Wave 1 report: calibration of the strategy library

Plan: 0005-G0-part-P2-calibration.md v3, section 9 of 2026-10-02 (87b57c01). Engine: monark-governance main 207f021f. Trial registry: 80 trials, head 648709d0ae8e858e80a527b4b69cf6629f4f9fb7e8b4b5d15752bb7e383caa0e.
Every item below is report-only: none of them changes a status. Cost-net values, deflated Sharpe ratios, PBO and the Benjamini-Hochberg list are reference computations under the stated assumptions of the plan, not statements of MONARK.

## Statuses

- Direction cells: region 0, silence 239, under_calib 0, vetoed 1.
- Range and path cells: region 2, silence 37, under_calib 0, vetoed 1.
- Null reading (direction cells expected to open on CALIB if every kata missed at 0.50): 0.1378 at the nominal n of the pre-registration, 0.1940 at the realized n; opened on CALIB 1 (region or vetoed), still open after the TEST veto 0.

## Cells (CALIB and TEST)

| Cell | Status | n | k* | misses | qhat | U | check 1 | check 2 | drops | n_test | k_test | U_test |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b1 | silence | 632 | 263 | 324 | 1 | 0.4494240 | empty | pass | 0/0 | 676 | 351 | 0.5514708 |
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b2 | silence | 650 | 271 | 339 | 1 | 0.4497360 | empty | pass | 0/0 | 813 | 403 | 0.5251299 |
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b3 | silence | 501 | 206 | 245 | 1 | 0.4486559 | empty | pass | 0/0 | 835 | 402 | 0.5104933 |
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b1 | silence | 668 | 278 | 342 | 1 | 0.4485170 | empty | pass | 0/0 | 655 | 316 | 0.5153323 |
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b2 | silence | 695 | 290 | 361 | 1 | 0.4489710 | empty | pass | 0/0 | 629 | 321 | 0.5438271 |
| btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b3 | silence | 1222 | 520 | 595 | 1 | 0.4493203 | empty | pass | 0/0 | 784 | 399 | 0.5388727 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b1 | silence | 679 | 283 | 331 | 1 | 0.4488727 | empty | pass | 0/0 | 739 | 368 | 0.5288662 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b2 | silence | 724 | 303 | 374 | 1 | 0.4495626 | empty | pass | 0/0 | 819 | 417 | 0.5384426 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b3 | silence | 671 | 280 | 357 | 1 | 0.4495708 | empty | pass | 0/0 | 774 | 397 | 0.5430439 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b1 | silence | 648 | 270 | 320 | 1 | 0.4495298 | empty | pass | 0/0 | 604 | 311 | 0.5490693 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b2 | silence | 734 | 307 | 378 | 1 | 0.4490905 | empty | pass | 0/0 | 679 | 337 | 0.5285821 |
| btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b3 | silence | 912 | 385 | 463 | 1 | 0.4497572 | empty | pass | 0/0 | 777 | 406 | 0.5525401 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b1 | silence | 688 | 287 | 348 | 1 | 0.4490206 | empty | reject | 0/0 | 694 | 347 | 0.5318955 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b2 | silence | 766 | 321 | 352 | 1 | 0.4492315 | empty | pass | 0/0 | 732 | 357 | 0.5187730 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b3 | silence | 779 | 327 | 384 | 1 | 0.4496856 | empty | pass | 0/0 | 659 | 290 | 0.4727787 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b1 | silence | 793 | 333 | 396 | 1 | 0.4495697 | empty | pass | 0/0 | 767 | 382 | 0.5283601 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b2 | silence | 676 | 282 | 314 | 1 | 0.4493189 | empty | pass | 0/0 | 766 | 370 | 0.5133908 |
| btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b3 | silence | 666 | 278 | 314 | 1 | 0.4498260 | empty | pass | 0/0 | 774 | 361 | 0.4966072 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b1 | silence | 475 | 195 | 230 | 1 | 0.4490456 | empty | pass | 0/0 | 469 | 226 | 0.5208993 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b2 | silence | 447 | 183 | 228 | 1 | 0.4491349 | empty | pass | 0/0 | 706 | 356 | 0.5358529 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b3 | silence | 404 | 164 | 215 | 1 | 0.4477836 | empty | pass | 0/0 | 906 | 444 | 0.5179308 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b1 | silence | 1041 | 441 | 525 | 1 | 0.4494398 | empty | pass | 0/0 | 864 | 428 | 0.5239078 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b2 | silence | 961 | 406 | 479 | 1 | 0.4493564 | empty | pass | 0/0 | 900 | 441 | 0.5179592 |
| btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b3 | silence | 1040 | 441 | 516 | 1 | 0.4498622 | empty | pass | 0/0 | 547 | 280 | 0.5478407 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/up-b1 | silence | 514 | 212 | 266 | 1 | 0.4494479 | empty | pass | 0/0 | 704 | 353 | 0.5330796 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/up-b2 | silence | 547 | 226 | 261 | 1 | 0.4489955 | empty | pass | 0/0 | 752 | 369 | 0.5213304 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/up-b3 | silence | 452 | 185 | 231 | 1 | 0.4488019 | empty | pass | 0/0 | 735 | 348 | 0.5044818 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/down-b1 | silence | 849 | 357 | 421 | 1 | 0.4491239 | empty | reject | 0/0 | 916 | 455 | 0.5244230 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/down-b2 | silence | 960 | 406 | 473 | 1 | 0.4498135 | empty | pass | 0/0 | 686 | 336 | 0.5219067 |
| btc-dir-1h vote4-v1/BTCUSDT/1h/down-b3 | silence | 1046 | 443 | 524 | 1 | 0.4492630 | empty | pass | 0/0 | 599 | 292 | 0.5218979 |
| btc-range-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.199767270602931 | 0.0098280 | pass | reject | 0/0 | 4392 | 29 | 0.0089922 |
| btc-range-1h realized-vol-hw-v1/BTCUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.344699816281276 | 0.0098280 | pass | reject | 0/0 | 4392 | 24 | 0.0076765 |
| btc-range-1h parkinson-hw-v1/BTCUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.9491846042307253 | 0.0098280 | reject | reject | 0/0 | 4392 | 34 | 0.0102932 |
| btc-mae-down-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.591219738629772 | 0.0098280 | reject | reject | 0/0 | 4392 | 27 | 0.0084679 |
| btc-mae-up-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.75836375516501 | 0.0098280 | pass | reject | 0/0 | 4392 | 46 | 0.0133721 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b1 | silence | 186 | 72 | 92 | 1 | 0.4495797 | empty | pass | 0/0 | 238 | 127 | 0.5883636 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b2 | silence | 81 | 28 | 46 | 1 | 0.4420448 | empty | pass | 0/0 | 223 | 99 | 0.5012301 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b3 | silence | 56 | 18 | 28 | 1 | 0.4385116 | empty | pass | 0/0 | 212 | 107 | 0.5632378 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b1 | silence | 187 | 72 | 98 | 1 | 0.4473004 | empty | pass | 0/0 | 86 | 49 | 0.6604740 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b2 | silence | 151 | 57 | 83 | 1 | 0.4470833 | empty | pass | 0/0 | 91 | 40 | 0.5311619 |
| btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b3 | silence | 431 | 176 | 214 | 1 | 0.4488390 | empty | pass | 0/0 | 248 | 128 | 0.5699853 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b1 | silence | 177 | 68 | 89 | 1 | 0.4482745 | empty | pass | 0/0 | 159 | 82 | 0.5834154 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b2 | silence | 143 | 54 | 77 | 1 | 0.4492672 | empty | pass | 0/0 | 211 | 117 | 0.6123062 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b3 | silence | 160 | 61 | 83 | 1 | 0.4488110 | empty | reject | 0/0 | 189 | 95 | 0.5647593 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b1 | silence | 128 | 47 | 74 | 1 | 0.4429762 | empty | pass | 0/0 | 163 | 89 | 0.6121873 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b2 | silence | 165 | 63 | 83 | 1 | 0.4482966 | empty | pass | 0/0 | 199 | 108 | 0.6025371 |
| btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b3 | silence | 319 | 128 | 164 | 1 | 0.4485109 | empty | pass | 0/0 | 177 | 95 | 0.6003779 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b1 | silence | 187 | 72 | 94 | 1 | 0.4473004 | empty | pass | 0/0 | 143 | 68 | 0.5476042 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b2 | silence | 195 | 75 | 94 | 1 | 0.4455213 | empty | pass | 0/0 | 178 | 81 | 0.5194751 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b3 | silence | 233 | 91 | 119 | 1 | 0.4461038 | empty | pass | 0/0 | 197 | 93 | 0.5331394 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b1 | silence | 153 | 58 | 83 | 1 | 0.4482294 | empty | pass | 0/0 | 192 | 102 | 0.5924136 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b2 | silence | 176 | 67 | 95 | 1 | 0.4449088 | empty | pass | 0/0 | 192 | 86 | 0.5098482 |
| btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b3 | silence | 148 | 56 | 66 | 1 | 0.4487404 | empty | pass | 0/0 | 196 | 93 | 0.5356967 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b1 | silence | 71 | 24 | 33 | 1 | 0.4413290 | empty | pass | 0/0 | 104 | 55 | 0.6127248 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b2 | silence | 58 | 19 | 33 | 1 | 0.4426493 | empty | pass | 0/0 | 141 | 62 | 0.5124825 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b3 | silence | 62 | 21 | 33 | 1 | 0.4499952 | empty | pass | 0/0 | 264 | 132 | 0.5523183 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b1 | silence | 335 | 135 | 171 | 1 | 0.4490721 | empty | pass | 0/0 | 318 | 156 | 0.5381708 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b2 | silence | 276 | 110 | 139 | 1 | 0.4494833 | empty | pass | 0/0 | 162 | 78 | 0.5489881 |
| btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b3 | silence | 290 | 116 | 150 | 1 | 0.4496504 | empty | pass | 0/0 | 109 | 63 | 0.6580168 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/up-b1 | silence | 106 | 38 | 46 | 1 | 0.4421314 | empty | pass | 0/0 | 207 | 107 | 0.5759911 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/up-b2 | silence | 90 | 32 | 47 | 1 | 0.4468349 | empty | pass | 0/0 | 199 | 104 | 0.5828148 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/up-b3 | silence | 99 | 35 | 56 | 1 | 0.4401835 | empty | pass | 0/0 | 205 | 93 | 0.5135152 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/down-b1 | silence | 193 | 75 | 100 | 1 | 0.4499013 | empty | pass | 0/0 | 197 | 103 | 0.5833536 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/down-b2 | silence | 227 | 89 | 118 | 1 | 0.4484040 | empty | pass | 0/0 | 163 | 87 | 0.6002117 |
| btc-dir-4h vote4-v1/BTCUSDT/4h/down-b3 | silence | 377 | 153 | 188 | 1 | 0.4492070 | empty | pass | 0/0 | 127 | 60 | 0.5491415 |
| btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 | region | 1092 | 5 | 5 | 5.069855126100256 | 0.0096031 | pass | pass | 0/0 | 1098 | 4 | 0.0083170 |
| btc-range-4h realized-vol-hw-v1/BTCUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.95268689043219 | 0.0096031 | pass | reject | 0/0 | 1098 | 5 | 0.0095507 |
| btc-range-4h parkinson-hw-v1/BTCUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.677117724070616 | 0.0096031 | pass | reject | 0/0 | 1098 | 6 | 0.0107568 |
| btc-mae-down-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 | silence | 1092 | 5 | 5 | 5.475551421312206 | 0.0096031 | pass | reject | 0/0 | 1098 | 1 | 0.0043132 |
| btc-mae-up-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 | silence | 1092 | 5 | 5 | 3.7034681203462334 | 0.0096031 | pass | reject | 0/0 | 1098 | 10 | 0.0153994 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b1 | silence | 669 | 279 | 337 | 1 | 0.4493713 | empty | pass | 0/0 | 804 | 436 | 0.5716612 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b2 | silence | 670 | 279 | 354 | 1 | 0.4487194 | empty | pass | 0/0 | 792 | 384 | 0.5146962 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b3 | silence | 522 | 215 | 258 | 1 | 0.4485751 | empty | pass | 0/0 | 657 | 346 | 0.5593011 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b1 | silence | 580 | 240 | 300 | 1 | 0.4485645 | empty | pass | 0/0 | 793 | 407 | 0.5429940 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b2 | silence | 938 | 396 | 485 | 1 | 0.4493884 | empty | pass | 0/0 | 833 | 447 | 0.5655045 |
| eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b3 | silence | 989 | 418 | 473 | 1 | 0.4491377 | empty | pass | 0/0 | 513 | 268 | 0.5595006 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b1 | silence | 755 | 316 | 381 | 1 | 0.4489358 | empty | pass | 0/0 | 826 | 420 | 0.5376356 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b2 | silence | 737 | 308 | 375 | 1 | 0.4486779 | empty | pass | 0/0 | 794 | 403 | 0.5373134 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b3 | silence | 623 | 259 | 347 | 1 | 0.4492587 | empty | pass | 0/0 | 694 | 362 | 0.5534119 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b1 | silence | 655 | 273 | 353 | 1 | 0.4494767 | empty | reject | 0/0 | 704 | 357 | 0.5387407 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b2 | silence | 641 | 267 | 323 | 1 | 0.4495830 | empty | pass | 0/0 | 620 | 336 | 0.5754546 |
| eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b3 | silence | 957 | 404 | 482 | 1 | 0.4490879 | empty | pass | 0/0 | 754 | 385 | 0.5411480 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b1 | silence | 739 | 309 | 359 | 1 | 0.4488588 | empty | pass | 0/0 | 766 | 379 | 0.5251219 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b2 | silence | 767 | 322 | 365 | 1 | 0.4499738 | empty | pass | 0/0 | 707 | 342 | 0.5153634 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b3 | silence | 729 | 305 | 347 | 1 | 0.4493251 | empty | pass | 0/0 | 635 | 280 | 0.4742958 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b1 | silence | 744 | 312 | 367 | 1 | 0.4499832 | empty | pass | 0/0 | 750 | 368 | 0.5213473 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b2 | silence | 705 | 295 | 330 | 1 | 0.4499209 | empty | pass | 0/0 | 775 | 373 | 0.5114732 |
| eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b3 | silence | 684 | 285 | 308 | 1 | 0.4486282 | empty | pass | 0/0 | 759 | 361 | 0.5061336 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b1 | silence | 577 | 239 | 274 | 1 | 0.4490793 | empty | pass | 0/0 | 538 | 280 | 0.5566549 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b2 | silence | 530 | 219 | 290 | 1 | 0.4496294 | empty | pass | 0/0 | 574 | 289 | 0.5386101 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b3 | silence | 541 | 223 | 279 | 1 | 0.4482289 | empty | pass | 0/0 | 671 | 352 | 0.5569198 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b1 | silence | 787 | 330 | 411 | 1 | 0.4490709 | empty | pass | 0/0 | 618 | 315 | 0.5435076 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b2 | silence | 906 | 382 | 443 | 1 | 0.4493320 | empty | pass | 0/0 | 769 | 396 | 0.5451688 |
| eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b3 | silence | 1027 | 435 | 512 | 1 | 0.4495515 | empty | pass | 0/0 | 1222 | 635 | 0.5435041 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/up-b1 | silence | 688 | 287 | 340 | 1 | 0.4490206 | empty | pass | 0/0 | 732 | 364 | 0.5283159 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/up-b2 | silence | 574 | 238 | 288 | 1 | 0.4495993 | empty | pass | 0/0 | 558 | 281 | 0.5392202 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/up-b3 | silence | 421 | 172 | 210 | 1 | 0.4495348 | empty | pass | 0/0 | 613 | 322 | 0.5591326 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/down-b1 | silence | 881 | 371 | 450 | 1 | 0.4492076 | empty | pass | 0/0 | 875 | 455 | 0.5482715 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/down-b2 | silence | 987 | 417 | 472 | 1 | 0.4490075 | empty | pass | 0/0 | 822 | 413 | 0.5316861 |
| eth-dir-1h vote4-v1/ETHUSDT/1h/down-b3 | silence | 817 | 343 | 403 | 1 | 0.4490233 | empty | pass | 0/0 | 792 | 405 | 0.5411438 |
| eth-range-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.229512612478789 | 0.0098280 | pass | reject | 0/0 | 4392 | 37 | 0.0110681 |
| eth-range-1h realized-vol-hw-v1/ETHUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.029607424541976 | 0.0098280 | pass | reject | 0/0 | 4392 | 46 | 0.0133721 |
| eth-range-1h parkinson-hw-v1/ETHUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.908965962182538 | 0.0098280 | pass | reject | 0/0 | 4392 | 40 | 0.0118392 |
| eth-mae-down-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.446185274924918 | 0.0098280 | pass | reject | 0/0 | 4392 | 37 | 0.0110681 |
| eth-mae-up-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.045013680093748 | 0.0098280 | pass | reject | 0/0 | 4392 | 51 | 0.0146411 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b1 | silence | 251 | 99 | 127 | 1 | 0.4478948 | empty | pass | 0/0 | 255 | 127 | 0.5513160 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b2 | silence | 98 | 35 | 48 | 1 | 0.4443601 | empty | pass | 0/0 | 290 | 134 | 0.5120737 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b3 | silence | 20 | 4 | 12 | 1 | 0.4010282 | empty | pass | 0/0 | 149 | 77 | 0.5867535 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b1 | silence | 179 | 69 | 91 | 1 | 0.4492101 | empty | pass | 0/0 | 150 | 79 | 0.5961955 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b2 | silence | 267 | 106 | 136 | 1 | 0.4488073 | empty | pass | 0/0 | 65 | 28 | 0.5402704 |
| eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b3 | silence | 277 | 110 | 148 | 1 | 0.4479304 | empty | pass | 0/0 | 189 | 92 | 0.5490546 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b1 | silence | 154 | 58 | 72 | 1 | 0.4454842 | empty | pass | 0/0 | 187 | 92 | 0.5545551 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b2 | silence | 186 | 72 | 96 | 1 | 0.4495797 | empty | reject | 0/0 | 255 | 149 | 0.6361045 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b3 | silence | 142 | 53 | 72 | 1 | 0.4450686 | empty | pass | 0/0 | 127 | 60 | 0.5491415 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b1 | silence | 171 | 65 | 88 | 1 | 0.4453210 | empty | pass | 0/0 | 183 | 88 | 0.5442538 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b2 | silence | 188 | 72 | 92 | 1 | 0.4450439 | empty | pass | 0/0 | 228 | 130 | 0.6253714 |
| eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b3 | silence | 251 | 99 | 135 | 1 | 0.4478948 | empty | pass | 0/0 | 118 | 69 | 0.6613209 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b1 | silence | 163 | 62 | 90 | 1 | 0.4472522 | empty | pass | 0/0 | 190 | 94 | 0.5567727 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b2 | silence | 203 | 79 | 91 | 1 | 0.4488615 | empty | pass | 0/0 | 161 | 69 | 0.4964219 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b3 | silence | 220 | 86 | 106 | 1 | 0.4481605 | empty | pass | 0/0 | 178 | 76 | 0.4913326 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b1 | silence | 168 | 64 | 91 | 1 | 0.4467848 | empty | pass | 0/0 | 211 | 106 | 0.5610599 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b2 | silence | 178 | 68 | 88 | 1 | 0.4458897 | empty | pass | 0/0 | 195 | 87 | 0.5075857 |
| eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b3 | silence | 160 | 61 | 79 | 1 | 0.4488110 | empty | pass | 0/0 | 163 | 73 | 0.5153049 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b1 | silence | 125 | 46 | 60 | 1 | 0.4447731 | empty | pass | 0/0 | 85 | 41 | 0.5767458 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b2 | silence | 113 | 41 | 49 | 1 | 0.4437500 | empty | pass | 0/0 | 82 | 46 | 0.6543576 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b3 | silence | 94 | 33 | 51 | 1 | 0.4401046 | empty | pass | 0/0 | 160 | 75 | 0.5367904 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b1 | silence | 207 | 80 | 97 | 1 | 0.4455214 | empty | pass | 0/0 | 218 | 107 | 0.5486472 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b2 | silence | 229 | 90 | 117 | 1 | 0.4491009 | empty | pass | 0/0 | 260 | 123 | 0.5259649 |
| eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b3 | silence | 324 | 130 | 171 | 1 | 0.4481100 | empty | pass | 0/0 | 293 | 161 | 0.5984672 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/up-b1 | silence | 181 | 69 | 85 | 1 | 0.4445073 | empty | pass | 0/0 | 220 | 122 | 0.6111290 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/up-b2 | silence | 134 | 50 | 68 | 1 | 0.4472144 | empty | reject | 0/0 | 154 | 63 | 0.4784078 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/up-b3 | silence | 46 | 14 | 24 | 1 | 0.4342212 | empty | pass | 0/0 | 151 | 70 | 0.5337273 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/down-b1 | silence | 225 | 88 | 105 | 1 | 0.4476934 | empty | pass | 0/0 | 250 | 124 | 0.5498395 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/down-b2 | silence | 234 | 92 | 123 | 1 | 0.4486201 | empty | pass | 0/0 | 170 | 89 | 0.5887883 |
| eth-dir-4h vote4-v1/ETHUSDT/4h/down-b3 | silence | 272 | 108 | 145 | 1 | 0.4483629 | empty | pass | 0/0 | 153 | 72 | 0.5402178 |
| eth-range-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.59305635024895 | 0.0096031 | pass | reject | 0/0 | 1098 | 4 | 0.0083170 |
| eth-range-4h realized-vol-hw-v1/ETHUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.154282494942086 | 0.0096031 | reject | reject | 0/0 | 1098 | 6 | 0.0107568 |
| eth-range-4h parkinson-hw-v1/ETHUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.270402233999815 | 0.0096031 | reject | reject | 0/0 | 1098 | 3 | 0.0070464 |
| eth-mae-down-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 | silence | 1092 | 5 | 5 | 5.086148810226193 | 0.0096031 | reject | reject | 0/0 | 1098 | 4 | 0.0083170 |
| eth-mae-up-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.006804065665244 | 0.0096031 | pass | reject | 0/0 | 1098 | 10 | 0.0153994 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b1 | silence | 470 | 193 | 226 | 1 | 0.4493700 | empty | pass | 0/0 | 673 | 343 | 0.5420201 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b2 | silence | 835 | 351 | 418 | 1 | 0.4492328 | empty | pass | 0/0 | 910 | 444 | 0.5157169 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b3 | silence | 581 | 241 | 304 | 1 | 0.4495507 | empty | pass | 0/0 | 810 | 406 | 0.5307109 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b1 | silence | 549 | 227 | 272 | 1 | 0.4492471 | empty | pass | 0/0 | 599 | 311 | 0.5534868 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b2 | silence | 679 | 283 | 357 | 1 | 0.4488727 | empty | pass | 0/0 | 659 | 354 | 0.5697137 |
| bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b3 | silence | 1254 | 534 | 626 | 1 | 0.4493154 | empty | pass | 0/0 | 741 | 404 | 0.5757996 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b1 | silence | 730 | 305 | 360 | 1 | 0.4487261 | empty | pass | 0/0 | 769 | 377 | 0.5205395 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b2 | silence | 706 | 295 | 371 | 1 | 0.4493010 | empty | pass | 0/0 | 808 | 402 | 0.5270481 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b3 | silence | 666 | 278 | 344 | 1 | 0.4498260 | empty | pass | 0/0 | 772 | 383 | 0.5263344 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b1 | silence | 640 | 266 | 320 | 1 | 0.4486910 | empty | pass | 0/0 | 602 | 311 | 0.5508279 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b2 | silence | 654 | 272 | 336 | 1 | 0.4486040 | empty | pass | 0/0 | 652 | 332 | 0.5420934 |
| bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b3 | silence | 971 | 410 | 508 | 1 | 0.4489815 | empty | pass | 0/0 | 786 | 435 | 0.5830534 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b1 | silence | 683 | 285 | 364 | 1 | 0.4492668 | empty | pass | 0/0 | 657 | 308 | 0.5016389 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b2 | silence | 765 | 321 | 363 | 1 | 0.4498032 | empty | pass | 0/0 | 773 | 361 | 0.4972312 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b3 | silence | 757 | 317 | 349 | 1 | 0.4491113 | empty | pass | 0/0 | 652 | 295 | 0.4853961 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b1 | silence | 762 | 319 | 378 | 1 | 0.4488849 | empty | pass | 0/0 | 748 | 386 | 0.5466806 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b2 | silence | 730 | 305 | 380 | 1 | 0.4487261 | empty | reject | 0/0 | 774 | 396 | 0.5417574 |
| bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b3 | silence | 671 | 280 | 307 | 1 | 0.4495708 | empty | pass | 0/0 | 788 | 368 | 0.4969293 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b1 | silence | 900 | 379 | 448 | 1 | 0.4489007 | empty | pass | 0/0 | 621 | 286 | 0.4943407 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b2 | silence | 743 | 311 | 372 | 1 | 0.4492175 | empty | pass | 0/0 | 536 | 254 | 0.5103309 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b3 | silence | 409 | 167 | 230 | 1 | 0.4499133 | empty | pass | 0/0 | 516 | 268 | 0.5563754 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b1 | silence | 789 | 331 | 419 | 1 | 0.4492381 | empty | pass | 0/0 | 527 | 238 | 0.4883552 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b2 | silence | 748 | 313 | 376 | 1 | 0.4489871 | empty | pass | 0/0 | 706 | 364 | 0.5471353 |
| bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b3 | silence | 779 | 327 | 395 | 1 | 0.4496856 | empty | pass | 0/0 | 1486 | 802 | 0.5612359 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b1 | silence | 872 | 367 | 442 | 1 | 0.4491135 | empty | pass | 0/0 | 725 | 363 | 0.5318804 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b2 | silence | 687 | 287 | 351 | 1 | 0.4496560 | empty | pass | 0/0 | 720 | 359 | 0.5299183 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b3 | silence | 459 | 188 | 238 | 1 | 0.4487856 | empty | pass | 0/0 | 509 | 243 | 0.5148328 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b1 | silence | 658 | 274 | 351 | 1 | 0.4490166 | empty | pass | 0/0 | 676 | 365 | 0.5720361 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b2 | silence | 783 | 328 | 409 | 1 | 0.4487339 | empty | pass | 0/0 | 752 | 380 | 0.5359189 |
| bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b3 | silence | 908 | 383 | 445 | 1 | 0.4494744 | empty | pass | 0/0 | 1007 | 532 | 0.5545875 |
| bnb-range-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.7923899198767668 | 0.0098280 | pass | reject | 0/0 | 4392 | 38 | 0.0113255 |
| bnb-range-1h realized-vol-hw-v1/BNBUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.7703729033189495 | 0.0098280 | pass | reject | 0/0 | 4392 | 44 | 0.0128624 |
| bnb-range-1h parkinson-hw-v1/BNBUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.5071815936799164 | 0.0098280 | reject | reject | 0/0 | 4392 | 55 | 0.0156517 |
| bnb-mae-down-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 | region | 4368 | 32 | 32 | 4.464607917356067 | 0.0098280 | pass | pass | 0/0 | 4392 | 31 | 0.0095142 |
| bnb-mae-up-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 | vetoed | 4368 | 32 | 32 | 3.312435313799688 | 0.0098280 | pass | pass | 0/0 | 4392 | 66 | 0.0184129 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b1 | silence | 137 | 51 | 74 | 1 | 0.4454567 | empty | pass | 0/0 | 177 | 94 | 0.5948468 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b2 | silence | 99 | 35 | 49 | 1 | 0.4401835 | empty | pass | 0/0 | 185 | 87 | 0.5333604 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b3 | silence | 146 | 55 | 67 | 1 | 0.4475541 | empty | pass | 0/0 | 314 | 151 | 0.5288503 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b1 | silence | 133 | 49 | 70 | 1 | 0.4427009 | empty | pass | 0/0 | 140 | 77 | 0.6214173 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b2 | silence | 121 | 44 | 52 | 1 | 0.4416596 | empty | pass | 0/0 | 85 | 41 | 0.5767458 |
| bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b3 | silence | 456 | 187 | 231 | 1 | 0.4494251 | empty | pass | 0/0 | 197 | 103 | 0.5833536 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b1 | silence | 185 | 71 | 100 | 1 | 0.4463917 | empty | pass | 0/0 | 233 | 117 | 0.5579164 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b2 | silence | 192 | 74 | 91 | 1 | 0.4468356 | empty | pass | 0/0 | 232 | 111 | 0.5345211 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b3 | silence | 127 | 47 | 66 | 1 | 0.4462471 | empty | pass | 0/0 | 153 | 84 | 0.6172925 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b1 | silence | 131 | 49 | 66 | 1 | 0.4490434 | empty | pass | 0/0 | 127 | 74 | 0.6565349 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b2 | silence | 170 | 65 | 78 | 1 | 0.4477982 | empty | pass | 0/0 | 152 | 78 | 0.5824860 |
| bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b3 | silence | 287 | 114 | 154 | 1 | 0.4470992 | empty | pass | 0/0 | 201 | 107 | 0.5920618 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b1 | silence | 143 | 54 | 75 | 1 | 0.4492672 | empty | pass | 0/0 | 134 | 54 | 0.4775204 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b2 | silence | 173 | 66 | 87 | 1 | 0.4463309 | empty | pass | 0/0 | 164 | 76 | 0.5306143 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b3 | silence | 256 | 101 | 118 | 1 | 0.4474556 | empty | pass | 0/0 | 201 | 94 | 0.5281056 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b1 | silence | 187 | 72 | 97 | 1 | 0.4473004 | empty | pass | 0/0 | 210 | 103 | 0.5494273 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b2 | silence | 172 | 66 | 78 | 1 | 0.4487853 | empty | pass | 0/0 | 193 | 102 | 0.5895495 |
| bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b3 | silence | 161 | 61 | 78 | 1 | 0.4461787 | empty | pass | 0/0 | 196 | 86 | 0.5000289 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b1 | silence | 241 | 95 | 119 | 1 | 0.4488118 | empty | pass | 0/0 | 166 | 74 | 0.5125963 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b2 | silence | 206 | 80 | 98 | 1 | 0.4475770 | empty | pass | 0/0 | 145 | 70 | 0.5542481 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b3 | silence | 43 | 13 | 24 | 1 | 0.4371153 | empty | pass | 0/0 | 70 | 37 | 0.6314142 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b1 | silence | 179 | 69 | 87 | 1 | 0.4492101 | empty | pass | 0/0 | 119 | 66 | 0.6320727 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b2 | silence | 179 | 69 | 78 | 1 | 0.4492101 | empty | pass | 0/0 | 159 | 78 | 0.5586344 |
| bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b3 | silence | 244 | 96 | 131 | 1 | 0.4477003 | empty | pass | 0/0 | 439 | 221 | 0.5437018 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b1 | silence | 172 | 66 | 85 | 1 | 0.4487853 | empty | pass | 0/0 | 190 | 101 | 0.5930656 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b2 | silence | 154 | 58 | 68 | 1 | 0.4454842 | empty | pass | 0/0 | 194 | 88 | 0.5152065 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b3 | silence | 109 | 40 | 57 | 1 | 0.4495640 | empty | pass | 0/0 | 142 | 66 | 0.5372150 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b1 | silence | 148 | 56 | 69 | 1 | 0.4487404 | empty | pass | 0/0 | 119 | 58 | 0.5665450 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b2 | silence | 184 | 71 | 93 | 1 | 0.4486907 | empty | pass | 0/0 | 133 | 72 | 0.6149283 |
| bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b3 | silence | 325 | 131 | 158 | 1 | 0.4498979 | empty | pass | 0/0 | 320 | 164 | 0.5597933 |
| bnb-range-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.062664001748883 | 0.0096031 | pass | reject | 0/0 | 1098 | 6 | 0.0107568 |
| bnb-range-4h realized-vol-hw-v1/BNBUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.103362675405421 | 0.0096031 | reject | reject | 0/0 | 1098 | 8 | 0.0131079 |
| bnb-range-4h parkinson-hw-v1/BNBUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.43822001614557 | 0.0096031 | reject | reject | 0/0 | 1098 | 8 | 0.0131079 |
| bnb-mae-down-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.885243134005842 | 0.0096031 | pass | reject | 0/0 | 1098 | 3 | 0.0070464 |
| bnb-mae-up-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.020849361303885 | 0.0096031 | pass | reject | 0/0 | 1098 | 11 | 0.0165281 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b1 | silence | 759 | 318 | 404 | 1 | 0.4492857 | empty | pass | 0/0 | 784 | 409 | 0.5515692 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b2 | silence | 685 | 286 | 357 | 1 | 0.4494620 | empty | pass | 0/0 | 705 | 362 | 0.5450628 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b3 | silence | 358 | 145 | 186 | 1 | 0.4495719 | empty | pass | 0/0 | 759 | 377 | 0.5271878 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b1 | silence | 674 | 281 | 354 | 1 | 0.4491204 | empty | pass | 0/0 | 827 | 427 | 0.5454353 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b2 | silence | 808 | 339 | 418 | 1 | 0.4489137 | empty | pass | 0/0 | 760 | 408 | 0.5671072 |
| sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b3 | silence | 1084 | 460 | 554 | 1 | 0.4496382 | empty | pass | 0/0 | 557 | 296 | 0.5669092 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b1 | silence | 789 | 331 | 405 | 1 | 0.4492381 | empty | pass | 0/0 | 821 | 421 | 0.5420238 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b2 | silence | 686 | 286 | 363 | 1 | 0.4488250 | empty | pass | 0/0 | 785 | 398 | 0.5369382 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b3 | silence | 554 | 229 | 302 | 1 | 0.4489575 | empty | pass | 0/0 | 717 | 370 | 0.5473440 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b1 | silence | 706 | 295 | 381 | 1 | 0.4493010 | empty | pass | 0/0 | 653 | 335 | 0.5458638 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b2 | silence | 692 | 289 | 347 | 1 | 0.4494081 | empty | reject | 0/0 | 649 | 338 | 0.5537079 |
| sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b3 | silence | 936 | 395 | 498 | 1 | 0.4492508 | empty | pass | 0/0 | 761 | 426 | 0.5898360 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b1 | silence | 764 | 320 | 393 | 1 | 0.4490587 | empty | pass | 0/0 | 739 | 378 | 0.5423501 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b2 | silence | 812 | 341 | 384 | 1 | 0.4492383 | empty | pass | 0/0 | 753 | 365 | 0.5153545 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b3 | silence | 758 | 318 | 366 | 1 | 0.4498628 | empty | pass | 0/0 | 643 | 280 | 0.4685706 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b1 | silence | 703 | 294 | 347 | 1 | 0.4497332 | empty | pass | 0/0 | 747 | 367 | 0.5220407 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b2 | silence | 693 | 289 | 338 | 1 | 0.4487775 | empty | pass | 0/0 | 765 | 389 | 0.5388188 |
| sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b3 | silence | 637 | 265 | 300 | 1 | 0.4491616 | empty | pass | 0/0 | 745 | 358 | 0.5113347 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b1 | silence | 684 | 285 | 329 | 1 | 0.4486282 | empty | pass | 0/0 | 664 | 325 | 0.5221081 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b2 | silence | 629 | 262 | 321 | 1 | 0.4499036 | empty | pass | 0/0 | 682 | 332 | 0.5190156 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b3 | silence | 448 | 183 | 226 | 1 | 0.4481666 | empty | pass | 0/0 | 1125 | 552 | 0.5156240 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b1 | silence | 888 | 374 | 435 | 1 | 0.4491530 | empty | pass | 0/0 | 738 | 386 | 0.5538463 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b2 | silence | 842 | 354 | 420 | 1 | 0.4491782 | empty | pass | 0/0 | 599 | 306 | 0.5451870 |
| sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b3 | silence | 877 | 369 | 443 | 1 | 0.4489111 | empty | pass | 0/0 | 584 | 284 | 0.5211717 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/up-b1 | silence | 822 | 345 | 435 | 1 | 0.4488106 | empty | pass | 0/0 | 767 | 356 | 0.4944827 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/up-b2 | silence | 610 | 253 | 310 | 1 | 0.4486410 | empty | pass | 0/0 | 725 | 384 | 0.5607046 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/up-b3 | silence | 348 | 140 | 170 | 1 | 0.4474743 | empty | pass | 0/0 | 894 | 431 | 0.5101647 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/down-b1 | silence | 874 | 368 | 448 | 1 | 0.4492626 | empty | pass | 0/0 | 828 | 433 | 0.5520078 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/down-b2 | silence | 885 | 373 | 453 | 1 | 0.4495012 | empty | pass | 0/0 | 602 | 287 | 0.5110887 |
| sol-dir-1h vote4-v1/SOLUSDT/1h/down-b3 | silence | 823 | 346 | 414 | 1 | 0.4495022 | empty | pass | 0/0 | 570 | 297 | 0.5562066 |
| sol-range-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.7438797665447856 | 0.0098280 | pass | reject | 0/0 | 4392 | 51 | 0.0146411 |
| sol-range-1h realized-vol-hw-v1/SOLUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.7226027740994674 | 0.0098280 | pass | reject | 0/0 | 4392 | 47 | 0.0136264 |
| sol-range-1h parkinson-hw-v1/SOLUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.7096224776088467 | 0.0098280 | reject | reject | 0/0 | 4392 | 43 | 0.0126071 |
| sol-mae-down-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 | silence | 4368 | 32 | 32 | 4.451389834082856 | 0.0098280 | pass | reject | 0/0 | 4392 | 34 | 0.0102932 |
| sol-mae-up-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 | silence | 4368 | 32 | 32 | 3.6592071553632555 | 0.0098280 | pass | reject | 0/0 | 4392 | 62 | 0.0174116 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b1 | silence | 156 | 59 | 87 | 1 | 0.4466250 | empty | pass | 0/0 | 292 | 153 | 0.5734114 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b2 | silence | 120 | 44 | 57 | 1 | 0.4451052 | empty | pass | 0/0 | 87 | 51 | 0.6755020 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b3 | silence | 20 | 4 | 12 | 1 | 0.4010282 | empty | pass | 0/0 | 234 | 119 | 0.5641263 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b1 | silence | 238 | 94 | 122 | 1 | 0.4499491 | empty | pass | 0/0 | 283 | 149 | 0.5767071 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b2 | silence | 221 | 86 | 100 | 1 | 0.4462296 | empty | pass | 0/0 | 118 | 55 | 0.5458603 |
| sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b3 | silence | 337 | 136 | 182 | 1 | 0.4495116 | empty | pass | 0/0 | 84 | 39 | 0.5595842 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b1 | silence | 212 | 83 | 110 | 1 | 0.4498951 | empty | reject | 0/0 | 213 | 97 | 0.5140760 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b2 | silence | 155 | 59 | 92 | 1 | 0.4493423 | empty | pass | 0/0 | 169 | 103 | 0.6723326 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b3 | silence | 104 | 37 | 53 | 1 | 0.4402033 | empty | pass | 0/0 | 184 | 97 | 0.5897656 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b1 | silence | 169 | 64 | 92 | 1 | 0.4442845 | empty | pass | 0/0 | 187 | 91 | 0.5492580 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b2 | silence | 219 | 85 | 107 | 1 | 0.4454756 | empty | pass | 0/0 | 202 | 105 | 0.5795877 |
| sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b3 | silence | 233 | 91 | 128 | 1 | 0.4461038 | empty | pass | 0/0 | 135 | 61 | 0.5262774 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b1 | silence | 189 | 73 | 90 | 1 | 0.4481878 | empty | pass | 0/0 | 174 | 87 | 0.5648554 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b2 | silence | 202 | 78 | 94 | 1 | 0.4459467 | empty | pass | 0/0 | 157 | 83 | 0.5965373 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b3 | silence | 223 | 87 | 105 | 1 | 0.4469688 | empty | pass | 0/0 | 181 | 92 | 0.5717247 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b1 | silence | 176 | 67 | 83 | 1 | 0.4449088 | empty | pass | 0/0 | 210 | 109 | 0.5776638 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b2 | silence | 176 | 67 | 81 | 1 | 0.4449088 | empty | pass | 0/0 | 208 | 103 | 0.5543923 |
| sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b3 | silence | 126 | 47 | 54 | 1 | 0.4495661 | empty | pass | 0/0 | 168 | 73 | 0.5009010 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b1 | silence | 165 | 63 | 91 | 1 | 0.4482966 | empty | pass | 0/0 | 161 | 78 | 0.5521671 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b2 | silence | 138 | 52 | 69 | 1 | 0.4498104 | empty | pass | 0/0 | 195 | 98 | 0.5636861 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b3 | silence | 104 | 37 | 40 | 1 | 0.4402033 | empty | pass | 0/0 | 384 | 206 | 0.5793001 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b1 | silence | 178 | 68 | 95 | 1 | 0.4458897 | empty | pass | 0/0 | 126 | 67 | 0.6076632 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b2 | silence | 260 | 103 | 124 | 1 | 0.4486716 | empty | pass | 0/0 | 111 | 50 | 0.5329160 |
| sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b3 | silence | 247 | 97 | 118 | 1 | 0.4466139 | empty | pass | 0/0 | 121 | 55 | 0.5333465 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/up-b1 | silence | 171 | 65 | 86 | 1 | 0.4453210 | empty | pass | 0/0 | 194 | 100 | 0.5765720 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/up-b2 | silence | 122 | 45 | 62 | 1 | 0.4466473 | empty | pass | 0/0 | 190 | 105 | 0.6136595 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/up-b3 | vetoed | 41 | 12 | 12 | 0 | 0.4306517 | pass | pass | 0/0 | 235 | 119 | 0.5618646 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/down-b1 | silence | 204 | 79 | 99 | 1 | 0.4467707 | empty | pass | 0/0 | 194 | 97 | 0.5613146 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/down-b2 | silence | 282 | 112 | 131 | 1 | 0.4475094 | empty | pass | 0/0 | 175 | 90 | 0.5787412 |
| sol-dir-4h vote4-v1/SOLUSDT/4h/down-b3 | silence | 272 | 108 | 140 | 1 | 0.4483629 | empty | pass | 0/0 | 102 | 45 | 0.5274282 |
| sol-range-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.153174393729102 | 0.0096031 | pass | reject | 0/0 | 1098 | 5 | 0.0095507 |
| sol-range-4h realized-vol-hw-v1/SOLUSDT/4h/b0 | silence | 1092 | 5 | 5 | 3.7313789139258695 | 0.0096031 | reject | reject | 0/0 | 1098 | 9 | 0.0142599 |
| sol-range-4h parkinson-hw-v1/SOLUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.358740650959539 | 0.0096031 | reject | reject | 0/0 | 1098 | 5 | 0.0095507 |
| sol-mae-down-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 | silence | 1092 | 5 | 5 | 4.600003361506995 | 0.0096031 | reject | pass | 0/0 | 1098 | 3 | 0.0070464 |
| sol-mae-up-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 | silence | 1092 | 5 | 5 | 3.571106460624201 | 0.0096031 | pass | reject | 0/0 | 1098 | 14 | 0.0198615 |

TEST by UTC month (n/k per month):

- btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b1: 2026-04 165/82, 2026-05 111/58, 2026-06 81/47, 2026-07 136/72, 2026-08 57/31, 2026-09 126/61
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b2: 2026-04 200/100, 2026-05 102/55, 2026-06 70/37, 2026-07 196/92, 2026-08 150/75, 2026-09 95/44
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b3: 2026-04 161/77, 2026-05 89/38, 2026-06 63/35, 2026-07 134/66, 2026-08 243/118, 2026-09 145/68
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b1: 2026-04 81/40, 2026-05 149/76, 2026-06 88/44, 2026-07 132/64, 2026-08 55/25, 2026-09 150/67
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b2: 2026-04 103/54, 2026-05 76/40, 2026-06 139/59, 2026-07 85/50, 2026-08 88/50, 2026-09 138/68
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b3: 2026-04 10/7, 2026-05 217/109, 2026-06 279/135, 2026-07 61/32, 2026-08 151/81, 2026-09 66/35
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b1: 2026-04 109/44, 2026-05 145/70, 2026-06 106/55, 2026-07 107/51, 2026-08 141/75, 2026-09 131/73
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b2: 2026-04 128/72, 2026-05 144/74, 2026-06 126/71, 2026-07 148/66, 2026-08 163/78, 2026-09 110/56
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b3: 2026-04 147/78, 2026-05 112/54, 2026-06 77/45, 2026-07 173/92, 2026-08 145/73, 2026-09 120/55
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b1: 2026-04 121/62, 2026-05 97/52, 2026-06 100/43, 2026-07 92/48, 2026-08 103/58, 2026-09 91/48
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b2: 2026-04 119/60, 2026-05 76/39, 2026-06 143/63, 2026-07 100/50, 2026-08 96/55, 2026-09 145/70
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b3: 2026-04 96/56, 2026-05 170/82, 2026-06 168/89, 2026-07 124/65, 2026-08 96/46, 2026-09 123/68
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b1: 2026-04 107/58, 2026-05 114/56, 2026-06 117/67, 2026-07 107/49, 2026-08 117/57, 2026-09 132/60
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b2: 2026-04 139/63, 2026-05 128/65, 2026-06 144/68, 2026-07 106/59, 2026-08 102/45, 2026-09 113/57
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b3: 2026-04 92/33, 2026-05 118/52, 2026-06 139/67, 2026-07 107/47, 2026-08 88/39, 2026-09 115/52
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b1: 2026-04 118/59, 2026-05 132/68, 2026-06 121/56, 2026-07 127/65, 2026-08 141/75, 2026-09 128/59
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b2: 2026-04 128/66, 2026-05 131/58, 2026-06 106/45, 2026-07 147/80, 2026-08 148/69, 2026-09 106/52
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b3: 2026-04 136/59, 2026-05 121/63, 2026-06 93/34, 2026-07 150/72, 2026-08 148/72, 2026-09 126/61
- btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b1: 2026-04 119/58, 2026-05 80/35, 2026-06 54/35, 2026-07 47/22, 2026-08 120/55, 2026-09 49/21
- btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b2: 2026-04 154/76, 2026-05 95/44, 2026-06 78/44, 2026-07 121/64, 2026-08 169/87, 2026-09 89/41
- btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b3: 2026-04 136/71, 2026-05 214/106, 2026-06 73/36, 2026-07 150/66, 2026-08 178/90, 2026-09 155/75
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b1: 2026-04 164/88, 2026-05 109/56, 2026-06 188/79, 2026-07 149/78, 2026-08 123/68, 2026-09 131/59
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b2: 2026-04 100/55, 2026-05 173/82, 2026-06 216/107, 2026-07 157/75, 2026-08 115/60, 2026-09 139/62
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b3: 2026-04 47/21, 2026-05 73/34, 2026-06 111/57, 2026-07 120/63, 2026-08 39/19, 2026-09 157/86
- btc-dir-1h vote4-v1/BTCUSDT/1h/up-b1: 2026-04 117/62, 2026-05 130/62, 2026-06 108/60, 2026-07 107/54, 2026-08 153/72, 2026-09 89/43
- btc-dir-1h vote4-v1/BTCUSDT/1h/up-b2: 2026-04 184/90, 2026-05 137/69, 2026-06 76/37, 2026-07 134/65, 2026-08 139/69, 2026-09 82/39
- btc-dir-1h vote4-v1/BTCUSDT/1h/up-b3: 2026-04 143/66, 2026-05 107/50, 2026-06 44/23, 2026-07 139/68, 2026-08 169/79, 2026-09 133/62
- btc-dir-1h vote4-v1/BTCUSDT/1h/down-b1: 2026-04 137/75, 2026-05 118/63, 2026-06 156/67, 2026-07 137/73, 2026-08 170/78, 2026-09 198/99
- btc-dir-1h vote4-v1/BTCUSDT/1h/down-b2: 2026-04 106/52, 2026-05 126/61, 2026-06 145/64, 2026-07 121/63, 2026-08 65/35, 2026-09 123/61
- btc-dir-1h vote4-v1/BTCUSDT/1h/down-b3: 2026-04 33/15, 2026-05 126/59, 2026-06 191/94, 2026-07 106/53, 2026-08 48/28, 2026-09 95/43
- btc-range-1h ewma-vol-hw-v1/BTCUSDT/1h/b0: 2026-04 720/6, 2026-05 744/5, 2026-06 720/4, 2026-07 744/4, 2026-08 744/4, 2026-09 720/6
- btc-range-1h realized-vol-hw-v1/BTCUSDT/1h/b0: 2026-04 720/7, 2026-05 744/5, 2026-06 720/2, 2026-07 744/2, 2026-08 744/2, 2026-09 720/6
- btc-range-1h parkinson-hw-v1/BTCUSDT/1h/b0: 2026-04 720/6, 2026-05 744/6, 2026-06 720/5, 2026-07 744/4, 2026-08 744/5, 2026-09 720/8
- btc-mae-down-1h ewma-vol-hw-v1/BTCUSDT/1h/b0: 2026-04 720/4, 2026-05 744/5, 2026-06 720/3, 2026-07 744/6, 2026-08 744/3, 2026-09 720/6
- btc-mae-up-1h ewma-vol-hw-v1/BTCUSDT/1h/b0: 2026-04 720/12, 2026-05 744/8, 2026-06 720/5, 2026-07 744/4, 2026-08 744/10, 2026-09 720/7
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b1: 2026-04 26/14, 2026-05 24/16, 2026-07 113/59, 2026-08 34/18, 2026-09 41/20
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b2: 2026-04 68/31, 2026-05 48/23, 2026-07 43/20, 2026-08 20/7, 2026-09 44/18
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b3: 2026-04 49/26, 2026-05 23/10, 2026-08 61/29, 2026-09 79/42
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b1: 2026-04 7/2, 2026-05 7/3, 2026-06 11/4, 2026-07 14/9, 2026-08 31/19, 2026-09 16/12
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b2: 2026-04 19/10, 2026-05 30/10, 2026-06 13/4, 2026-07 6/3, 2026-08 23/13
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b3: 2026-04 11/8, 2026-05 54/34, 2026-06 156/71, 2026-07 10/5, 2026-08 17/10
- btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b1: 2026-04 31/15, 2026-05 27/14, 2026-06 31/15, 2026-07 48/28, 2026-08 10/3, 2026-09 12/7
- btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b2: 2026-04 55/29, 2026-05 27/19, 2026-06 17/12, 2026-07 39/17, 2026-08 40/22, 2026-09 33/18
- btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b3: 2026-04 40/26, 2026-05 19/10, 2026-06 16/8, 2026-07 29/14, 2026-08 56/24, 2026-09 29/13
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b1: 2026-04 27/18, 2026-05 33/16, 2026-06 22/10, 2026-07 30/15, 2026-08 18/10, 2026-09 33/20
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b2: 2026-04 23/15, 2026-05 40/21, 2026-06 31/11, 2026-07 20/10, 2026-08 41/24, 2026-09 44/27
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b3: 2026-04 4/3, 2026-05 40/26, 2026-06 63/29, 2026-07 20/12, 2026-08 21/12, 2026-09 29/13
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b1: 2026-04 25/12, 2026-05 17/8, 2026-06 26/12, 2026-07 24/11, 2026-08 19/9, 2026-09 32/16
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b2: 2026-04 28/10, 2026-05 34/19, 2026-06 30/15, 2026-07 21/9, 2026-08 26/10, 2026-09 39/18
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/up-b3: 2026-04 16/5, 2026-05 39/17, 2026-06 55/34, 2026-07 30/14, 2026-08 24/10, 2026-09 33/13
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b1: 2026-04 33/17, 2026-05 38/21, 2026-06 22/8, 2026-07 33/21, 2026-08 35/19, 2026-09 31/16
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b2: 2026-04 39/16, 2026-05 33/17, 2026-06 26/10, 2026-07 46/19, 2026-08 32/16, 2026-09 16/8
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b3: 2026-04 39/17, 2026-05 25/9, 2026-06 21/11, 2026-07 32/13, 2026-08 50/28, 2026-09 29/15
- btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b1: 2026-04 30/14, 2026-05 28/17, 2026-06 7/3, 2026-07 14/8, 2026-08 19/9, 2026-09 6/4
- btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b2: 2026-04 40/18, 2026-05 34/13, 2026-06 10/5, 2026-07 15/9, 2026-08 24/9, 2026-09 18/8
- btc-dir-4h takerflow-v1/BTCUSDT/4h/up-b3: 2026-04 40/25, 2026-05 38/21, 2026-06 17/12, 2026-07 21/11, 2026-08 89/38, 2026-09 59/25
- btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b1: 2026-04 64/34, 2026-05 67/34, 2026-06 59/25, 2026-07 86/46, 2026-08 23/8, 2026-09 19/9
- btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b2: 2026-04 5/4, 2026-05 15/8, 2026-06 56/25, 2026-07 35/17, 2026-08 28/16, 2026-09 23/8
- btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b3: 2026-04 1/1, 2026-05 4/2, 2026-06 31/15, 2026-07 15/9, 2026-08 3/3, 2026-09 55/33
- btc-dir-4h vote4-v1/BTCUSDT/4h/up-b1: 2026-04 41/23, 2026-05 39/23, 2026-06 16/11, 2026-07 34/16, 2026-08 47/21, 2026-09 30/13
- btc-dir-4h vote4-v1/BTCUSDT/4h/up-b2: 2026-04 50/30, 2026-05 35/21, 2026-06 6/4, 2026-07 40/21, 2026-08 39/13, 2026-09 29/15
- btc-dir-4h vote4-v1/BTCUSDT/4h/up-b3: 2026-04 47/18, 2026-05 26/12, 2026-07 22/10, 2026-08 49/23, 2026-09 61/30
- btc-dir-4h vote4-v1/BTCUSDT/4h/down-b1: 2026-04 27/15, 2026-05 28/18, 2026-06 31/13, 2026-07 40/23, 2026-08 42/18, 2026-09 29/16
- btc-dir-4h vote4-v1/BTCUSDT/4h/down-b2: 2026-04 8/5, 2026-05 36/21, 2026-06 45/22, 2026-07 43/20, 2026-08 3/3, 2026-09 28/16
- btc-dir-4h vote4-v1/BTCUSDT/4h/down-b3: 2026-04 7/5, 2026-05 22/10, 2026-06 82/37, 2026-07 7/2, 2026-08 6/4, 2026-09 3/2
- btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0: 2026-04 180/1, 2026-05 186/1, 2026-06 180/0, 2026-07 186/0, 2026-08 186/1, 2026-09 180/1
- btc-range-4h realized-vol-hw-v1/BTCUSDT/4h/b0: 2026-04 180/1, 2026-05 186/1, 2026-06 180/0, 2026-07 186/0, 2026-08 186/1, 2026-09 180/2
- btc-range-4h parkinson-hw-v1/BTCUSDT/4h/b0: 2026-04 180/1, 2026-05 186/1, 2026-06 180/0, 2026-07 186/0, 2026-08 186/2, 2026-09 180/2
- btc-mae-down-4h ewma-vol-hw-v1/BTCUSDT/4h/b0: 2026-04 180/0, 2026-05 186/1, 2026-06 180/0, 2026-07 186/0, 2026-08 186/0, 2026-09 180/0
- btc-mae-up-4h ewma-vol-hw-v1/BTCUSDT/4h/b0: 2026-04 180/1, 2026-05 186/2, 2026-06 180/0, 2026-07 186/2, 2026-08 186/1, 2026-09 180/4
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b1: 2026-04 96/54, 2026-05 112/60, 2026-06 130/74, 2026-07 138/69, 2026-08 62/37, 2026-09 266/142
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b2: 2026-04 181/81, 2026-05 99/53, 2026-06 49/26, 2026-07 183/91, 2026-08 178/92, 2026-09 102/41
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b3: 2026-04 123/64, 2026-05 3/1, 2026-06 55/31, 2026-07 187/95, 2026-08 175/88, 2026-09 114/67
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b1: 2026-04 168/83, 2026-05 109/53, 2026-06 79/39, 2026-07 159/86, 2026-08 140/77, 2026-09 138/69
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b2: 2026-04 139/79, 2026-05 226/116, 2026-06 184/88, 2026-07 55/28, 2026-08 146/85, 2026-09 83/51
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b3: 2026-04 13/6, 2026-05 195/106, 2026-06 223/109, 2026-07 22/13, 2026-08 43/25, 2026-09 17/9
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b1: 2026-04 99/46, 2026-05 145/70, 2026-06 120/65, 2026-07 126/59, 2026-08 200/107, 2026-09 136/73
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b2: 2026-04 119/53, 2026-05 160/84, 2026-06 108/57, 2026-07 153/81, 2026-08 152/80, 2026-09 102/48
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b3: 2026-04 137/74, 2026-05 56/33, 2026-06 71/44, 2026-07 186/86, 2026-08 106/54, 2026-09 138/71
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b1: 2026-04 105/51, 2026-05 122/64, 2026-06 128/64, 2026-07 89/41, 2026-08 128/73, 2026-09 132/64
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b2: 2026-04 133/72, 2026-05 93/50, 2026-06 136/63, 2026-07 78/49, 2026-08 83/51, 2026-09 97/51
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b3: 2026-04 127/63, 2026-05 168/87, 2026-06 157/79, 2026-07 112/51, 2026-08 75/43, 2026-09 115/62
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b1: 2026-04 118/59, 2026-05 123/57, 2026-06 153/83, 2026-07 94/49, 2026-08 124/55, 2026-09 154/76
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b2: 2026-04 135/61, 2026-05 138/69, 2026-06 129/70, 2026-07 109/54, 2026-08 94/38, 2026-09 102/50
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b3: 2026-04 109/51, 2026-05 128/56, 2026-06 131/60, 2026-07 95/43, 2026-08 72/25, 2026-09 100/45
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b1: 2026-04 121/60, 2026-05 120/59, 2026-06 108/58, 2026-07 123/61, 2026-08 161/77, 2026-09 117/53
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b2: 2026-04 111/58, 2026-05 110/52, 2026-06 115/44, 2026-07 167/93, 2026-08 163/73, 2026-09 109/53
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b3: 2026-04 126/60, 2026-05 125/57, 2026-06 84/37, 2026-07 156/74, 2026-08 130/63, 2026-09 138/70
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b1: 2026-04 102/53, 2026-05 73/34, 2026-06 92/49, 2026-07 85/41, 2026-08 75/41, 2026-09 111/62
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b2: 2026-04 96/49, 2026-05 50/27, 2026-06 106/58, 2026-07 149/70, 2026-08 104/44, 2026-09 69/41
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b3: 2026-04 25/15, 2026-05 84/47, 2026-06 148/88, 2026-07 182/89, 2026-08 129/66, 2026-09 103/47
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b1: 2026-04 139/72, 2026-05 92/42, 2026-06 128/61, 2026-07 76/37, 2026-08 91/48, 2026-09 92/55
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b2: 2026-04 185/107, 2026-05 111/58, 2026-06 138/71, 2026-07 92/49, 2026-08 110/53, 2026-09 133/58
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b3: 2026-04 173/84, 2026-05 334/176, 2026-06 108/56, 2026-07 160/78, 2026-08 235/126, 2026-09 212/115
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b1: 2026-04 128/56, 2026-05 83/38, 2026-06 118/64, 2026-07 129/67, 2026-08 150/73, 2026-09 124/66
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b2: 2026-04 92/50, 2026-05 49/26, 2026-06 107/63, 2026-07 135/62, 2026-08 94/44, 2026-09 81/36
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b3: 2026-04 92/51, 2026-05 51/32, 2026-06 51/29, 2026-07 174/85, 2026-08 124/60, 2026-09 121/65
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b1: 2026-04 155/85, 2026-05 137/75, 2026-06 147/72, 2026-07 135/70, 2026-08 139/69, 2026-09 162/84
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b2: 2026-04 165/94, 2026-05 156/76, 2026-06 164/82, 2026-07 94/44, 2026-08 124/59, 2026-09 119/58
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b3: 2026-04 88/35, 2026-05 268/137, 2026-06 133/65, 2026-07 77/42, 2026-08 113/66, 2026-09 113/60
- eth-range-1h ewma-vol-hw-v1/ETHUSDT/1h/b0: 2026-04 720/8, 2026-05 744/9, 2026-06 720/8, 2026-07 744/3, 2026-08 744/4, 2026-09 720/5
- eth-range-1h realized-vol-hw-v1/ETHUSDT/1h/b0: 2026-04 720/11, 2026-05 744/8, 2026-06 720/8, 2026-07 744/5, 2026-08 744/7, 2026-09 720/7
- eth-range-1h parkinson-hw-v1/ETHUSDT/1h/b0: 2026-04 720/7, 2026-05 744/9, 2026-06 720/6, 2026-07 744/4, 2026-08 744/8, 2026-09 720/6
- eth-mae-down-1h ewma-vol-hw-v1/ETHUSDT/1h/b0: 2026-04 720/8, 2026-05 744/9, 2026-06 720/6, 2026-07 744/4, 2026-08 744/4, 2026-09 720/6
- eth-mae-up-1h ewma-vol-hw-v1/ETHUSDT/1h/b0: 2026-04 720/10, 2026-05 744/5, 2026-06 720/7, 2026-07 744/8, 2026-08 744/12, 2026-09 720/9
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b1: 2026-04 66/37, 2026-05 61/32, 2026-07 29/17, 2026-08 63/26, 2026-09 36/15
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b2: 2026-04 67/32, 2026-07 111/48, 2026-08 17/7, 2026-09 95/47
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/up-b3: 2026-04 11/6, 2026-07 31/20, 2026-08 65/28, 2026-09 42/23
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b1: 2026-04 36/21, 2026-05 29/14, 2026-06 32/13, 2026-07 5/5, 2026-08 41/22, 2026-09 7/4
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b2: 2026-05 17/5, 2026-06 39/19, 2026-07 9/4
- eth-dir-4h trend-ema-v1/ETHUSDT/4h/down-b3: 2026-05 79/43, 2026-06 109/48, 2026-07 1/1
- eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b1: 2026-04 43/21, 2026-05 27/16, 2026-06 17/7, 2026-07 35/13, 2026-08 30/15, 2026-09 35/20
- eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b2: 2026-04 47/29, 2026-05 17/9, 2026-06 43/28, 2026-07 57/36, 2026-08 52/25, 2026-09 39/22
- eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b3: 2026-04 19/13, 2026-05 8/7, 2026-06 3/3, 2026-07 42/17, 2026-08 32/12, 2026-09 23/8
- eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b1: 2026-04 43/23, 2026-05 29/14, 2026-06 25/12, 2026-07 20/9, 2026-08 24/11, 2026-09 42/19
- eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b2: 2026-04 22/16, 2026-05 64/30, 2026-06 44/23, 2026-07 24/13, 2026-08 43/28, 2026-09 31/20
- eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b3: 2026-04 6/5, 2026-05 41/27, 2026-06 48/20, 2026-07 8/6, 2026-08 5/5, 2026-09 10/6
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b1: 2026-04 41/24, 2026-05 30/17, 2026-06 33/14, 2026-07 24/13, 2026-08 29/12, 2026-09 33/14
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b2: 2026-04 41/15, 2026-05 31/17, 2026-06 26/12, 2026-07 23/10, 2026-08 15/4, 2026-09 25/11
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/up-b3: 2026-04 11/1, 2026-05 47/18, 2026-06 51/30, 2026-07 25/12, 2026-08 20/6, 2026-09 24/9
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b1: 2026-04 30/15, 2026-05 39/22, 2026-06 27/10, 2026-07 29/16, 2026-08 45/27, 2026-09 41/16
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b2: 2026-04 21/6, 2026-05 25/9, 2026-06 30/12, 2026-07 39/21, 2026-08 47/23, 2026-09 33/16
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h/down-b3: 2026-04 36/16, 2026-05 14/4, 2026-06 13/4, 2026-07 46/23, 2026-08 30/14, 2026-09 24/12
- eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b1: 2026-04 12/6, 2026-05 5/3, 2026-06 16/7, 2026-07 27/14, 2026-08 10/4, 2026-09 15/7
- eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b2: 2026-04 12/9, 2026-05 8/4, 2026-06 16/10, 2026-07 31/17, 2026-08 13/5, 2026-09 2/1
- eth-dir-4h takerflow-v1/ETHUSDT/4h/up-b3: 2026-04 7/4, 2026-05 8/3, 2026-06 37/19, 2026-07 32/15, 2026-08 35/17, 2026-09 41/17
- eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b1: 2026-04 54/23, 2026-05 33/17, 2026-06 31/14, 2026-07 48/28, 2026-08 24/15, 2026-09 28/10
- eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b2: 2026-04 67/34, 2026-05 31/14, 2026-06 56/20, 2026-07 39/20, 2026-08 29/17, 2026-09 38/18
- eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b3: 2026-04 28/21, 2026-05 101/49, 2026-06 24/13, 2026-07 9/5, 2026-08 75/42, 2026-09 56/31
- eth-dir-4h vote4-v1/ETHUSDT/4h/up-b1: 2026-04 83/47, 2026-05 21/12, 2026-06 22/15, 2026-07 40/22, 2026-08 23/11, 2026-09 31/15
- eth-dir-4h vote4-v1/ETHUSDT/4h/up-b2: 2026-04 44/18, 2026-05 2/0, 2026-06 7/3, 2026-07 40/17, 2026-08 17/5, 2026-09 44/20
- eth-dir-4h vote4-v1/ETHUSDT/4h/up-b3: 2026-04 2/0, 2026-07 53/29, 2026-08 49/20, 2026-09 47/21
- eth-dir-4h vote4-v1/ETHUSDT/4h/down-b1: 2026-04 32/12, 2026-05 46/20, 2026-06 43/23, 2026-07 40/25, 2026-08 52/30, 2026-09 37/14
- eth-dir-4h vote4-v1/ETHUSDT/4h/down-b2: 2026-04 10/5, 2026-05 45/26, 2026-06 52/24, 2026-07 9/6, 2026-08 37/19, 2026-09 17/9
- eth-dir-4h vote4-v1/ETHUSDT/4h/down-b3: 2026-04 9/9, 2026-05 72/34, 2026-06 56/22, 2026-07 4/0, 2026-08 8/4, 2026-09 4/3
- eth-range-4h ewma-vol-hw-v1/ETHUSDT/4h/b0: 2026-04 180/2, 2026-05 186/0, 2026-06 180/0, 2026-07 186/0, 2026-08 186/1, 2026-09 180/1
- eth-range-4h realized-vol-hw-v1/ETHUSDT/4h/b0: 2026-04 180/2, 2026-05 186/0, 2026-06 180/0, 2026-07 186/0, 2026-08 186/3, 2026-09 180/1
- eth-range-4h parkinson-hw-v1/ETHUSDT/4h/b0: 2026-04 180/1, 2026-05 186/0, 2026-06 180/0, 2026-07 186/0, 2026-08 186/2, 2026-09 180/0
- eth-mae-down-4h ewma-vol-hw-v1/ETHUSDT/4h/b0: 2026-04 180/0, 2026-05 186/2, 2026-06 180/0, 2026-07 186/0, 2026-08 186/2, 2026-09 180/0
- eth-mae-up-4h ewma-vol-hw-v1/ETHUSDT/4h/b0: 2026-04 180/2, 2026-05 186/1, 2026-06 180/2, 2026-07 186/1, 2026-08 186/2, 2026-09 180/2
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b1: 2026-04 173/83, 2026-05 96/50, 2026-06 75/47, 2026-07 146/75, 2026-08 89/38, 2026-09 94/50
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b2: 2026-04 134/70, 2026-05 213/98, 2026-06 77/38, 2026-07 158/73, 2026-08 228/118, 2026-09 100/47
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b3: 2026-04 95/52, 2026-05 156/75, 2026-06 50/27, 2026-07 99/52, 2026-08 220/106, 2026-09 190/94
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b1: 2026-04 87/41, 2026-05 52/29, 2026-06 101/48, 2026-07 146/80, 2026-08 91/48, 2026-09 122/65
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b2: 2026-04 91/51, 2026-05 66/37, 2026-06 139/77, 2026-07 139/77, 2026-08 68/32, 2026-09 156/80
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b3: 2026-04 140/82, 2026-05 161/82, 2026-06 278/140, 2026-07 56/38, 2026-08 48/27, 2026-09 58/35
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b1: 2026-04 131/60, 2026-05 157/80, 2026-06 111/58, 2026-07 139/63, 2026-08 135/74, 2026-09 96/42
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b2: 2026-04 147/72, 2026-05 144/72, 2026-06 104/48, 2026-07 140/72, 2026-08 135/67, 2026-09 138/71
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b3: 2026-04 127/73, 2026-05 138/63, 2026-06 78/40, 2026-07 138/66, 2026-08 155/72, 2026-09 136/69
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b1: 2026-04 91/54, 2026-05 95/51, 2026-06 104/47, 2026-07 125/65, 2026-08 92/49, 2026-09 95/45
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b2: 2026-04 81/42, 2026-05 108/55, 2026-06 123/53, 2026-07 113/67, 2026-08 112/56, 2026-09 115/59
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b3: 2026-04 142/74, 2026-05 102/60, 2026-06 200/108, 2026-07 88/49, 2026-08 114/64, 2026-09 140/80
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b1: 2026-04 88/36, 2026-05 112/54, 2026-06 112/58, 2026-07 102/45, 2026-08 120/54, 2026-09 123/61
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b2: 2026-04 129/61, 2026-05 148/64, 2026-06 155/82, 2026-07 107/48, 2026-08 110/47, 2026-09 124/59
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/up-b3: 2026-04 104/49, 2026-05 86/38, 2026-06 150/68, 2026-07 105/44, 2026-08 96/48, 2026-09 111/48
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b1: 2026-04 126/65, 2026-05 111/56, 2026-06 106/58, 2026-07 150/80, 2026-08 131/62, 2026-09 124/65
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b2: 2026-04 141/73, 2026-05 126/63, 2026-06 116/56, 2026-07 144/81, 2026-08 144/77, 2026-09 103/46
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b3: 2026-04 132/59, 2026-05 161/82, 2026-06 81/30, 2026-07 136/61, 2026-08 143/64, 2026-09 135/72
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b1: 2026-04 143/73, 2026-05 104/47, 2026-06 87/46, 2026-07 63/24, 2026-08 118/48, 2026-09 106/48
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b2: 2026-04 162/76, 2026-05 74/40, 2026-06 55/27, 2026-07 33/11, 2026-08 121/53, 2026-09 91/47
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b3: 2026-04 97/54, 2026-05 86/42, 2026-06 88/39, 2026-07 40/27, 2026-08 116/62, 2026-09 89/44
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b1: 2026-04 81/44, 2026-05 89/39, 2026-06 93/40, 2026-07 72/31, 2026-08 85/34, 2026-09 107/50
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b2: 2026-04 102/61, 2026-05 111/62, 2026-06 102/49, 2026-07 123/64, 2026-08 105/46, 2026-09 163/82
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b3: 2026-04 135/66, 2026-05 280/155, 2026-06 295/148, 2026-07 413/230, 2026-08 199/109, 2026-09 164/94
- bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b1: 2026-04 119/66, 2026-05 96/50, 2026-06 143/79, 2026-07 88/33, 2026-08 127/61, 2026-09 152/74
- bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b2: 2026-04 160/80, 2026-05 125/65, 2026-06 80/32, 2026-07 75/43, 2026-08 142/70, 2026-09 138/69
- bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b3: 2026-04 93/48, 2026-05 113/49, 2026-06 14/7, 2026-07 47/25, 2026-08 159/72, 2026-09 83/42
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b1: 2026-04 92/61, 2026-05 105/57, 2026-06 106/54, 2026-07 146/78, 2026-08 102/47, 2026-09 125/68
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b2: 2026-04 108/56, 2026-05 115/59, 2026-06 135/59, 2026-07 171/96, 2026-08 100/45, 2026-09 123/65
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b3: 2026-04 147/75, 2026-05 190/105, 2026-06 242/123, 2026-07 216/114, 2026-08 113/63, 2026-09 99/52
- bnb-range-1h ewma-vol-hw-v1/BNBUSDT/1h/b0: 2026-04 720/9, 2026-05 744/6, 2026-06 720/4, 2026-07 744/4, 2026-08 744/10, 2026-09 720/5
- bnb-range-1h realized-vol-hw-v1/BNBUSDT/1h/b0: 2026-04 720/6, 2026-05 744/9, 2026-06 720/5, 2026-07 744/6, 2026-08 744/10, 2026-09 720/8
- bnb-range-1h parkinson-hw-v1/BNBUSDT/1h/b0: 2026-04 720/8, 2026-05 744/14, 2026-06 720/5, 2026-07 744/7, 2026-08 744/13, 2026-09 720/8
- bnb-mae-down-1h ewma-vol-hw-v1/BNBUSDT/1h/b0: 2026-04 720/9, 2026-05 744/5, 2026-06 720/5, 2026-07 744/3, 2026-08 744/3, 2026-09 720/6
- bnb-mae-up-1h ewma-vol-hw-v1/BNBUSDT/1h/b0: 2026-04 720/6, 2026-05 744/11, 2026-06 720/7, 2026-07 744/13, 2026-08 744/14, 2026-09 720/15
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b1: 2026-04 21/11, 2026-05 52/29, 2026-06 5/4, 2026-07 73/41, 2026-09 26/9
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b2: 2026-04 54/25, 2026-05 37/17, 2026-06 12/9, 2026-07 6/3, 2026-08 39/16, 2026-09 37/17
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b3: 2026-04 11/7, 2026-05 39/16, 2026-08 147/69, 2026-09 117/59
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b1: 2026-04 14/8, 2026-05 36/22, 2026-06 16/5, 2026-07 74/42
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b2: 2026-04 34/14, 2026-05 22/16, 2026-06 14/4, 2026-07 15/7
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b3: 2026-04 46/23, 2026-06 133/69, 2026-07 18/11
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b1: 2026-04 41/25, 2026-05 34/14, 2026-06 37/20, 2026-07 47/23, 2026-08 50/22, 2026-09 24/13
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b2: 2026-04 34/16, 2026-05 66/28, 2026-06 26/14, 2026-07 32/18, 2026-08 42/23, 2026-09 32/12
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b3: 2026-04 23/16, 2026-05 21/12, 2026-06 8/7, 2026-07 16/10, 2026-08 44/18, 2026-09 41/21
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b1: 2026-04 21/14, 2026-05 11/7, 2026-06 18/10, 2026-07 43/25, 2026-08 14/8, 2026-09 20/10
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b2: 2026-04 26/12, 2026-05 20/12, 2026-06 28/11, 2026-07 26/15, 2026-08 20/10, 2026-09 32/18
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b3: 2026-04 35/21, 2026-05 34/18, 2026-06 63/31, 2026-07 22/11, 2026-08 16/10, 2026-09 31/16
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b1: 2026-04 27/9, 2026-05 17/6, 2026-06 12/4, 2026-07 22/13, 2026-08 23/7, 2026-09 33/15
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b2: 2026-04 27/14, 2026-05 20/8, 2026-06 32/19, 2026-07 33/13, 2026-08 29/13, 2026-09 23/9
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/up-b3: 2026-04 33/13, 2026-05 31/16, 2026-06 61/33, 2026-07 27/12, 2026-08 20/8, 2026-09 29/12
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b1: 2026-04 38/16, 2026-05 36/24, 2026-06 33/13, 2026-07 27/14, 2026-08 40/21, 2026-09 36/15
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b2: 2026-04 28/12, 2026-05 35/20, 2026-06 24/13, 2026-07 41/21, 2026-08 38/20, 2026-09 27/16
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b3: 2026-04 27/10, 2026-05 47/22, 2026-06 18/7, 2026-07 36/16, 2026-08 36/16, 2026-09 32/15
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b1: 2026-04 43/16, 2026-05 24/11, 2026-06 25/9, 2026-07 5/2, 2026-08 47/26, 2026-09 22/10
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b2: 2026-04 40/24, 2026-05 7/4, 2026-06 24/13, 2026-08 42/18, 2026-09 32/11
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/up-b3: 2026-04 20/11, 2026-05 23/10, 2026-06 6/4, 2026-08 8/4, 2026-09 13/8
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b1: 2026-04 16/9, 2026-05 24/15, 2026-06 15/9, 2026-07 21/14, 2026-08 25/13, 2026-09 18/6
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b2: 2026-04 18/7, 2026-05 27/14, 2026-06 34/11, 2026-07 25/12, 2026-08 26/21, 2026-09 29/13
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b3: 2026-04 43/20, 2026-05 81/46, 2026-06 76/33, 2026-07 135/66, 2026-08 38/18, 2026-09 66/38
- bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b1: 2026-04 39/19, 2026-05 37/21, 2026-06 14/11, 2026-07 24/11, 2026-08 33/17, 2026-09 43/22
- bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b2: 2026-04 30/14, 2026-05 31/13, 2026-06 16/6, 2026-07 4/3, 2026-08 61/27, 2026-09 52/25
- bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b3: 2026-04 26/14, 2026-05 19/7, 2026-06 5/5, 2026-08 54/22, 2026-09 38/18
- bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b1: 2026-04 30/15, 2026-05 20/10, 2026-06 7/3, 2026-07 31/15, 2026-08 15/6, 2026-09 16/9
- bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b2: 2026-04 17/8, 2026-05 18/9, 2026-06 30/16, 2026-07 36/18, 2026-08 16/10, 2026-09 16/11
- bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b3: 2026-04 38/17, 2026-05 61/39, 2026-06 108/50, 2026-07 91/48, 2026-08 7/3, 2026-09 15/7
- bnb-range-4h ewma-vol-hw-v1/BNBUSDT/4h/b0: 2026-04 180/1, 2026-05 186/2, 2026-06 180/0, 2026-07 186/1, 2026-08 186/2, 2026-09 180/0
- bnb-range-4h realized-vol-hw-v1/BNBUSDT/4h/b0: 2026-04 180/0, 2026-05 186/4, 2026-06 180/0, 2026-07 186/1, 2026-08 186/3, 2026-09 180/0
- bnb-range-4h parkinson-hw-v1/BNBUSDT/4h/b0: 2026-04 180/0, 2026-05 186/4, 2026-06 180/0, 2026-07 186/1, 2026-08 186/3, 2026-09 180/0
- bnb-mae-down-4h ewma-vol-hw-v1/BNBUSDT/4h/b0: 2026-04 180/1, 2026-05 186/1, 2026-06 180/0, 2026-07 186/1, 2026-08 186/0, 2026-09 180/0
- bnb-mae-up-4h ewma-vol-hw-v1/BNBUSDT/4h/b0: 2026-04 180/1, 2026-05 186/3, 2026-06 180/0, 2026-07 186/1, 2026-08 186/4, 2026-09 180/2
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b1: 2026-04 136/69, 2026-05 120/68, 2026-06 90/42, 2026-07 141/81, 2026-08 171/86, 2026-09 126/63
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b2: 2026-04 140/80, 2026-05 79/38, 2026-06 137/70, 2026-07 89/43, 2026-08 133/67, 2026-09 127/64
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b3: 2026-04 44/24, 2026-05 117/56, 2026-06 109/55, 2026-07 104/47, 2026-08 243/117, 2026-09 142/78
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b1: 2026-04 198/100, 2026-05 165/96, 2026-06 76/37, 2026-07 86/43, 2026-08 101/45, 2026-09 201/106
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b2: 2026-04 148/82, 2026-05 106/56, 2026-06 136/68, 2026-07 207/112, 2026-08 76/47, 2026-09 87/43
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b3: 2026-04 54/29, 2026-05 157/80, 2026-06 172/80, 2026-07 117/73, 2026-08 20/14, 2026-09 37/20
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b1: 2026-04 133/67, 2026-05 157/88, 2026-06 90/51, 2026-07 157/74, 2026-08 174/88, 2026-09 110/53
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b2: 2026-04 150/76, 2026-05 138/73, 2026-06 106/44, 2026-07 129/66, 2026-08 140/76, 2026-09 122/63
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b3: 2026-04 96/63, 2026-05 92/42, 2026-06 122/62, 2026-07 113/54, 2026-08 153/75, 2026-09 141/74
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b1: 2026-04 89/49, 2026-05 141/85, 2026-06 122/45, 2026-07 102/53, 2026-08 94/51, 2026-09 105/52
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b2: 2026-04 105/56, 2026-05 73/40, 2026-06 160/79, 2026-07 105/56, 2026-08 99/54, 2026-09 107/53
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b3: 2026-04 146/79, 2026-05 139/79, 2026-06 120/70, 2026-07 138/73, 2026-08 83/53, 2026-09 135/72
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b1: 2026-04 106/49, 2026-05 122/66, 2026-06 123/71, 2026-07 122/62, 2026-08 124/60, 2026-09 142/70
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b2: 2026-04 138/67, 2026-05 139/58, 2026-06 140/78, 2026-07 119/55, 2026-08 104/46, 2026-09 113/61
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b3: 2026-04 105/50, 2026-05 99/45, 2026-06 121/50, 2026-07 122/56, 2026-08 85/32, 2026-09 111/47
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b1: 2026-04 132/64, 2026-05 134/68, 2026-06 114/52, 2026-07 123/66, 2026-08 134/71, 2026-09 110/46
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b2: 2026-04 119/57, 2026-05 132/73, 2026-06 117/60, 2026-07 136/72, 2026-08 150/69, 2026-09 111/58
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b3: 2026-04 120/53, 2026-05 118/55, 2026-06 105/54, 2026-07 122/59, 2026-08 147/70, 2026-09 133/67
- sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b1: 2026-04 145/78, 2026-05 87/43, 2026-06 117/60, 2026-07 100/45, 2026-08 112/50, 2026-09 103/49
- sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b2: 2026-04 92/50, 2026-05 149/70, 2026-06 122/57, 2026-07 139/72, 2026-08 92/39, 2026-09 88/44
- sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b3: 2026-04 236/118, 2026-05 229/113, 2026-06 101/52, 2026-07 162/72, 2026-08 215/106, 2026-09 182/91
- sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b1: 2026-04 133/69, 2026-05 123/62, 2026-06 98/54, 2026-07 143/78, 2026-08 112/54, 2026-09 129/69
- sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b2: 2026-04 65/38, 2026-05 114/60, 2026-06 111/52, 2026-07 137/73, 2026-08 83/39, 2026-09 89/44
- sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b3: 2026-04 49/22, 2026-05 42/28, 2026-06 171/77, 2026-07 63/27, 2026-08 130/72, 2026-09 129/58
- sol-dir-1h vote4-v1/SOLUSDT/1h/up-b1: 2026-04 141/66, 2026-05 139/67, 2026-06 119/59, 2026-07 126/58, 2026-08 125/56, 2026-09 117/50
- sol-dir-1h vote4-v1/SOLUSDT/1h/up-b2: 2026-04 114/67, 2026-05 116/58, 2026-06 102/52, 2026-07 173/92, 2026-08 109/56, 2026-09 111/59
- sol-dir-1h vote4-v1/SOLUSDT/1h/up-b3: 2026-04 131/67, 2026-05 147/71, 2026-06 118/57, 2026-07 99/41, 2026-08 227/102, 2026-09 172/93
- sol-dir-1h vote4-v1/SOLUSDT/1h/down-b1: 2026-04 183/98, 2026-05 127/71, 2026-06 124/67, 2026-07 123/60, 2026-08 132/58, 2026-09 139/79
- sol-dir-1h vote4-v1/SOLUSDT/1h/down-b2: 2026-04 102/51, 2026-05 108/50, 2026-06 106/43, 2026-07 123/65, 2026-08 62/29, 2026-09 101/49
- sol-dir-1h vote4-v1/SOLUSDT/1h/down-b3: 2026-04 48/22, 2026-05 103/61, 2026-06 151/73, 2026-07 100/56, 2026-08 88/52, 2026-09 80/33
- sol-range-1h ewma-vol-hw-v1/SOLUSDT/1h/b0: 2026-04 720/8, 2026-05 744/9, 2026-06 720/7, 2026-07 744/6, 2026-08 744/11, 2026-09 720/10
- sol-range-1h realized-vol-hw-v1/SOLUSDT/1h/b0: 2026-04 720/8, 2026-05 744/8, 2026-06 720/7, 2026-07 744/4, 2026-08 744/12, 2026-09 720/8
- sol-range-1h parkinson-hw-v1/SOLUSDT/1h/b0: 2026-04 720/7, 2026-05 744/6, 2026-06 720/7, 2026-07 744/3, 2026-08 744/10, 2026-09 720/10
- sol-mae-down-1h ewma-vol-hw-v1/SOLUSDT/1h/b0: 2026-04 720/7, 2026-05 744/10, 2026-06 720/4, 2026-07 744/3, 2026-08 744/5, 2026-09 720/5
- sol-mae-up-1h ewma-vol-hw-v1/SOLUSDT/1h/b0: 2026-04 720/11, 2026-05 744/9, 2026-06 720/9, 2026-07 744/5, 2026-08 744/16, 2026-09 720/12
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b1: 2026-04 94/52, 2026-05 15/7, 2026-06 40/23, 2026-07 43/25, 2026-08 62/27, 2026-09 38/19
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b2: 2026-04 2/2, 2026-05 25/16, 2026-07 29/14, 2026-08 8/3, 2026-09 23/16
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b3: 2026-05 27/14, 2026-07 31/20, 2026-08 68/34, 2026-09 108/51
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b1: 2026-04 44/24, 2026-05 71/35, 2026-06 52/29, 2026-07 80/40, 2026-08 25/12, 2026-09 11/9
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b2: 2026-04 26/14, 2026-05 48/23, 2026-06 21/7, 2026-07 3/1, 2026-08 20/10
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b3: 2026-04 14/7, 2026-06 67/30, 2026-08 3/2
- sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b1: 2026-04 54/29, 2026-05 26/10, 2026-06 44/18, 2026-07 21/13, 2026-08 36/13, 2026-09 32/14
- sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b2: 2026-04 27/20, 2026-05 20/12, 2026-06 29/20, 2026-07 17/11, 2026-08 32/15, 2026-09 44/25
- sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b3: 2026-04 7/5, 2026-05 35/19, 2026-06 21/11, 2026-07 31/18, 2026-08 63/32, 2026-09 27/12
- sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b1: 2026-04 34/19, 2026-05 31/13, 2026-06 21/10, 2026-07 36/18, 2026-08 36/15, 2026-09 29/16
- sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b2: 2026-04 51/29, 2026-05 36/19, 2026-06 23/13, 2026-07 46/21, 2026-08 15/10, 2026-09 31/13
- sol-dir-4h tsmom-v1/SOLUSDT/4h/down-b3: 2026-04 6/4, 2026-05 37/15, 2026-06 40/12, 2026-07 33/18, 2026-08 2/1, 2026-09 17/11
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b1: 2026-04 42/20, 2026-05 27/17, 2026-06 18/7, 2026-07 36/17, 2026-08 21/10, 2026-09 30/16
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b2: 2026-04 28/11, 2026-05 30/18, 2026-06 20/13, 2026-07 30/19, 2026-08 26/12, 2026-09 23/10
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/up-b3: 2026-04 25/11, 2026-05 32/15, 2026-06 47/33, 2026-07 38/18, 2026-08 12/2, 2026-09 27/13
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b1: 2026-04 33/15, 2026-05 34/19, 2026-06 29/16, 2026-07 28/12, 2026-08 40/21, 2026-09 46/26
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b2: 2026-04 28/12, 2026-05 35/22, 2026-06 41/23, 2026-07 31/11, 2026-08 41/20, 2026-09 32/15
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h/down-b3: 2026-04 24/7, 2026-05 28/10, 2026-06 25/13, 2026-07 23/11, 2026-08 46/22, 2026-09 22/10
- sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b1: 2026-04 21/9, 2026-05 25/10, 2026-06 38/20, 2026-07 35/19, 2026-08 12/6, 2026-09 30/14
- sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b2: 2026-04 45/25, 2026-05 44/22, 2026-06 23/8, 2026-07 39/19, 2026-08 10/6, 2026-09 34/18
- sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b3: 2026-04 102/52, 2026-05 62/36, 2026-06 32/18, 2026-07 56/37, 2026-08 85/39, 2026-09 47/24
- sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b1: 2026-04 11/4, 2026-05 24/15, 2026-06 31/16, 2026-07 31/18, 2026-08 17/8, 2026-09 12/6
- sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b2: 2026-04 1/1, 2026-05 19/4, 2026-06 16/8, 2026-07 22/10, 2026-08 11/5, 2026-09 42/22
- sol-dir-4h takerflow-v1/SOLUSDT/4h/down-b3: 2026-05 12/6, 2026-06 40/11, 2026-07 3/0, 2026-08 51/29, 2026-09 15/9
- sol-dir-4h vote4-v1/SOLUSDT/4h/up-b1: 2026-04 47/22, 2026-05 34/18, 2026-06 23/12, 2026-07 42/26, 2026-08 21/8, 2026-09 27/14
- sol-dir-4h vote4-v1/SOLUSDT/4h/up-b2: 2026-04 32/18, 2026-05 24/12, 2026-06 19/11, 2026-07 49/30, 2026-08 23/10, 2026-09 43/24
- sol-dir-4h vote4-v1/SOLUSDT/4h/up-b3: 2026-04 27/14, 2026-05 28/15, 2026-06 10/6, 2026-07 30/16, 2026-08 74/35, 2026-09 66/33
- sol-dir-4h vote4-v1/SOLUSDT/4h/down-b1: 2026-04 44/20, 2026-05 42/18, 2026-06 33/16, 2026-07 25/14, 2026-08 22/9, 2026-09 28/20
- sol-dir-4h vote4-v1/SOLUSDT/4h/down-b2: 2026-04 25/12, 2026-05 45/22, 2026-06 41/21, 2026-07 26/16, 2026-08 22/12, 2026-09 16/7
- sol-dir-4h vote4-v1/SOLUSDT/4h/down-b3: 2026-04 4/2, 2026-05 12/6, 2026-06 52/22, 2026-07 12/4, 2026-08 22/11
- sol-range-4h ewma-vol-hw-v1/SOLUSDT/4h/b0: 2026-04 180/0, 2026-05 186/1, 2026-06 180/0, 2026-07 186/1, 2026-08 186/3, 2026-09 180/0
- sol-range-4h realized-vol-hw-v1/SOLUSDT/4h/b0: 2026-04 180/1, 2026-05 186/4, 2026-06 180/1, 2026-07 186/0, 2026-08 186/3, 2026-09 180/0
- sol-range-4h parkinson-hw-v1/SOLUSDT/4h/b0: 2026-04 180/0, 2026-05 186/1, 2026-06 180/1, 2026-07 186/0, 2026-08 186/3, 2026-09 180/0
- sol-mae-down-4h ewma-vol-hw-v1/SOLUSDT/4h/b0: 2026-04 180/0, 2026-05 186/1, 2026-06 180/0, 2026-07 186/0, 2026-08 186/2, 2026-09 180/0
- sol-mae-up-4h ewma-vol-hw-v1/SOLUSDT/4h/b0: 2026-04 180/1, 2026-05 186/3, 2026-06 180/2, 2026-07 186/1, 2026-08 186/4, 2026-09 180/3

## TEST labels per symbol

| Symbol | Horizon | n | flat share | up rate |
|---|---|---|---|---|
| BTCUSDT | 1h | 4392 | 0.0000 | 0.5018 |
| BTCUSDT | 4h | 1098 | 0.0000 | 0.5073 |
| ETHUSDT | 1h | 4392 | 0.0009 | 0.5023 |
| ETHUSDT | 4h | 1098 | 0.0009 | 0.5055 |
| BNBUSDT | 1h | 4392 | 0.0023 | 0.5153 |
| BNBUSDT | 4h | 1098 | 0.0009 | 0.5146 |
| SOLUSDT | 1h | 4392 | 0.0137 | 0.5016 |
| SOLUSDT | 4h | 1098 | 0.0082 | 0.4818 |

## Regime descriptors per block

The net log move of SELECT reads n/a: its start needs the candle before the first recorded one.

| Symbol | Block | annualised realized vol | net log move |
|---|---|---|---|
| BTCUSDT | SELECT | 0.4572 | n/a |
| BTCUSDT | CALIB | 0.4878 | -0.5129 |
| BTCUSDT | TEST | 0.3846 | 0.2026 |
| ETHUSDT | SELECT | 0.7163 | n/a |
| ETHUSDT | CALIB | 0.6878 | -0.6774 |
| ETHUSDT | TEST | 0.5099 | 0.2435 |
| BNBUSDT | SELECT | 0.5360 | n/a |
| BNBUSDT | CALIB | 0.5916 | -0.4907 |
| BNBUSDT | TEST | 0.3924 | 0.2199 |
| SOLUSDT | SELECT | 0.8730 | n/a |
| SOLUSDT | CALIB | 0.7609 | -0.9196 |
| SOLUSDT | TEST | 0.5686 | 0.3505 |

## Bucket monotonicity (TEST miss rates b1, b2, b3; decreasing means strictly)

- trend-ema-v1 BTCUSDT 1h up: 0.5192, 0.4957, 0.4814; decreasing: true
- trend-ema-v1 BTCUSDT 1h down: 0.4824, 0.5103, 0.5089; decreasing: false
- tsmom-v1 BTCUSDT 1h up: 0.4980, 0.5092, 0.5129; decreasing: false
- tsmom-v1 BTCUSDT 1h down: 0.5149, 0.4963, 0.5225; decreasing: false
- meanrev-z-v1 BTCUSDT 1h up: 0.5000, 0.4877, 0.4401; decreasing: true
- meanrev-z-v1 BTCUSDT 1h down: 0.4980, 0.4830, 0.4664; decreasing: true
- takerflow-v1 BTCUSDT 1h up: 0.4819, 0.5042, 0.4901; decreasing: false
- takerflow-v1 BTCUSDT 1h down: 0.4954, 0.4900, 0.5119; decreasing: false
- vote4-v1 BTCUSDT 1h up: 0.5014, 0.4907, 0.4735; decreasing: true
- vote4-v1 BTCUSDT 1h down: 0.4967, 0.4898, 0.4875; decreasing: true
- trend-ema-v1 BTCUSDT 4h up: 0.5336, 0.4439, 0.5047; decreasing: false
- trend-ema-v1 BTCUSDT 4h down: 0.5698, 0.4396, 0.5161; decreasing: false
- tsmom-v1 BTCUSDT 4h up: 0.5157, 0.5545, 0.5026; decreasing: false
- tsmom-v1 BTCUSDT 4h down: 0.5460, 0.5427, 0.5367; decreasing: true
- meanrev-z-v1 BTCUSDT 4h up: 0.4755, 0.4551, 0.4721; decreasing: false
- meanrev-z-v1 BTCUSDT 4h down: 0.5313, 0.4479, 0.4745; decreasing: false
- takerflow-v1 BTCUSDT 4h up: 0.5288, 0.4397, 0.5000; decreasing: false
- takerflow-v1 BTCUSDT 4h down: 0.4906, 0.4815, 0.5780; decreasing: false
- vote4-v1 BTCUSDT 4h up: 0.5169, 0.5226, 0.4537; decreasing: false
- vote4-v1 BTCUSDT 4h down: 0.5228, 0.5337, 0.4724; decreasing: false
- trend-ema-v1 ETHUSDT 1h up: 0.5423, 0.4848, 0.5266; decreasing: false
- trend-ema-v1 ETHUSDT 1h down: 0.5132, 0.5366, 0.5224; decreasing: false
- tsmom-v1 ETHUSDT 1h up: 0.5085, 0.5076, 0.5216; decreasing: false
- tsmom-v1 ETHUSDT 1h down: 0.5071, 0.5419, 0.5106; decreasing: false
- meanrev-z-v1 ETHUSDT 1h up: 0.4948, 0.4837, 0.4409; decreasing: true
- meanrev-z-v1 ETHUSDT 1h down: 0.4907, 0.4813, 0.4756; decreasing: true
- takerflow-v1 ETHUSDT 1h up: 0.5204, 0.5035, 0.5246; decreasing: false
- takerflow-v1 ETHUSDT 1h down: 0.5097, 0.5150, 0.5196; decreasing: false
- vote4-v1 ETHUSDT 1h up: 0.4973, 0.5036, 0.5253; decreasing: false
- vote4-v1 ETHUSDT 1h down: 0.5200, 0.5024, 0.5114; decreasing: false
- trend-ema-v1 ETHUSDT 4h up: 0.4980, 0.4621, 0.5168; decreasing: false
- trend-ema-v1 ETHUSDT 4h down: 0.5267, 0.4308, 0.4868; decreasing: false
- tsmom-v1 ETHUSDT 4h up: 0.4920, 0.5843, 0.4724; decreasing: false
- tsmom-v1 ETHUSDT 4h down: 0.4809, 0.5702, 0.5847; decreasing: false
- meanrev-z-v1 ETHUSDT 4h up: 0.4947, 0.4286, 0.4270; decreasing: true
- meanrev-z-v1 ETHUSDT 4h down: 0.5024, 0.4462, 0.4479; decreasing: false
- takerflow-v1 ETHUSDT 4h up: 0.4824, 0.5610, 0.4688; decreasing: false
- takerflow-v1 ETHUSDT 4h down: 0.4908, 0.4731, 0.5495; decreasing: false
- vote4-v1 ETHUSDT 4h up: 0.5545, 0.4091, 0.4636; decreasing: false
- vote4-v1 ETHUSDT 4h down: 0.4960, 0.5235, 0.4706; decreasing: false
- trend-ema-v1 BNBUSDT 1h up: 0.5097, 0.4879, 0.5012; decreasing: false
- trend-ema-v1 BNBUSDT 1h down: 0.5192, 0.5372, 0.5452; decreasing: false
- tsmom-v1 BNBUSDT 1h up: 0.4902, 0.4975, 0.4961; decreasing: false
- tsmom-v1 BNBUSDT 1h down: 0.5166, 0.5092, 0.5534; decreasing: false
- meanrev-z-v1 BNBUSDT 1h up: 0.4688, 0.4670, 0.4525; decreasing: true
- meanrev-z-v1 BNBUSDT 1h down: 0.5160, 0.5116, 0.4670; decreasing: true
- takerflow-v1 BNBUSDT 1h up: 0.4605, 0.4739, 0.5194; decreasing: false
- takerflow-v1 BNBUSDT 1h down: 0.4516, 0.5156, 0.5397; decreasing: false
- vote4-v1 BNBUSDT 1h up: 0.5007, 0.4986, 0.4774; decreasing: true
- vote4-v1 BNBUSDT 1h down: 0.5399, 0.5053, 0.5283; decreasing: false
- trend-ema-v1 BNBUSDT 4h up: 0.5311, 0.4703, 0.4809; decreasing: false
- trend-ema-v1 BNBUSDT 4h down: 0.5500, 0.4824, 0.5228; decreasing: false
- tsmom-v1 BNBUSDT 4h up: 0.5021, 0.4784, 0.5490; decreasing: false
- tsmom-v1 BNBUSDT 4h down: 0.5827, 0.5132, 0.5323; decreasing: false
- meanrev-z-v1 BNBUSDT 4h up: 0.4030, 0.4634, 0.4677; decreasing: false
- meanrev-z-v1 BNBUSDT 4h down: 0.4905, 0.5285, 0.4388; decreasing: false
- takerflow-v1 BNBUSDT 4h up: 0.4458, 0.4828, 0.5286; decreasing: false
- takerflow-v1 BNBUSDT 4h down: 0.5546, 0.4906, 0.5034; decreasing: false
- vote4-v1 BNBUSDT 4h up: 0.5316, 0.4536, 0.4648; decreasing: false
- vote4-v1 BNBUSDT 4h down: 0.4874, 0.5414, 0.5125; decreasing: false
- trend-ema-v1 SOLUSDT 1h up: 0.5217, 0.5135, 0.4967; decreasing: true
- trend-ema-v1 SOLUSDT 1h down: 0.5163, 0.5368, 0.5314; decreasing: false
- tsmom-v1 SOLUSDT 1h up: 0.5128, 0.5070, 0.5160; decreasing: false
- tsmom-v1 SOLUSDT 1h down: 0.5130, 0.5208, 0.5598; decreasing: false
- meanrev-z-v1 SOLUSDT 1h up: 0.5115, 0.4847, 0.4355; decreasing: true
- meanrev-z-v1 SOLUSDT 1h down: 0.4913, 0.5085, 0.4805; decreasing: false
- takerflow-v1 SOLUSDT 1h up: 0.4895, 0.4868, 0.4907; decreasing: false
- takerflow-v1 SOLUSDT 1h down: 0.5230, 0.5109, 0.4863; decreasing: true
- vote4-v1 SOLUSDT 1h up: 0.4641, 0.5297, 0.4821; decreasing: false
- vote4-v1 SOLUSDT 1h down: 0.5229, 0.4767, 0.5211; decreasing: false
- trend-ema-v1 SOLUSDT 4h up: 0.5240, 0.5862, 0.5085; decreasing: false
- trend-ema-v1 SOLUSDT 4h down: 0.5265, 0.4661, 0.4643; decreasing: true
- tsmom-v1 SOLUSDT 4h up: 0.4554, 0.6095, 0.5272; decreasing: false
- tsmom-v1 SOLUSDT 4h down: 0.4866, 0.5198, 0.4519; decreasing: false
- meanrev-z-v1 SOLUSDT 4h up: 0.5000, 0.5287, 0.5083; decreasing: false
- meanrev-z-v1 SOLUSDT 4h down: 0.5190, 0.4952, 0.4345; decreasing: true
- takerflow-v1 SOLUSDT 4h up: 0.4845, 0.5026, 0.5365; decreasing: false
- takerflow-v1 SOLUSDT 4h down: 0.5317, 0.4505, 0.4545; decreasing: false
- vote4-v1 SOLUSDT 4h up: 0.5155, 0.5526, 0.5064; decreasing: false
- vote4-v1 SOLUSDT 4h down: 0.5000, 0.5143, 0.4412; decreasing: false

## Stress subset (TEST decisions with RV24 above the CALIB rank ceil(0.9 n))

- BTCUSDT 1h: threshold 0.007521
- BTCUSDT 4h: threshold 0.013972
  - btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0: n 30, misses 0
- ETHUSDT 1h: threshold 0.010758
- ETHUSDT 4h: threshold 0.020697
- BNBUSDT 1h: threshold 0.009114
  - bnb-mae-down-1h ewma-vol-hw-v1/BNBUSDT/1h/b0: n 127, misses 1
- BNBUSDT 4h: threshold 0.018423
- SOLUSDT 1h: threshold 0.011794
- SOLUSDT 4h: threshold 0.023127

## Cost-net reference rule (C-1, 10 basis points per side, an assumption dated 2026-10-01)

- No direction cell is a region after the veto.

## Deflated Sharpe ratio (C-2, diagnostic; N = 40 direction trials, SR0 0.255289)

- btc-dir-1h trend-ema-v1/BTCUSDT/1h: T 4392, SR -0.480313, DSR 0.0000
- btc-dir-1h tsmom-v1/BTCUSDT/1h: T 4392, SR -0.471683, DSR 0.0000
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h: T 4392, SR -0.480124, DSR 0.0000
- btc-dir-1h takerflow-v1/BTCUSDT/1h: T 4392, SR -0.457621, DSR 0.0000
- btc-dir-1h vote4-v1/BTCUSDT/1h: T 4392, SR -0.470385, DSR 0.0000
- btc-dir-4h trend-ema-v1/BTCUSDT/4h: T 1098, SR -0.211389, DSR 0.0000
- btc-dir-4h tsmom-v1/BTCUSDT/4h: T 1098, SR -0.267332, DSR 0.0000
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h: T 1098, SR -0.251912, DSR 0.0000
- btc-dir-4h takerflow-v1/BTCUSDT/4h: T 1098, SR -0.208712, DSR 0.0000
- btc-dir-4h vote4-v1/BTCUSDT/4h: T 1098, SR -0.234105, DSR 0.0000
- eth-dir-1h trend-ema-v1/ETHUSDT/1h: T 4392, SR -0.376472, DSR 0.0000
- eth-dir-1h tsmom-v1/ETHUSDT/1h: T 4392, SR -0.357234, DSR 0.0000
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h: T 4392, SR -0.361953, DSR 0.0000
- eth-dir-1h takerflow-v1/ETHUSDT/1h: T 4392, SR -0.371901, DSR 0.0000
- eth-dir-1h vote4-v1/ETHUSDT/1h: T 4392, SR -0.368898, DSR 0.0000
- eth-dir-4h trend-ema-v1/ETHUSDT/4h: T 1098, SR -0.148790, DSR 0.0000
- eth-dir-4h tsmom-v1/ETHUSDT/4h: T 1098, SR -0.216112, DSR 0.0000
- eth-dir-4h meanrev-z-v1/ETHUSDT/4h: T 1098, SR -0.168410, DSR 0.0000
- eth-dir-4h takerflow-v1/ETHUSDT/4h: T 1098, SR -0.169270, DSR 0.0000
- eth-dir-4h vote4-v1/ETHUSDT/4h: T 1098, SR -0.160098, DSR 0.0000
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h: T 4392, SR -0.473583, DSR 0.0000
- bnb-dir-1h tsmom-v1/BNBUSDT/1h: T 4389, SR -0.456680, DSR 0.0000
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h: T 4392, SR -0.479103, DSR 0.0000
- bnb-dir-1h takerflow-v1/BNBUSDT/1h: T 4392, SR -0.465093, DSR 0.0000
- bnb-dir-1h vote4-v1/BNBUSDT/1h: T 4389, SR -0.476375, DSR 0.0000
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h: T 1098, SR -0.254377, DSR 0.0000
- bnb-dir-4h tsmom-v1/BNBUSDT/4h: T 1098, SR -0.255944, DSR 0.0000
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h: T 1098, SR -0.223181, DSR 0.0000
- bnb-dir-4h takerflow-v1/BNBUSDT/4h: T 1098, SR -0.254428, DSR 0.0000
- bnb-dir-4h vote4-v1/BNBUSDT/4h: T 1098, SR -0.265357, DSR 0.0000
- sol-dir-1h trend-ema-v1/SOLUSDT/1h: T 4392, SR -0.323710, DSR 0.0000
- sol-dir-1h tsmom-v1/SOLUSDT/1h: T 4386, SR -0.315035, DSR 0.0000
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h: T 4392, SR -0.334233, DSR 0.0000
- sol-dir-1h takerflow-v1/SOLUSDT/1h: T 4392, SR -0.312931, DSR 0.0000
- sol-dir-1h vote4-v1/SOLUSDT/1h: T 4386, SR -0.321633, DSR 0.0000
- sol-dir-4h trend-ema-v1/SOLUSDT/4h: T 1098, SR -0.175010, DSR 0.0000
- sol-dir-4h tsmom-v1/SOLUSDT/4h: T 1090, SR -0.142814, DSR 0.0000
- sol-dir-4h meanrev-z-v1/SOLUSDT/4h: T 1098, SR -0.177242, DSR 0.0000
- sol-dir-4h takerflow-v1/SOLUSDT/4h: T 1098, SR -0.148300, DSR 0.0000
- sol-dir-4h vote4-v1/SOLUSDT/4h: T 1090, SR -0.182803, DSR 0.0000

## PBO by CSCV (C-3)

- 1h: 4392 rows, 12870 splits, PBO 0.7628, logit at zero in 0 splits
- 4h: 1098 rows, 12870 splits, PBO 0.8375, logit at zero in 0 splits

## Benjamini-Hochberg list (TEST, level 0.05, over the 280 cells; a cell without k_test counts with p = 1)

- bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b3
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b3
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b3
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b1
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b3
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b2
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b3
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b3
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b2
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b1
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b2
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b2
- sol-dir-1h vote4-v1/SOLUSDT/1h/up-b2
- eth-dir-4h tsmom-v1/ETHUSDT/4h/up-b2
- sol-dir-1h vote4-v1/SOLUSDT/1h/down-b1
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b1
- sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b2
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b3
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b1
- sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b1
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/up-b3
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b3
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b3
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/down-b1
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b3
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b3
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b1
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b2
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b2
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b1
- eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b2
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b1
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b1
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b3
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b3
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/down-b2
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b3
- bnb-dir-1h meanrev-z-v1/BNBUSDT/1h/down-b2
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b2
- sol-dir-1h vote4-v1/SOLUSDT/1h/down-b3
- eth-dir-4h takerflow-v1/ETHUSDT/4h/down-b3
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/down-b1
- sol-dir-4h takerflow-v1/SOLUSDT/4h/up-b3
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b2
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b1
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/up-b1
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b3
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b3
- eth-dir-1h trend-ema-v1/ETHUSDT/1h/down-b3
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b1
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b1
- eth-dir-1h tsmom-v1/ETHUSDT/1h/up-b2
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b2
- sol-dir-1h tsmom-v1/SOLUSDT/1h/down-b1
- sol-dir-1h tsmom-v1/SOLUSDT/1h/up-b2
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b1
- bnb-dir-1h takerflow-v1/BNBUSDT/1h/up-b3
- bnb-mae-up-1h ewma-vol-hw-v1/BNBUSDT/1h/b0
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b1
- eth-dir-4h vote4-v1/ETHUSDT/4h/up-b1
- bnb-dir-1h vote4-v1/BNBUSDT/1h/down-b2
- eth-dir-1h tsmom-v1/ETHUSDT/1h/down-b1
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/down-b2
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/down-b2
- eth-dir-1h vote4-v1/ETHUSDT/1h/down-b2
- btc-dir-4h tsmom-v1/BTCUSDT/4h/up-b2
- sol-dir-1h takerflow-v1/SOLUSDT/1h/down-b2
- eth-dir-1h takerflow-v1/ETHUSDT/1h/down-b1
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b1
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b3
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b3
- btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b2
- eth-dir-4h tsmom-v1/ETHUSDT/4h/down-b3
- btc-dir-1h vote4-v1/BTCUSDT/1h/down-b1
- sol-dir-4h vote4-v1/SOLUSDT/4h/up-b2
- sol-dir-1h takerflow-v1/SOLUSDT/1h/up-b3
- bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b1
- btc-dir-1h vote4-v1/BTCUSDT/1h/up-b1
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b2
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b1
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/down-b1
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b1
- btc-dir-4h takerflow-v1/BTCUSDT/4h/down-b3
- bnb-dir-1h vote4-v1/BNBUSDT/1h/up-b2
- btc-dir-1h tsmom-v1/BTCUSDT/1h/up-b1
- btc-dir-1h trend-ema-v1/BTCUSDT/1h/up-b2
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b2
- sol-dir-1h trend-ema-v1/SOLUSDT/1h/up-b3
- sol-mae-up-1h ewma-vol-hw-v1/SOLUSDT/1h/b0
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b3
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b1
- eth-dir-1h takerflow-v1/ETHUSDT/1h/up-b2
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/up-b1
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/down-b1
- eth-dir-1h vote4-v1/ETHUSDT/1h/up-b2
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b1
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/up-b1
- sol-dir-4h trend-ema-v1/SOLUSDT/4h/up-b2
- btc-dir-1h takerflow-v1/BTCUSDT/1h/up-b3
- btc-dir-1h tsmom-v1/BTCUSDT/1h/down-b2
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b1
- btc-dir-1h takerflow-v1/BTCUSDT/1h/down-b2
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/up-b3
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/down-b1
- bnb-dir-4h tsmom-v1/BNBUSDT/4h/down-b3
- bnb-dir-1h trend-ema-v1/BNBUSDT/1h/up-b2
- btc-dir-4h tsmom-v1/BTCUSDT/4h/down-b3
- sol-dir-1h meanrev-z-v1/SOLUSDT/1h/down-b1
- bnb-dir-1h tsmom-v1/BNBUSDT/1h/up-b1
- btc-dir-1h vote4-v1/BTCUSDT/1h/up-b2
- eth-dir-1h meanrev-z-v1/ETHUSDT/1h/down-b1
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b3
- bnb-dir-4h takerflow-v1/BNBUSDT/4h/down-b1
- bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b3
- btc-dir-4h meanrev-z-v1/BTCUSDT/4h/down-b1
- bnb-dir-4h vote4-v1/BNBUSDT/4h/up-b1
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b1
- bnb-dir-4h meanrev-z-v1/BNBUSDT/4h/down-b2
- bnb-dir-4h trend-ema-v1/BNBUSDT/4h/up-b1
- btc-dir-4h vote4-v1/BTCUSDT/4h/down-b2
- btc-dir-1h vote4-v1/BTCUSDT/1h/down-b2
- bnb-dir-4h vote4-v1/BNBUSDT/4h/down-b2
- sol-dir-4h tsmom-v1/SOLUSDT/4h/up-b3
- btc-dir-4h trend-ema-v1/BTCUSDT/4h/down-b3
- btc-dir-1h meanrev-z-v1/BTCUSDT/1h/up-b2

## Range e_commit (every range cell with a qhat; intent 0; COMMIT when h > 0 and the band 2h fits in tauInterval)

- btc-range-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0294, 129 commits, 0 misses
- btc-range-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2887, 1268 commits, 11 misses
- btc-range-1h ewma-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.7507, 3297 commits, 27 misses
- btc-range-1h realized-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0200, 88 commits, 0 misses
- btc-range-1h realized-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2443, 1073 commits, 7 misses
- btc-range-1h realized-vol-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.7240, 3180 commits, 21 misses
- btc-range-1h parkinson-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0173, 76 commits, 0 misses
- btc-range-1h parkinson-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2905, 1276 commits, 13 misses
- btc-range-1h parkinson-hw-v1/BTCUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.7885, 3463 commits, 30 misses
- btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 (region), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 (region), tauInterval 0.02: COMMIT share 0.0073, 8 commits, 0 misses
- btc-range-4h ewma-vol-hw-v1/BTCUSDT/4h/b0 (region), tauInterval 0.04: COMMIT share 0.1448, 159 commits, 1 misses
- btc-range-4h realized-vol-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- btc-range-4h realized-vol-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0036, 4 commits, 0 misses
- btc-range-4h realized-vol-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.1403, 154 commits, 1 misses
- btc-range-4h parkinson-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- btc-range-4h parkinson-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0046, 5 commits, 0 misses
- btc-range-4h parkinson-hw-v1/BTCUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.1494, 164 commits, 1 misses
- eth-range-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0034, 15 commits, 0 misses
- eth-range-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.1184, 520 commits, 7 misses
- eth-range-1h ewma-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.5280, 2319 commits, 24 misses
- eth-range-1h realized-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0023, 10 commits, 1 misses
- eth-range-1h realized-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.1204, 529 commits, 10 misses
- eth-range-1h realized-vol-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.5524, 2426 commits, 31 misses
- eth-range-1h parkinson-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0032, 14 commits, 0 misses
- eth-range-1h parkinson-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.1061, 466 commits, 8 misses
- eth-range-1h parkinson-hw-v1/ETHUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.5760, 2530 commits, 29 misses
- eth-range-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h ewma-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0355, 39 commits, 0 misses
- eth-range-4h realized-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h realized-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h realized-vol-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0310, 34 commits, 0 misses
- eth-range-4h parkinson-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h parkinson-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- eth-range-4h parkinson-hw-v1/ETHUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0273, 30 commits, 0 misses
- bnb-range-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0162, 71 commits, 2 misses
- bnb-range-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2489, 1093 commits, 18 misses
- bnb-range-1h ewma-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.8128, 3570 commits, 33 misses
- bnb-range-1h realized-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0125, 55 commits, 0 misses
- bnb-range-1h realized-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2234, 981 commits, 20 misses
- bnb-range-1h realized-vol-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.8119, 3566 commits, 40 misses
- bnb-range-1h parkinson-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0089, 39 commits, 0 misses
- bnb-range-1h parkinson-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.2514, 1104 commits, 23 misses
- bnb-range-1h parkinson-hw-v1/BNBUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.8634, 3792 commits, 51 misses
- bnb-range-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- bnb-range-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0009, 1 commits, 0 misses
- bnb-range-4h ewma-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.1211, 133 commits, 4 misses
- bnb-range-4h realized-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- bnb-range-4h realized-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- bnb-range-4h realized-vol-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0893, 98 commits, 5 misses
- bnb-range-4h parkinson-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- bnb-range-4h parkinson-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- bnb-range-4h parkinson-hw-v1/BNBUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0565, 62 commits, 4 misses
- sol-range-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0007, 3 commits, 0 misses
- sol-range-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.0854, 375 commits, 8 misses
- sol-range-1h ewma-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.5335, 2343 commits, 35 misses
- sol-range-1h realized-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0005, 2 commits, 0 misses
- sol-range-1h realized-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.0779, 342 commits, 8 misses
- sol-range-1h realized-vol-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.5266, 2313 commits, 35 misses
- sol-range-1h parkinson-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.01: COMMIT share 0.0002, 1 commits, 0 misses
- sol-range-1h parkinson-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.02: COMMIT share 0.0583, 256 commits, 5 misses
- sol-range-1h parkinson-hw-v1/SOLUSDT/1h/b0 (silence), tauInterval 0.04: COMMIT share 0.4986, 2190 commits, 29 misses
- sol-range-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h ewma-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0282, 31 commits, 1 misses
- sol-range-4h realized-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h realized-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h realized-vol-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0437, 48 commits, 2 misses
- sol-range-4h parkinson-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.01: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h parkinson-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.02: COMMIT share 0.0000, 0 commits, 0 misses
- sol-range-4h parkinson-hw-v1/SOLUSDT/4h/b0 (silence), tauInterval 0.04: COMMIT share 0.0128, 14 commits, 1 misses

