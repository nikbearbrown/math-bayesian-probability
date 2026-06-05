# CAJAL Figure Plans — Chapter 8: When Data Is Sparse

*Produced by CAJAL (silent mode). Plans only — no SVGs. Renderer writes SVGs to `images/` and PNGs via `SCRIPTS/svg-to-png.mjs`.*

---

## Figure 08.1 — Frequentist Wide CI vs. Bayesian Shrinkage

**Suggested filename:** 08-ci-vs-credible-interval.svg
**Figure type:** Comparison panels (interval comparison with zero baseline)
**One-sentence concept:** For 3 complications in 200 procedures, the exact binomial 95% CI ([0.31%, 4.35%]) is nearly five times wider than the Bayesian 95% credible interval ([0.55%, 3.18%]), because the Bayesian analysis imports the published prior Beta(3, 200) centered at ~1.5%.

**S — Specification:** Single-page textbook width, 700 × 380 px viewBox, 300 DPI, vector SVG. Two vertically stacked rows sharing a common horizontal axis (complication rate, %). Chart area `#F5F5F5`. 32 px margin all sides, chart margins top 48 / right 40 / bottom 64 / left 160. Labels on 8 px grid.

**C — Content:**
- Horizontal axis: complication rate (%), range 0% to 5%. Zero baseline required. Tick marks at 0%, 1%, 2%, 3%, 4%, 5%.
- Vertical reference line at 2.5% labeled "Accreditation threshold (2.5%)" — dashed, `stroke-dasharray="5 4"`.
- Row 1 (top): "Frequentist (exact binomial)." Horizontal interval bar spanning [0.31%, 4.35%]. Point estimate marker at 1.50% (filled circle). Interval extends substantially across the threshold line.
- Row 2 (bottom): "Bayesian Beta(6, 397)." Horizontal interval bar spanning [0.55%, 3.18%]. Point estimate marker at 1.49% (filled circle). Interval is visibly narrower and lies more fully to the left of the threshold.
- Interval width annotation for each row: bracket above or below each bar labeled "4.04 pp" (frequentist) and "2.63 pp" (Bayesian) respectively.
- Label below the Bayesian row: "Prior: Beta(3, 200) from published literature."
- Label at right margin of Bayesian row: "P(rate < 2.5%) = 0.92."
- The two point estimates (1.50% and 1.49%) are nearly identical — this must be visually apparent: markers align almost vertically.

**O — Organization:** Two-row dot-and-whisker layout, rows stacked vertically sharing the horizontal axis. The accreditation threshold line runs top to bottom across both rows, providing the shared reference that makes interval width legible. The narrow Bayesian interval and its near-complete containment left of the threshold is the pedagogical contrast. Point estimate markers are positioned at the same horizontal position in both rows to show near-identical estimates. Interval brackets appear above the Bayesian row and below the frequentist row to avoid overlap.

**P — Presentation:**
- Frequentist interval bar: `#787878` (neutral gray), `stroke-width="2"`, end caps as vertical ticks.
- Frequentist point estimate: `#787878`, filled circle, radius 5.
- Bayesian interval bar: `#0072B2` (Blue), `stroke-width="2"`, end caps as vertical ticks.
- Bayesian point estimate: `#0072B2`, filled circle, radius 5.
- Accreditation threshold line: `#D55E00` (Vermillion) dashed rule — this is a constraint/boundary, appropriate for the negative/blocking semantic role. `stroke-dasharray="5 4"` `stroke-width="1.5"`.
- Chart area: `#F5F5F5`. Canvas: `#FFFFFF`. Ink: `#2a1a0e`. Row labels: Inter 12pt `#2a1a0e`. Axis tick labels: JetBrains Mono 11pt `#545454`. Width annotations: Inter 11pt `#545454`.
- Grayscale test: Frequentist gray (L*≈51) vs. Bayesian blue (L*≈32) — distinct luminance bands; supplemented by color labeling at left margin.
- No gradient, no shadow, no 3D. Zero baseline required on horizontal axis.

**E — Exclusions:**
- Do NOT show the prior Beta(3, 200) distribution as a density curve — this figure is about interval output, not prior shape. Prior details belong in the text and Figure 07.1's design pattern.
- Do NOT show the year-over-year comparison (2/150 vs. 3/200) — that is a separate sub-analysis addressed in text; adding it would require a third row and exceed the 6–8 component limit.
- Do NOT show prior sensitivity alternatives (Beta(1,1), Beta(1,100), Beta(5,300)) — the sensitivity results are in the text table; this figure makes the single main contrast legible.
- Do NOT use a non-zero baseline on the horizontal axis.
- Do NOT show the posterior density curve — the interval representation is sufficient for the pedagogical purpose and the density would require a different figure type.
- Do NOT label P(rate < 2.5%) for the frequentist row — it is not directly available from that analysis and the absence is the point.

**Caption (draft):** For 3 complications in 200 procedures, the exact binomial 95% CI spans 4.04 percentage points ([0.31%, 4.35%]) while the Bayesian 95% credible interval spans 2.63 pp ([0.55%, 3.18%]); the point estimates are virtually identical (1.50% vs. 1.49%), but the Bayesian analysis — using a prior from published complication rate literature — also directly answers whether the rate is below the 2.5% accreditation threshold (P = 0.92).

**Accuracy check (figure-checker):**
- Frequentist interval must span exactly [0.31%, 4.35%] as computed by the exact binomial method for k = 3, n = 200 at 95% coverage.
- Bayesian interval must span approximately [0.55%, 3.18%] as computed from Beta(6, 397) at 95% credible probability.
- The posterior parameters Beta(6, 397) derive from the conjugate update: Beta(3+3, 200+200−3) = Beta(6, 397). Verify arithmetic: α₀ = 3, β₀ = 200, k = 3, n = 200 → posterior α = 6, β = 397.
- Posterior mean = 6/(6+397) = 6/403 ≈ 0.0149 = 1.49%. Point estimate marker must be at 1.49%, not 1.50%.
- Frequentist point estimate = 3/200 = 1.50%. Both markers must be visually indistinguishable in position — nearly co-located.
- Horizontal axis must start at 0%, not any positive value. Zero baseline is non-negotiable.
- The accreditation threshold line at 2.5% must be within the frequentist interval (2.5% < 4.35%) and within the Bayesian interval (2.5% < 3.18%) — both intervals straddle it, but the Bayesian interval contains less area above it, consistent with P(rate < 2.5%) = 0.92.

---

## Figure 08.2 — Winner's Curse: Significance Threshold Inflates Observed Effect Sizes

**Suggested filename:** 08-winners-curse-type-m.svg
**Figure type:** Statistical / quantitative (dot distribution with threshold annotation)
**One-sentence concept:** When a study has low power (12% for a true δ = 0.2 at n = 20), only the studies that randomly overestimate the effect to δ ≈ 0.8 or larger cross the significance threshold — so the published literature shows a false consensus around an inflated effect size.

**S — Specification:** Single-page textbook width, 700 × 420 px viewBox, 300 DPI, vector SVG. Single panel with a horizontal distribution of observed effect size estimates (dot strip or density strip), vertical threshold line, and annotated regions. Chart area `#F5F5F5`. 32 px margin all sides, chart margins top 48 / right 40 / bottom 64 / left 64.

**C — Content:**
- Horizontal axis: "Observed effect size (δ)" ranging from −0.5 to +1.5. Tick marks at −0.5, 0, 0.5, 1.0, 1.5. Zero baseline on vertical axis.
- Vertical axis: count or density of study estimates (from a conceptual simulation of 1,000 studies, true δ = 0.2, n = 20 per group). Roughly normal distribution centered at 0.2, SD ≈ 0.45 (reflecting sampling distribution at n = 20). Tick marks at 0, 50, 100, 150, 200 (if using counts of 1,000 simulated studies), or density scale 0 to 0.9.
- True effect reference line: vertical dashed line at δ = 0.2, labeled "True effect (δ = 0.2)."
- Significance threshold line: vertical solid line at δ ≈ 0.6 (the approximate minimum observed effect needed for p < 0.05 at n = 20 per group, two-sided — approximately 1.96 × SE, SE ≈ √(2/20) ≈ 0.316, threshold ≈ 0.62). Label: "Significance threshold (p < 0.05)."
- Region to the left of the threshold: shaded in neutral gray — "Filed away (not published): ~880 of 1,000 studies."
- Region to the right of the threshold: shaded in primary blue — "Published: ~120 of 1,000 studies." Arrow from this region pointing right with label: "Published mean ≈ 0.8."
- Annotated bracket above the published region: "Type M exaggeration ratio ≈ 4×" spanning from δ = 0.2 to δ = 0.8.

**O — Organization:** Single panel. Horizontal axis shows effect sizes; vertical axis shows count/density of simulated study estimates. The distribution is centered left of the threshold. The threshold line bisects the figure asymmetrically, with the bulk of the distribution to its left (unpublished) and the tail to its right (published). The "true effect" line is within the unpublished region, which is the visual surprise that communicates the winner's curse. Labels run top-down in reading order: true effect reference first, threshold second, published region annotation third.

**P — Presentation:**
- Distribution rendering: If a density/histogram strip — bars or smooth density curve in `#2a1a0e` (Ink) at 60% opacity or outlined bars.
- Unpublished region fill: neutral gray `#ADADAD` at 40% opacity, below the distribution curve/bars.
- Published region fill: `#0072B2` (Blue) at 30% opacity, below the distribution curve/bars.
- True effect line (δ = 0.2): `#009E73` (Bluish Green, positive/reference), dashed `stroke-dasharray="5 4"` `stroke-width="1.5"`.
- Significance threshold line: `#D55E00` (Vermillion, blocking/filter), solid `stroke-width="2"`.
- Type M bracket: `#2a1a0e`, bracket with annotation text at Inter 11pt `#545454`.
- Zero baseline: solid `#D4D4D4` `stroke-width="0.75"`.
- Chart area: `#F5F5F5`. Canvas: `#FFFFFF`.
- Grayscale test: True effect line (Bluish Green, L*≈60) vs. threshold line (Vermillion, L*≈40) — distinct; unpublished gray (L*≈70) vs. published blue (L*≈32) — distinct. All distinguishable in grayscale.
- No gradient, no shadow, no 3D. Vertical axis starts at zero.

**E — Exclusions:**
- Do NOT show individual study dots (a jitter plot of 1,000 points would exceed 8 labeled components and clutter the conceptual display) — use a density strip or histogram instead.
- Do NOT show a Bayesian posterior or credible interval in this figure — the winner's curse is a frequentist-mechanism figure; mixing in Bayesian output conflates two separate concepts.
- Do NOT show Type S errors (sign errors) in this figure — the chapter addresses Type S in the text; adding it here would require a second dimension or a second panel and exceeds the scope of a single-concept figure.
- Do NOT use exact simulation values as if they were empirical data — label the figure as "Conceptual illustration (n = 1,000 simulated studies, true δ = 0.2, n = 20 per group)" in the caption, not in the figure itself.
- Do NOT show the "correct" replication study result as a separate element — that belongs in Exercise 2 and the worked example text.
- Do NOT label the unpublished region with a value judgment ("suppressed," "hidden") — use neutral language ("not published," "filed away") consistent with the chapter's framing that this is a statistical mechanism, not misconduct.
- Do NOT use a non-zero baseline on the vertical axis.

**Caption (draft):** A conceptual simulation of 1,000 underpowered studies (true δ = 0.2, n = 20 per group, power ≈ 12%): only the studies that randomly overestimate the effect to δ ≥ 0.6 cross the significance threshold and enter the published record, producing a false consensus around δ ≈ 0.8 — a Type M exaggeration ratio of approximately 4×.

**Accuracy check (figure-checker):**
- The significance threshold position must be accurate: for n = 20 per group, two-sided α = 0.05, the threshold observed effect is approximately 1.96 × SE. With equal group sizes and assuming σ = 1 (standardized), SE = √(1/20 + 1/20) = √(0.1) ≈ 0.316, so threshold ≈ 1.96 × 0.316 ≈ 0.62. The threshold line must be at approximately δ = 0.62, not at δ = 0.5 or δ = 1.0.
- The distribution must be centered at the true effect δ = 0.2 (or very close), not at zero. Centering at zero would incorrectly imply the null hypothesis is true.
- The "published mean ≈ 0.8" annotation must be plausible given the threshold at 0.62: the mean of a truncated normal above 0.62, for a normal centered at 0.2 with SD ≈ 0.316, is approximately 0.8–0.9. The exact value is approximated; it must be labeled as approximate.
- The published region (right of threshold) must contain visually fewer studies than the unpublished region — approximately 12% of the distribution, consistent with 12% power. The visual proportions must reflect this asymmetry.
- The Type M exaggeration bracket must span from δ = 0.2 (true effect) to δ ≈ 0.8 (published apparent effect), not from zero to 0.8.
- Vertical axis must start at zero — no non-zero baseline.

---

*Split note: A third figure (Bayesian shrinkage as n increases — prior dominating at n = 3, posterior converging on data at n = 300) would directly illustrate Chapter 8's shrinkage mechanism and Bridge to Chapter 9. However, producing it requires specifying a simulation trajectory not enumerated in the chapter text. Flag as a companion-website interactive or a Chapter 9 carry-forward; do not add to this chapter's figure budget.*
