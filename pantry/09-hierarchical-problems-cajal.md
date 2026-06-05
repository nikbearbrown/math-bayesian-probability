# CAJAL Figure Plans — Chapter 09: Hierarchical Problems

**Chapter:** 09 — Hierarchical Problems
**Figures planned:** 2
**Plan date:** 2026-06-01

---

## Figure 09.1 — Complete Pooling vs. No Pooling vs. Partial Pooling: School Estimates

**Suggested filename:** 09-three-pooling-strategies.svg
**Figure type:** Comparison panels (three-panel dot plot)

**One-sentence concept:** Three estimation strategies applied to the same 30-school dataset produce dramatically different school-level estimates, with no pooling generating wildly unstable values for small schools and partial pooling producing calibrated shrinkage toward the district mean.

**S — Specification:** Three-panel horizontal layout; single textbook column (89 mm wide) × approx. 160 mm tall at 300 DPI; vector SVG.

**C — Content:**
Six representative schools plotted across all three panels (not all 30 — 6 covers the full range of sample sizes):
- School A (n = 200), School B (n = 45), School C (n = 12), School D (n = 8), School E (n = 6) — five schools chosen to span the full size range, plus the district grand mean reference line (≈ 72%).
- Panel 1 — Complete pooling: all schools shown at the district grand mean (72%); all dots collapse to one horizontal position.
- Panel 2 — No pooling: raw means plotted with large uncertainty bars; School C at 92%, School D at 61%, School E visibly unstable (wide error bar spanning 40+ points).
- Panel 3 — Partial pooling (Bayesian posterior means): small-school dots pulled toward 72%; large-school dots barely moved; uncertainty bars narrow monotonically as n increases.
- A vertical dashed reference line at 72% (grand mean) appears in all three panels.

**O — Organization:** Three vertical panels arranged left-to-right, labeled "Complete Pooling," "No Pooling," "Partial Pooling." Within each panel: y-axis = school identifier (A through E, sorted by sample size descending); x-axis = performance estimate (55% to 95%). Uncertainty bars are horizontal (CrI or SE). Panels share the same x-axis scale so direct visual comparison is valid. No panel uses a different baseline. Left-to-right flow encodes increasing methodological sophistication.

**P — Presentation:**
- Complete-pooling dots: neutral gray (#999999) — all identical, no meaningful variation.
- No-pooling dots and bars: Vermillion #D55E00 — signals instability/problem.
- Partial-pooling dots and bars: Bluish Green #009E73 — signals correct/improved inference.
- Grand-mean reference dashed line: Black #000000, weight 0.5 pt.
- Uncertainty bars: same color as dots, weight 1 pt.
- All panels white background; no grid fill; axis spines only on left (y) and bottom (x).

**E — Exclusions:**
- Do not show all 30 schools — only 5 representative schools plus the grand mean line.
- Do not show regression lines, posterior density curves, or MCMC trace plots.
- Do not show the shrinkage factor formula or any mathematical notation.
- Do not annotate individual bars with numeric values (kept as unlabeled figure; captions carry values).
- Do not use 3D perspective, drop shadows, or gradient fills.
- Do not include a legend for n (sample size) — panel labels and caption carry this.
- Do not show the Bayesian CrI separately from the REML SE in this figure — this figure is about strategy comparison, not model comparison (Figure 09.2 handles that).

**Caption (draft):** Three estimation strategies applied to five representative schools (sample sizes 6–200) from the 30-school district dataset; the vertical dashed line marks the district grand mean (72%); partial pooling shrinks small-school estimates toward the mean while preserving large-school estimates, avoiding both the erasure of complete pooling and the instability of no pooling.

**Accuracy check (figure-checker):**
- School A (n = 200) dot in the partial-pooling panel must be very close to its raw mean (≈ 74%), not pulled substantially toward 72% — large schools barely move.
- School D or E (n = 6–8) dots in the partial-pooling panel must be pulled visibly toward 72% — small schools shrink substantially.
- The no-pooling uncertainty bars for n = 6–8 schools must be substantially wider than for n = 200 — if all bars are similar width, the instability story is lost.
- The x-axis must start at a value below 55% and extend to at least 95% to accommodate the no-pooling outliers without cutting them off.
- No school's partial-pooling estimate may lie farther from the grand mean than its no-pooling estimate (shrinkage always moves toward the mean, never away).

---

## Figure 09.2 — Shrinkage in Action: Raw Means vs. Bayesian Posterior Means with Uncertainty

**Suggested filename:** 09-shrinkage-dotplot.svg
**Figure type:** Statistical / quantitative — connected dot plot (Cleveland dot chart with arrows)

**One-sentence concept:** The Bayesian hierarchical model pulls each school's posterior mean toward the district grand mean by an amount proportional to the school's small sample size, and the posterior uncertainty (CrI width) is wider for smaller schools — both effects made visible simultaneously.

**S — Specification:** Single-panel; full textbook column (170 mm wide) × approx. 140 mm tall at 300 DPI; vector SVG.

**C — Content:**
Four named schools from the chapter's canonical table:
- School A: n = 200, raw mean = 74.2%, posterior mean = 74.1%, 95% CrI [71.3%, 76.9%].
- School B: n = 12, raw mean = 81.5%, posterior mean = 79.4%, 95% CrI [73.1%, 85.7%].
- School C: n = 8, raw mean = 92.0%, posterior mean = 83.4%, 95% CrI [74.2%, 92.8%].
- School D: n = 6, raw mean = 61.0%, posterior mean = 67.6%, 95% CrI [56.9%, 78.3%].
Each school has: one open circle (raw mean), one filled circle (posterior mean), one horizontal CrI bar centered on the posterior mean, and one arrow connecting the raw mean to the posterior mean showing direction and magnitude of shrinkage.
Grand mean reference line at 72% (vertical dashed).

**O — Organization:** Single panel. Y-axis lists schools A, B, C, D top to bottom (sorted by sample size descending). X-axis = performance estimate, 50%–100%, zero-referenced only if the data range requires it (50% lower bound is acceptable since performance is bounded 0–100 and values cluster 60–95%). Arrow points from open circle (raw mean) to filled circle (posterior mean); arrow length encodes shrinkage magnitude. CrI bar extends from posterior mean ± half-width. The four elements per school are: open dot, filled dot, connecting arrow, horizontal CrI bar. Total labeled components: 4 schools × labeled axis + grand mean line = well within 8-component budget per school row.

**P — Presentation:**
- Raw mean open circles: Orange #E69F00 — secondary element, reference point.
- Posterior mean filled circles: Blue #0072B2 — primary structural anchor.
- CrI bars: Blue #0072B2, weight 1.5 pt, with small terminal caps.
- Shrinkage arrows: Vermillion #D55E00 — highlights the movement/displacement.
- Grand mean dashed line: Black #000000, weight 0.5 pt.
- Background: white; no fill; axis spines only.

**E — Exclusions:**
- Do not show REML standard errors or REML estimates in this figure — this is the Bayesian model's output only. The comparison with REML is handled verbally in the text and in the side-by-side table.
- Do not show all 30 schools — only the four canonical table schools.
- Do not show posterior density curves or histograms — CrI bars only.
- Do not annotate the arrows with numeric shrinkage values.
- Do not show the shrinkage factor formula λ = τ²/(τ² + σ²/n) in the figure.
- Do not include axis tick marks at values outside the data range.
- Do not show 3D effects, gradients, or drop shadows.

**Caption (draft):** Shrinkage of school estimates toward the district grand mean (dashed line, 72%) under the Bayesian hierarchical model; open circles are raw school means, filled circles are posterior means, arrows show the direction and magnitude of shrinkage, and horizontal bars are 95% credible intervals — School A (n = 200) barely moves while School D (n = 6) moves substantially and carries a 21-point-wide interval.

**Accuracy check (figure-checker):**
- All four posterior means must match the chapter table exactly: 74.1%, 79.4%, 83.4%, 67.6%.
- All four 95% CrI endpoints must match the chapter table: [71.3, 76.9], [73.1, 85.7], [74.2, 92.8], [56.9, 78.3].
- School A's arrow must be shorter than Schools B, C, D — it shrinks the least.
- School D's arrow must point right (from 61.0% toward 67.6%, i.e., toward 72%), not left.
- School C's arrow must point left (from 92.0% toward 83.4%, toward 72%).
- CrI widths must be monotonically wider from School A to School D: 5.6, 12.6, 18.6, 21.4 points.
- The grand mean reference line must fall at 72% on the x-axis — not at 70% or 74%.
- X-axis must not start above 50% (School D's CrI lower bound is 56.9%).
