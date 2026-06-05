# CAJAL Figure Plans — Chapter 05: Regression, Both Ways

*Figure plans for Chapter 5 — OLS line and Bayesian posterior predictive band on the same scatter (the lines converge; the uncertainty representations diverge), followed by the posterior predictive distribution showing P(ROI > 0) as a shaded region — the probability the marketing director actually needed.*

---

## Figure 05.1 — OLS Line vs. Bayesian Posterior Predictive Band: Convergence and Divergence

**Suggested filename:** 05-ols-vs-bayesian-regression-bands.svg
**Figure type:** Comparison panels
**One-sentence concept:** With 60 weekly observations, the OLS fitted line and the Bayesian posterior mean line are indistinguishable (MAP = OLS under weakly informative priors), but the Bayesian posterior predictive band — which integrates over parameter uncertainty — is wider than the frequentist prediction interval and yields a full probability distribution, not just a coverage range.

**S — Specification:** Double-column 170mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 460.

**C — Content:**
- Left panel — Frequentist (OLS): panel label "OLS regression." Scatter of approximately 15–20 illustrative data points (advertising spend on x-axis, weekly sales on y-axis). A single fitted line with slope 2.3 and intercept 124.7, labeled "ŷ = 124.7 + 2.3x." A narrow 95% confidence band for the conditional mean E[Y|X] (inner band). A wider 95% prediction interval band for a new observation Y_new (outer band). Both bands explicitly labeled. X-axis: "Advertising spend (£000/week)." Y-axis: "Sales (£000/week)"; baseline at zero. A callout box: "95% prediction interval — coverage guarantee, not a probability distribution."
- Right panel — Bayesian: panel label "Bayesian regression." Same illustrative scatter points. The same fitted line (identical slope 2.3 and intercept 124.7 to first approximation) labeled "Posterior mean line." A shaded posterior predictive band (wider than the OLS prediction interval, visually distinct by fill). A callout: "Posterior predictive band — full distribution; P(Y_new > threshold) computable."
- A shared note below both panels: "Advertising→sales scenario is illustrative; specific numbers constructed for pedagogy."
- Six labeled components: left-panel fitted line + CI band label + PI band label + output callout; right-panel posterior mean line + predictive band callout.

**O — Organization:** Two panels side by side at equal width, separated by a thin vertical dividing rule. Both panels use identical axes, identical scatter data positions, and identical fitted line positions — the point of visual convergence on the line is the pedagogical setup. The divergence in band width and interpretability is the contrast. Left panel has two explicitly labeled bands (inner CI band, outer PI band), each with a callout. Right panel has one wider shaded band with a single callout. The panels must be visually aligned so the reader can directly compare band widths at any x-value. Both axes baseline at zero.

**P — Presentation:** Data scatter points: #787878 neutral gray, filled circles, 3pt radius. Fitted line (both panels): #2a1a0e ink, stroke-width 2pt — identical in both panels to show convergence. Left-panel CI band (inner): very light gray fill, #D4D4D4, fill opacity 0.40. Left-panel PI band (outer): light gray fill, #ADADAD, fill opacity 0.30. Right-panel posterior predictive band: primary data accent (#C8102E), fill opacity 0.20 — signals the decision-relevant output. Callout boxes: solid border #C8102E 1pt for Bayesian panel; dashed border #D4D4D4 for frequentist panel. Panel labels: EB Garamond 14pt #2a1a0e. Axis labels and ticks: JetBrains Mono 11pt #545454. Chart area fill #F5F5F5. Dividing rule #D4D4D4 0.75pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The posterior distributions on α, β, and σ separately — these are described in chapter text; only the predictive band (which integrates over all three) appears here.
- Residuals or residual diagnostics (QQ plot, residual vs. fitted) — beyond the chapter's scope for this figure.
- The causal interpretation caveat (advertising vs. seasonal confounding) — chapter text; not a visual element.
- The OLS = MAP theorem derivation — chapter algebra; not shown here.
- A third panel showing the posterior on the slope alone — that would require splitting this figure; described in chapter text.
- The worked example (schooling–earnings Mincer regression) — a different example; this figure uses the advertising–sales scenario only.
- Axis values beyond what is needed to show the line and bands clearly — do not clutter with more than 5–6 x-axis ticks.
- 3D or perspective effects.

**Caption (draft):** With 60 weekly observations (illustrative advertising→sales scenario), the OLS line and Bayesian posterior mean line are indistinguishable — MAP equals OLS under weakly informative priors — but the Bayesian posterior predictive band integrates over parameter uncertainty to yield a full probability distribution from which P(sales increase > threshold) is directly computable, while the frequentist prediction interval provides only a coverage range.

**Accuracy check (figure-checker):**
- The OLS fitted line and the Bayesian posterior mean line must be visually identical (same slope 2.3, same intercept 124.7) — any visible divergence between them would misrepresent the MAP = OLS equivalence.
- The Bayesian posterior predictive band must be at least as wide as the frequentist prediction interval at every x-value — theoretically, the Bayesian band is wider because it integrates over parameter uncertainty in addition to residual variance. If the Bayesian band appears narrower, the render is wrong.
- The frequentist CI band must be visually narrower than the PI band in the left panel — CI for E[Y|X] does not include residual variance; PI does. Equalizing the two bands is a mathematical error.
- Both y-axes must baseline at zero — no truncated baseline.
- Both x-axes must baseline at zero — advertising spend cannot be negative.
- The scatter points must be identical in both panels — same positions, same count — to ensure the comparison is on the interval representation, not on the data.
- The Bayesian callout must appear in the RIGHT panel only; the coverage-guarantee callout must appear in the LEFT panel only.
- The posterior predictive band must be labeled as relating to a "full distribution," not a "confidence interval" or "prediction interval."

---

## Figure 05.2 — Posterior Predictive Distribution for ΔY with P(ROI > 0) Shaded

**Suggested filename:** 05-posterior-predictive-roi-threshold.svg
**Figure type:** Statistical / quantitative (density curve with shaded region)
**One-sentence concept:** The posterior predictive distribution for the weekly sales change ΔY from a 10% advertising budget increase is approximately Normal with mean 11.5 and the shaded area above the 5% sales-increase threshold (ΔY ≥ 12) represents P(ΔY ≥ 12 | data) ≈ 0.46 — a near-coin-flip that the OLS slope and p-value could not reveal.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- X-axis: weekly sales change ΔY (thousands of dollars), range −20 to +45, labeled "Predicted sales change ΔY (£000/week)"; zero baseline.
- Y-axis: posterior predictive density, labeled "Posterior predictive density"; baseline at zero; no numeric y-axis tick values (density not directly interpretable as probability).
- One smooth posterior predictive density curve, approximately Normal centered near 11.5, with spread reflecting both parameter uncertainty and residual variance.
- Shaded region: ΔY ≥ 12 (the 5% sales-increase threshold at current average sales ~240 K/week), filled with primary data accent (#C8102E). Labeled "P(ΔY ≥ 12) ≈ 0.46."
- Unshaded region: ΔY < 12, neutral mid-gray or unfilled. Labeled "P(ΔY < 12) ≈ 0.54."
- A vertical dashed reference line at ΔY = 12, labeled "5% target: ΔY = 12."
- A vertical tick or dot marker at ΔY = 0 with a secondary dashed reference line, labeled "No change" — to orient readers to the zero point.
- A vertical dot marker at ΔY = 11.5 (posterior predictive mean), labeled "Mean 11.5."

**O — Organization:** Single-panel density plot. X-axis horizontal from −20 to +45; tick marks at −20, −10, 0, 10, 20, 30, 40. Y-axis vertical from 0 to a maximum slightly above the curve's peak. The distribution is centered to the left of the decision threshold (mean 11.5 vs. threshold 12), creating a near-symmetric split of the shaded and unshaded areas — this near-coin-flip is the pedagogical payload, and the rendering must preserve this visual. The ΔY = 0 secondary reference line establishes the no-change baseline. Total labeled components: shaded area label, unshaded area label, threshold line label, ΔY = 0 label, posterior mean marker — five labeled elements.

**P — Presentation:** Shaded area (ΔY ≥ 12, above threshold): primary data accent (#C8102E), fill opacity 0.80. Unshaded area (ΔY < 12, below threshold): neutral mid-gray (#787878), fill opacity 0.35, or unfilled with only the curve outline. Density curve outline: #2a1a0e ink, stroke-width 1.5pt. Threshold line (ΔY = 12): #2a1a0e, dashed (stroke-dasharray 5 4), stroke-width 1pt. No-change line (ΔY = 0): #D4D4D4, dashed (stroke-dasharray 2 4), stroke-width 0.75pt — secondary reference. Posterior mean marker: vertical tick at ΔY = 11.5, #2a1a0e, stroke-width 1pt. Y-axis label: Inter 12pt #2a1a0e. X-axis tick labels: JetBrains Mono 11pt #545454. Chart area fill #F5F5F5. Grid lines #D4D4D4 0.75pt at x = 0, 10, 20 tick positions. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The OLS prediction interval — that is Figure 05.1's territory; do not duplicate as a separate curve here.
- The posterior distributions on β, α, or σ individually — this figure shows only the posterior predictive distribution for the outcome ΔY, which is the decision-relevant quantity.
- A second scenario (e.g., 20% budget increase) — one threshold question per figure; additional scenarios are exercises.
- The worked example (schooling–earnings / P(wage increase > 15%)) — a different example with different numbers; this figure uses the advertising–sales scenario only.
- Numeric y-axis tick labels — density values are not directly interpretable and would mislead students into reading them as probabilities.
- The frequentist prediction interval overlaid as a second curve — mixing frequentist and Bayesian representations in a single panel creates interpretive confusion; the contrast belongs in Figure 05.1.
- The "P(slope > 0)" question — a different query (the chapter resolves it at 97%+); this figure is about the threshold on the predicted outcome, not on the parameter.
- 3D or perspective effects.

**Caption (draft):** Posterior predictive distribution for weekly sales change ΔY under a 10% advertising budget increase (illustrative advertising→sales scenario): the distribution is centered at 11.5 (£000/week) with the 5% sales-increase target at ΔY = 12, giving P(ΔY ≥ 12 | data) ≈ 0.46 — a near-coin-flip the OLS slope and p-value could not reveal.

**Accuracy check (figure-checker):**
- Posterior predictive mean: E[ΔY] = β̂ × ΔX = 2.3 × 5 = 11.5 K/week (10% increase from X₀ = 50 to X₁ = 55). Verify the curve is centered near 11.5, not near 2.3 or 50.
- Decision threshold: 5% of current average sales ~240 K/week = 12 K/week. The threshold line must be placed at ΔY = 12, not at ΔY = 11.5 (the mean). These are distinct values and the near-coin-flip result depends on the threshold being above the mean.
- P(ΔY ≥ 12 | data) ≈ 0.46. For a distribution centered at 11.5 with threshold at 12, the value should be slightly below 0.50. If the labeled probability is substantially above 0.50, the threshold position or mean is wrong.
- P(ΔY < 12) ≈ 0.54. Verify the two labeled probabilities sum to 1.00.
- The shaded and unshaded areas must be nearly equal (46% vs. 54%) — visually they should appear close in size, not dramatically unequal. If one region visually dominates, the threshold or mean position is wrong.
- X-axis baseline must be at zero (ΔY = 0 is the no-change point, not the left edge of the axis) — the x-axis must extend below zero to show negative outcomes.
- Y-axis baseline must be at zero.
- Proportional Ink Rule: shaded area must be proportional to 0.46 of the total area under the curve, unshaded to 0.54. If the shading is applied to an area clearly larger than approximately half the curve, the render is wrong.
- The ΔY = 0 reference line must be visually to the left of both the posterior mean (11.5) and the threshold (12) — confirming that the expected outcome is positive even if not sufficient to clear the threshold with high confidence.
