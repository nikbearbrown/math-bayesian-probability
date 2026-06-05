# CAJAL Figure Plans — Chapter 11: Classification and Decision

**Chapter:** 11 — Classification and Decision
**Figures planned:** 3
**Plan date:** 2026-06-01

---

## Figure 11.1 — Expected Cost vs. Threshold: Finding the Optimal p*

**Suggested filename:** 11-expected-cost-vs-threshold.svg
**Figure type:** Statistical / quantitative — line chart with annotated optimum

**One-sentence concept:** For the 5:1 loan-default cost ratio, total expected cost per application is minimized at threshold p* = 1/6 ≈ 0.167 — well below the conventional 0.5 default — and this optimum is derivable from the cost structure alone, not from the model's accuracy.

**S — Specification:** Single-panel; single textbook column (89 mm wide) × approx. 100 mm tall at 300 DPI; vector SVG.

**C — Content:**
- A smooth curve showing expected cost per application (y-axis, in units of c_FP) as the decision threshold varies from 0 to 1 (x-axis).
- The curve is U-shaped: high expected cost near threshold = 0 (approve everyone, many false negatives), descends to a minimum near p* ≈ 0.167, then rises again as threshold increases toward 1.0 (decline everyone, many false positives).
- A vertical dashed marker line at p* = 0.167 labeled "p* = 1/(1+5) = 0.167."
- A second vertical dashed marker line at p = 0.5 labeled "default = 0.5."
- A horizontal dashed line from the minimum of the curve to the y-axis showing the minimum expected cost value (142 units per 100 applications from chapter text).
- A point marker at threshold = 0.5 on the curve showing the higher expected cost (189 units).
- Both cost values annotated with small labels adjacent to their horizontal guidelines.

**O — Organization:** Single panel. X-axis: threshold p, range 0 to 1, tick marks at 0, 0.167, 0.5, 1.0. Y-axis: expected cost per 100 applications (units = multiples of c_FP), range from 0 upward, labeled in approximate units (0, 100, 200). The U-shaped expected cost curve is the primary element. The two vertical markers divide the visible threshold axis into three zones: below p* (too permissive), optimal zone, above p* (too strict). The minimum is marked with a filled circle. The p = 0.5 point on the curve is marked with an open circle.

**P — Presentation:**
- Expected cost curve: Blue #0072B2, weight 2 pt — primary structural element.
- Optimal p* vertical dashed line: Bluish Green #009E73, weight 1 pt — signals the correct solution.
- Default p = 0.5 vertical dashed line: Vermillion #D55E00, weight 1 pt — signals the problematic convention.
- Minimum cost point on curve (filled circle): Bluish Green #009E73.
- Default cost point on curve (open circle): Vermillion #D55E00.
- Horizontal guideline from minimum to y-axis: Black #000000, weight 0.5 pt, dashed.
- Y-axis starts at zero (hard rule: bar-chart or quantitative figure; zero baseline required).
- Background: white; bottom and left spines only; no grid lines.

**E — Exclusions:**
- Do not show separate curves for c_FP and c_FN components — only the total expected cost curve.
- Do not show the ROC curve in this figure — Figure 11.2 handles ROC.
- Do not show the Bayesian posterior distribution over the threshold — this figure makes the decision-theoretic point; parameter uncertainty on the threshold is a text discussion.
- Do not label the three zones (too permissive / optimal / too strict) with bracket annotations — would exceed the 8-component limit; caption carries this.
- Do not show the derivation algebra (5p > 1−p) in the figure.
- Do not add a second y-axis.
- Do not use 3D, drop shadows, or gradient fills.
- Do not show tick marks at values other than 0, 0.167, 0.5, 1.0 on the x-axis.

**Caption (draft):** Expected cost per 100 loan applications as a function of decision threshold, given cost(false negative) = 5 × cost(false positive); the cost-optimal threshold p* = 1/(1+5) ≈ 0.167 (green dashed line, expected cost 142 units) is well below the conventional default of 0.5 (red dashed line, expected cost 189 units), a 25% reduction achieved without changing the model.

**Accuracy check (figure-checker):**
- The y-axis must start at zero — any non-zero baseline would distort the cost comparison.
- The curve minimum must occur at p ≈ 0.167, not at 0.5 or any other value — a minimum at 0.5 would imply equal costs, contradicting the stated 5:1 ratio.
- The expected cost at p = 0.167 must be lower than at p = 0.5 (142 < 189 from chapter text) — if the annotated values are reversed, the figure contradicts the chapter.
- The curve must be U-shaped (convex): monotonically decreasing from 0 to p*, then monotonically increasing from p* to 1 — a non-U shape would misrepresent the expected-cost function under logistic regression.
- The optimal threshold formula annotation "p* = 1/(1+5) = 0.167" must evaluate correctly: 1/(1+5) = 1/6 ≈ 0.167 — verify arithmetic.
- The general formula p* = c_FP / (c_FP + c_FN) with c_FP = 1, c_FN = 5 gives 1/6; annotating it as c_FN/(c_FP + c_FN) would be wrong.

---

## Figure 11.2 — ROC Curve with Cost-Optimal and Default Operating Points

**Suggested filename:** 11-roc-curve-operating-points.svg
**Figure type:** Statistical / quantitative — ROC curve with annotated threshold points

**One-sentence concept:** The ROC curve displays the full range of sensitivity/specificity trade-offs as the decision threshold varies, and marking both the default threshold (0.5) and the cost-optimal threshold (0.167) shows precisely what is gained and lost by moving to the decision-theoretically correct operating point.

**S — Specification:** Single-panel square; 89 mm × 89 mm at 300 DPI; vector SVG.

**C — Content:**
- A smooth ROC curve from (0, 0) to (1, 1) with AUC ≈ 0.76 shape (bowed toward the upper-left).
- A diagonal reference line from (0, 0) to (1, 1) representing a random classifier (AUC = 0.50).
- Two labeled operating points on the ROC curve:
  - Point A: threshold = 0.5 → (FPR = 0.15, TPR = 0.71) — chapter text values.
  - Point B: threshold = 0.167 → (FPR = 0.36, TPR = 0.91) — chapter text values.
- AUC label (0.76) placed in the upper-left interior of the figure.
- Axis labels: x = "False Positive Rate (1 − Specificity)"; y = "True Positive Rate (Sensitivity)"; both run 0 to 1.

**O — Organization:** Square panel with equal x- and y-axis scales (0 to 1 on both). The ROC curve is the primary element. The diagonal reference line establishes the random-classifier baseline. The two operating points are the key annotations. The operating points divide the curve into the "conventional" region (around 0.5) and the "cost-optimized" region (around 0.167). Axes must include tick marks at 0, 0.25, 0.50, 0.75, 1.00 on both. Total labeled components: ROC curve, diagonal line, Point A, Point B, AUC label = 5 elements — well within limit.

**P — Presentation:**
- ROC curve: Blue #0072B2, weight 2 pt — primary structural element.
- Diagonal reference line: neutral gray #999999, weight 1 pt, dashed.
- Operating Point A (threshold = 0.5, default): Vermillion #D55E00, filled circle, radius 4 pt — marks the problematic default.
- Operating Point B (threshold = 0.167, cost-optimal): Bluish Green #009E73, filled circle, radius 4 pt — marks the correct solution.
- AUC label: Black #000000.
- Axis spines: Black #000000; both axes start at zero (hard rule for quantitative axes).
- Background: white; bottom and left spines only; no grid fill.

**E — Exclusions:**
- Do not show a third operating point for "high-sensitivity alternative" — two points are the chapter's comparison; a third would exceed the focused message.
- Do not shade the area under the ROC curve — AUC shading with two operating points creates visual clutter that competes with the key comparison.
- Do not show confidence bands around the ROC curve.
- Do not annotate the curve with threshold values at every point — only at the two named operating points.
- Do not show the expected-cost calculation on this figure — Figure 11.1 handles cost; this figure handles discrimination.
- Do not use the same color for both operating points — they represent different decisions and must be visually distinct.
- Do not use 3D, drop shadows, or gradient fills.

**Caption (draft):** ROC curve for the loan-default logistic regression model (AUC = 0.76); the red circle marks the conventional threshold = 0.5 operating point (FPR = 0.15, TPR = 0.71); the green circle marks the cost-optimal threshold = 0.167 operating point (FPR = 0.36, TPR = 0.91); moving from the default to the cost-optimal point increases sensitivity (catches more defaulters) at the cost of a higher false positive rate, a trade-off that is correct given the 5:1 cost asymmetry.

**Accuracy check (figure-checker):**
- Both axes must start at zero and end at 1.0 — the ROC space is the unit square; any other range misrepresents the curve.
- The diagonal reference line must connect exactly (0, 0) to (1, 1) — any deviation misrepresents the random classifier baseline.
- The ROC curve must be monotonically non-decreasing from lower-left to upper-right — any portion that decreases violates the monotonicity property of ROC curves.
- Point A coordinates must match chapter text: (FPR = 0.15, TPR = 0.71) — verify against the performance table at threshold = 0.5.
- Point B coordinates must match chapter text: (FPR = 0.36, TPR = 0.91) — verify against the performance table at threshold = 0.167.
- Point B (lower threshold, 0.167) must appear higher and to the right of Point A (higher threshold, 0.5) on the ROC curve — lowering the threshold always moves the operating point up and right on the ROC curve; if Point B is below or to the left of Point A, the placement is wrong.
- The AUC = 0.76 label must be consistent with the curve shape: an AUC of 0.76 curves noticeably toward the upper-left but does not reach the perfect-classifier corner; a curve that looks like AUC ≈ 0.95 or AUC ≈ 0.55 would be inconsistent.

---

## Figure 11.3 — Threshold Sensitivity: Fraction of Occupations at Risk vs. Decision Threshold

**Suggested filename:** 11-onet-threshold-sensitivity.svg
**Figure type:** Statistical / quantitative — step/line chart with annotated operating points

**One-sentence concept:** The fraction of US occupations classified as "at high automation risk" changes dramatically with threshold choice — from roughly 47% at the Frey-Osborne 0.70 threshold to substantially fewer at higher thresholds — demonstrating that the policy conclusion is a threshold decision, not a model finding.

**S — Specification:** Single-panel; single textbook column (89 mm wide) × approx. 90 mm tall at 300 DPI; vector SVG.

**C — Content:**
- A smooth curve (or step function) showing the fraction of O*NET occupations classified as "high automation risk" (y-axis, 0 to 1) as the classification threshold varies from 0 to 1 (x-axis).
- Curve is monotonically decreasing: as threshold increases, fewer occupations are labeled at-risk.
- Three annotated threshold points:
  - Threshold = 0.50: fraction labeled (chapter Exercise 3 — approximately 60–65%, illustrative).
  - Threshold = 0.70: fraction ≈ 0.47 (Frey & Osborne 2013/2017 canonical 47% finding).
  - Threshold = 0.80: fraction visibly lower (illustrative).
- Horizontal dashed reference line at 0.47 from threshold = 0.70.
- The curve passes through (0.70, 0.47) exactly.

**O — Organization:** Single panel. X-axis: classification threshold, 0 to 1, tick marks at 0, 0.25, 0.50, 0.70, 1.0. Y-axis: fraction of occupations classified at-risk, 0 to 1 (zero baseline), tick marks at 0, 0.25, 0.47, 0.50, 0.75, 1.0. Y-axis must start at zero. Three operating-point markers on the curve. Total labeled components: curve + 3 operating points + 1 reference line = 5 — within limit.

**P — Presentation:**
- Sensitivity curve: Blue #0072B2, weight 2 pt — primary structural element.
- Threshold = 0.50 operating point: Orange #E69F00, filled circle — secondary reference; the "neutral" threshold.
- Threshold = 0.70 operating point (Frey-Osborne): Vermillion #D55E00, filled circle — marks a specific published threshold choice.
- Threshold = 0.80 operating point: neutral gray #999999, filled circle — illustrative alternative.
- Horizontal reference dashed line at 0.47: Vermillion #D55E00, weight 0.5 pt, dashed.
- Y-axis must start at zero — hard rule.
- Background: white; bottom and left spines only; no grid fill.

**E — Exclusions:**
- Do not show the Arntz et al. 9% task-level estimate as a separate curve — the figure's purpose is threshold sensitivity for a single model, not a multi-model comparison; the disagreement between Frey-Osborne and Arntz is a text discussion.
- Do not show the underlying O*NET probability distribution or individual occupation points.
- Do not show more than three annotated threshold operating points — three is sufficient to make the sensitivity argument without cluttering.
- Do not annotate the curve with cost-ratio equivalents (what cost ratio each threshold implies) — that algebra belongs in the text or Exercise 3 instructions.
- Do not show confidence intervals on the curve — this figure is about threshold sensitivity, not estimation uncertainty.
- Do not use 3D, drop shadows, or gradient fills.
- Do not label the y-axis as "accuracy" — it is fraction classified at-risk, a count quantity, not a model quality metric.

**Caption (draft):** Fraction of O*NET occupations classified as "high automation risk" as a function of the classification threshold; the red circle marks the Frey and Osborne (2017) threshold = 0.70, which labels approximately 47% of occupations at-risk; moving the threshold from 0.50 to 0.70 or 0.80 reduces the at-risk fraction substantially, illustrating that the widely cited 47% figure is a threshold decision, not a model output.

**Accuracy check (figure-checker):**
- The y-axis must start at zero — any non-zero baseline would distort the visual impression of how steeply the at-risk fraction changes.
- The curve must be monotonically non-increasing (non-decreasing threshold = weakly fewer at-risk) — any upward slope would mean that a higher threshold labels more occupations at risk, which is logically impossible under a standard threshold classifier.
- The threshold = 0.70 operating point must lie at approximately (0.70, 0.47) — this matches the Frey-Osborne published finding; label the point clearly.
- The threshold = 0.50 operating point must produce a higher at-risk fraction than 0.47 (since 0.50 < 0.70, more occupations are labeled at-risk at the lower threshold).
- The curve endpoints must be logically consistent: at threshold = 0 all occupations are labeled at-risk (y = 1.0); at threshold = 1.0 no occupations are labeled at-risk (y = 0) — if the curve does not approach these limits, the renderer has misconfigured the axes.
- The 0.47 horizontal dashed reference line must intersect the curve at exactly threshold = 0.70 — a mismatch between the reference line height and the curve value at x = 0.70 is an accuracy error.
