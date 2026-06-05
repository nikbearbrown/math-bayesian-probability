# Research: Chapter 01 — The Same Question, Two Answers
## Bayesian Probability
**Chapter one-line:** The medical testing problem reveals what frequentist statistics can and cannot say — and introduces the Bayesian alternative that answers the question the test actually asks.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

1. **Casscells, W., Schoenberger, A., & Graboys, T. B.** (1978). "Interpretation by physicians of clinical laboratory results." *New England Journal of Medicine*, 299(18), 999–1001. PMID: 692627.
   - The empirical anchor for Chapter 1's opening problem. Documents that trained physicians at Harvard medical schools systematically gave the wrong answer to the exact question the chapter poses. Establishes that this is not a student failure — it is a general cognitive failure that training does not fix. The problem parameters (rare disease, accurate test, low posterior) are directly usable as the chapter's Case.

2. **Eddy, D. M.** (1982). "Probabilistic reasoning in clinical medicine: Problems and opportunities." In D. Kahneman, P. Slovic, & A. Tversky (Eds.), *Judgment under Uncertainty: Heuristics and Biases* (pp. 249–267). Cambridge University Press.
   - Documents a second physician-error study (mammography context; 95 of 100 physicians estimated 70–80% when the correct answer is ~8%). Demonstrates the error generalizes across test types and clinical domains. Also provides Eddy's analysis of *why* the error occurs — physicians are performing approximate likelihood ratio reasoning, not Bayesian reasoning. This structural explanation is what Chapter 1's "Where Frequentist Strains" block needs.

3. **Wasserstein, R. L., & Lazar, N. A.** (2016). "The ASA's Statement on p-Values: Context, Process, and Purpose." *The American Statistician*, 70(2), 129–133. DOI: 10.1080/00031305.2016.1154108.
   - The American Statistical Association's formal statement on what p-values do and do not mean. Directly relevant to Chapter 1's "Learning Outcome 1: Explain what a p-value does and does not say." The statement's six principles — particularly that a p-value does not give the probability that the null hypothesis is true — are exactly the gap Chapter 1 is designed to fill. Verified; open access via Taylor & Francis.

4. **Gigerenzer, G., & Hoffrage, U.** (1995). "How to Improve Bayesian Reasoning Without Instruction: Frequency Formats." *Psychological Review*, 102(4), 684–704.
   - Directly relevant to Chapter 1's pedagogical design: presenting the medical-test problem in natural frequencies ("1 in 1,000 has the disease; of 999 without it, about 10 test positive...") rather than probabilities substantially improves correct Bayesian reasoning among naïve participants. The worked example in Chapter 1 should use a frequency format at least once alongside the probability format.

5. **Ioannidis, J. P. A.** (2005). "Why Most Published Research Findings Are False." *PLOS Medicine*, 2(8), e124. DOI: 10.1371/journal.pmed.0020124.
   - The formal Bayesian argument for why low prior probability of hypotheses, combined with p < 0.05 threshold, produces a high false-discovery rate. This is the structural extension of Chapter 1's medical-test lesson to the scientific literature. Chapter 1 can preview it (it receives full treatment in Chapter 4), or cite it in a footnote. The argument is precisely: P(H is true | p < 0.05) depends heavily on the prior probability of H — the same logic as the disease test. Open access on PLOS.

### Key empirical cases

1. **The Standard Medical-Test Case: Rare Disease Screening (Chapter 1's own worked example)**
   Problem as stated in TIKTOC: prevalence 1/1,000; sensitivity 99%; false-positive rate 1%. Posterior P(disease | positive) = (0.99 × 0.001) / (0.99 × 0.001 + 0.01 × 0.999) ≈ 0.090 = ~9%.
   - Why appropriate: The numbers are designed for pedagogical clarity. The "99% accurate test gives only 9% confidence" result is counterintuitive enough to motivate learning but simple enough to compute by hand. Readers at this level have personal experience with medical tests (COVID, flu, etc.), making engagement high.
   - Documentation: The specific parameters are a pedagogical construction, but the *phenomenon* is documented by Casscells et al. (1978) and Eddy (1982). The numbers are ILLUSTRATIVE — should be labeled as constructed for clarity.
   - Real-world calibration: For HIV testing at population screening scale, the CDC's sensitivity/specificity figures and US prevalence data (~0.3% general population, higher in high-risk groups) produce similar posterior-probability surprises. This can be cited as a real anchor without fabricating specific case data.

2. **The Sally Clark Case / Prosecutor's Fallacy (documented real case)**
   Described fully in Chapter 0 research. The TIKTOC Chapter 1 Exercise 2 uses the DNA version of this logic: "A lawyer argues that a DNA match (1 in 1,000,000 false positive rate) proves guilt. What is missing from this argument?" This is a direct application of the Chapter 1 framework to a legal context.
   - Documentation: People v. Collins (1968, California Supreme Court) is a documented case where a probabilistic argument based on product rule reasoning was overturned on appeal for inverting conditional probabilities. The Sally Clark case (England, 1999–2003) is more recent and more widely discussed in statistical literature. Both are confirmed documented cases.
   - The insight: The defense must supply the prior — P(defendant committed the crime before the DNA match was known) — which is the base rate of guilt among people who might have committed this crime. The prosecution's error is presenting P(DNA match | innocent) as if it were P(innocent | DNA match).

3. **HIV Screening in Low-Prevalence Populations (real, documented phenomenon)**
   A real-world case that can be cited without fabrication: routine HIV screening in the general US population (prevalence ~0.3%) with a test having 99.9% sensitivity and 99.6% specificity produces P(HIV | positive) ≈ 43% — meaning more than half of positive tests in this population are false positives. This is documented in CDC testing guidelines and academic literature on positive predictive value.
   - Source: CDC HIV Testing resources; also discussed in Bayes' theorem pedagogy literature. [FACT-CHECK RECOMMENDED on exact PPV figure — the calculation is correct for these parameters, but confirm CDC guidance on two-test confirmation protocols which are designed specifically to address this problem.]
   - Why appropriate: The two-test confirmation protocol (confirmatory Western blot after ELISA positive) is itself a Bayesian sequential update. Connects to Chapter 10's sequential updating theme.

---

## 2. The Core Concept — State of the Field

### What is settled

- **The mathematical content of Chapter 1** is completely settled. P(H|D) = P(H)·P(D|H)/P(D) is a mathematical theorem. The computation in the chapter (posterior ≈ 9% from 99% test accuracy and 0.1% prevalence) is straightforward arithmetic, not subject to debate.
- **What a p-value does not say**: The ASA statement (Wasserstein & Lazar, 2016) is definitive. A p-value does not give the probability that the null hypothesis is true. This is not a minority view — it is the official position of the primary professional statistics organization, endorsed by the statistical community. The six ASA principles are stable.
- **That physicians systematically err on this type of problem**: Casscells et al. (1978), Eddy (1982), and subsequent replications all confirm this. The failure mode is well-documented and robust.
- **That natural frequency formats improve performance**: Confirmed by Gigerenzer & Hoffrage (1995) and replicated in multiple subsequent studies.

### What is disputed

- **Whether the p-value problem is a fault of the tool or of users.** Some statisticians (notably Andrew Gelman) argue that p-values are fine when used correctly; the problem is misuse. Others (including many in the "reform" camp) argue that NHST is structurally unable to answer the questions applied researchers actually have. Chapter 1 should present the structural limitation clearly without overstating the "frequentism is wrong" position — the book's thesis requires balance.
- **Whether base-rate neglect is a fundamental cognitive limitation or a representation artifact.** Gigerenzer argues it is representation: show frequencies, not probabilities, and the error disappears. Others maintain there is a genuine cognitive limitation. For Chapter 1, this distinction matters for pedagogy (use frequency formats!) but not for the mathematical point.
- **Whether Bayesian methods are appropriate as alternatives to NHST in regulated clinical contexts.** FDA guidance on Bayesian adaptive trial design (2019 guidance) allows Bayesian methods in some contexts but frequentist analysis remains the default for drug approval. Chapter 1 should not claim Bayesian > frequentist universally — it establishes that they answer different questions. [Aging risk: FDA guidance may evolve; flag for review in 3 years]

### What has changed recently (last 5 years)

- **The "statistical significance" debate intensified.** Wasserstein, Schirm & Lazar (2019, "Moving to a World Beyond 'p < 0.05'," *The American Statistician*) called for retiring the term "statistical significance" entirely. Over 800 signatories in a *Nature* comment (Amrhein, Greenland, McShane, 2019: "Retire Statistical Significance," *Nature*, 567, 305–307). This is directly relevant to Chapter 1: the chapter's claim that "p < 0.01 says nothing about P(disease | positive)" is now supported by the mainstream of the statistics profession, not just Bayesian advocates.
- **Replication crisis in psychology and medicine accelerated awareness.** The Open Science Collaboration's 2015 result (100 psychology studies, ~36% replicated) and subsequent large-scale replication failures have made the frequentist-limitations argument more widely recognized. Students arriving in 2025 may already have heard "p-values are unreliable" — Chapter 1 should provide the precise mechanism, not just validate the vague critique.
- **COVID-19 testing** gave the general public visceral experience with sensitivity/specificity/positive predictive value. Students in 2025 have lived through the "antigen test positive but probably false positive at this stage of the pandemic" problem. This is a direct real-world referent that Chapter 1 can use without explanation.

---

## 3. Application Domain Examples

Chapter 1's primary domain is medical/clinical testing. Three documented examples accessible to the reader:

1. **COVID-19 Rapid Antigen Testing (2020–2022, widely documented)**
   During Omicron wave (late 2021–2022), when prevalence in the general population was moderately high (~5–10% in many US regions during peak weeks), rapid antigen tests with ~80% sensitivity and ~99.5% specificity produced P(COVID | positive) of ~94% — confirming infection reliably. But in low-prevalence periods (prevalence ~0.3%), the same test produces P(COVID | positive) of ~32% — most positive results are false positives. The CDC and public health authorities recommended different testing interpretations at different prevalence levels — this is Bayesian updating in action.
   - Documentation: CDC COVID-19 testing guidance; multiple peer-reviewed papers on antigen test performance across prevalence conditions. [VERIFY exact prevalence/PPV figures against CDC guidance before final text — numbers are directionally correct but specific values change with variant and test generation]

2. **Mammography Screening Debate (ongoing, documented)**
   The ongoing policy debate about mammography screening for women in their 40s is directly anchored in the positive predictive value problem Eddy described in 1982. The US Preventive Services Task Force updated its guidance in 2024 to recommend screening from age 40, reversing a previous 50+ recommendation, partly on the basis of improved sensitivity but also acknowledging that false-positive rates remain significant (10–50% of screened women will have at least one false-positive in 10 years of screening). Published: USPSTF Mammography Recommendation Statement, *JAMA*, 2024.
   - Why appropriate: It is a live policy debate that students may have heard about; it requires exactly the Chapter 1 calculation; it connects to Eddy's 1982 finding and shows the question has not been resolved.

3. **DNA Evidence in Criminal Trials (prosecutor's fallacy, documented)**
   The confusion between P(DNA match | innocent) and P(innocent | DNA match) has produced wrongful convictions and appellate reversals. The National Academy of Sciences 2009 report *Strengthening Forensic Science in the United States* explicitly addressed probabilistic reasoning errors in forensic contexts. Chapter 1's Exercise 2 (the DNA match exercise) is grounded in documented legal failures.
   - Source: National Research Council. (2009). *Strengthening Forensic Science in the United States: A Path Forward*. National Academies Press.

---

## 4. The Book's Thesis Connection

Chapter 1 is the thesis-establishing chapter. Its specific contribution:

**The frequentist test (NHST) and the Bayesian calculation are answering different questions.** The frequentist test answers: "How surprising is this result assuming the null hypothesis is true?" — P(data | H₀). The Bayesian calculation answers: "Given the data, how probable is the hypothesis?" — P(H | data). These are not the same question. The chapter's medical-test worked example makes this concrete: the p-value (P(positive | no disease) = 0.01) gives the clinician a useful signal, but not the answer to the question "should I treat this patient?"

**The prior is the crux.** The Bayesian calculation requires the prevalence (prior probability); the frequentist test ignores it. This is not a bug to be fixed — it is a structural consequence of what each approach is designed to do. The frequentist approach is not wrong for ignoring the prior; it is answering a different question. The clinician needs to know which question to ask.

**What the student must supply:** Identifying *which* conditional probability is the decision-relevant one for a given stakeholder. The algorithm computes both; the student decides which one the decision-maker actually needs. This is the metacognitive move the book is designed to build.

**Literature bearing on the thesis here:**
- Gigerenzer (2002, *Calculated Risks*) argues that statistical illiteracy in medicine is a systemic problem caused by probability-format reporting, not a fundamental cognitive limitation. His prescription (natural frequencies, visual displays) supports Chapter 1's pedagogy.
- Senn (2011, "You May Believe You are a Bayesian but You Are Probably Wrong," *Rationality, Markets and Morals*) and others argue that frequentist methods are not as ignorant of priors as critics claim (Fisher had informal prior reasoning). The book's balanced position — frequentist and Bayesian answer different questions, both legitimately — is defensible against both sides.

---

## 5. The AI Wayback Machine — Candidate Figures

1. **Jerzy Neyman** (1894–1981)
   - Wikipedia page: "Jerzy Neyman"
   - Substantive connection: Neyman formalized the frequentist confidence interval (1937) and co-developed (with Egon Pearson) the null hypothesis significance testing framework. Chapter 1 is precisely about the limits of that framework. Neyman's framework answers "how surprising is the data given the null?" — which is the specific question Chapter 1 demonstrates cannot answer what the clinician needs.
   - Attributes: Polish-American, male, 20th century, mathematician/statistician. Born in Russia (Bendery, then Russian Empire, now Moldova); worked in London, then UC Berkeley. Less romantically famous than Fisher or Bayes; the actual architect of modern NHST.
   - Anchor prompt: "What hypothesis-testing framework did Jerzy Neyman and Egon Pearson develop in the 1930s, and how does it differ from Fisher's approach to significance testing?"

2. **David M. Eddy** (1941–)
   - Wikipedia page: "David M. Eddy" [VERIFY — his Wikipedia page existence should be confirmed; he is primarily known via cited work rather than a major biographical entry]
   - Substantive connection: Eddy's 1982 mammography study is the empirical foundation for Chapter 1. He continued working on evidence-based medicine and clinical decision-making, and his work sits at the intersection of medical statistics and Bayesian reasoning. He later developed the Archimedes simulation model for diabetes care — work that used Bayesian methods.
   - Attributes: American, male, 20th–21st century, physician/statistician/policy analyst. Unusual figure — not a pure mathematician or statistician, but a physician who brought probability theory into clinical practice.
   - Anchor prompt: "What did David Eddy find when he studied how physicians interpret mammography results, and what did it reveal about base-rate reasoning in medicine?"
   - [NOTE: Eddy is a living figure (born 1941); verify status before finalizing as Wayback candidate — may be better framed as "contemporary figure" than historical.]

3. **Florence Nightingale** (1820–1910)
   - Wikipedia page: "Florence Nightingale"
   - Substantive connection: Nightingale used statistical analysis — including her famous polar-area ("coxcomb") diagrams — to demonstrate that British soldiers in the Crimean War were dying of preventable disease at far higher rates than from battle wounds. This is a classic case of using evidence to answer "what is actually causing the deaths?" — exactly the kind of decision-support question that Chapter 1 argues Bayesian reasoning can answer. Her work was statistical communication in service of a decision.
   - Attributes: British, female, 19th century, nurse/statistician/reformer. High name recognition; documented in detail; clear connection to statistics for policy decisions.
   - Anchor prompt: "How did Florence Nightingale use statistical diagrams to change the British government's approach to soldier mortality during the Crimean War?"

---

## 6. Pedagogical Delivery Research

### Required prior knowledge and common misconceptions

- **Required from Chapter 0:** Ability to compute P(A|B) = P(A∩B)/P(B); ability to apply Bayes' theorem to a two-hypothesis problem; recognition that P(A|B) ≠ P(B|A).
- **Key incoming misconception for Chapter 1:** Students who have taken a prior statistics course typically believe that a p-value of 0.01 means "there is a 99% chance the result is real" or "there is a 1% chance the null is true." This is documented in multiple surveys:
  - Oakes (1986): ~90% of academic psychologists misinterpreted p-values.
  - Lyu et al. (2020, *Journal of Pacific Rim Psychology*): The misinterpretation is widespread across fields, not just psychology.
  - Recent PLOS Mental Health (2025): "99% of surveyed researchers misinterpreted at least one p-value statement."
  - Chapter 1 must name this misconception explicitly and show students who have not seen a statistics course that they are not starting with incorrect habits (they have no habits — they learn it right the first time).

### Instructional sequences shown to work

- **The surprising-result hook**: Presenting the 99% accurate test / 9% posterior result as a puzzle before any theory is the classic "productive failure" technique (Kapur, 2016, *Educational Psychologist*). Letting students guess first, seeing that most say "99%," then showing the correct answer raises cognitive engagement.
- **Side-by-side articulation**: The chapter's side-by-side table (from TIKTOC) should appear *after* the reader has seen both solutions independently. Presenting the comparison before both sides are built makes the table overwhelming.
- **The prevalence variation exercise** (TIKTOC Exercise 1: recompute for prevalence = 0.01 and 0.1): This is the key pedagogical move that converts understanding into insight. Watching the posterior jump from 9% to 50% to 91% as prevalence changes from 0.1% to 1% to 10% makes the prior's role visible. No existing textbook reviewed in this research does this as the first exercise — it is a pedagogical innovation.

### Known teaching failure modes

- **Treating the result as an argument against medical testing**: The chapter must be careful not to imply that the medical test is useless. The test *is* valuable — it shifts the posterior from 0.1% to 9%, a 90-fold increase. The decision to treat or do a confirmatory test is the separate question. Students often take the "the test is wrong" message rather than "the test must be combined with a prior."
- **Presenting the p-value critique without the legitimate use case.** The ASA statement's principles include both what p-values don't say *and* what they do — they measure the compatibility of data with a null model. Chapter 1 should not leave students thinking p-values are worthless, only that they are answering a different question than the clinician needs.
- **Over-complicating the hand calculation.** The two-hypothesis Bayesian calculation in Chapter 1 requires only arithmetic. Introducing notation like Σ over all hypotheses before the student has comfort with the two-hypothesis case is a well-documented teaching failure in introductory Bayesian courses.

---

## 7. Representation and Display Research

Chapter 1 uses the book's standard frequentist-vs-Bayesian side-by-side comparison (from TIKTOC). Here is the worked example expressed in both columns:

**Problem**: Patient tests positive for a disease. Test sensitivity = 99%. False positive rate = 1%. Disease prevalence = 0.1% (1 in 1,000).

| | **Frequentist (NHST)** | **Bayesian** |
|---|---|---|
| **Question answered** | How likely is a positive test if the patient is healthy? P(positive \| no disease) = 0.01 | How likely is disease given positive test? P(disease \| positive) = ? |
| **Inputs used** | Sensitivity (0.99) and false positive rate (0.01) | Sensitivity (0.99), false positive rate (0.01), AND prevalence (0.001) |
| **Calculation** | p-value = P(positive \| null) = 0.01 | P(disease \| positive) = (0.001 × 0.99) / (0.001 × 0.99 + 0.999 × 0.01) ≈ 0.090 |
| **Output** | p = 0.01; "reject the null at α = 0.01" | P(disease \| positive test) ≈ 9% |
| **Clinician can conclude** | The positive result would be surprising if the patient were healthy | There is about a 9% chance this patient actually has the disease |
| **What is missing** | Cannot tell the clinician the probability of disease | Requires knowing the prevalence — which must be supplied or estimated |

**Natural frequency version (for Gigerenzer-style presentation alongside the probability version):**

Imagine 10,000 people. 10 have the disease; 9,990 do not. Of the 10 with disease, 10 test positive. Of the 9,990 without disease, about 100 test positive. So 110 people total test positive. Of those, 10 have disease. P(disease | positive) = 10/110 ≈ 9%.

Research supports presenting both representations (Gigerenzer & Hoffrage, 1995; Navarrete et al., 2015).

---

## 8. Open Questions and Research Gaps

1. **USPSTF Mammography guidance (2024)**: Cited above as relevant to the application domain. Should be verified against the actual JAMA 2024 publication for specific false-positive statistics. [FACT-CHECK — the recommendation change to age 40 was confirmed, but specific PPV figures need the primary source]

2. **The Oakes (1986) survey**: Widely cited as showing ~90% of academic psychologists misinterpreted p-values. The original book (*Statistical Inference*, 1986, Wiley) is not open access and exact figures should be verified. Used here from secondary citations. [UNVERIFIED exact figures — confirm against original]

3. **"Moving to a World Beyond 'p < 0.05'" (Wasserstein, Schirm & Lazar, 2019)**: This *The American Statistician* editorial/supplement is highly relevant to Chapter 1's "what has changed recently" and to the Chapter 13 "choosing" framework. Citation confirmed as *The American Statistician*, 73(S1), 1–19 but should be verified. [VERIFY full citation details]

4. **David Eddy's Wikipedia presence**: His work is extensively cited in academic literature but his Wikipedia page may not have the detail of a major historical figure. The anchor prompt for the Wayback section may need to be built from primary literature rather than Wikipedia. [VERIFY]

5. **Aging risk**: The LLM-generated code / prompting material (Chapter 2) is the fastest-aging part of the book. Chapter 1 itself — the medical testing problem, NHST critique, Bayesian calculation — is highly stable. The ASA statement is unlikely to be reversed. The empirical cases (Casscells, Eddy) are historical. Low aging risk for this chapter's core content.

---

## 9. Sourcing Notes

- **Wasserstein & Lazar (2016)**: Verified via Taylor & Francis DOI (10.1080/00031305.2016.1154108), Penn State institutional repository, and Berkeley open PDF. Confirmed journal, volume, pages, year. The paper has an open-access PDF available via the ASA (stat.berkeley.edu/~aldous/Real_World/ASA_statement.pdf).
- **Ioannidis (2005)**: Verified via PLOS Medicine direct link (journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124). Confirmed: *PLOS Medicine*, 2(8), e124. Open access.
- **Lyu et al. (2020)** "Beyond psychology: prevalence of p value and confidence interval misinterpretation across different fields": Verified via *Journal of Pacific Rim Psychology* (Cambridge Core) and SAGE Journals. Confirmed journal, year, title.
- **PLOS Mental Health (2025) p-value misinterpretation study**: Returned in research search with URL (journals.plos.org/mentalhealth/article?id=10.1371/journal.pmen.0000242). Authors and exact statistics should be verified before final citation. [VERIFY]
- **National Research Council (2009) Forensic Science report**: Verified as a National Academies Press publication, ISBN confirmed via multiple library sources. Full title: *Strengthening Forensic Science in the United States: A Path Forward*.
- **People v. Collins (1968)**: Verified via legal sources as a California Supreme Court case (68 Cal. 2d 319) frequently cited in statistics literature on probabilistic reasoning in court.
- **Casscells et al. (1978)**: See Chapter 0 sourcing notes. Verified.
- **Eddy (1982)**: See Chapter 0 sourcing notes. Verified venue/year; exact statistics from secondary sources only.
