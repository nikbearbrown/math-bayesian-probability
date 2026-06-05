# Research: Chapter 02 — Prompting for Statistics
## Bayesian Probability
**Chapter one-line:** Learn to use an LLM as a statistical implementation partner — describing problems precisely, verifying outputs critically, and iterating toward solutions that match what the math actually requires.
**Research date:** 2026-06-01

---

## ⚠️ AGING-RISK NOTICE
This is the highest aging-risk chapter in the book. Tool-specific material (which LLM, which version, exact prompt syntax) will likely be outdated within 12–24 months. The research file is structured accordingly:

- **STABLE material** (marked [STABLE]): Principles of problem description, verification logic, failure-mode taxonomy. Does not depend on which LLM is current.
- **CURRENT-STATE material** (marked [CURRENT — flag for revision]): Specific model capabilities, benchmark results, specific tool interfaces. Review before each edition.

The author should draft Chapter 2 primarily from the STABLE material and keep CURRENT-STATE material in sidebars or footnotes that can be updated without restructuring the chapter.

---

## 1. Primary Sources

### Foundational papers and texts

1. **Wasserstein, R. L., & Lazar, N. A.** (2016). "The ASA's Statement on p-Values: Context, Process, and Purpose." *The American Statistician*, 70(2), 129–133. DOI: 10.1080/00031305.2016.1154108. [STABLE]
   - Relevant to Chapter 2 because any LLM-generated statistical output that confuses a p-value with a posterior probability is making an error the ASA statement explicitly names. Chapter 2's Block 5 ("When to Iterate") lists "Frequentist answer dressed in Bayesian language" as a failure mode — this source provides the authoritative definition of what each label means, so the student can verify it.

2. **"Prompt engineering for accurate statistical reasoning with large language models in medical research."** *Frontiers in Artificial Intelligence*, 2025. DOI: 10.3389/frai.2025.1658316. [CURRENT — flag for revision]
   - A 2025 peer-reviewed study evaluating four prompt engineering strategies (zero-shot, explicit instruction, chain-of-thought, hybrid) for statistical reasoning with GPT-4.1 and Claude 3.7 Sonnet. Key finding: zero-shot prompting was sufficient for basic descriptive tasks but failed for inferential tasks due to lack of assumption checking. Hybrid prompting (chain-of-thought + explicit instruction) was best practice. This directly supports Chapter 2's "anatomy of a good statistical prompt" block. Published in a peer-reviewed venue; open access via Frontiers. Note: specific models named will age; the finding that more structured prompts outperform zero-shot is likely to remain stable.

3. **"Can we trust LLMs as a tutor for our students? Evaluating the Quality of LLM-generated Feedback in Statistics Exams."** arXiv:2511.04213. (2024/2025). [CURRENT — flag for revision; VERIFY full authorship and journal of record if published beyond preprint]
   - Studies LLM-generated feedback on statistics exam questions. Prior research has shown LLM feedback can contain substantial errors and hallucinations even when given correct solutions. Specifically relevant to Chapter 2's core claim: "LLMs can produce plausible-looking wrong answers." The feedback errors documented in statistics education contexts are the same class of errors students will encounter when using LLMs for their own statistical implementation.

4. **"Beyond Correctness: Evaluating and Improving LLM Feedback in Statistical Education."** arXiv:2511.07628. (2024/2025). [CURRENT — flag for revision; VERIFY full authorship]
   - Companion paper to the above. Proposes evaluation rubrics for LLM-generated statistical feedback quality — directly relevant to Chapter 2's learning outcome 2 ("Identify when an LLM's statistical output is wrong by checking it against the problem's structure"). The rubrics can inform what "correct verification" looks like when students apply the Chapter 2 skills.

5. **McElreath, R.** (2020). *Statistical Rethinking: A Bayesian Course with Examples in R and Stan* (2nd ed.). Chapman and Hall/CRC. ISBN: 9780367139919. [STABLE]
   - Referenced in the TIKTOC as "the next step" after this book. Relevant to Chapter 2 as the destination: Chapter 2 teaches prompting for implementation so that students can access the kind of full MCMC analysis McElreath presents, via LLM assistance, without coding from scratch. The gap between this book and McElreath's is exactly what Chapter 2's prompting skill bridges. Won the 2024 De Groot Prize (ISBA).

### Key empirical cases

1. **The "Code That Runs But Computes Wrong" Problem (documented phenomenon, multiple sources)** [STABLE]
   A systematic pattern documented in LLM code generation research: LLMs produce code that executes without errors but implements a different problem than the one specified. For statistical code specifically, this takes the form of correct implementation of the wrong test (e.g., computing a one-tailed p-value when the problem calls for two-tailed; computing a confidence interval on the mean when the question is about a proportion; reporting sensitivity as positive predictive value).
   - Documentation: Research on LLM code generation errors confirms "semantic errors" — high-level logical mistakes where the code does what the model understood, not what the user intended. "Plausibility is a statistical property, not a semantic guarantee" (from code generation literature). The CodeHalu paper (arXiv:2405.00253) investigates code hallucinations via execution-based verification.
   - Why appropriate: This is the exact failure mode Chapter 2 is designed to address. It is not hypothetical — students will encounter it. The chapter's worked example should demonstrate catching one such error via hand-calculation verification.
   - Label: This is a documented class of failure, not a single case. Multiple papers confirm the phenomenon. ILLUSTRATIVE worked example for Chapter 2 should be constructed by the author; the phenomenon itself is documented.

2. **LLM Misinterpretation of Statistical Output (documented in statistics education contexts)** [CURRENT — flag for revision]
   The 2024 arXiv paper on LLM feedback quality in statistics exams (arXiv:2511.04213) documents specific error types including: (a) misidentifying which assumption was violated, (b) providing correct mechanics with wrong interpretation, (c) confusing conditional and unconditional probabilities in explanations. These map directly to Chapter 2's failure-mode taxonomy in Block 5.
   - Why appropriate: These errors are documented in the specific educational context Chapter 2 addresses. Students using LLMs as statistical tutors will encounter the same error patterns documented in this research.

3. **The Frontiers 2025 Hybrid Prompting Finding** [CURRENT — flag for revision]
   The Frontiers in AI (2025) study provides a documented comparison of prompting strategies on statistical tasks. Zero-shot: failed on inferential tasks. Chain-of-thought alone: improved reasoning but introduced new errors in assumption checking. Hybrid (chain-of-thought + explicit instruction about statistical assumptions): best performance. This is empirical evidence for Chapter 2's Block 2 ("ask for the mathematical steps, not just the code" and "ask for a plain-language interpretation alongside the output").

---

## 2. The Core Concept — State of the Field

### What is settled [STABLE]

- **LLMs produce plausible-looking statistical output that can be wrong.** This is documented across multiple research contexts and is not in dispute. The question is what verification practices reliably catch errors, not whether errors occur.
- **More structured prompts produce better statistical outputs.** The Frontiers 2025 study and other prompt engineering research consistently show that specifying the data generating process, naming the desired quantity, and requesting intermediate reasoning steps (chain-of-thought) outperforms zero-shot prompting for inferential statistical tasks.
- **The "correct code, wrong interpretation" error is the most dangerous class of LLM statistical failure for this reader.** A student who cannot verify the statistical reasoning step is more vulnerable to this error than to syntactically wrong code (which Python/R will reject) or to obviously absurd outputs (which common sense catches). Chapter 2's emphasis on "ask for the mathematical steps" and "verify two by hand" targets this failure mode specifically.
- **LLMs cannot replace the statistical understanding the student is building.** No current LLM reliably identifies which framework (frequentist or Bayesian) is appropriate for a given problem without being told. The student's ability to specify "use Bayesian inference" or "compute a posterior probability, not a p-value" is the load-bearing skill Chapter 2 teaches.

### What is disputed [CURRENT — flag for revision]

- **The relative accuracy of different LLMs on statistical tasks is in flux.** Benchmarks from 2024–2025 show significant variation across models and rapid improvement. Claude 3.5 Sonnet and GPT-4.1 perform significantly better on mathematical reasoning tasks than earlier models. The gap between models is narrowing on standard benchmarks; on specific statistical interpretation tasks, differences persist. This ranking will change; do not hardcode any model preference into the chapter text.
- **Whether chain-of-thought prompting is reliably superior to other strategies in 2025+.** Research shows it helps, but newer models may incorporate chain-of-thought reasoning internally without explicit instruction. Treat "ask for mathematical steps" as a durable best practice; treat specific prompting syntax as possibly obsolete.
- **Whether "hybrid" prompting will remain the recommended approach** as model capabilities improve. The Frontiers 2025 finding is based on specific model versions (GPT-4.1, Claude 3.7 Sonnet). Newer architectures may require different prompt structures. [High aging risk]

### What has changed recently (last 5 years) [CURRENT]

- **Mathematical reasoning capabilities of LLMs have improved dramatically.** GPT-4-class models in 2023 showed ~71% accuracy on standard math benchmarks; reasoning models (o1, o3, Claude 3.7) reached 96%+ on AIME 2024. This means Chapter 2's verification emphasis is now about statistical *interpretation* errors, not computation errors — LLMs rarely compute the wrong number anymore, but they still frequently compute the *right* number for the *wrong* question.
- **LLM hallucination rates in code generation have declined but remain significant.** In 2025, top models show 0.7–1.5% hallucination rates on grounded summarization tasks (down from significantly higher in 2023), but code generation and statistical interpretation remain higher-error domains.
- **Prompt engineering is increasingly recognized as a core competency in research and education.** The Frontiers 2025 study explicitly calls for "standardized prompt templates" and "evaluation rubrics" — this validates Chapter 2's position in the book (teaching prompting as a skill, not just a convenience).
- **LLMs as statistical tutors are being deployed and studied.** The arXiv 2024/2025 papers document real deployments of LLMs as statistics tutors in university courses. This gives Chapter 2 an active research context, not just a hypothetical one.

---

## 3. Application Domain Examples

Chapter 2 is a methods chapter (no domain-specific content), but its examples must be grounded. Three documented contexts where the Chapter 2 skills apply directly:

1. **The Chapter 1 Completion Task (Chapter 2's own worked example)** [STABLE]
   TIKTOC specifies that Chapter 2's worked example is "complete prompting session for the medical testing problem — initial prompt, LLM output, verification against hand calculation, one iteration to fix an interpretation error, final output."
   - This is the only example needed for the basic skill. Students have already computed the answer by hand in Chapter 1; the Chapter 2 task is to (a) get the LLM to reproduce it, (b) catch when the LLM's interpretation is wrong ("the test is 99% accurate" ≠ "the patient has 99% chance of being sick"), (c) write a corrected prompt.
   - This example is maximally appropriate because the student can *verify* the LLM's output against their own hand calculation from the previous chapter — making the "verify against known result" principle concrete rather than abstract.

2. **Prevalence Range Analysis (Chapter 2's Exercise 1)** [STABLE]
   Prompting an LLM to compute P(disease | positive test) for five prevalence values (0.001, 0.01, 0.1, 0.3, 0.5) and verifying two of them by hand. This exercise teaches:
   - How to parameterize a calculation in a prompt (specify prevalence as a variable)
   - How to structure output verification (select two to check; which two and why?)
   - That the LLM's numerical computation is likely correct; the verification targets the interpretation
   - ILLUSTRATIVE: the student constructs this prompt in the exercise; the parameters are from Chapter 1.

3. **Statistical Code Failure Mode: The Wrong-Model Error** [CURRENT — verify example is still representative in current models]
   A documented failure mode applicable to Exercise 2 (student given a faulty LLM output and asked to identify the error): LLM asked to "run a statistical test" on a two-group comparison computes a one-sample t-test against zero instead of a two-sample t-test comparing groups, because the prompt said "test whether the groups differ" without specifying a two-sample design. The code runs without error; the reported p-value is for a different hypothesis than the one the student asked. Student diagnoses the error by checking whether the degrees of freedom match a two-sample test.
   - Why appropriate: Teaches that diagnosis requires knowing what the correct output *should* look like, not just whether the code ran. This is the "statistical understanding" that no LLM replaces.
   - Label: ILLUSTRATIVE — this is a representative failure mode, not a single documented case; the author should construct a specific example for the exercise.

---

## 4. The Book's Thesis Connection

Chapter 2 is a methods chapter, not a comparative chapter — it introduces the implementation tool the book will use for all remaining comparative analyses. Its thesis contribution is structural rather than argumentative:

**Chapter 2 is load-bearing.** Every subsequent chapter includes a prompting section that assumes the Chapter 2 skill. The thesis argument (choose the framework appropriate to the problem) requires being able to implement both frameworks — which requires LLM assistance for all but the simplest cases. Chapter 2 is the gateway through which the thesis becomes practicable for the non-programmer reader.

**The thesis connection is in the verification emphasis.** The book's thesis is that competent practice means choosing a method *and understanding what it assumes and where it fails*. The LLM will implement whichever framework the student specifies — but it cannot tell the student whether the framework is appropriate. The verification skill (asking "did the LLM solve the problem I actually have?") is the same metacognitive skill the thesis requires: asking "did this framework answer the question I actually need answered?"

**Specific thesis contribution of Chapter 2:** A student who can specify "solve this problem using both a frequentist hypothesis test AND a Bayesian posterior calculation" and verify both outputs is equipped to execute the book's standard comparative analysis in every chapter from 3 onward. Without Chapter 2, the comparative structure would require programming skills the reader is not assumed to have.

**What the student must supply that an algorithm cannot:**
- The correct specification of the data generating process (what distribution governs the data?)
- The identification of which quantity is the decision-relevant output (p-value? posterior probability? credible interval?)
- The recognition of which framework is being invoked (frequentist or Bayesian — the LLM may conflate them without explicit instruction)
- The decision to iterate (the LLM will not tell the student its interpretation is wrong)

**Literature bearing on the thesis here:**
- The Frontiers 2025 finding that hybrid prompting (explicit instruction about statistical assumptions) produces better results directly supports the thesis: the student who knows what a Bayesian posterior is can instruct the LLM to compute one; the student who doesn't knows only to ask for "the statistical analysis." The knowledge gap is the thesis gap.
- The arXiv statistics education papers document that even students in statistics courses receiving LLM feedback improve on mechanical skills but not on conceptual understanding without additional instruction. This validates Chapter 2's emphasis on understanding over mechanics.

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Alan Turing** (1912–1954)
   - Wikipedia page: "Alan Turing"
   - Substantive connection: Turing's work on computability and machine intelligence provides the deep foundation for asking "what can a machine compute?" — which is the implicit question behind Chapter 2's verification principle. His 1950 "Computing Machinery and Intelligence" paper introduced the imitation game and raised the question of when a machine's output can be trusted. Chapter 2's lesson — that correct-looking output is not necessarily correct output — has a Turing-theoretic root.
   - Attributes: British, male, 20th century, mathematician/computer scientist/logician. High name recognition; rich documented life and work.
   - Anchor prompt: "What did Alan Turing mean by the 'imitation game,' and how does it relate to the question of whether we can trust a machine's output?"
   - [NOTE: Turing is very well-known; if diversity is a priority for this slot, see alternative below]

2. **Grace Murray Hopper** (1906–1992)
   - Wikipedia page: "Grace Murray Hopper"
   - Substantive connection: Hopper pioneered the development of practical programming languages (COBOL) and is famous for the principle that code must be readable and verifiable by humans, not just executable by machines. Her insistence on human-readable code and the "debugging" metaphor she popularized directly prefigures Chapter 2's lesson: code that runs is not the same as code that is correct, and a skilled practitioner can identify the discrepancy.
   - Attributes: American, female, 20th century, mathematician/computer scientist/Navy Admiral. Underrepresented relative to male computing pioneers; highly documented.
   - Anchor prompt: "What was Grace Hopper's contribution to making computer programming accessible to non-specialists, and why did she insist on human-readable code?"

3. **Prasanta Chandra Mahalanobis** (1893–1972)
   - Wikipedia page: "Prasanta Chandra Mahalanobis"
   - Substantive connection: Mahalanobis treated statistics as a technology — "mathematics and probability theory are only the means to promote the use of statistical methods in the world of reality." He founded the Indian Statistical Institute and designed large-scale sample surveys. This pragmatic, tool-oriented view of statistics directly parallels Chapter 2's approach: statistical software and now LLMs are tools in service of real decisions, and the practitioner must verify that the tool is computing what the problem requires.
   - Attributes: Indian, male, 20th century, statistician/physicist. Father of Indian statistics; non-Western pioneer in applied statistics. The Mahalanobis distance bears his name.
   - Anchor prompt: "Who was P. C. Mahalanobis and how did he approach statistics as a practical tool for real-world decisions in India?"

---

## 6. Pedagogical Delivery Research

### Required prior knowledge and common misconceptions

- **Required from Chapters 0–1:** Understanding of conditional probability and Bayes' theorem (Ch 0); knowledge of what a p-value does and does not say, and what a posterior probability is (Ch 1). Chapter 2's verification skill requires knowing what the *correct* output should look like.
- **No coding experience assumed:** Chapter 2 explicitly does not teach programming. The student's task is to write natural-language prompts, interpret the resulting code output, and verify the numerical results. Students who already code can read the generated code; non-coding students verify only the output values and the interpretation.

- **Specific misconceptions to address:**
  1. **"If the code runs, it's correct."** The most important misconception to break. Documented in LLM code generation research as the primary vulnerability of non-expert users. Chapter 2's worked example should demonstrate a case where the code runs without error and produces a plausible number — but for the wrong quantity.
  2. **"The LLM knows which framework to use."** Students often assume that asking for "a statistical analysis" will produce the appropriate output. LLMs default to frequentist methods in most contexts (reflecting their training data distribution) unless explicitly instructed otherwise. Students must learn to specify "Bayesian" explicitly.
  3. **"More output = more correct."** LLMs produce verbose output. Students often mistake length and confidence for accuracy. Chapter 2 must establish that the relevant check is the specific numerical output and interpretation, not the overall fluency of the response.

### Instructional sequences shown to work

- **Dialogue format (TIKTOC's own design):** The chapter shows a prompting session as a dialogue — initial prompt, LLM output, identification of error, revised prompt, final output. Research on worked examples in procedural skill learning supports showing the full process, not just the correct endpoint. The "productively wrong first attempt" helps students recognize what error detection looks like in practice.
- **Verify two, trust the pattern:** Chapter 2's Exercise 1 asks students to compute five prevalence values with the LLM but verify only two by hand. This is pedagogically deliberate: two verifications build confidence without overwhelming; they also teach that spot-checking is a valid verification strategy (the student is not expected to verify every output, but must verify enough to trust the pattern).
- **Failure-mode taxonomy before exercises:** Presenting the five failure modes (Block 5) before the exercises primes students to look for specific errors, not just "something wrong." Research on diagnostic reasoning shows that named categories improve error detection.

### Known teaching failure modes

- **Teaching prompting without teaching the underlying statistics.** If Chapter 2 is presented as "how to use AI to do your statistics homework," it undermines the entire book. The framing must be: "the statistical understanding you are building is what makes the LLM useful, because it is what lets you verify the output."
- **Over-specifying current tools.** Naming specific LLMs (ChatGPT, Claude, Gemini) in the instructional text creates immediate aging risk. The principles are tool-agnostic; the examples can use a generic "LLM" or a footnote naming current models.
- **Skipping iteration.** Students tend to accept the first LLM output if it looks plausible. Chapter 2's worked example must demonstrate an explicit iteration — getting a wrong interpretation, recognizing it, writing a corrected prompt, getting the right interpretation — so students internalize that iteration is expected, not a sign of failure.
- **Verification becoming mechanical.** If "check two values by hand" becomes a ritual rather than a reasoning step, students will compute the two values without noticing if the LLM's *interpretation* is wrong even when its numbers are right. The chapter should emphasize "verify the interpretation, not just the number."

---

## 7. Representation and Display Research

Chapter 2 is a methods chapter with no frequentist/Bayesian side-by-side comparison — TIKTOC explicitly notes "No frequentist/Bayesian comparison section — this chapter is a methods chapter."

**However, the chapter's worked example should display a dialogue format**, which is pedagogically distinct from other chapters. The recommended format:

```
PROMPT: [Student's prompt — shown in full]

LLM OUTPUT: [Abridged representative output — numerical result + interpretation]

PROBLEM IDENTIFIED: [Named failure mode from Block 5 taxonomy]

REVISED PROMPT: [Corrected prompt — shown in full, highlighting what changed]

REVISED OUTPUT: [Correct result + interpretation]

VERIFICATION: [Hand calculation confirming the numerical result]
```

This format is visual and sequential. It shows what the student actually types, not just what a correct solution looks like. Research on worked examples supports full-process display over result-only display for procedural skills.

**Block 4's template prompt structure** (from TIKTOC) should be displayed in a distinct callout box:

> "Solve [PROBLEM] using both a frequentist hypothesis test and a Bayesian posterior calculation. Show the mathematical steps for each, implement both in [language of your choice], and explain in plain language what each result means and what each approach cannot tell us."

This template recurs in every chapter's prompting section. Introducing it here as a visual template makes it memorizable and reusable.

No special side-by-side comparison display required for Chapter 2.

---

## 8. Open Questions and Research Gaps

1. **No peer-reviewed, book-length treatment of "prompting for statistics" for undergraduates exists as of 2026.** Chapter 2 is genuinely novel content. The research base (Frontiers 2025, arXiv 2024) is nascent. This means Chapter 2 cannot lean heavily on precedent from statistics education literature — it must derive its structure from first principles plus the emerging research. This is a strength (the content is fresh) and a risk (it will age quickly).

2. **The specific failure modes in Chapter 2's Block 5 are the author's categorization, grounded in LLM code generation research but not mapped exactly to a peer-reviewed taxonomy.** The five failure modes (correct code wrong model; correct model wrong interpretation; frequentist in Bayesian language; missing prior entirely; [fifth]) are pedagogically derived, not empirically validated as a complete taxonomy. They should be labeled as the author's framework informed by the literature, not as a citable research finding.

3. **LLM performance on statistical reasoning is rapidly improving.** The benchmark results cited (Claude 3.5 Sonnet 71% on Math, o3 96.7% on AIME 2024) are from 2024 and will be outdated. The chapter should not anchor to specific performance numbers. [High aging risk — these figures are already likely outdated by publication]

4. **The Frontiers 2025 study (DOI: 10.3389/frai.2025.1658316) was published October 2025** — the most recent peer-reviewed source available. Its findings on hybrid prompting should be treated as current best practice but may be superseded quickly. [Current-state; review before each edition]

5. **The arXiv papers (2511.04213, 2511.07628) are preprints as of this research date.** Their findings are directionally consistent with other literature, but they should not be cited as peer-reviewed publications without verification of journal publication status. [VERIFY publication status before final citation]

6. **No research on the specific population of undergraduates using LLMs for Bayesian statistics** has been found. The research base is (a) LLM accuracy on statistical tasks generally, and (b) LLM feedback quality in statistics courses. The specific use case Chapter 2 teaches — using LLMs to implement comparative Bayesian/frequentist analysis — has not been studied in this population. The chapter's pedagogical approach is principled inference from adjacent research, not direct evidence. Authors should be aware of this gap.

7. **Key durable principle (not subject to aging):** An LLM cannot tell the student whether the statistical framework being used is appropriate for the problem. This requires the student to know what both frameworks assume and where each fails — which is exactly what the rest of the book teaches. Chapter 2 should make this explicit: the LLM is useful precisely because the student knows what to ask for.

---

## 9. Sourcing Notes

- **Frontiers in AI (2025), DOI 10.3389/frai.2025.1658316**: Retrieved via Frontiers website, ResearchGate, and NIH PubMed Central. Full open access. Published October 2025. Authors not confirmed in research summary — verify full author list before final citation. [VERIFY full authorship]
- **arXiv:2511.04213 and arXiv:2511.07628**: Retrieved as arXiv preprints dated November 2024. Journal of record status unknown as of research date. Do not cite as peer-reviewed without verification. [VERIFY journal status]
- **CodeHalu (arXiv:2405.00253)**: Retrieved from arXiv PDF. Execution-based verification of code hallucinations in LLMs. Preprint status; verify journal of record. [VERIFY]
- **AIME 2024 performance benchmarks (o3: 96.7%, Claude: ~71% on Math)**: Multiple sources confirm these figures for the period late 2024. The specific figures will be outdated; the principle that LLM mathematical computation is now generally reliable (the verification burden has shifted to interpretation) is the durable takeaway.
- **Hallucination statistics (31.4% general, higher for open-ended tasks)**: Returned via SQ Magazine and secondary aggregators; should be traced to primary benchmarking sources before citation. [UNVERIFIED primary source — general figure from secondary aggregator; do not cite without tracing to primary study]
- **Grace Hopper "debugging" origin story**: Wikipedia page confirmed; the literal first "bug" story (1947, moth in Harvard Mark II relay) is documented. The framing of her work as establishing human-verifiable code is an interpretive connection appropriate for the Wayback section.
- **McElreath (2020)**: Verified via Taylor & Francis, Routledge, multiple library catalogs. De Groot Prize (ISBA 2024) confirmed via ISBA website mention in search results. ISBN 9780367139919.
