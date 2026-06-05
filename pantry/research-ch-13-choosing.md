# Research: Chapter 13 — Choosing
## Bayesian Probability
**Chapter one-line:** Not a verdict — a framework for choosing between statistical approaches based on what the problem actually requires, what the decision maker actually needs, and what the data can actually support.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Bayarri, M.J. & Berger, J.O. (2004). "The Interplay of Bayesian and Frequentist Analysis." *Statistical Science*, 19(1), 58–80. DOI: 10.1214/088342304000000116**
The single most directly useful paper for Ch 13. Bayarri and Berger argue that the Bayesian/frequentist debate at the *methodological* level is substantially resolved: each approach has indispensable contributions and is "actually essential for full development of the other approach." The paper provides documented cases where Bayesian and frequentist perspectives are complementary rather than competing — Bayesian model checking using frequentist-style p-values, frequentist calibration of Bayesian credible intervals, etc. Freely available via Project Euclid (projecteuclid.org) and a PDF at isye.gatech.edu/isyebayes/bank/interplay.pdf. This is the theoretical anchor for Ch 13's framing that the choice is pragmatic, not philosophical.

**Efron, B. (2005). "Bayesians, Frequentists, and Scientists." *Journal of the American Statistical Association*, 100(469), 1–5. DOI: 10.1198/016214505000000033**
Efron's ASA Presidential Address, arguing that 19th-century statistics was Bayesian, 20th-century was frequentist, and 21st-century scientists are bringing problems (massive datasets, thousands of parameters) that require both. His empirical Bayes framework explicitly bridges the two. Crucially, Efron argues for problem-driven method selection rather than paradigm loyalty — the exact framing of Ch 13. Freely available via Taylor & Francis and in PDF from multiple academic repositories.

**Gelman, A. & Shalizi, C.R. (2013). "Philosophy and the Practice of Bayesian Statistics." *British Journal of Mathematical and Statistical Psychology*, 66(1), 8–38. DOI: 10.1111/j.2044-8317.2011.02037.x**
Gelman and Shalizi argue against the "inductive inference" interpretation of Bayesian statistics and in favor of a hypothetico-deductive model: Bayesian inference is powerful when combined with model checking (which is fundamentally frequentist in spirit — testing whether the model could have produced the data). The paper's message for Ch 13 is that "being Bayesian" is not a complete philosophy of science; it requires frequentist-style model criticism to be intellectually honest. The paper generated substantial published commentary (Kruschke, Borsboom & Haig, Mayo — all published in the same journal issue). Freely available via Wiley Online Library.

**Wasserstein, R.L. & Lazar, N.A. (2016). "The ASA's Statement on p-Values: Context, Process, and Purpose." *The American Statistician*, 70(2), 129–133. DOI: 10.1080/00031305.2016.1154108**
The ASA's authoritative description of what p-values do and do not establish. Directly relevant to Ch 13 Block 1: the case for frequentist methods includes their legal/regulatory status, but that status has been refined since 2016. The ASA statement explicitly warns against mechanical use of p < 0.05 while defending p-values as legitimate tools when correctly interpreted. Open access.

**Lakens, D., Scheel, A.M. & Isager, P.M. (2018). "Equivalence Testing for Psychological Research: A Tutorial." *Advances in Methods and Practices in Psychological Science*, 1(2), 259–269. DOI: 10.1177/2515245918770963**
A tutorial on the Two One-Sided Tests (TOST) procedure — a frequentist method for testing for the *absence* of an effect rather than its presence. Relevant to Ch 13 because it demonstrates that frequentist methods are not limited to "significance vs. not" dichotomies; they can be chosen and designed for specific inferential goals. A student building the choosing framework needs to know that frequentist tools have been developed to answer questions (like "is this effect negligible?") that naive readers assume only Bayesian methods can address. Open access.

### Key empirical cases

**Case 1 (documented): The replication crisis as a system-level consequence of method misapplication.**
Ioannidis (2005, PLOS Medicine, journals.plos.org) documented that most published research findings are false when the prior probability of effects is low and power is limited — a Bayesian framing of a frequentist procedural failure. This is a documented, large-scale case where method choice (NHST with implicit flat prior, no power consideration) materially changed conclusions across thousands of studies. The Open Science Collaboration (2015, *Science*, 349, aac4716) replicated 100 psychology studies and found 36–39% replicated. These two studies together constitute the empirical backbone for Ch 13 Block 1's caution about reflexive frequentist use.

**Case 2 (documented): FDA and EMA regulatory requirements for frequentist primary endpoints in clinical trials.**
The FDA's guidance on adaptive clinical trial designs (FDA 2019, "Adaptive Designs for Clinical Trials of Drugs and Biologics") and the European Medicines Agency's guidelines permit Bayesian methods in adaptive designs but require frequentist operating characteristics (Type I error control) for primary regulatory submissions. This is a documented institutional case where the *audience and regulatory environment* — not statistical optimality — determines method choice. Freely available from fda.gov and ema.europa.eu. [VERIFY specific document title and URL before citing in chapter.]

**Case 3 (documented): Bayesian methods in adaptive clinical trial design, where they have displaced frequentist approaches for interim analyses.**
Thall & Simon (1994) and subsequent applied work at MD Anderson Cancer Center demonstrated that Bayesian sequential updating is practically superior for adaptive designs — trials that update enrollment criteria based on accumulating data. This is a documented case where Bayesian methods are the standard of care, not the challenger. See Berry (2006, *Statistical Science*, "Bayesian Clinical Trials") for a review. Documented in peer-reviewed literature; constitutes evidence that the choice question has different answers in different sub-domains of the same field (clinical research).

---

## 2. The Core Concept — State of the Field

### What is settled

The meta-level consensus among statisticians who have written about it is that neither paradigm is universally superior; the debate at the methodological level is "considerably muted" (Bayarri & Berger 2004). There is broad agreement on several practical principles:

1. **For large samples with flat priors, the two methods give nearly identical answers.** This is arithmetic, not philosophy; frequentist and Bayesian point estimates coincide when the prior is uninformative and the likelihood dominates.

2. **Frequentist methods provide regulatory defensibility and reproducibility guarantees** that Bayesian methods with subjective priors do not, in contexts where those guarantees are required (clinical trials, manufacturing standards, legal proceedings).

3. **Bayesian methods are preferred when probability statements about parameters are needed, when data is sparse, when sequential updating is required, or when prior information is available and defensible.** These criteria are not contested; they appear consistently across review articles.

4. **Both frameworks have internal coherence problems when pushed to extremes.** Bayesian methods are vulnerable to prior sensitivity; frequentist methods are vulnerable to the multiple comparisons problem and to the base-rate fallacy.

### What is disputed

**The right language for "choosing."** Some statisticians argue the choice is never purely pragmatic — that Bayesian methods are epistemologically correct and frequentist methods are used only for legacy/regulatory reasons (Jaynes 2003 is the canonical strong Bayesian position). Others (Shalizi; Gelman) argue that even Bayesian analyses require frequentist-style checking. The book's position (thesis: neither is universally correct; competence = choosing per problem) is consistent with the pragmatist camp but should acknowledge the philosophical dispute exists.

**Empirical Bayes as a bridge.** Efron's empirical Bayes framework uses the data to estimate the prior — which is philosophically frequentist in one reading and Bayesian in another. Its status as a "third way" is disputed; some classify it as frequentist, some as Bayesian, some as neither. For Ch 13, it is useful as an example of how the divide is blurrier in practice than in principle.

**Whether the replication crisis is a frequentist problem or a user problem.** Some statisticians argue NHST is not the problem; misuse and underpowered studies are. Others (Gelman; Clayton in *Bernoulli's Fallacy*) argue NHST structurally incentivizes the failures observed. Ch 13 should represent both positions.

### What has changed recently (last 5 years)

The ASA's 2019 editorial "Moving to a World Beyond 'p < 0.05'" (Wasserstein, Schirm & Lazar, *The American Statistician* 73:S1, 2019) went further than the 2016 statement, recommending against the use of "statistical significance" as a binary decision rule altogether. This is a significant shift in official frequentist practice guidance and directly affects Ch 13 Block 1. The 2025–2026 landscape is one where several major journals (e.g., *Basic and Applied Social Psychology*) have banned p-values entirely while others have introduced mandatory effect size reporting. These are documented, current developments that a Ch 13 student should know about.

Bayesian methods have become substantially more accessible computationally since 2015: Stan (mc-stan.org), PyMC, and brms all allow non-expert users to fit complex Bayesian models. The computational cost argument for frequentist methods has weakened. As of 2025–2026, LLM-assisted Bayesian analysis is accessible to undergraduates. This changes the practical calculus for the "computational constraints" criterion in the choosing framework.

---

## 3. Application Domain Examples

Documented cases where method choice materially changed a conclusion:

**Case A: The base-rate / disease screening problem (Ch 1 revisited at scale).**
Multiple published analyses of mass screening programs (mammography, PSA testing, COVID serology) show that sensitivity/specificity numbers routinely mislead clinicians and patients because the base rate (prevalence) is ignored — which is exactly the Bayesian quantity frequentist significance testing omits. Gigerenzer, Gaissmaier, Kurz-Milcke et al. (2007, *Psychological Science in the Public Interest*) documented systematic misunderstanding of conditional probabilities among physicians, lawyers, and students. This is a case where adopting a Bayesian framework (computing the posterior probability of disease given the test result, explicitly including prevalence) changes the recommended action — not just the numerical output.

**Case B: The replication crisis in psychology and education (documented, large scale).**
Open Science Collaboration (2015, *Science*, 349): 36–39% replication rate for 100 psychology studies. Ioannidis (2005): majority of published findings in some fields are false positives under realistic priors. These are documented consequences of using NHST without prior consideration. Studies that replicate tend to have larger samples and larger effects — consistent with the Bayesian "winner's curse" argument. Method choice (or its absence) materially changed the scientific literature over decades.

**Case C: Adaptive clinical trials — Bayesian interim analyses at MD Anderson.**
Berry (2006, *Statistical Science*, "Bayesian Clinical Trials") documents cases where Bayesian adaptive designs reached correct conclusions with substantially fewer patients than fixed-design frequentist trials, because the Bayesian design updated the enrollment and stopping rules as data accumulated. This is a documented case where Bayesian methods are standard practice and frequentist alternatives would have been less efficient. The I-SPY 2 breast cancer trial (Barker et al. 2009, *Clinical Cancer Research*) is the canonical applied example.

**Case D: Frequentist required for regulatory submission, Bayesian used internally.**
Multiple pharmaceutical companies use Bayesian methods for internal go/no-go decisions during drug development while submitting frequentist primary endpoints to the FDA. This is a documented, practical case where the same data is analyzed both ways for different audiences — exactly the book's thesis enacted in industry practice. [Documented in FDA 2019 adaptive design guidance and in published reviews of Bayesian regulatory submissions; specific company-level details are not public.]

---

## 4. The Book's Thesis Connection

Chapter 13 names the choosing framework explicitly. The thesis — "neither paradigm is universally correct; competence = choosing per problem, data, decision, and audience" — is stated in its strongest form here. What the student must supply that an algorithm cannot:

1. **Identification of the decision-maker's actual need.** An LLM asked "should I use frequentist or Bayesian methods?" will produce a generic list of criteria. The student must identify *for this specific problem and this specific decision-maker* what quantity is needed — a probability, a significance threshold, a point estimate, a ranking — and which framework naturally produces it.

2. **Honest assessment of prior defensibility.** Whether a prior is "available and defensible" is a judgment about the state of knowledge in a domain, the credibility of prior studies, and the stakes of the decision. It is not algorithmic. A student who says "I used a uniform prior because I didn't have prior information" without checking whether prior information exists has made a methodological error that cannot be caught by any downstream check.

3. **Audience assessment.** Whether the audience can receive and act on a posterior probability vs. a p-value is a social and institutional judgment, not a statistical one. The student must assess whether the audience is a regulatory body, a business decision-maker, a scientific reviewer, or a policy maker — and choose accordingly.

4. **Integrity about limitations.** The choosing framework is not a guarantee of correctness. The student must articulate what would change their method choice — what additional data, different prior, different audience, different regulatory requirement would flip the decision. This is metacognition about statistical judgment, not statistical computation.

The chapter's close ("Statistics can inform judgments. It cannot replace them.") is the capstone of the series theme. The "irreducibly human" framing of Bear Brown LLC is explicit here: the judgment about which method to use, and why, given this problem and this audience, is not automatable. The LLM can implement either framework; only the analyst can choose.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Jerzy Neyman (1894–1981)**
- Wikipedia: "Jerzy Neyman"
- Connection: Neyman invented the confidence interval (1937) and, with Egon Pearson, developed the Neyman-Pearson framework for hypothesis testing — the foundational machinery of frequentist inference that this chapter asks students to choose between or against. Neyman's philosophical position was explicitly frequentist: probabilities are properties of procedures, not of individual events. He disagreed vehemently with both Fisher and the Bayesians. His framework is the other side of the choice the chapter names. For Ch 13, he represents the frequentist option at its most intellectually rigorous.
- Attributes: Polish, male, mathematician/statistician, 20th century (emigrated to U.S., Berkeley)
- Anchor prompt: "Jerzy Neyman developed the confidence interval and the Neyman-Pearson framework for hypothesis testing. Describe his philosophical argument for why probabilities should be understood as properties of repeated procedures rather than of single events, and why he believed this was superior to Bayesian approaches."

**Figure 2: Grace Wahba (born 1934)**
- Wikipedia: "Grace Wahba"
- Connection: Wahba's most influential contribution is the mathematical connection between spline smoothing (frequentist regularization) and Bayesian posterior estimation — she showed that the frequentist spline solution is the mean of the posterior under a specific Gaussian process prior. This is the technical embodiment of Ch 13's thesis: the divide is blurrier in practice than in principle, and the best methods often borrow from both. She was elected to the National Academy of Sciences in 2000 and is the I.J. Schoenberg-Hilldale Professor Emerita at Wisconsin. Lesser-known to undergraduates; her work is directly relevant to the "bridging" theme.
- Attributes: American, female, statistician/mathematician, 20th–21st century (born 1934, still active into the 2010s)
- Anchor prompt: "Grace Wahba showed a formal mathematical connection between spline smoothing (a frequentist regularization technique) and Bayesian posterior estimation. Describe that connection and what it implies about the relationship between the two statistical paradigms."

**Figure 3: Leonard J. "Jimmie" Savage (1917–1971)**
- Wikipedia: "Leonard Jimmie Savage"
- Connection: Savage's *The Foundations of Statistics* (1954) established the axiomatic basis for subjective Bayesian probability and expected utility theory — the philosophical foundation for the Bayesian side of Ch 13's choice. Savage demonstrated that any internally coherent decision-maker must behave as if they have a subjective prior probability and maximize expected utility. This is the deepest argument *for* Bayesian methods: not that they give better answers, but that rational decision-making under uncertainty requires them. For Ch 13, he represents the Bayesian option at its most intellectually rigorous — the counterpart to Neyman.
- Attributes: American, male, mathematician/statistician, 20th century (University of Chicago, Yale)
- Anchor prompt: "Jimmie Savage's 'The Foundations of Statistics' (1954) argued that rational decision-making under uncertainty requires behaving as if you have a subjective prior probability. Describe his axiomatic argument and why it is considered the philosophical foundation of Bayesian statistics."

*Diversity note: Neyman (Polish/American male, 20th century) and Savage (American male, 20th century) are both male. The author should strongly favor Wahba (American female) as the anchor figure for Ch 13 if only one or two are used, to balance gender representation across the book.*

---

## 6. Pedagogical Delivery Research

### How to teach method selection

The difficulty in teaching Ch 13 is that students arriving from Chs 1–11 may have developed a Bayesian preference — the book's structure naturally makes Bayesian methods look more sophisticated because they get more coverage in the second half. Ch 13 must correct this without undermining the learning in earlier chapters.

The research literature offers a useful framing: Pek & Van Zandt (2020, *Assessment and Evaluation in Higher Education*) and the *BJMSP* paper by Gelman & Shalizi (2013) both emphasize that statistical method selection is a metacognitive skill, not a declarative one — students need to practice choosing, not just learn the criteria. The best exercises for Ch 13 are the ones that present genuine ambiguity (problems where both approaches are defensible) rather than cases with obvious right answers.

From the 2024 Data Pedagogy post on Bayesian education: students who learn both frameworks simultaneously tend to understand each better because the contrast makes assumptions visible. Ch 13 can leverage this: the student has been doing comparative analysis for 11 chapters; now they are asked to articulate the criteria they have been implicitly using.

**Structured method-selection exercise design (from capstone pedagogy literature):**
- Present a problem with enough context that the method choice is non-trivial
- Require students to state which criteria from the framework apply to this problem
- Require students to name the single most important criterion (forced prioritization)
- Require students to write one sentence explaining what a reviewer who preferred the other approach would object to, and respond to that objection

This structure prevents the most common failure mode in Ch 13 exercises: the "both methods have merits" non-answer.

### Common failure modes in method-selection writing

1. **Circular justification:** "I used Bayesian methods because I had prior information" without specifying what the prior information was, where it came from, or why it was appropriate. Cure: require students to name the prior distribution and its parameters.

2. **Audience blindness:** Student correctly identifies the optimal statistical method but ignores that the audience (a regulatory body, a business manager, a jury) cannot use the output. Cure: make audience identification explicit in the decision framework questions.

3. **Complexity inflation:** Student chooses the more complex method (typically Bayesian) without argument, as if complexity signals competence. Cure: include exercises where the frequentist approach is clearly more appropriate (large sample, no prior information, required by a regulator); penalize unjustified complexity.

4. **The verdict fallacy:** Student concludes "Bayesian methods are better" or "frequentist methods are better" as if the answer is global. This is the exact misconception Ch 13 is designed to correct. Cure: Exercise 3 in the chapter (respond to "I always use Bayesian methods because they're more principled") directly addresses this.

### Rubric dimensions for Ch 13 exercises

Based on general capstone rubric research (Assessing a Capstone Research Project, PMC8883397; UNC assessment rubric guidance):

| Criterion | Strong | Weak |
|---|---|---|
| Criteria identification | Names 2+ specific decision criteria (sample size, prior availability, audience, decision type) and applies each to the problem | Lists generic criteria without applying them |
| Prioritization | States which criterion is most important for this problem and why | Treats all criteria equally; no prioritization |
| Objection handling | Anticipates the strongest objection from a reviewer preferring the alternative and responds substantively | Ignores or dismisses the alternative |
| Epistemic honesty | Acknowledges at least one condition that would change the choice | Claims choice is definitive regardless of conditions |

---

## 7. Representation and Display Research

### The decision framework as a display table

Ch 13 Block 3 is a "set of questions, not a flowchart." The author should present this as a structured decision table with five rows (one per criterion) and three columns: (1) the criterion/question, (2) when it favors frequentist, (3) when it favors Bayesian.

Proposed structure for the Decision Framework table:

| Decision Criterion | Favors Frequentist | Favors Bayesian |
|---|---|---|
| **What quantity does the decision-maker need?** | A significance threshold, a ranking, a go/no-go decision against a pre-specified rule | A probability statement about a parameter or outcome (P(θ > threshold)) |
| **Is prior information available and defensible?** | No prior information exists, or it would be contested by an adversarial reviewer | Prior information is documented (published studies, expert consensus, prior data) and appropriate to the question |
| **How large is the sample relative to the effect size?** | Large sample; effect size moderate to large; central limit theorem applies | Small sample; rare event; sparse data; prior can stabilize the estimate |
| **Who will receive the results?** | Regulatory body requiring frequentist operating characteristics; audience fluent in p-values; court or audit process | Internal decision-maker; audience comfortable with probability; sequential decision with updating |
| **What are computational and time constraints?** | MCMC not feasible; rapid turnaround needed; simple descriptive goal | Full posterior distribution required; uncertainty in all parameters matters for the decision |

**Note for the author:** The framework table should include a sixth row labeled "When the answer is not clear-cut" — acknowledging that many real problems fall in the middle and require judgment that no table can supply. This is the honest close to the table.

### Secondary display: the "When approaches converge" callout box

One key finding from Bayarri & Berger (2004) that should be displayed separately: for large samples with flat priors, frequentist and Bayesian results converge numerically. A callout box listing the conditions under which convergence is expected (large N, flat prior, well-specified model) prevents students from treating the two methods as always-different when in many practical cases they produce identical answers.

---

## 8. Open Questions and Research Gaps

1. **The LLM-assisted method selection question.** The prompting section of Ch 13 asks students to prompt an LLM to recommend a statistical approach for a new problem. This is genuinely uncertain territory: LLMs as of 2025–2026 tend to recommend Bayesian methods more often than warranted because training data over-represents Bayesian advocacy writing. The author should test this empirically before finalizing the prompting section and note observed biases. *Likely outdated within 3 years.*

2. **The ASA "beyond p < 0.05" follow-through.** Wasserstein, Schirm & Lazar (2019, *The American Statistician* 73:S1) recommended moving away from "statistical significance" as a binary threshold — but adoption has been uneven. As of 2026, the situation in applied fields varies: some journals have adopted new standards, most have not. Ch 13 should acknowledge this transition without overstating how far it has progressed. *Flag as likely to change significantly within 3 years.*

3. **Empirical Bayes as a "third way."** The chapter's Block 4 ("What the book has not covered") mentions non-parametric Bayesian methods but does not address empirical Bayes. Efron's empirical Bayes framework is arguably the most used "Bayesian" technique in practice (via shrinkage estimators, regularization in machine learning), and it blurs the frequentist/Bayesian boundary in ways that complicate the choosing framework. The author should decide whether to mention it in Block 4 or add a brief note in Block 3.

4. **The regulatory Bayesian gap.** FDA has approved Bayesian adaptive trial designs but still requires frequentist primary endpoints for most submissions. The current state of this regulatory boundary is documented in FDA guidance documents (2019, 2020) but changes periodically. *Verify FDA guidance document currency before publication.*

5. **The "both approaches have merits" failure mode in student writing.** The most important unresolved pedagogical question for Ch 13 is how to prevent students from writing "it depends on the context" as their entire answer. The exercises and rubric suggestions above are derived from general capstone pedagogy literature; there is no published research specifically on this failure mode in frequentist/Bayesian method-selection writing. The author may need to develop the rubric through pilot testing.

6. **Settled-looking-but-contested: the cost of Bayesian complexity.** It is commonly stated that Bayesian methods are "more principled" but computationally expensive. In 2025–2026, with Stan, PyMC, and LLM-assisted implementation, the computational cost argument has largely collapsed for simple models. The chapter's Block 1 criterion "computational constraints where MCMC is not feasible" is now a narrower category than it was in 2015. The author should update the framing accordingly.

---

## 9. Sourcing Notes

- **Bayarri & Berger (2004):** Verified via Project Euclid (projecteuclid.org/journals/statistical-science/volume-19/issue-1/The-Interplay-of-Bayesian-and-Frequentist-Analysis/10.1214/088342304000000116.full) and Duke faculty page (stat.duke.edu/~berger/papers/interplay.pdf). Full text freely available. Citation confirmed: *Statistical Science*, 19(1), 58–80, DOI 10.1214/088342304000000116.
- **Efron (2005):** Verified via Taylor & Francis (tandfonline.com/doi/abs/10.1198/016214505000000033) and UCSD course PDF mirror. Presidential address delivered August 2004, published 2005. Citation confirmed: *JASA*, 100(469), 1–5.
- **Gelman & Shalizi (2013):** Verified via Wiley Online Library (bpspsychub.onlinelibrary.wiley.com/doi/abs/10.1111/j.2044-8317.2011.02037.x). Published online 2011, volume 66 issue 1, 2013. DOI confirmed. Commentary papers in same issue also verified.
- **Wasserstein & Lazar (2016):** Verified open access at tandfonline.com/doi/full/10.1080/00031305.2016.1154108.
- **Lakens, Scheel & Isager (2018):** Verified open access at journals.sagepub.com/doi/10.1177/2515245918770963. PDF available.
- **Ioannidis (2005):** Verified open access at PLOS Medicine, DOI 10.1371/journal.pmed.0020124.
- **Open Science Collaboration (2015):** Published in *Science*, 349(6251), aac4716. DOI 10.1126/science.aac4716. [VERIFY open access status — may require institutional access. The abstract is public; the full paper may require subscription.]
- **Jaynes (2003), *Probability Theory: The Logic of Science*:** Cambridge University Press. Published posthumously. Full PDF available freely at bayes.wustl.edu/etj/prob/book.pdf with apparent author permission. Use with caveat that this is a strong advocacy position, not a balanced treatment.
- **Savage (1954), *The Foundations of Statistics*:** Dover reprint widely available. Not freely available online in full text; cite the book. The International Society for Bayesian Analysis names its best-dissertation award after Savage (bayesian.org/project/savage-award/) — confirms ongoing recognition.
- **FDA Adaptive Design Guidance (2019):** "Adaptive Designs for Clinical Trials of Drugs and Biologics," available at fda.gov. [VERIFY exact URL and version — FDA guidance documents are updated periodically. Confirm this is the current guidance before publishing.]
- **Wasserstein, Schirm & Lazar (2019), "Moving to a World Beyond 'p < 0.05'":** *The American Statistician*, 73:S1, 1–19. DOI 10.1080/00031305.2019.1583913. [VERIFY open access status.]
- **Berry (2006), "Bayesian Clinical Trials":** *Statistical Science*, 21(3). [VERIFY full citation details before publishing — confirmed journal and author but full volume/page details not independently checked in this search.]
