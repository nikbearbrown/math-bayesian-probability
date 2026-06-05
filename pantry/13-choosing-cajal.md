# CAJAL Figure Plans — Chapter 13: Choosing

---

## Figure 13.1 — The Five-Question Decision Flow

**Suggested filename:** 13-five-question-decision-flow.svg
**Figure type:** Process flowchart
**One-sentence concept:** The five decision questions form a sequential filter where Q1 (what quantity does the decision-maker need?) is the dominant branch point and the remaining four questions refine or override the initial direction.

**S — Specification:** Single-column canvas, viewBox 0 0 700 540, 300 DPI, vector SVG; top-to-bottom flow with left/right branches at each question node.

**C — Content:** Five question nodes in vertical sequence, labeled by abbreviated criterion exactly as in the chapter's decision framework:
1. What quantity does the decision-maker need?
2. Is defensible prior information available?
3. How large is the sample relative to the effect size?
4. Who will receive the results?
5. What are the computational and time constraints?

Each node branches left (→ Favors Frequentist) and right (→ Favors Bayesian). A terminal note at the bottom reads: "Split answer → run both; explain the translation." The Q1 node is visually larger or more prominent than Q2–Q5 to signal its dominant role.

**O — Organization:** Vertical spine of five rectangular question nodes connected top-to-bottom. At each node, two short horizontal branch lines extend left and right, each ending in a small pill-shaped label reading "Frequentist" (left) or "Bayesian" (right). The terminal "split answer" note sits below Q5, centered, connected by a dashed rule. Q1 node is rendered at 1.25× the height of Q2–Q5 nodes to encode its primacy. All arrows on the main spine point downward; branch arrows point laterally from the node midpoint.

**P — Presentation:** Question nodes: fill #F5F5F5, stroke #D4D4D4, stroke-width 1, rx=0. Q1 node: stroke #0072B2 (Blue, primary conceptual anchor), stroke-width 2 — to signal dominance without color-filling the node. Frequentist branch labels: fill #2a1a0e at 10% opacity background with stroke #2a1a0e, stroke-width 1. Bayesian branch labels: fill #009E73 (Bluish Green, positive/active) at 15% opacity background with stroke #009E73, stroke-width 1 — encoding Bayesian as the "active choice when conditions favor it," not as universally preferred. Spine arrows: stroke #2a1a0e, stroke-width 1.5 with arrowhead marker. Terminal "split answer" box: stroke-dasharray 4 3, stroke #545454, fill #FFFFFF. Node label text: Inter 12px, #2a1a0e. Branch label text: Inter 11px, #2a1a0e. All fills flat; no gradients; no shadows; rx=0 throughout.

**E — Exclusions:** Do not include the full criterion descriptions or the "favors" column text from the chapter's decision table — branch labels are short (one or two words only); full text is applied manually post-generation. Do not show a "verdict" at the top or bottom declaring either approach generally superior. Do not show more than five question nodes — the framework has exactly five criteria; do not subdivide or add sub-criteria. Do not add a feedback loop or cycle back to Q1 — this is a single-pass filter, not an iterative loop. Do not color-fill the Frequentist branch labels with Vermillion (#D55E00) — frequentist is not a negative or blocking state; neutral ink encoding applies.

**Caption (draft):** The five-question decision framework applied in sequence: Q1 sets the dominant direction by identifying what quantity the decision-maker needs, and Q2–Q5 refine or override; a split answer across questions calls for running both approaches.

**Accuracy check (figure-checker):** Logical correctness conditions: (1) exactly five question nodes appear in the order the chapter specifies (Q1 output type → Q2 prior availability → Q3 sample size → Q4 audience → Q5 computation); (2) each node has exactly two lateral branches, one labeled toward frequentist and one toward Bayesian — no node is missing a branch; (3) Q1 is visually distinguished as the primary node; (4) the terminal "split answer" note is present and is not attached to any single branch — it sits outside the branching structure, applying to the overall outcome; (5) no branch points to a conclusion of "always Bayesian" or "always Frequentist" — each branch label is conditional on that criterion, not a global verdict; (6) branch directions are consistent — Frequentist branches all go to the same side (left), Bayesian to the other (right).

---

## Figure 13.2 — Frequentist Strengths / Bayesian Strengths Comparison Panels

**Suggested filename:** 13-framework-comparison-panels.svg
**Figure type:** Comparison panels
**One-sentence concept:** The two frameworks have distinct and non-overlapping strength zones — a side-by-side panel makes those zones visible without implying one framework is universally superior.

**S — Specification:** Single-column canvas, viewBox 0 0 700 420, 300 DPI, vector SVG; two equal-width panels side by side with a shared vertical center divider.

**C — Content:** Left panel — "Frequentist: When to Choose" — lists four strength conditions drawn verbatim or near-verbatim from the chapter:
- Large sample; CLT applies
- Regulatory / preregistered environment
- Exploratory research; no strong prior
- Audience requires p-values

Right panel — "Bayesian: When to Choose" — lists four parallel strength conditions:
- P(θ > threshold) needed
- Small sample or rare event; prior stabilizes
- Sequential updating; data arrives over time
- Hierarchical data; partial pooling needed

A center divider line separates the panels. A note at the bottom, spanning both panels: "When both point the same direction: choose by communication; results converge numerically."

**O — Organization:** Two equal-width rectangular panels side by side, sharing the full canvas width minus 32px margins each side. Each panel contains a header (panel title) and four bulleted items in a vertical list. The center divider is a single vertical stroke. The spanning bottom note sits below both panels, centered, in a visually recessed style (smaller text, lighter color). No arrows within panels — this is a static two-column comparison, not a flow. Items within each panel are parallel in position (item 1 left aligns with item 1 right, etc.) to enable easy cross-reading.

**P — Presentation:** Left panel (Frequentist) header background: #F5F5F5, stroke #D4D4D4, stroke-width 1. Right panel (Bayesian) header background: #009E73 (Bluish Green) at 12% opacity, stroke #009E73, stroke-width 1 — encoding Bayesian as the active/positive choice when conditions favor it, while keeping the frequentist panel neutral rather than negative. Panel body fills: #FFFFFF for both. Center divider: stroke #D4D4D4, stroke-width 1.5. Bullet markers: filled squares #2a1a0e, 4×4px, rx=0. Header text: EB Garamond 14px, #2a1a0e. Item text: Inter 12px, #2a1a0e. Bottom note text: Inter 10px, #545454. All fills flat; no gradients; no shadows; rx=0.

**E — Exclusions:** Do not include the full prose explanations from the chapter for each strength condition — bullet items are short phrases only; full prose is in the chapter text. Do not show a "winner" column or any visual element suggesting one panel is superior overall. Do not include the five decision-framework questions in this figure — that is Figure 13.1's job; this figure shows the resulting strength zones, not the decision process. Do not include the "What this book has not covered" section items (MCMC, non-parametric Bayes, causal inference). Do not use Vermillion (#D55E00) for the Frequentist panel header — frequentist is not a negative or blocking state; neutral gray encoding applies.

**Caption (draft):** Frequentist and Bayesian methods have non-overlapping strength zones; when both criteria point the same direction the results converge numerically and the choice is primarily one of communication.

**Accuracy check (figure-checker):** Logical correctness conditions: (1) exactly four items appear in each panel — not three, not five; (2) the four frequentist items correspond to conditions named in the chapter's "When Frequentist Methods Are the Right Choice" section (large samples, regulated/preregistered, exploratory, audience requires p-values); (3) the four Bayesian items correspond to conditions named in the "When Bayesian Methods Earn Their Complexity Cost" section (P(θ > threshold), small sample/rare event, sequential updating, hierarchical/partial pooling); (4) no item appears in both panels — the panels are mutually exclusive in their content; (5) the bottom convergence note is present and spans both panels; (6) neither panel header claims general superiority.
