# CAJAL Figure Plans — Chapter 02: Prompting for Statistics

*Figure plans for Chapter 2 — Learn to use an LLM as a statistical implementation partner: describing problems precisely, verifying outputs critically, and iterating toward solutions that match what the math actually requires.*

---

## Figure 02.1 — The Prompt–Verify–Iterate Loop

**Suggested filename:** 02-prompt-verify-iterate-loop.svg
**Figure type:** Process flowchart
**One-sentence concept:** Effective LLM-assisted statistical analysis follows a three-stage cycle — specify (prompt), check (verify against known structure), and fix (iterate) — with the verification stage requiring the statistical knowledge the LLM cannot supply.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 420.

**C — Content:**
- Stage 1 node: "SPECIFY — state the data generating process, name the quantity, specify the framework (Bayesian or frequentist)."
- Stage 2 node: "VERIFY — check the interpretation against the problem structure; confirm the quantity computed matches the quantity asked for."
- Stage 3a node (pass): "Output accepted — record result."
- Stage 3b node (fail): "ITERATE — write a corrected prompt naming the specific error."
- Decision diamond between Stage 2 and Stage 3: "Is the interpretation correct?" → Yes (→ Stage 3a); No (→ Stage 3b → back to Stage 1).
- A "Human judgment required" callout attached to the Stage 2 node — the verification step is the one stage the LLM cannot perform on itself.

**O — Organization:** Top-to-bottom flowchart with a back-loop. Main path flows downward: Specify → Verify → (Decision) → Accept or Iterate. The Iterate node has a left-pointing return arrow looping back up to Specify. Decision diamond sits between Verify and the two exit paths. The "Human judgment required" callout is positioned to the right of the Verify node, attached by a short horizontal rule — not an arrow, just a bracket annotation. Total labeled components: 6 (three stage nodes + decision diamond + accept node + human-judgment callout). No additional sub-steps within nodes — the block descriptions are for the plan only; the rendered figure carries only node labels (e.g., "SPECIFY," "VERIFY," "ITERATE," "Correct?").

**O (arrow semantics):** Standard → for forward progression; curved left-to-top arrow for the iterate return path; ⊣ block symbol is not used here (no inhibition path). Decision diamond uses Y/N branch labels.

**P — Presentation:** Stage 1 node (SPECIFY): chart-area fill #F5F5F5, #D4D4D4 border 1pt. Stage 2 node (VERIFY): primary data accent border (#C8102E) 1.5pt, white fill — this is the load-bearing human step and must be visually prominent. Stage 3a accept node: Bluish Green semantic (#009E73 border, white fill) — positive outcome. Stage 3b iterate node: Vermillion semantic (#D55E00 border, white fill) — correction required. Decision diamond: #2a1a0e border 1pt, #F5F5F5 fill. Arrows: #2a1a0e 1.5pt with arrowhead marker. Human-judgment callout: #787878 text, bracket in #D4D4D4. Node labels Inter 12pt #2a1a0e. Note: house SVG style guide governs final render; Okabe-Ito semantic colors (Bluish Green, Vermillion) used for the pass/fail exits per the CAJAL semantic color roles.

**E — Exclusions:**
- The five failure-mode taxonomy (Block 5) — that is chapter text and a table, not a figure.
- The full prompt anatomy (five components from Block 2) — a labeled list, not a process flow; would inflate the component count beyond 8.
- Any statistical formula or equation — this is a workflow figure, not a math figure.
- LLM-specific details (model names, interface elements) — the figure must be model-agnostic and durable.
- The natural-frequency cross-check step — this is a specific verification technique, a sub-step of VERIFY; including it as a separate node would over-specify.
- Any reference to coding language or Python syntax.
- Decorative elements representing the LLM (chat bubbles, robot icons, etc.).

**Caption (draft):** The prompt–verify–iterate loop: specify the problem precisely (naming the data generating process, the target quantity, and the statistical framework), verify the output by checking the interpretation against known structure, and iterate with a corrected prompt when the interpretation is wrong — the verification step is the one stage that requires the statistical understanding the LLM cannot supply.

**Accuracy check (figure-checker):**
- This is a workflow figure, not a quantitative figure. No numerical values are encoded.
- Structural check: the back-loop from ITERATE must return to SPECIFY (not to VERIFY), because iteration requires rewriting the prompt, not re-running verification on unchanged output.
- Decision diamond must have exactly two exits: one labeled "Yes" (or "Correct") leading to accept, and one labeled "No" (or "Error found") leading to ITERATE. A diamond with only one exit is a rendering error.
- The "Human judgment required" annotation must attach to VERIFY, not to SPECIFY or ITERATE — the chapter's load-bearing claim is that verification requires human statistical knowledge; the annotation must reflect this placement.
- No arrow may point from accept back into the loop (accept is a terminal state in this figure).
- Proportional Ink Rule does not apply to flowchart nodes (no quantitative encoding). Check that no node is drawn disproportionately large in a way that implies importance beyond its label.

---

## Figure 02.2 — The Five-Component Prompt Anatomy

**Suggested filename:** 02-prompt-anatomy-components.svg
**Figure type:** Annotated example
**One-sentence concept:** A statistically correct LLM prompt has five named components — data generating process, target quantity, framework specification, reasoning request, and interpretation guard — and omitting any one of them shifts the error risk from the LLM to the human.

**S — Specification:** Single-column 89mm textbook width; 300 DPI minimum; vector SVG; viewBox 700 × 480.

**C — Content:**
- A vertically stacked set of five labeled boxes, each representing one component of the Block 2 prompt anatomy from the chapter:
  1. "Data generating process — describe how the data were produced, not just the data values"
  2. "Target quantity — name P(disease | positive), not 'what does this tell us'"
  3. "Framework — specify Bayesian or frequentist explicitly"
  4. "Reasoning steps — request mathematical derivation before code"
  5. "Interpretation guard — ask the model to distinguish sensitivity from PPV (or analogous pair)"
- Each box has a short risk callout to the right: what goes wrong if that component is omitted (e.g., "Omit this → wrong model selected"; "Omit this → LLM defaults to frequentist").
- A single downward arrow running along the left edge, from box 1 to box 5, labeled "Prompt completeness."

**O — Organization:** Five stacked horizontal boxes in descending order, left-justified. Each box is the same height. Risk callouts are short horizontal annotations extending to the right of each box, connected by a short horizontal rule. The left-edge arrow spans all five boxes. No inter-box arrows — these are parallel components of a single prompt, not a sequence. Layout resembles a structured checklist rather than a flowchart. Five labeled components + five risk callouts = 10 elements; the callouts are sub-labels, not full components, so this respects the 6–8 labeled-component rule for the primary structure. If the renderer cannot handle 10 distinct text zones, the five risk callouts should be condensed to a single shared callout below: "Omitting any component shifts error risk to the human verifier."

**O (split note):** If the five-component anatomy and the iterate loop are too dense for adjacent placement in a single chapter, Figure 02.2 can be demoted to a sidebar annotated example rather than a main figure. The iterate loop (Figure 02.1) is the higher-priority figure.

**P — Presentation:** Boxes 1–5: chart-area fill #F5F5F5, #D4D4D4 border 1pt. Component number labels: Inter 12pt 600 weight #2a1a0e. Component description text: Inter 12pt 400 #2a1a0e. Risk callouts: Inter 11pt #545454. Left-edge arrow: #2a1a0e 1.5pt. Boxes are equal height; no box is highlighted over another — all five components are equally necessary. Note: house SVG style guide governs final render.

**E — Exclusions:**
- Actual prompt text (full prose) — too long for a figure; the chapter prose carries this.
- Code syntax or Python — belongs in text blocks, not a figure.
- LLM model names or interface screenshots — model-agnostic and durable only.
- The failure-mode taxonomy (Block 5) — a separate conceptual framework, not part of prompt anatomy.
- Any quantitative values from the medical test example — this figure illustrates the structural components of a prompt, not a specific prompt instance.
- The iterate loop mechanics — those are in Figure 02.1.
- Tick-boxes or checkmark icons — the figure should be structural, not an interactive checklist metaphor.

**Caption (draft):** A complete statistical prompt has five components: specifying the data generating process, naming the target quantity, declaring the statistical framework, requesting intermediate reasoning steps, and adding an interpretation guard — each omission opens a distinct failure mode documented in Block 5 of this chapter.

**Accuracy check (figure-checker):**
- This is a structural/conceptual figure; no statistical values are encoded.
- Structural check: exactly five component boxes must be present, corresponding to the five components in Block 2 of the chapter. Verify correspondence: (1) data generating process, (2) target quantity, (3) framework specification, (4) reasoning steps, (5) interpretation guard.
- The chapter text (Block 2) lists these as an ordered set. The figure boxes must appear in the same order (1 through 5 top to bottom).
- No box should describe a failure mode directly — the risk callouts describe consequences of omission, not the failure modes themselves (those are in Block 5 and are different).
- Component 3 must specify that "Bayesian or frequentist" is what the framework declaration refers to — matching the chapter's own language exactly.
- No probability values or mathematical notation should appear in this figure — it is a structural map of a prompt, not a mathematical derivation.
