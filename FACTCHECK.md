# FACTCHECK — math-bayesian-probability

**Run date:** 2026-06-01
**Checker:** automated pre-publication pass (Claude Sonnet 4.6)
**Scope:** all files in `chapters/*.md`

---

## Summary

**15 items total** flagged with `[verify]`, `[AGING]`, or `[verify citation...]`

- **CITATION/STAT: 12** — 9 CONFIRMED, 1 CORRECTED, 1 UNCONFIRMED (partial), 1 NOTE (no error but attribution nuance)
- **PRODUCT/PLATFORM: 2** — deferred to publication-time check
- **CONTESTED: 1**

Additional load-bearing citations verified (not flagged by author but listed in instructions): Ioannidis 2005, Wasserstein & Lazar 2016, OSC 2015, Morey et al. 2016, Kruschke 2013, Akaike 1974, Schwarz 1978, Kass & Raftery 1995, Gelman & Carlin 2014, Efron & Morris 1977, Scott & Varian 2014 — all CONFIRMED.

---

## Item Table

| # | Chapter file | Flagged claim | Type | Verdict | Action needed |
|---|---|---|---|---|---|
| 1 | `04-comparing-two-groups.md` line 122 | Gilbert et al. (2016) criticized OSC 2015 design, arguing some failed replications reflect context differences | CITATION/STAT | CONFIRMED | Supply full citation: Gilbert, D. T., King, G., Pettigrew, S., & Wilson, T. D. (2016). Comment on "Estimating the reproducibility of psychological science." *Science*, 351(6277), 1037. https://doi.org/10.1126/science.aad7243 |
| 2 | `04-comparing-two-groups.md` line 347 | Gilbert et al. (2016) [duplicate flag, same claim as #1] | CITATION/STAT | CONFIRMED (same as #1) | Remove duplicate `[verify]` tag once citation is supplied |
| 3 | `05-regression-both-ways.md` line 266 | Slope prior Normal(0.10, 0.05) described as "based on labor economics literature"; ~10% returns to schooling | CITATION/STAT | CONFIRMED — with note | The ~10% figure is in the right ballpark (Mincer literature estimates typically 5–12% per year across countries/periods; 10% is a reasonable round figure for US estimates). Suggest adding a Mincer (1974) or Card (1999) citation for anchoring. No correction needed. |
| 4 | `05-regression-both-ways.md` line 408 | Gelman, Hill & Vehtari (2020) *Regression and Other Stories* `[verify publication details]` | CITATION/STAT | CONFIRMED | Year and publisher confirmed: Cambridge University Press, 2020. Remove `[verify]` tag; citation is correct. |
| 5 | `07-priors.md` line 299 | "The FDA's 2026 draft guidance [verify] moves toward endorsing Bayesian methods with conditions" | CITATION/STAT | CONFIRMED — with correction | The FDA issued a draft guidance titled "Use of Bayesian Methodology in Clinical Trials of Drug and Biological Products" published January 9, 2026 in the Federal Register (FDA-2025-D-3217). This matches the claim. However, the citation tag says "FDA 2019 [verify]" in Ch 13 (item 9 below), which refers to a different (2019) guidance for medical devices — these are two distinct documents. The Ch 07 reference is to the correct 2026 draft. |
| 6 | `08-when-data-is-sparse.md` line 61 | OSC 2015, *Science*, 349: aac4716 — "61 of 100 published psychology findings failed to replicate" | CITATION/STAT | CONFIRMED — with note | Citation details confirmed: Open Science Collaboration (2015), *Science*, 349(6251), aac4716. DOI: 10.1126/science.aac4716. The number "61 of 100 failed to replicate" is consistent with the published 36% significant-replication rate (64 failed to produce significant results; the "61" figure uses a slightly different operationalization). This discrepancy between Ch 08 ("61 failed") and Ch 04 ("36% produced significant results") is consistent with the OSC paper itself, which reports multiple metrics. Recommend Ch 08 add the qualifier: "61 of 100 failed to replicate (using the significance threshold criterion; the OSC reports 36% replication on that metric across the 97 experiments that used significance tests)." Not a factual error, but could cause reader confusion. |
| 7 | `08-when-data-is-sparse.md` line 318 (sources note) | OSC 2015 `[verify citation: Science, 349:aac4716]` — same paper as #6 | CITATION/STAT | CONFIRMED (same as #6) | Remove `[verify]` tags; citation is correct. |
| 8 | `08-when-data-is-sparse.md` line 318 (sources note) | James & Stein (1961) "Estimation with Quadratic Loss," Proceedings of the Fourth Berkeley Symposium | CITATION/STAT | CONFIRMED | James, W., & Stein, C. (1961). Estimation with quadratic loss. *Proceedings of the Fourth Berkeley Symposium on Mathematical Statistics and Probability*, Vol. 1, pp. 361–379. University of California Press. This is the correct venue and title. |
| 9 | `10-time-and-sequence.md` line 264 (M4 Competition) | M4 Competition: Makridakis, Spiliotis & Assimakopoulos 2020 `[verify]`; "M5 Competition 2020" | CITATION/STAT | CONFIRMED — with note | Makridakis, S., Spiliotis, E., & Assimakopoulos, V. (2020). The M4 Competition: 100,000 time series and 61 forecasting methods. *International Journal of Forecasting*, 36(1), 54–74. DOI: 10.1016/j.ijforecast.2019.04.014. CONFIRMED. M5 Competition: the M5 results were published separately — Makridakis et al. (2022), *International Journal of Forecasting*, 38(4). If citing M5 for 2020, the competition ran in 2020 but the main results paper appeared in 2022; clarify or cite the M5 overview paper directly. |
| 10 | `10-time-and-sequence.md` line 326 | Amazon Chronos `[verify publication status]` | PRODUCT/PLATFORM | DEFER TO PUBLICATION-TIME CHECK — with note | As of June 2026: Chronos (Ansari et al., 2024) was published as an arXiv preprint (arXiv:2403.07815) in March 2024 and had not appeared in a peer-reviewed journal as of the author's writing. Chronos-2 was released Oct 2025. Status may change before print. |
| 11 | `10-time-and-sequence.md` line 326 | Nixtla TimeGPT `[verify]` | PRODUCT/PLATFORM | DEFER TO PUBLICATION-TIME CHECK — with note | As of June 2026: TimeGPT-1 (Garza, Challu & Mergenthaler-Canseco) exists as arXiv preprint 2310.03589, not peer-reviewed in a major journal. Status ongoing. |
| 12 | `10-time-and-sequence.md` line 340 (sources note) | "Forecasting competition accuracy claims refer to M4/M5 competitions [verify full Makridakis et al. 2020 citation before print]" | CITATION/STAT | CONFIRMED | M4 citation confirmed (see item 9). Full citation to add: Makridakis, S., Spiliotis, E., & Assimakopoulos, V. (2020). *International Journal of Forecasting*, 36(1), 54–74. |
| 13 | `11-classification-and-decision.md` line 109 | Normal(0, 2.5) prior on log-odds coefficients attributed to "Gelman and colleagues 2008 [verify]" | CITATION/STAT | CORRECTED — see action | The 2008 paper (Gelman, Jakulin, Pittau, & Su, *Annals of Applied Statistics*, 2(4), 1360–1383) recommends a **Cauchy(0, 2.5)** prior (Student-t with 1 df) as the default, not a Normal(0, 2.5). Normal(0, 2.5²) is used as a default in Stan/rstanarm and is widely applied, but that specific choice is from later Stan defaults documentation, not from the 2008 paper itself. The claim is defensible in practice; the attribution is imprecise. Either: (a) keep Normal(0, 2.5) and cite the Stan/rstanarm defaults instead; or (b) change to Cauchy(0, 2.5) and cite Gelman et al. 2008. |
| 14 | `13-choosing.md` line 112 | "The FDA is aware that this practice exists; the data is analyzed both ways for different purposes (FDA 2019 [verify])" | CITATION/STAT | CONFIRMED — with note | An FDA guidance document does exist from 2019: "Adaptive Designs for Clinical Trials of Drugs and Biologics" (finalized November 2019), which acknowledges Bayesian adaptive designs. However, the most directly relevant document for the "both-ways analysis" claim is the **2018** FDA guidance "Guidance for the Use of Bayesian Statistics in Medical Device Clinical Trials" (not 2019 specifically). The 2026 draft guidance is the most recent and most relevant. Recommend citing: FDA (2018, 2019, or 2026) with the specific guidance title, since "FDA 2019" alone is ambiguous across multiple guidance documents. |
| 15 | `13-choosing.md` line 112 | `[AGING]` tag on Ch 10's Still Puzzling section re: deep learning models displacing ARIMA/BSTS | CONTESTED | MARK AS EDITORIAL NOTE | The author explicitly flags this as "genuinely unclear as of 2026." This is a fair description; the M4/M5 evidence supports the chapter's framing (simple methods competitive on accuracy). No correction needed; retain the AGING note and verify model landscape at final submission. |

---

## Load-bearing Citations Verified (not flagged by author)

All of the following were verified against web sources and found correct:

| Citation as written in chapter | Verdict |
|---|---|
| Ioannidis, J. P. A. (2005). *PLoS Medicine*, 2(8), e124. DOI: 10.1371/journal.pmed.0020124 | CONFIRMED |
| Wasserstein, R. L., & Lazar, N. A. (2016). *The American Statistician*, 70(2), 129–133. DOI: 10.1080/00031305.2016.1154108 | CONFIRMED |
| Open Science Collaboration (2015). *Science*, 349, aac4716. DOI: 10.1126/science.aac4716 | CONFIRMED |
| Morey, R. D., et al. (2016). *Psychonomic Bulletin & Review*, 23(1), 103–123. DOI: 10.3758/s13423-015-0947-8 | CONFIRMED |
| Kruschke, J. K. (2013). *Journal of Experimental Psychology: General*, 142(2), 573–603. DOI: 10.1037/a0029146 | CONFIRMED |
| Akaike, H. (1974). *IEEE Transactions on Automatic Control*, 19(6), 716–723. DOI: 10.1109/TAC.1974.1100705 | CONFIRMED |
| Schwarz, G. (1978). *Annals of Statistics*, 6(2), 461–464. DOI: 10.1214/aos/1176344136 | CONFIRMED |
| Kass, R. E., & Raftery, A. E. (1995). *Journal of the American Statistical Association*, 90(430), 773–795. DOI: 10.1080/01621459.1995.10476572 | CONFIRMED |
| Gelman, A., & Carlin, J. (2014). *Perspectives on Psychological Science*, 9(6), 641–651. DOI: 10.1177/1745691614551642 | CONFIRMED |
| Efron, B., & Morris, C. (1977). Stein's paradox in statistics. *Scientific American*, 236(5), 119–127. DOI: 10.1038/scientificamerican0577-119 | CONFIRMED |
| Scott, S. L., & Varian, H. R. (2014). Predicting the present with Bayesian structural time series. *International Journal of Mathematical Modelling and Numerical Optimisation*, 5(1/2), 4–23. | CONFIRMED |

---

## Corrections to Apply

1. **Ch 04 and Ch 08 — Gilbert et al. (2016):** Replace bare `[verify]` tag with full citation: Gilbert, D. T., King, G., Pettigrew, S., & Wilson, T. D. (2016). Comment on "Estimating the reproducibility of psychological science." *Science*, 351(6277), 1037. https://doi.org/10.1126/science.aad7243

2. **Ch 05 line 408 — Gelman, Hill & Vehtari (2020):** Remove `[verify publication details]` — year and publisher confirmed correct.

3. **Ch 08 lines 61 and 318 — OSC 2015:** Remove `[verify citation details before citing]` and `[verify citation]` tags. Citation is correct: Open Science Collaboration (2015), *Science*, 349(6251), aac4716. Consider adding a parenthetical noting the 36% vs. 61 discrepancy (two different operationalizations of replication success used in different chapters).

4. **Ch 10 line 264 — M4 Competition:** Remove `[verify]`. Full citation: Makridakis, S., Spiliotis, E., & Assimakopoulos, V. (2020). *International Journal of Forecasting*, 36(1), 54–74. DOI: 10.1016/j.ijforecast.2019.04.014. For M5, add: Makridakis, S., et al. (2022). M5 accuracy competition: Results, findings, and conclusions. *International Journal of Forecasting*, 38(4), 1346–1364.

5. **Ch 11 line 109 — Gelman et al. 2008 prior attribution (HIGHEST-PRIORITY CORRECTION):** The chapter attributes Normal(0, 2.5) to Gelman et al. 2008, but that paper recommends Cauchy(0, 2.5). Either change the prior to Cauchy(0, 2.5) and cite Gelman et al. 2008 accurately, or keep Normal(0, 2.5) and cite the rstanarm/Stan documentation instead. The current state is a factual misattribution. Full citation if keeping: Gelman, A., Jakulin, A., Pittau, M. G., & Su, Y.-S. (2008). A weakly informative default prior distribution for logistic and other regression models. *Annals of Applied Statistics*, 2(4), 1360–1383.

6. **Ch 13 line 112 — FDA 2019:** The citation "FDA 2019" is ambiguous (multiple 2019 guidance documents exist). Add the specific document title. Most relevant: either the 2019 adaptive designs guidance for drugs/biologics, or the 2018 Bayesian statistics guidance for medical devices. The new 2026 draft guidance (FDA-2025-D-3217) is now the most prominent and directly relevant document.

---

## Deferred to Publication-Time Check

1. **Ch 10 — Amazon Chronos publication status:** arXiv:2403.07815 (2024). Confirm peer-reviewed publication status before print; Chronos-2 released Oct 2025 may also be relevant.

2. **Ch 10 — Nixtla TimeGPT publication status:** arXiv:2310.03589. Confirm peer-reviewed status before print.

---

## Highest-Risk Unverified Claim

**Ch 11, line 109 — the Normal(0, 2.5) prior attribution to Gelman et al. (2008).** This is the highest-risk item because: (a) it is presented as a factual citation of a specific paper; (b) the actual paper recommends Cauchy(0, 2.5) not Normal; (c) it will be checked by statistically sophisticated readers who know the 2008 paper well; and (d) it affects a teaching moment about prior choice in logistic regression. This needs resolution before publication — either correct the prior distribution or correct the citation.
