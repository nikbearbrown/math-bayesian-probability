# CAJAL Figure Plans — Chapter 01: The Same Question, Two Answers

*Figure plans for Chapter 1 — The medical testing problem reveals what frequentist statistics can and cannot say, and introduces the Bayesian alternative that answers the question the test actually asks.*

---

## Figure 01.1 — True Positives vs. False Positives in 10,000 Screened Persons

**Suggested filename:** 01-true-vs-false-positives-frequency.svg
**Figure type:** Statistical / quantitative (stacked bar chart)
**One-sentence concept:** When 10,000 people are screened for a disease with 0.1% prevalence, false positives from healthy people outnumber true positives from sick people by approximately 10 to 1, producing a posterior of 9%.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- Single stacked bar representing all 110 positive test results from a screened population of 10,000.
- Bottom segment: 10 true positives (people who have the disease and test positive); labeled "True positives: 10 (9%)".
- Top segment: 100 false positives (healthy people who test positive); labeled "False positives: 100 (91%)".
- Y-axis: count of positive tests, baseline at zero, maximum 110, labeled "Positive test results."
- A callout arrow pointing to the true-positive segment with the posterior probability: "P(disease | positive) ≈ 9%."
- Population context note: "From 10,000 screened; 10 have disease, 9,990 do not."
- X-axis: single bar labeled "Positive test results."

**O — Organization:** Single vertical stacked bar, y-axis at zero, annotation callout to the right. The two segments are visually distinct by color and are drawn in proportion: 10-unit bottom segment vs. 100-unit top segment (1:10 ratio). The extreme visual dominance of the false-positive segment is the pedagogical payload — the rendering must not flatten the ratio. Do not normalize to percentages in the bar itself; show raw counts so the 10 vs. 100 ratio is immediately legible.

**P — Presentation:** True-positive segment: primary data accent (#C8102E) — the signal. False-positive segment: neutral mid-gray (#787878) — the noise. Y-axis and axis labels: #2a1a0e ink, JetBrains Mono 11pt for tick labels. Bar background: chart-area fill #F5F5F5. Structural strokes #D4D4D4 0.75pt for gridlines. Callout arrow #2a1a0e 1.5pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The full 10,000-person population decomposition (all four cells of the 2×2 contingency table) — this figure shows only the positive-test subgroup, not all 10,000.
- True negatives (9,890 correct non-detections) — including them would dwarf the figure and obscure the point about positive predictive value.
- False negatives (the ~0 missed cases, since sensitivity = 0.99 × 10 ≈ 10 ≈ all cases detected) — omitting for clarity; the chapter discusses them in text.
- The p-value annotation — this figure illustrates the Bayesian natural-frequency result only; the frequentist answer appears in Figure 01.2.
- Multiple prevalence scenarios (0.01, 0.1) — the exercise variant; this figure shows only the 0.001 base case.
- Any 3D bar or perspective effect.

**Caption (draft):** Of the approximately 110 people who test positive when 10,000 are screened (prevalence 0.1%, sensitivity 99%, false positive rate 1%), only 10 have the disease — the false positives from the large healthy population outnumber true positives by about 10 to 1, giving a posterior probability of roughly 9%.

**Accuracy check (figure-checker):**
- True positives: 10,000 × 0.001 × 0.99 = 9.9 ≈ 10. Verify segment height = 10.
- False positives: 10,000 × 0.999 × 0.01 = 99.9 ≈ 100. Verify segment height = 100.
- Total bar height: 110. Y-axis maximum must be at least 110; baseline must be exactly zero.
- Posterior displayed: 10/110 = 0.0909... ≈ 9%. Verify the callout value matches the chapter's stated "approximately 9%."
- The true-positive segment must be visually smaller than the false-positive segment (1:10 ratio). If the rendering equalizes them, the cognitive load check fails.
- No probability expressed on the y-axis — this is a count axis. Confirm the axis label says "count" or "number of people," not "probability."
- Proportional Ink Rule: segment areas must be proportional to counts (10 and 100), not normalized.

---

## Figure 01.2 — Frequentist vs. Bayesian: The Same Test, Two Answers

**Suggested filename:** 01-frequentist-vs-bayesian-comparison.svg
**Figure type:** Comparison panels
**One-sentence concept:** The frequentist p-value (0.01) and the Bayesian posterior (9%) are computed from the same test performance data but answer structurally different questions, and only the Bayesian calculation uses the disease prevalence.

**S — Specification:** Double-column 170mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 460.

**C — Content:**
- Left panel — Frequentist path: labeled "Question: How surprising is a positive test if the patient is healthy?" Input box: "False positive rate = 0.01." Computation: "P(positive | no disease) = 0.01." Output box: "p = 0.01 → reject H₀ at α = 0.01." A prominent "MISSING" callout for the prevalence input (shown as a grayed-out dashed box labeled "Prevalence — not used").
- Right panel — Bayesian path: labeled "Question: Given a positive test, how likely is disease?" Three input boxes: "Prior: P(disease) = 0.001," "Likelihood: P(positive | disease) = 0.99," "False positive rate: P(positive | no disease) = 0.01." Computation arrow leading to: "Denominator = 0.01098." Output box: "P(disease | positive) ≈ 9%."
- Shared horizontal separator with the test description at the top of both panels: "Test: 99% sensitivity, 1% false positive rate; prevalence = 0.001."
- Six labeled components total: left-panel question, left-panel missing-input callout, left-panel output; right-panel three inputs, right-panel output.

**O — Organization:** Two panels side by side at equal width. Each panel flows top-to-bottom: question → inputs → computation → output. The missing-prevalence callout in the left panel is the visual anchor — it must be legible. Standard → arrows for computational flow within each panel. A thin vertical dividing rule separates the panels. Both panels share the same horizontal question-strip at top.

**P — Presentation:** Right-panel output box (Bayesian posterior) uses primary data accent border (#C8102E) to signal the decision-relevant answer. Left-panel output box uses neutral gray border (#787878). The missing-prevalence dashed box in the left panel uses #D4D4D4 dashed border to signal absence. Input boxes use chart-area fill #F5F5F5 with #D4D4D4 border 1pt. Arrows #2a1a0e 1.5pt with arrowhead marker. Panel labels in EB Garamond 14pt. Computation values in JetBrains Mono 11pt. Dividing rule #D4D4D4 0.75pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The full law of total probability derivation steps — show only the resolved denominator value (0.01098).
- The natural frequency version (10/110 out of 10,000) — that is Figure 01.1's territory; do not duplicate.
- Any claim about which approach is "correct" — this figure shows what each approach outputs, not which is better.
- P-value definition derivation or NHST mechanics beyond what is shown.
- The prevalence sensitivity analysis (how the posterior changes at 0.01 and 0.1 prevalence) — belongs in exercises.
- Any third framework (likelihood ratio, etc.).
- Clinical interpretation beyond the output values — that is chapter text.

**Caption (draft):** Same test, same data, two questions: the frequentist p-value of 0.01 measures how surprising a positive test is under the null, while the Bayesian posterior of approximately 9% measures how likely disease actually is given the positive test — the second calculation requires the disease prevalence (0.001) that the first ignores.

**Accuracy check (figure-checker):**
- Left-panel p-value: P(positive | no disease) = 0.01. This is the false positive rate, exactly as stated in the chapter. Verify no rounding error.
- Right-panel denominator: (0.001)(0.99) + (0.999)(0.01) = 0.00099 + 0.00999 = 0.01098. Verify this value if shown.
- Right-panel posterior: 0.00099 / 0.01098 = 0.09016... ≈ 0.090 ≈ 9%. Verify displayed value is "approximately 9%" or "≈ 0.090," matching the chapter text.
- The missing-prevalence callout must appear in the LEFT (frequentist) panel, not the right.
- The prevalence value must appear as an INPUT in the RIGHT (Bayesian) panel only.
- No probability displayed may exceed 1.0.
- The two output values (0.01 and 9%) must be visually distinguishable without color — the Bayesian output box must differ in border weight or box shape from the frequentist output box for grayscale accessibility.

---

## Figure 01.3 — Posterior Probability as a Function of Prevalence

**Suggested filename:** 01-posterior-vs-prevalence.svg
**Figure type:** Statistical / quantitative (line chart)
**One-sentence concept:** As disease prevalence rises from near zero to near one, the posterior probability P(disease | positive test) rises nonlinearly from near zero to near one, with the curve's position set entirely by the test's sensitivity and false positive rate.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- X-axis: disease prevalence, range 0 to 1, labeled "Prevalence P(disease)"; zero baseline.
- Y-axis: posterior P(disease | positive test), range 0 to 1, labeled "Posterior P(disease | positive)"; zero baseline.
- One smooth S-shaped curve for the test parameters used throughout Chapter 1: sensitivity = 0.99, false positive rate = 0.01.
- Three annotated points on the curve: (prevalence = 0.001, posterior ≈ 0.090); (prevalence = 0.01, posterior ≈ 0.50); (prevalence = 0.1, posterior ≈ 0.917).
- A horizontal reference line at posterior = 0.5 (labeled "Equal odds") as a visual anchor showing where positive tests become "more likely than not to be true."

**O — Organization:** Single-panel line chart. X-axis horizontal from 0 to 1. Y-axis vertical from 0 to 1. The curve runs from bottom-left to top-right with its inflection point near prevalence = 0.01 for these parameters. The three annotated points are labeled with dot markers and callout values. The equal-odds reference line is dashed. No second curve (no alternative test parameter set) — one concept per figure.

**P — Presentation:** Curve: primary data accent (#C8102E), stroke-width 2pt. Annotated point markers: filled circles (#C8102E). Reference line (posterior = 0.5): #787878 dashed (stroke-dasharray 5 4). Axis labels and tick labels: JetBrains Mono 11pt #545454. Chart area fill #F5F5F5. Grid lines #D4D4D4 0.75pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- A second curve for different sensitivity/specificity parameters — would require a legend and risks comparing rather than illustrating.
- The frequentist p-value plotted on the same axes — p-values and posteriors are not commensurable; mixing them would be a hard mathematical error.
- Any portion of the x-axis below zero or above one.
- Tick marks denser than 0.1 intervals — visual clutter for an illustrative curve.
- Confidence band or uncertainty envelope — Chapter 1 uses point prevalence only; uncertainty is Ch 7–8.
- The log-prevalence rescaling (used in epidemiology) — this chapter works on the linear scale.

**Caption (draft):** P(disease | positive) rises steeply through the rare-disease range: at prevalence 0.1% the posterior is 9%, at 1% it reaches 50%, and at 10% it climbs to 92% — with sensitivity 0.99 and false positive rate 0.01 held fixed, the prior prevalence alone drives the posterior across an order of magnitude.

**Accuracy check (figure-checker):**
- At prevalence = 0.001: posterior = (0.001 × 0.99) / (0.001 × 0.99 + 0.999 × 0.01) = 0.00099 / 0.01098 = 0.0902. Labeled value must be approximately 9% (or 0.090), matching the chapter.
- At prevalence = 0.01: posterior = (0.01 × 0.99) / (0.01 × 0.99 + 0.99 × 0.01) = 0.0099 / 0.0198 = 0.500. Labeled value must be 50%.
- At prevalence = 0.1: posterior = (0.1 × 0.99) / (0.1 × 0.99 + 0.9 × 0.01) = 0.099 / 0.108 = 0.9167. Labeled value must be approximately 91–92%, matching any chapter text that names this value.
- Both axes must start at zero. No truncated baseline.
- The curve must be monotonically increasing — if any rendered segment shows a decrease in posterior as prevalence increases, the render is wrong.
- The inflection point of the curve (where the slope is steepest) occurs near prevalence = false-positive-rate / (false-positive-rate + sensitivity) = 0.01 / (0.01 + 0.99) ≈ 0.01. Verify the curve shape is consistent with this.
- The equal-odds line must intersect the curve at prevalence = 0.01 (the point computed above). Verify this intersection is consistent.
