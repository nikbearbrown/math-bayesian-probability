# CAJAL Figure Plans — Chapter 7: Priors

*Produced by CAJAL (silent mode). Plans only — no SVGs. Renderer writes SVGs to `images/` and PNGs via `SCRIPTS/svg-to-png.mjs`.*

---

## Figure 07.1 — Same Data, Three Posteriors

**Suggested filename:** 07-three-priors-three-posteriors.svg
**Figure type:** Comparison panels (overlaid density curves on a shared axis)
**One-sentence concept:** Three priors applied to the same clinical trial data (mean difference = 4.9 mmHg, SE = 2.3, n = 40) yield posteriors whose modes barely move but whose tails — including the clinically critical P(δ > 3) region — diverge substantially.

**S — Specification:** Single-page textbook width, 700 × 420 px viewBox, 300 DPI, vector SVG. Single panel with three overlaid density curves on a shared horizontal axis (δ, treatment effect in mmHg). Chart area `#F5F5F5`. 32 px margin all sides, chart margins top 48 / right 40 / bottom 56 / left 64. Labels on 8 px grid.

**C — Content:**
- Horizontal axis: δ (treatment effect, mmHg), range −4 to +14. Tick marks at −2, 0, 2, 4, 6, 8, 10, 12. Zero baseline required (axis passes through δ = 0).
- Vertical axis: probability density, starting at 0. Tick marks at 0, 0.05, 0.10, 0.15, 0.20. No non-zero baseline.
- Three density curves overlaid:
  - Curve 1 (Prior 1: Flat): Normal(4.9, 2.3²). Posterior mean = 4.9, 95% CrI ≈ [0.4, 9.4]. Rendered as a medium-weight solid line.
  - Curve 2 (Prior 2: Weakly informative, Normal(0, 10²)): Posterior ≈ Normal(4.75, ~5.0²) — very similar to Curve 1 visually. Rendered as a dashed line of the same weight.
  - Curve 3 (Prior 3: Informative, Normal(0, 2²)): Posterior ≈ Normal(2.11, ~1.5²), shifted left and taller (less variance). Rendered as a solid line, visually distinct from Curve 1.
- Vertical reference line at δ = 3 mmHg labeled "Clinical threshold (3 mmHg)" — dashed, `stroke-dasharray="5 4"`.
- Vertical reference line at δ = 0 (the axis itself) labeled "No effect."
- Label each curve directly on the figure (no legend box): "Prior 1: Flat — P(δ>3) = 0.79," "Prior 2: Weak — P(δ>3) = 0.76," "Prior 3: Informative — P(δ>3) = 0.27." Labels positioned at each curve's peak or along the right descending tail, non-overlapping.
- Shaded region to the right of δ = 3 for Curve 3 only, to make the small P(δ>3) area visually salient. Fill at low opacity.

**O — Organization:** Single panel. Curves overlaid on shared axis system. The clinical threshold line (δ = 3) bisects the display horizontally and is the visual anchor that makes the tail divergence legible. Curve labels follow the curves' right tails rightward, staggered vertically to avoid overlap. The shaded tail region for Curve 3 appears behind all three curves. The zero line on the vertical axis must be visually present (curves approach but do not cross below zero density).

**P — Presentation:**
- Curve 1 (Flat prior): `#2a1a0e` (Ink) — solid, stroke-width 2. Represents the implicit frequentist baseline.
- Curve 2 (Weakly informative): `#0072B2` (Blue) — dashed (`stroke-dasharray="6 3"`), stroke-width 2. Near-identical to Curve 1 in this example; the dashing distinguishes it without implying a different kind of result.
- Curve 3 (Informative prior): `#D55E00` (Vermillion) — solid, stroke-width 2. Used here in its negative/contrasting semantic role: this is the prior that most sharply reduces the tail probability. NOT encoding "wrong" — encoding "most constraining."
- Tail shading under Curve 3 right of δ = 3: `#D55E00` at 15% opacity.
- Clinical threshold line: `#C8860E` (Ochre) dashed rule — decorative/reference role, not data encoding. `stroke-dasharray="5 4"` `stroke-width="1"`.
- Zero-effect line at δ = 0: `#D4D4D4` (border gray), solid, `stroke-width="0.75"`.
- Chart area fill: `#F5F5F5`. Canvas: `#FFFFFF`. All text: `#2a1a0e` (headings EB Garamond) / `#545454` (axis labels Inter, JetBrains Mono for numerics).
- Grayscale test: Ink (L*≈10) vs. Vermillion (L*≈40) vs. Blue (L*≈32) — Blue and Vermillion are close in luminance; dashing of Curve 2 provides the secondary encoding that separates them in grayscale. All three curves distinguishable in grayscale.
- No gradient. No shadow. No 3D. Areas must visually integrate to 1 (each curve is a proper density).

**E — Exclusions:**
- Do NOT show the raw data scatter or the likelihood curve separately — the figure illustrates posterior output, not the likelihood.
- Do NOT show the prior distributions themselves — showing both prior and posterior would double the component count (6 curves) and shift the concept from "posteriors diverge" to "priors diverge." The prior values are in the labels; the figure shows only the posteriors.
- Do NOT use a 95% credible interval bracket annotation on this figure — the density curves communicate uncertainty directly; adding brackets would clutter the display. CrI values belong in the chapter's comparison table.
- Do NOT show the frequentist confidence interval as a separate panel — it is addressed in the text's side-by-side table; adding it here would require a second panel and exceeds the figure's scope.
- Do NOT shade the tail regions for Curve 1 or Curve 2 — the pedagogical contrast is that the informative prior uniquely shifts the tail, and shading all three curves obscures this.
- Do NOT label the δ axis with negative values beyond −4 (the densities are negligible there and the axis would extend meaninglessly).
- Do NOT label P(δ > 3) values anywhere except directly on the curve labels — no separate probability annotation box.

**Caption (draft):** Three posteriors from the same blood pressure trial data (n = 40, observed mean difference 4.9 mmHg): the flat prior and weakly informative prior yield nearly identical posteriors, but the informative prior — encoding that two prior trials showed null effects — shifts P(δ > 3 mmHg) from 0.79 to 0.27, demonstrating that tails are more sensitive to prior choice than point estimates.

**Accuracy check (figure-checker):**
- All three curves must be valid probability density functions: non-negative everywhere, visually integrating to 1 (area under each curve = 1). No density value below zero.
- Curve 1 (flat prior) must peak at δ = 4.9 with SD ≈ 2.3 — matching the likelihood, since a flat prior yields a posterior equal to the likelihood.
- Curve 2 must peak slightly left of 4.9 (posterior mean ≈ 4.75) and be only marginally narrower than Curve 1. If Curve 2 looks substantially different from Curve 1, the prior specification is wrong.
- Curve 3 must peak near δ = 2.11 and be substantially taller (lower variance) than Curves 1 and 2.
- The clinical threshold line at δ = 3 must be to the left of Curve 1's peak (4.9) and to the right of Curve 3's peak (2.11) — this geometric relationship is the pedagogical point.
- P(δ > 3) for Curve 3 must be visually plausible as ~27%: the shaded region should appear notably smaller than the complementary left tail.
- Vertical axis must start at zero — no non-zero baseline.
- The zero-effect reference line at δ = 0 must be present and labeled.

---

## Figure 07.2 — The Hidden Flat Prior (Conceptual Map)

**Suggested filename:** 07-hidden-flat-prior.svg
**Figure type:** Conceptual map (annotated schematic comparing implicit vs. explicit prior)
**One-sentence concept:** A frequentist t-test and a Bayesian analysis with a flat prior are mathematically equivalent, because the t-test implicitly uses a uniform prior — but that uniform prior assigns equal probability to a 1 mmHg drug effect and a 1,000 mmHg drug effect.

**S — Specification:** Single-column textbook width, 700 × 320 px viewBox, 300 DPI, vector SVG. Two annotated schematic boxes side by side with a central equivalence annotation. 32 px margin all sides.

**C — Content:**
- Left box: "Frequentist t-test." Interior bullet list (3 items, rendered as labeled rectangles or text blocks): "Implicit prior: uniform on δ," "Assigns equal weight to δ = 1 mmHg and δ = 1,000 mmHg," "Prior is fixed; cannot encode domain knowledge."
- Right box: "Bayesian (flat prior)." Interior bullet list (3 matching items): "Explicit prior: Uniform / improper flat," "Same mathematical result as t-test," "Prior is named; can be audited and changed."
- Central annotation (between boxes, on the connecting axis): double-headed arrow labeled "Mathematically equivalent" above; below, a dashed bracket with note "Prior is hidden vs. prior is visible — not the same as no prior vs. prior."
- Below the two-box row: a single narrow horizontal strip labeled "What both assign equal probability to:" with three evenly spaced tick marks labeled "δ = −1,000 mmHg," "δ = 0 mmHg," "δ = +1,000 mmHg" — illustrating the absurdity of the flat prior on the observable scale for this domain.

**O — Organization:** Three horizontal zones. Top zone: two side-by-side annotated boxes (left: frequentist, right: Bayesian flat) connected by a double-headed equivalence arrow. Middle zone: the dashed bracket clarification note. Bottom zone: the flat-prior implications strip. Flow is top-to-bottom; the bottom strip is the punchline.

**P — Presentation:** Both main boxes: `stroke="#D4D4D4"` `stroke-width="1"` `fill="#FFFFFF"` — neutral structural containers. The "mathematically equivalent" arrow: `#2a1a0e` (Ink), double-headed, `stroke-width="1.5"`. The dashed bracket: `stroke-dasharray="4 3"` `stroke="#545454"` — secondary/cautionary annotation. The bottom strip: `fill="#F5F5F5"` border, with the three tick marks in `#2a1a0e`. No color encoding on the main boxes — they are parallel, not evaluated as better or worse. The distinction is structural, not evaluative. No gradient, no shadow, no rounded corners.

**E — Exclusions:**
- Do NOT use color to imply one approach is superior — the point is equivalence, not ranking.
- Do NOT show the posterior from this comparison — this figure is about the prior structure, not the resulting inference.
- Do NOT show the weakly informative or informative prior in this figure — those belong to Figure 07.1. This figure addresses only the flat-prior case.
- Do NOT extend the flat-prior strip to include density curve rendering — that level of detail duplicates Figure 07.1.
- Do NOT label the boxes with value judgments ("dishonest," "better") — the chapter is careful to call the flat prior a convention, not a deception.
- Do NOT include the regulatory gaming case (prior centered at +8 mmHg to favor the drug) — that is a separate concept addressed in Exercise 2, not in this conceptual map.

**Caption (draft):** A frequentist t-test and a Bayesian analysis with a flat prior produce identical results because they use the same prior — uniform over all values of δ — but only one names it; the flat prior assigns equal probability to a 1 mmHg blood pressure reduction and a 1,000 mmHg reduction, which is not neutrality on the observable scale.

**Accuracy check (figure-checker):**
- The equivalence claim (t-test = Bayesian flat prior) must be accurate for the normal likelihood case as specified in the chapter. It holds for normal models with flat improper priors; the caption or annotation must not extend this claim to non-normal likelihoods.
- The flat-prior strip at the bottom must cover symmetric negative and positive values — showing that the uniform prior has equal mass at extreme negative and extreme positive effect sizes, not just at large positive values.
- No assertion that the t-test is "wrong" — the figure must show the structure without editorializing.
- The double-headed arrow between boxes must clearly read as equivalence, not as superiority of one over the other.

---

*Split note: Figure 07.1 is the chapter's critical figure and is the only one strictly required. Figure 07.2 is important but supplementary — it can be omitted if page budget requires. A third figure showing Bayesian update as n increases (prior dominating at small n, likelihood dominating at large n) would be valuable but would require data not specified in this chapter's worked examples; flag for the companion website interactive.*
