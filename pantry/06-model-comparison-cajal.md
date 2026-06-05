# CAJAL Figure Plans — Chapter 6: Model Comparison

*Produced by CAJAL (silent mode). Plans only — no SVGs. Renderer writes SVGs to `images/` and PNGs via `SCRIPTS/svg-to-png.mjs`.*

---

## Figure 06.1 — AIC Ranking vs. Bayes Factor Evidence

**Suggested filename:** 06-aic-vs-bayes-factor.svg
**Figure type:** Comparison panels
**One-sentence concept:** AIC produces a ranking (ΔAIC = 4.2 favors M2) while the Bayes factor produces an evidence ratio (BF₂₁ = 8.3), and the two outputs cannot be read interchangeably.

**S — Specification:** Single-page textbook width, 700 × 420 px viewBox, 300 DPI, vector SVG. Two equal side-by-side panels sharing a common vertical axis label zone. 32 px margin all sides. Labels on 8 px grid.

**C — Content:**
- Left panel label: "Frequentist (AIC)"
- Right panel label: "Bayesian (Bayes Factor)"
- Left panel: two horizontal bars for M1 and M2 anchored at zero. M1 bar length proportional to AIC = 142.3; M2 bar length proportional to AIC = 138.1. ΔAIC = 4.2 annotated as a gap bracket between the bar ends. Label: "Lower AIC = better fit." Scale tick marks at 130, 135, 140, 145.
- Right panel: a single horizontal ratio arrow or log-scaled bar showing BF₂₁ = 8.3 on a reference line at BF = 1. The BF = 8.3 position is marked with a labeled point. The label reads "Data are 8.3× more consistent with M2." No posterior model probability is shown in this panel (that belongs to the caption, not the figure).
- Dividing vertical rule between panels: dashed, `stroke="#D4D4D4"`.
- Both panels share a bottom-axis label zone: "Model M1 (linear)" and "Model M2 (exponential)" as row identifiers in the left panel; "BF = 1 (no evidence)" at left anchor and "BF = 8.3" marked in right panel.

**O — Organization:** Left-to-right two-panel layout. Left panel: horizontal bar chart, bars extend right from a zero baseline, M1 above M2, ΔAIC bracket annotated above the bar pair. Right panel: horizontal number line from BF = 1 (left anchor) to BF = 15 (right edge), log-scaled optional; single marked point at BF = 8.3 with a vertical tick and label. No arrows connecting the panels — the point is their independence, not their equivalence.

**P — Presentation:** Primary structural anchor color (#0072B2, Blue) for M2 bars and the BF = 8.3 marker. Neutral gray (#787878) for M1 bars and the BF = 1 anchor. Panel background: `#F5F5F5`. Canvas: `#FFFFFF`. Ink: `#2a1a0e`. Dashed divider: `#D4D4D4`. No red encoding. Grayscale distinguishable: M2 (#0072B2, L*≈32) vs. M1 (gray, L*≈51) — distinct luminance bands. No gradient, no shadow, no 3D. House SVG style governs render: EB Garamond for panel titles (14pt), Inter for bar labels and axis ticks (11–12pt), JetBrains Mono for numeric tick values.

**E — Exclusions:**
- Do NOT show posterior model probability (P(M2|data) = 89%) — that claim requires the prior model probability assumption and belongs in the text, not this figure.
- Do NOT show BIC or PSIS-LOO — out of scope for this comparison figure.
- Do NOT show likelihood curves or data scatter — figure is about the output metrics, not the fit curves.
- Do NOT connect the two panels with an equivalence arrow or "=" sign.
- Do NOT show the Jeffreys evidence scale categories here — that belongs to Figure 06.2.
- Do NOT use a non-zero baseline on the AIC bar chart.
- Do NOT label bars with raw log-likelihood values.

**Caption (draft):** The same epidemic dataset produces two different outputs: the frequentist AIC gives a ranking (ΔAIC = 4.2 favors exponential growth), while the Bayes factor gives an evidence ratio (BF₂₁ = 8.3) — quantities that answer related but distinct questions about model quality.

**Accuracy check (figure-checker):**
- AIC bars must both start at zero; M2 bar must be visibly shorter than M1, with the ΔAIC = 4.2 gap correctly annotated.
- BF scale must anchor at BF = 1 (no evidence), not BF = 0; a log scale is acceptable only if the 1-unit anchor is clearly labeled.
- No statement in the figure or caption may equate ΔAIC with a probability or BF with a frequentist p-value.
- The figure must not imply that the two panels are measuring the same quantity at different scales.

---

## Figure 06.2 — Jeffreys Evidence Scale with Prior-Sensitivity Caveat

**Suggested filename:** 06-jeffreys-scale-caveat.svg
**Figure type:** Annotated example (labeled scale strip with annotated case and caveat note)
**One-sentence concept:** The Jeffreys/Kass-Raftery evidence scale classifies Bayes factor values into named tiers, with BF₂₁ = 8.3 falling in "Moderate," but an annotation must flag that the scale's tiers assume a well-specified prior — a contested condition.

**S — Specification:** Single-column textbook width, 700 × 300 px viewBox, 300 DPI, vector SVG. Horizontal scale strip occupying center two-thirds of canvas height, with annotation below. 32 px margin all sides.

**C — Content:**
- Horizontal scale strip on a log₁₀ axis from BF = 1 (left) to BF = 100+ (right). Five labeled segments: [1–3] "Anecdotal," [3–10] "Moderate," [10–30] "Strong," [30–100] "Very strong," [>100] "Decisive." Segment boundaries marked with vertical ticks.
- Filled marker at BF = 8.3 with label "BF₂₁ = 8.3 (this chapter's example)" positioned above the scale strip.
- Below the scale strip: a dashed-border annotation box with text: "Tier boundaries assume the prior on model parameters is well-specified. Prior sensitivity analysis is required — different reasonable priors can shift BF₂₁ from 6.1 to 11.4 in this example."
- Source attribution at bottom right: "Scale: Kass & Raftery (1995); Jeffreys (1961)."

**O — Organization:** Top zone: horizontal labeled scale strip with log axis. Middle zone: annotated case marker (BF = 8.3). Bottom zone: caveat annotation box (dashed border, lighter background `#F5F5F5`, interior `#FAFAFA`). Flow is top-down; the caveat reads after the scale, not beside it.

**P — Presentation:** Tier segments rendered as filled rectangles with graduated neutral grays from light (Anecdotal, L*≈84) to medium-dark (Decisive, L*≈51), so grayscale ordering matches evidential strength. The BF = 8.3 marker: `#0072B2` (Blue, primary structural anchor). Caveat box border: `stroke-dasharray="4 3"` `stroke="#D4D4D4"`. Caveat box interior: `#F5F5F5`. All text: Inter (labels), JetBrains Mono (numeric values), EB Garamond for strip title if used. No red encoding. No gradient on the tier segments — flat fills only.

**E — Exclusions:**
- Do NOT label any BF tier as "the Bayesian probability that the model is correct" — this is the misconception the caveat exists to rebut.
- Do NOT show the conversion to P(M2|data) = 89% — that computation requires the prior model probability and is addressed in the text.
- Do NOT include DIC, WAIC, or PSIS-LOO scores on the same scale.
- Do NOT show negative BF values or BF < 1 tiers in this figure (those favor M1 and are symmetric; adding them doubles component count without pedagogical payoff here).
- Do NOT use a linear axis for BF — the tier boundaries span two orders of magnitude and require log scale or unequal segment widths.
- Do NOT omit the caveat annotation — the chapter explicitly flags the prior-sensitivity problem and the figure must not overstate BF as a clean probability.

**Caption (draft):** The Jeffreys/Kass-Raftery scale classifies BF₂₁ = 8.3 as "Moderate" evidence for exponential growth, but tier membership depends on the prior being well-specified: prior sensitivity analysis showed BF₂₁ ranging from 6.1 to 11.4 across reasonable prior choices.

**Accuracy check (figure-checker):**
- Tier boundaries must match Kass & Raftery (1995): [1–3] Anecdotal, [3–10] Moderate, [10–30] Strong, [30–100] Very strong, [>100] Decisive. Any deviation is a factual error.
- BF = 8.3 must fall visually within the Moderate segment [3–10].
- Axis must be log-scaled or use visually proportional segment widths reflecting the log scale.
- Caveat annotation must be present and must not be removable by the renderer without explicit instruction — it is substantive content, not a design note.
- No text in the figure may assert that the BF tier equals a posterior probability.

---

*Split note: The prior-sensitivity problem for Bayes factors could support a third figure (e.g., a sensitivity plot showing BF vs. prior width), but that would exceed 2 figures for this chapter and requires quantitative data not fully specified in the chapter text. Flag for the "Still Puzzling" video candidate if a dynamic visualization is developed.*
