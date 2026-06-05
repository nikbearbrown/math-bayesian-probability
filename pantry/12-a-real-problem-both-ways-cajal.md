# CAJAL Figure Plans — Chapter 12: A Real Problem, Both Ways

---

## Figure 12.1 — Six-Question Analysis Scaffold

**Suggested filename:** 12-six-question-scaffold.svg
**Figure type:** Process flowchart
**One-sentence concept:** The six comparative-analysis questions form a sequential scaffold where Q1–Q4 are retrievable from outputs but Q5–Q6 require irreducibly human judgment.

**S — Specification:** Single-column canvas, viewBox 0 0 700 540, 300 DPI, vector SVG; portrait orientation with top-to-bottom flow.

**C — Content:** Six numbered nodes in vertical sequence, labeled exactly as in the chapter:
1. What is the data generating process? What does each framework assume about it?
2. What did the frequentist analysis find? What can it not tell you?
3. What did the Bayesian analysis find? What prior did you use and why?
4. Where do the analyses agree? Where do they diverge?
5. Which approach better serves the analysis goal, and why?
6. What would change your conclusion?

A horizontal dividing rule between Q4 and Q5 marks the boundary between output-retrievable questions (Q1–Q4) and judgment-required questions (Q5–Q6). A label on the left margin reads "From outputs" (Q1–Q4 zone) and "Requires judgment" (Q5–Q6 zone).

**O — Organization:** Single vertical column of six rectangular nodes, connected top-to-bottom by → arrows. Left-side bracket groups Q1–Q4 together; a second bracket groups Q5–Q6. The dividing line between the two zones is the visual center of gravity of the figure. Nodes are equal-width; Q5 and Q6 nodes are given a distinct fill to signal the qualitative shift.

**P — Presentation:** Q1–Q4 nodes: fill #F5F5F5, stroke #D4D4D4, stroke-width 1. Q5–Q6 nodes: fill #0072B2 (Blue, primary conceptual anchor) at low opacity (~15%), stroke #0072B2 stroke-width 1.5 — marking them as the intellectually elevated zone. Arrows: stroke #2a1a0e, stroke-width 1.5 with arrowhead marker. Dividing rule: stroke-dasharray 5 4, stroke #545454, stroke-width 1. Left-margin bracket labels: Inter 11px, #545454. Node numbering: EB Garamond 14px, #2a1a0e. All fills flat; no gradients, no shadows, no rounded corners (rx=0).

**E — Exclusions:** Do not show the six-question content in the nodes (text is applied manually post-generation). Do not include the dataset selection table, the writing guide sections, or the worked example. Do not show the frequentist or Bayesian analysis procedures. Do not include arrows pointing left or branching structures — this is a strictly linear progression, not a decision tree. Do not differentiate Q1–Q4 node colors from each other.

**Caption (draft):** The six comparative-analysis questions form a scaffold where questions 1–4 are answered from model outputs and questions 5–6 require the statistical judgment that this chapter's deliverable is designed to demonstrate.

**Accuracy check (figure-checker):** Logical correctness conditions: (1) exactly six nodes appear in order 1–6 with no omissions; (2) the Q1–Q4 / Q5–Q6 boundary is visually present and correctly placed between nodes 4 and 5; (3) all arrows point downward (progression direction), none upward or lateral; (4) the two zones are visually distinguishable but the nodes within each zone are uniform; (5) no branch points exist — this is a linear scaffold, not a decision tree.

---

## Figure 12.2 — Dataset Selection Decision Aid

**Suggested filename:** 12-dataset-selection-aid.svg
**Figure type:** Comparison panels
**One-sentence concept:** The five vetted datasets differ on three decision dimensions — analysis type required, data complexity, and prior knowledge needed — giving students a structured basis for choosing.

**S — Specification:** Single-column canvas, viewBox 0 0 700 420, 300 DPI, vector SVG; landscape-oriented comparison table rendered as a visual matrix.

**C — Content:** Five dataset rows (A through E) compared across three columns:
- Column 1 — Analysis type (e.g., "Distribution + comparison," "Correlation + logistic," "Regression + threshold," "Two-group + regression," "Hierarchical")
- Column 2 — Data complexity / wrangling burden (Low / Medium / High — encoded visually as filled dots: 1 dot = Low, 2 = Medium, 3 = High)
- Column 3 — Recommended-if label (a single short phrase per dataset drawn from the chapter's Quick Selection Table: e.g., "Clean data; no merge," "Ch 11 machinery; merge needed," "Sharpest F/B contrast," "Ch 4 revisit," "Ch 9 advanced")

Dataset E carries a distinct visual marker (Orange #E69F00 border) indicating advanced/optional status, matching the chapter's framing.

**O — Organization:** Five rows × three columns grid. Row headers (A–E dataset labels) on the left; column headers at top. Each cell contains a short text label or dot-scale encoding. A horizontal rule separates Dataset E (advanced option) from Datasets A–D. The three column headers are the only structural labels; dataset names (A–E) are the only row identifiers.

**P — Presentation:** Grid lines: stroke #D4D4D4, stroke-width 0.75. Header row background: #F5F5F5. Dataset E row: left border stroke #E69F00 (Orange, secondary), stroke-width 2, indicating optional/advanced status — not a data encoding. Filled dots for complexity: #0072B2 (Blue) for active/present dots, #D4D4D4 for empty/absent dot outlines. Row backgrounds alternate: #FFFFFF and #F5F5F5 for readability. Column header text: Inter 12px weight 600, #2a1a0e. Cell text: Inter 11px, #2a1a0e. No gradients, no shadows, rx=0.

**E — Exclusions:** Do not include URLs, source documentation, or the full dataset descriptions from the chapter. Do not show the pre-specified analysis questions for each dataset. Do not include the worked partial example content. Do not add a fourth column for "why it works both ways" — this overloads the figure. Do not use color to encode the analysis-type column — text labels only in that column. Do not include Dataset E in the primary comparison group visually (it is separated by a rule and marked as advanced).

**Caption (draft):** Five vetted datasets compared on analysis type, data-wrangling complexity, and recommended student profile; Dataset E (advanced) is separated and marked for students who completed Chapter 9.

**Accuracy check (figure-checker):** Logical correctness conditions: (1) exactly five dataset rows appear, labeled A through E; (2) complexity dot-scale is consistent — each dataset's dot count matches the chapter's characterization (A: Low, B: Medium, C: Low, D: Low, E: High); (3) Dataset E is visually separated from A–D by a horizontal rule; (4) no dataset is marked as universally "easiest" or "hardest" — the chapter states difficulty is roughly equal for A–D; (5) column count is exactly three; no fourth column appears.
