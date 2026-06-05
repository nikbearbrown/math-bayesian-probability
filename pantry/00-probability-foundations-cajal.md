# CAJAL Figure Plans — Chapter 00: Probability Foundations

*Figure plans for Chapter 0 — Everything you need before Chapter 1: conditional probability, Bayes' theorem as arithmetic, nothing more.*

---

## Figure 00.1 — The Conditional Probability Asymmetry

**Suggested filename:** 00-conditional-probability-asymmetry.svg
**Figure type:** Comparison panels
**One-sentence concept:** P(passed | studied) and P(studied | passed) are computed from the same joint count but answer different questions and produce different numbers.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- One 2×2 joint frequency table (the class-of-100 example from the chapter): rows = studied / not-studied; columns = passed / not-passed; cell values 25, 55, 15, 5; row and column totals.
- Left panel annotation: arrow tracing P(passed | studied) = 25 / 80 ≈ 0.833 — numerator and denominator cells highlighted.
- Right panel annotation: arrow tracing P(studied | passed) = 25 / 40 = 0.625 — numerator and denominator cells highlighted with a distinct secondary color.
- Two result callouts: "0.833" and "0.625" rendered in contrasting colors.
- Shared label strip above both panels identifying this as the same table read two ways.

**O — Organization:** Two side-by-side panels sharing the same 2×2 table; left panel highlights the "row-denominator" conditioning (P(passed | studied)); right panel highlights the "column-denominator" conditioning (P(studied | passed)). Flow direction left to right. No arrows between panels — the contrast is structural, not sequential. Both panels drawn at equal width within the double-column span.

**P — Presentation:** Primary data accent (#C8102E) for the P(passed | studied) trace (left panel numerator and denominator cells); ink (#2a1a0e) for the P(studied | passed) trace (right panel) encoded as dark fill. Highlighted cells use light-tinted fill (#F5F5F5 base with a single colored border rule in the respective encoding color). Neutral gray (#787878) for non-highlighted cells. Chart-area background #F5F5F5. Structural strokes #2a1a0e at 1pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The Bayes' theorem formula — belongs to Figure 00.2, not here.
- The urn problem — separate example, would split focus from the asymmetry.
- The noisy-friend Bayesian update calculation — Chapter 0 Section 6, too advanced for this concept.
- The Sally Clark case — belongs in exercises / narrative, not a figure.
- Any three-way or multi-hypothesis extension.
- Probability notation derivation steps (derivation is in text).
- Interpretive labels about clinical consequences — belongs in Chapter 1.

**Caption (draft):** The same 2×2 table yields P(passed | studied) ≈ 0.833 (left, conditioning on rows) and P(studied | passed) = 0.625 (right, conditioning on columns) — the same joint count, two different denominators, two different answers.

**Accuracy check (figure-checker):**
- Cell values must sum to row and column totals: 25 + 55 = 80; 15 + 5 = 20; 25 + 15 = 40; 55 + 5 = 60; grand total = 100. Verify all sums before render.
- P(passed | studied) = 25/80 = 0.8125 — chapter rounds to 0.833; confirm the displayed value matches the chapter text (0.833 used there; 0.8125 is exact — the chapter uses 0.25/0.30 proportions not counts; if adapting to counts, the exact fraction is 25/80 = 0.3125 — NOTE: the chapter example uses proportions P = 0.25, 0.30, 0.40, not raw counts. Adapting to counts: 0.25×100=25 studied-and-passed; 0.30×100=30 studied total; so 25/30 = 0.833. Cell (studied, passed) = 25; cell (studied, not-passed) = 5; cell (not-studied, passed) = 15; cell (not-studied, not-passed) = 55). Verify the table reflects the chapter's proportions scaled to 100 students.
- P(studied | passed) = 25/40 = 0.625 — matches the chapter exactly.
- The two highlighted denominators must be visually distinct and non-overlapping (30 vs. 40).
- No probability value displayed should exceed 1.0 or be negative.
- No y-axis present (this is a table, not a chart) — zero-baseline rule does not apply; verify no distorted scale is implied.

---

## Figure 00.2 — Bayes' Theorem: Prior → Likelihood → Posterior

**Suggested filename:** 00-bayes-theorem-update-flow.svg
**Figure type:** Process flowchart
**One-sentence concept:** Bayes' theorem transforms a prior probability into a posterior probability by multiplying by the likelihood and dividing by the marginal probability of the data.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 360.

**C — Content:**
- Three labeled nodes in left-to-right sequence: (1) Prior P(H) — value 3/10 from the urn worked example; (2) Likelihood P(D|H) — value 0.90 from the noisy-friend variant; (3) Posterior P(H|D) — value 0.72.
- A fourth node for the denominator: P(D) = 0.375, placed below the main flow as the normalization step.
- Arrows: Prior × Likelihood → numerator 0.27; denominator node feeds upward into the division step; result = Posterior 0.72.
- Each node labeled with its role name (Prior, Likelihood, Marginal Data Probability, Posterior) and the specific numerical value from the chapter's noisy-friend worked example.
- A compact formula strip above the flow: P(H|D) = P(H) · P(D|H) / P(D) — structural label only, not decorative.

**O — Organization:** Horizontal left-to-right flowchart. Main computation path: Prior → multiply by Likelihood → divide by P(D) → Posterior. The P(D) denominator node drops below the main axis with an upward-pointing arrow feeding the division step. Standard → arrows for progression. No branching paths in this figure — the two-term sum that constitutes P(D) is shown as a single resolved number (0.375) with a footnote callout indicating it comes from the law of total probability (detail is in text). Six labeled components total: Prior, Likelihood, P(D) node, numerator product, division arrow, Posterior.

**P — Presentation:** Primary anchor node (Posterior) filled with primary data accent border (#C8102E stroke, white fill); input nodes (Prior, Likelihood) filled with chart-area gray (#F5F5F5, #2a1a0e stroke 1pt); denominator node filled with a light neutral (border #D4D4D4). Arrows #2a1a0e stroke-width 1.5 with arrowhead marker. Formula strip in EB Garamond 14pt display. Node labels Inter 12pt. Numerical values JetBrains Mono 11pt. Note: house SVG style guide governs final render.

**E — Exclusions:**
- The full law of total probability expansion (P(H)·P(D|H) + P(¬H)·P(D|¬H)) — one computed number (0.375) is shown; the expansion is in the chapter text.
- The perfect-reliability variant of the urn problem (P(D|¬H)=0, posterior=1.0) — showing both cases requires two figures; only the informative noisy case is shown here.
- The medical test parameters from Chapter 1 — those belong in Chapter 1's figures.
- Multiple hypotheses (¬H branch values) — the denominator node absorbs these; show only the result.
- Any frequentist comparator — this is a Chapter 0 mechanics figure, not a comparison figure.
- Cycle-style or feedback arrows — this update is one-directional here.

**Caption (draft):** Bayes' theorem as a data-flow: the prior P(H) = 0.30 is multiplied by the likelihood P(D|H) = 0.90, divided by the marginal probability of the data P(D) = 0.375, and yields posterior P(H|D) = 0.72 — the updated probability after the imperfect friend's report.

**Accuracy check (figure-checker):**
- Numerator: 0.30 × 0.90 = 0.27. Verify this is the value shown on the arrow.
- Denominator: P(D) = (0.30)(0.90) + (0.70)(0.15) = 0.27 + 0.105 = 0.375. Verify 0.375 is shown in the P(D) node.
- Posterior: 0.27 / 0.375 = 0.72 exactly. Verify displayed value.
- Prior P(H) = 0.30 (from 3 red in 10 balls) — must match chapter text exactly.
- Likelihood P(D|H) = 0.90 (says "not blue" | red) — must match chapter text exactly.
- P(D|¬H) = 0.15 (says "not blue" | blue) — used in denominator calculation; if shown in a callout, must match chapter text.
- No probability value may exceed 1.0.
- All arrow directions must follow the computational sequence; no backward arrows.
