# CAJAL Figure Plans — Chapter 04: Comparing Two Groups

*Figure plans for Chapter 4 — The two-sample t-test and its Bayesian analog on tutorial data (p = 0.03 / P(B better) ≈ 0.91), followed by the Ioannidis PPV argument showing how base rate of true hypotheses drives the false-positive share of significant results.*

---

## Figure 04.1 — p = 0.03 vs. P(B better) ≈ 0.91: The Same Data, Two Answers

**Suggested filename:** 04-ttest-vs-bayesian-posterior-comparison.svg
**Figure type:** Comparison panels
**One-sentence concept:** The frequentist t-test returns p = 0.03 (a statement about the data given no effect) while the Bayesian posterior on δ = μ_B − μ_A gives P(δ > 0 | data) ≈ 0.91 (a direct probability that Tutorial B outperforms Tutorial A), and only the second quantity answers the university's decision question.

**S — Specification:** Double-column 170mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 460.

**C — Content:**
- Left panel — Frequentist: panel label "Welch t-test result." A horizontal axis labeled "t-statistic" centered at zero; a t-distribution curve for df ≈ 76 (approximately normal in shape). The observed t = 2.21 marked with a vertical line; the tail area to the right (and mirrored left) shaded to represent p = 0.03. Output callout box: "p = 0.03 → reject H₀ at α = 0.05." A "MISSING" callout for the decision-relevant probability, shown as a grayed-out dashed box labeled "P(Tutorial B better) — not computable."
- Right panel — Bayesian: panel label "Posterior on δ = μ_B − μ_A." A horizontal axis labeled "δ (percentage points)"; a Normal posterior curve approximately Normal(3.9, 1.9), centered near 3.9, range roughly −4 to +12. A vertical reference line at δ = 0 (no-effect boundary). The region δ > 0 shaded; labeled "P(δ > 0 | data) ≈ 0.91." The 95% credible interval [0.2, 7.6] marked as a horizontal bar below the curve.
- Both panels share x-axis conceptual structure: the left shows the t-distribution tail; the right shows the posterior over the difference.
- Six labeled components: left-panel t-value marker + shaded tail + missing-callout; right-panel δ = 0 line + shaded region label + 95% CrI bar.

**O — Organization:** Two panels side by side, equal width, separated by a thin vertical dividing rule. Left panel: the t-distribution is drawn from roughly −4 to +4 standard units; the observed t = 2.21 divides the right tail; the two-sided tail area is labeled p = 0.03. Right panel: the posterior density is drawn on a scale in percentage-point units; the δ = 0 line is the natural decision boundary; the shaded area to the right (91% of the distribution) is the key quantity. The missing-probability callout in the left panel creates the visual asymmetry with the probability callout in the right panel — this asymmetry is the pedagogical payload. Standard → arrows not used; the figure is a static comparison. Both panels share the same height for visual alignment.

**P — Presentation:** Shaded tail area (left panel, frequentist): neutral mid-gray (#787878), fill opacity 0.50 — represents an imprecise probability concept. Shaded region δ > 0 (right panel, Bayesian): primary data accent (#C8102E), fill opacity 0.75 — represents the decision-relevant probability. Density curve outlines: #2a1a0e ink, stroke-width 1.5pt. δ = 0 reference line: #2a1a0e, dashed (stroke-dasharray 5 4), stroke-width 1pt. 95% CrI bar: #2a1a0e solid, stroke-width 2pt, end caps. Missing-probability callout box (left): dashed border #D4D4D4, fill #F5F5F5, text #545454. Decision-probability callout box (right): solid border #C8102E 1pt, fill #F5F5F5. Panel labels: EB Garamond 14pt #2a1a0e. Axis tick labels: JetBrains Mono 11pt #545454. Chart area fill #F5F5F5. Dividing rule #D4D4D4 0.75pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The posterior distributions on μ_A and μ_B separately — this figure focuses on the posterior on the difference δ, which is the decision-relevant quantity; the individual group posteriors belong to chapter text description.
- The effect size (Cohen's d = 0.50) — a scalar annotation not needed for the comparison panels visual; described in chapter text.
- The prior specification (Normal(70,15) on each mean) — shown in chapter text as context for the Bayesian column; not a visual element in this comparison figure.
- The Welch-Satterthwaite df calculation — chapter algebra; not shown here.
- Any third framework (permutation test, Mann-Whitney U) — one comparison per figure.
- The p = 0.054 result from s = 9% — the chapter settles on p = 0.03 from s = 8%; use only that value.
- The replication crisis / Ioannidis argument — that is Figure 04.2's territory.
- 3D or perspective effects.

**Caption (draft):** Same tutorial data (n_A = 40, n_B = 38; 4-point score gap), two answers: the Welch t-test finds p = 0.03 — the data are inconsistent with no effect at α = 0.05 — while the Bayesian posterior on the group difference δ gives P(δ > 0 | data) ≈ 0.91, the direct probability that Tutorial B outperforms Tutorial A that the university's decision requires.

**Accuracy check (figure-checker):**
- Left panel: t = (76−72)/SE_δ where SE_δ = √(64/40 + 64/38) ≈ 1.81, so t ≈ 4/1.81 ≈ 2.21. The t-value marker must be placed at t = 2.21, not at t = 1.96.
- Left panel: p = 0.03 is a two-sided p-value. The shaded tail area must appear on both sides (or be clearly labeled as two-sided) — a one-sided shaded area mislabeled p = 0.03 is a mathematical error.
- Right panel: posterior on δ is approximately Normal(3.9, 1.9). The distribution must be centered near 3.9 (positive), not at 0. A curve centered at zero would misrepresent the posterior.
- Right panel: P(δ > 0) ≈ 0.91 — verify the shaded area to the right of δ = 0 under a Normal(3.9, 1.9) is consistent with this value. For Normal(3.9, 1.9): z = (0 − 3.9)/1.9 ≈ −2.05, P(Z > −2.05) ≈ 0.98. The chapter states 0.91–0.98 depending on prior width; confirm the labeled value is within this range and matches the chapter's stated value.
- Right panel: 95% CrI = [0.2, 7.6]. Verify the CrI bar endpoints match these values.
- Both y-axes (density) must baseline at zero.
- The missing-probability callout must appear in the LEFT (frequentist) panel; the probability value must appear in the RIGHT (Bayesian) panel.
- δ = 0 reference line must pass through the x-axis at zero, not at the posterior mean.

---

## Figure 04.2 — How Prior Probability Drives False-Positive Share (Ioannidis PPV)

**Suggested filename:** 04-ioannidis-ppv-base-rate.svg
**Figure type:** Statistical / quantitative (bar chart)
**One-sentence concept:** When the prior probability of a true hypothesis is low (R = 0.20), most statistically significant results are false positives — at 50% power and α = 0.05, only 100 of 140 significant results from 1,000 tests are true discoveries, giving a positive predictive value of approximately 71%.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 460.

**C — Content:**
- One stacked bar representing the 140 significant results from testing 1,000 hypotheses where R = 0.20, power = 0.50, α = 0.05.
- Bottom segment: 100 true positives (correct discoveries from the 200 truly effective hypotheses). Labeled "True positives: 100 (71%)."
- Top segment: 40 false positives (Type I errors from the 800 null hypotheses). Labeled "False positives: 40 (29%)."
- Y-axis: count of significant results, baseline at zero, maximum 140, labeled "Significant results (p < 0.05)."
- A callout arrow pointing to the full bar: "From 1,000 tests; R = 0.20."
- PPV annotation: "PPV = 100/140 ≈ 71%."
- Three parameter values displayed as a compact legend or subtitle: "R = 0.20 · Power = 0.50 · α = 0.05."

**O — Organization:** Single vertical stacked bar, y-axis at zero, parameter annotations to the right or below. The two segments are drawn in proportion to their counts: 100 (bottom, true positives) vs. 40 (top, false positives), giving a 5:2 ratio. The bar must be wide enough to accommodate both labels without overlap. The three parameters (R, power, α) are displayed compactly outside the bar — they are the inputs to the calculation, not part of the bar itself. The PPV callout is the output label. Total labeled components: two segment labels, PPV callout, parameter annotation — five elements.

**P — Presentation:** True-positive segment: primary data accent (#C8102E) — the signal, the real discoveries. False-positive segment: neutral mid-gray (#787878) — the noise, the misleading results. Y-axis and axis labels: #2a1a0e ink, JetBrains Mono 11pt for tick labels. Chart area fill #F5F5F5. Structural strokes #D4D4D4 0.75pt for gridlines at count = 0, 50, 100, 140. Parameter annotation text: Inter 11pt #545454. PPV callout arrow: #2a1a0e 1.5pt with arrowhead marker. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The full 1,000-hypothesis population decomposition (all four cells: true positives, false positives, true negatives, false negatives) — this figure shows only the significant-result subgroup; the full 2×2 table would require a separate figure.
- True negatives (760 correctly non-significant results from 800 null hypotheses) — their inclusion would dwarf the figure and obscure the PPV argument; they are non-events and not the point.
- False negatives (100 missed true effects) — described in chapter text; omitting keeps focus on what the university sees (significant results) rather than what it misses.
- Multiple R-value scenarios on the same bar chart — different prior probabilities produce different PPV values; exploring multiple scenarios is an exercise task, not a single-bar pedagogical figure.
- The specific tutorial example (p = 0.03) — this figure is the general Ioannidis argument, not the specific tutorial case; cross-reference to chapter text for the connection.
- The OSC 2015 replication rate (36%) — a different empirical claim; described in chapter text.
- 3D or perspective effects.

**Caption (draft):** Of 1,000 tested educational interventions where 20% are truly effective (R = 0.20), with 50% power and α = 0.05, the 140 significant results split into 100 true discoveries and 40 false positives — a positive predictive value of 71% — because the large pool of ineffective interventions generates false positives even at a modest α level.

**Accuracy check (figure-checker):**
- True positives: 1,000 × 0.20 × 0.50 = 100. Verify segment height = 100.
- False positives: 1,000 × 0.80 × 0.05 = 40. Verify segment height = 40.
- Total bar height: 100 + 40 = 140. Y-axis maximum must be at least 140; baseline must be zero.
- PPV: 100/140 = 0.7143 ≈ 71%. Verify the labeled PPV value is approximately 71%.
- The true-positive segment must be taller than the false-positive segment (5:2 ratio, 100 vs. 40). If the rendering equalizes them or inverts them, the figure is wrong.
- Parameter values displayed: R = 0.20, power = 0.50, α = 0.05 — verify all three appear and match the chapter's stated values.
- Proportional Ink Rule: segment areas must be proportional to counts (100 and 40), not normalized.
- Y-axis baseline must be at zero; no truncated baseline.
- The false-positive count (40) is exactly 1,000 × 0.80 × 0.05 = 40.0 — no rounding required; verify the exact value.
