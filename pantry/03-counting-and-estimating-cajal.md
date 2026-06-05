# CAJAL Figure Plans — Chapter 03: Counting and Estimating

*Figure plans for Chapter 3 — The binomial problem run both ways: a frequentist confidence interval and a Bayesian credible interval from the same 8-in-50 circuit-board data, culminating in the posterior probability that answers the engineer's decision question.*

---

## Figure 03.1 — Frequentist CI vs. Bayesian Credible Interval: Two Answers from 8 in 50

**Suggested filename:** 03-ci-vs-credible-interval-comparison.svg
**Figure type:** Comparison panels
**One-sentence concept:** The Wilson 95% confidence interval [0.074, 0.284] and the Beta(9,43) 95% credible interval [0.082, 0.295] are drawn from identical data but carry different meanings — only the credible interval licenses a probability statement about whether the defect rate falls below the 20% threshold.

**S — Specification:** Double-column 170mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- Left panel — Frequentist: panel label "Wilson 95% CI." Horizontal number line from 0.00 to 0.40, x-axis baseline at zero; tick marks at 0.00, 0.10, 0.20, 0.30, 0.40. A horizontal interval bar spanning [0.074, 0.284]. A dot marker at the point estimate 0.16 (p̂ = 8/50). A vertical dashed reference line at 0.20 (threshold). A "MISSING" callout for probability of interest, shown as a grayed-out dashed box labeled "P(rate < 0.20) — not computable."
- Right panel — Bayesian: panel label "Beta(9, 43) 95% CrI." Same number-line scale [0.00, 0.40]. A horizontal interval bar spanning [0.082, 0.295]. A dot marker at the posterior mean 0.173. The same vertical dashed reference line at 0.20. A callout: "P(rate < 0.20 | data) ≈ 0.76."
- Shared x-axis label: "Defect rate p."
- Six labeled components: left-panel interval bar + point estimate + missing-callout; right-panel interval bar + posterior mean dot + probability callout.

**O — Organization:** Two panels arranged side by side at equal width, separated by a thin vertical dividing rule. Each panel contains: panel label at top, horizontal number line in the center, interval bar and marker, threshold reference line. The missing-probability callout in the left panel is the visual asymmetry — it must be visually distinct (dashed gray box). Both panels share an identical x-axis scale so the interval widths are directly comparable. Arrows not used; the figure is a static comparison, not a flow.

**P — Presentation:** Both interval bars: primary data accent (#C8102E), stroke-width 3pt horizontal line with end caps. Point estimate and posterior mean dots: filled circles (#C8102E). Threshold reference line (p = 0.20): neutral mid-gray (#787878), dashed (stroke-dasharray 5 4), stroke-width 1pt, both panels. Missing-probability callout box: dashed border #D4D4D4, fill #F5F5F5, text #545454 — signals absence. Bayesian probability callout box: solid border #C8102E 1pt, fill #F5F5F5 — signals the decision-relevant answer. Axis tick labels: JetBrains Mono 11pt #545454. Panel labels: EB Garamond 14pt #2a1a0e. Chart area fill #F5F5F5. Dividing rule #D4D4D4 0.75pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The full Beta(9,43) posterior density curve — that belongs to Figure 03.2; this figure shows intervals only.
- The Wald interval [0.058, 0.262] — the chapter establishes that the Wilson interval is preferred; include only the Wilson interval to avoid cluttering the comparison with a deprecated alternative.
- Any third framework (Jeffreys interval, HPD interval) — one comparison per figure.
- The conjugate update derivation (Beta(1,1) + data = Beta(9,43)) — shown in chapter text, not a visual element here.
- Numeric tick values denser than 0.10 intervals — visual clutter at this column width.
- Any claim about which method is "correct" — the figure shows what each produces, not which is better.
- 3D or perspective effects.

**Caption (draft):** Same data (8 defective in 50), two intervals: the Wilson 95% confidence interval [0.074, 0.284] guarantees only that 95% of such intervals cover the true rate over repeated sampling, while the Beta(9,43) credible interval [0.082, 0.295] directly licenses P(rate < 0.20 | data) ≈ 0.76 — the probability the engineer's decision question requires.

**Accuracy check (figure-checker):**
- Wilson 95% CI endpoints: [0.074, 0.284] — verify both endpoint markers lie at these x-positions.
- Frequentist point estimate: p̂ = 8/50 = 0.16 — verify the dot marker is at x = 0.16, not 0.173.
- Beta(9,43) 95% CrI endpoints: [0.082, 0.295] — verify both endpoint markers lie at these x-positions.
- Posterior mean: 9/(9+43) = 9/52 ≈ 0.173 — verify the dot marker in the Bayesian panel is at x = 0.173, not 0.16.
- Both x-axes must start at zero; no truncated baseline.
- Threshold line at p = 0.20 must appear in both panels at the same x-position.
- The missing-probability callout must appear in the LEFT (frequentist) panel only; the probability value must appear in the RIGHT (Bayesian) panel only.
- P(rate < 0.20 | data) ≈ 0.76 — this is the CDF of Beta(9,43) at 0.20; verify the displayed value matches the chapter's stated "approximately 0.76."
- Both interval bars must be visually wider than the separation between the dot marker and the threshold line — confirming 0.20 lies inside both intervals.

---

## Figure 03.2 — Beta(9, 43) Posterior with P(rate < 0.20) Shaded

**Suggested filename:** 03-beta-posterior-shaded-region.svg
**Figure type:** Statistical / quantitative (density curve with shaded region)
**One-sentence concept:** The Beta(9,43) posterior for the defect rate peaks near 0.17 and the shaded area to the left of the 0.20 threshold — approximately 76% of the total area — is exactly the probability that answers the engineer's batch-acceptance question.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- X-axis: defect rate p, range 0.00 to 0.50, labeled "Defect rate p"; zero baseline.
- Y-axis: posterior density, labeled "Posterior density"; baseline at zero; no probability values on y-axis (it is a density, not a probability).
- One smooth Beta(9,43) density curve, mode near 0.16, mean at approximately 0.173.
- Shaded region: the area under the curve from 0.00 to 0.20, filled with primary data accent (#C8102E), labeled "P(rate < 0.20) ≈ 0.76."
- Unshaded region: the area under the curve from 0.20 to 0.50, filled with neutral mid-gray (#787878) or left unfilled, labeled "P(rate ≥ 0.20) ≈ 0.24."
- A vertical dashed reference line at p = 0.20, labeled "Threshold 0.20."
- A vertical tick or dot marker at the posterior mean p = 0.173, labeled "Mean 0.173."

**O — Organization:** Single-panel density plot. X-axis horizontal from 0.00 to 0.50; tick marks at 0.00, 0.10, 0.20, 0.30, 0.40, 0.50. Y-axis vertical from 0 to a maximum slightly above the curve's peak. The shaded region visually dominates the unshaded region (76% vs. 24% of the area), which is the pedagogical payload — do not compress the left region or expand the right. The threshold line divides the curve cleanly into the decision-relevant left and right portions. The area labels are the primary annotation; axis ticks are secondary. Total labeled components: shaded area label, unshaded area label, threshold line label, posterior mean marker — four labeled elements.

**P — Presentation:** Shaded area (left of threshold): primary data accent (#C8102E), fill opacity 0.80. Unshaded area (right of threshold): neutral mid-gray (#787878), fill opacity 0.35, or unfilled with only the curve outline. Density curve outline: #2a1a0e ink, stroke-width 1.5pt. Threshold line (p = 0.20): #2a1a0e, dashed (stroke-dasharray 5 4), stroke-width 1pt. Posterior mean marker: vertical tick or small triangle at p = 0.173, #2a1a0e. Y-axis: labeled "Posterior density" in Inter 12pt #2a1a0e; no numeric tick values required (density scale is not directly interpretable to students). X-axis tick labels: JetBrains Mono 11pt #545454. Chart area fill #F5F5F5. Grid lines #D4D4D4 0.75pt at x = 0.10 increments. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The prior Beta(1,1) curve — showing the flat prior alongside the posterior risks visual clutter and shifts focus from the decision probability to the update mechanics; the update is explained in chapter text.
- The likelihood curve — same reason; the posterior is the endpoint the figure communicates.
- A second posterior for the alternative worked example (Beta(4,28) from 3/30 boards) — one example per figure; see the Worked Example section of the chapter for that case.
- Numeric y-axis tick labels — the density scale is not naturally interpretable and would mislead students into reading density values as probabilities.
- The 95% credible interval endpoints [0.082, 0.295] as separate annotations — they are shown in Figure 03.1; do not duplicate.
- Any value above p = 0.50 on the x-axis — the Beta(9,43) density is negligible above 0.40 and adding space above would compress the decision-relevant region.
- HPD interval vs. equal-tailed interval distinction — mentioned in chapter text, not a visual element here.
- 3D effects.

**Caption (draft):** The Beta(9,43) posterior density for the defect rate, derived from 8 defective boards in 50 using a uniform prior: the shaded region to the left of the 0.20 threshold contains approximately 76% of the total probability mass, giving P(rate < 0.20 | data) ≈ 0.76 — the answer to the engineer's batch-acceptance question.

**Accuracy check (figure-checker):**
- The posterior must be Beta(9,43): α = 1 + 8 = 9, β = 1 + 42 = 43. Verify mode = (α−1)/(α+β−2) = 8/50 = 0.16 and mean = 9/52 ≈ 0.173.
- The curve must peak near 0.16 (mode) and be right-skewed with mean slightly above the mode — if the peak appears at 0.173 rather than 0.16, the distribution parameters are wrong.
- The shaded area must be the region [0.00, 0.20], not [0.00, 0.173] — the threshold is 0.20, not the posterior mean.
- The labeled probability for the shaded area must be approximately 0.76 (CDF of Beta(9,43) at 0.20). Verify against the chapter text.
- The labeled probability for the unshaded area must be approximately 0.24 = 1 − 0.76. Verify the two labeled probabilities sum to 1.00.
- Y-axis baseline must be at zero — no truncated baseline.
- X-axis must start at 0.00 — no truncated baseline at the left edge.
- The Proportional Ink Rule: the shaded area must visually represent approximately three times the unshaded area (76% vs. 24%). If the rendering equalizes them, the cognitive load check fails.
- Posterior mean marker must be placed at p = 0.173, not at the mode p = 0.16 — the two are distinct and both are named in the chapter.
