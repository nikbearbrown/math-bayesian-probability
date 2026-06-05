# Research: Chapter 07 — Priors
## Bayesian Probability
**Chapter one-line:** Every statistical analysis has prior assumptions. Frequentist methods hide theirs in the machinery. Bayesian methods name theirs explicitly. This chapter makes both visible — and shows what changes when you change them.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Jeffreys, H. (1961). Theory of Probability (3rd ed.). Oxford: Oxford University Press.**
The foundational text for objective Bayesian inference. Jeffreys developed "noninformative" priors (Jeffreys prior) that are invariant under reparameterization — the first principled attempt to formalize "prior ignorance." Chapter 7 needs this as historical backdrop: the attempt to make Bayesian inference "objective" by specifying ignorance priors directly anticipates the chapter's hidden-prior argument.

**Gelman, A. (2006). "Prior distributions for variance parameters in hierarchical models (comment on article by Browne and Draper)." Bayesian Analysis, 1(3), 515–534. DOI: 10.1214/06-BA117A**
Argues that standard "noninformative" inverse-gamma priors for variance components can produce badly behaved posteriors in hierarchical models. Proposes half-t and uniform priors on the standard deviation scale instead — the practical foundation for "weakly informative priors." Primary source for Chapter 7's demonstration that "ignorance" is not neutral.

**Gelman, A., Jakulin, A., Pittau, M. G., & Su, Y.-S. (2008). "A weakly informative default prior distribution for logistic and other regression models." Annals of Applied Statistics, 2(4), 1360–1383. DOI: 10.1214/08-AOAS191**
Develops the Cauchy(0, 2.5) prior as a practical default for logistic regression coefficients. Demonstrates via cross-validation that weakly informative priors outperform both flat priors and Laplace priors. The paper introduces the concept of "weakly informative" as a middle ground between "ignorance" and "informative" — the register Chapter 7 uses for Prior 2.

**Kass, R. E., & Wasserman, L. (1996). "The selection of prior distributions by formal rules." Journal of the American Statistical Association, 91(435), 1343–1370.**
[UNVERIFIED — confirm DOI and page numbers; verify via JASA archives. Included as lead to pursue.]
Comprehensive review of objective prior selection methods: reference priors, Jeffreys priors, maximum entropy priors. Distinguishes among types of "noninformativeness" and documents where each breaks down. Useful for Chapter 7's nuanced treatment of why "flat" is not neutral.

**Gelman, A., Simpson, D., & Betancourt, M. (2017). "The prior can often only be understood in the context of the likelihood." American Statistician, 71(3), 294–303. DOI: 10.1080/00031305.2017.1285776**
[UNVERIFIED — verify exact volume/page; arxiv preprint at sites.stat.columbia.edu/gelman/research/unpublished/prior_context_2.pdf suggests this is published; verify journal and year.]
Argues that evaluating priors requires seeing how they interact with the likelihood — a "prior" that looks flat in parameter space may be highly informative about observables. Foundational for the "hidden prior" demonstration: Chapter 7 should note that even "flat" priors encode strong assumptions about the predictive distribution.

### Key empirical cases

**FDA clinical trial prior gaming concern (documented regulatory case).**
The FDA's 2026 draft guidance on Bayesian clinical trials (fda.gov/media/190505/download) explicitly addresses the risk that informative priors could be constructed to favor a drug's efficacy. The guidance requires pre-specified priors, sensitivity analysis, and frequentist operating characteristics. This is a documented regulatory concern — not a hypothetical — and directly supports Chapter 7's balanced treatment: the demand for explicit priors is a feature when knowledge exists AND a gaming risk when the analyst is not disinterested.

**Prior sensitivity in published Bayesian clinical trials: systematic review (documented).**
BMC Medical Research Methodology (Springer, 2026, DOI: 10.1186/s12874-026-02803-6): a systematic survey finding that sensitivity analysis was underused in Bayesian trials — among 64 trials using non-informative priors, only 17.2% performed sensitivity analyses. This is a documented failure mode, not a hypothetical: real published trials fail to check whether their conclusions depend on prior choice.

**Three-prior analysis in psychology replication (hypothetical framing for worked example; no single definitive published case).**
The chapter's worked example — three priors on the same clinical trial data, showing where posteriors agree and diverge — is a pedagogical construct. No single documented case serves as a clean archetype, though McElreath's Statistical Rethinking and Gelman's BDA3 contain similar demonstrations. Label as pedagogical construction when writing the chapter.

---

## 2. The Core Concept — State of the Field

### What is settled

- Every statistical analysis uses prior assumptions; frequentist methods use implicit flat (uniform) priors on parameters, which encode their own assumptions (Andrew Gelman, blog and papers, consistently documented).
- Weakly informative priors (Gelman 2006, 2008) are now the recommended default in Bayesian practice: they regularize estimates, prevent computational pathologies from flat priors, and are more honest about what "ignorance" means.
- Prior sensitivity analysis is the correct response to uncertainty about prior choice: if the posterior conclusion changes drastically across reasonable priors, this is informative (not a failure of Bayesian analysis — it is the analysis being honest about data sparsity).
- BDA3 (Gelman et al. 2013, CRC Press) is the standard graduate reference for prior specification in practice.

### What is disputed

- **The "objectivity" of frequentist analysis:** The claim that frequentist methods are "prior-free" and therefore objective is disputed by Bayesians who argue that implicit flat priors are priors, just undeclared. Frequentists counter that the uniform prior's effect is well-characterized and doesn't favor any hypothesis. The chapter must present both arguments with equal rigor.
- **Regulatory preference is shifting:** TIKTOC.md states that the FDA and EMA "often require frequentist analyses." This is broadly true but becoming less absolute. The 2026 FDA draft guidance now explicitly endorses Bayesian methods with appropriate prior justification. The EMA has issued a reflection paper on Bayesian methods (seek confirmation). The "FDA prefers frequentist" framing needs nuance: the FDA requires pre-specification and operating characteristics, which Bayesian methods can provide.
- **What "weakly informative" means in practice:** Different practitioners draw the line differently. A prior that Gelman calls "weakly informative" may be informative relative to a skeptic's prior. There is no objective definition of "weakly informative."
- **Empirical Bayes vs. full Bayes:** Using the data to estimate the prior (empirical Bayes) is widespread in practice but philosophically contested — it violates the Bayesian principle that the prior is specified before seeing data. Chapter 7 should mention this tension briefly.

### What has changed recently (last 5 years)

- The FDA's January 2026 draft guidance on Bayesian clinical trials explicitly addresses prior construction, sensitivity analysis, and operating characteristics. This is major: the largest drug regulator in the world is now providing detailed technical guidance on Bayesian prior specification. See: fda.gov/media/190505/download.
- The EMA issued a public consultation on Bayesian methods in 2020 (RAPS coverage), seeking feedback on when Bayesian methods can be accepted in confirmatory settings — reflecting regulatory movement toward qualified acceptance, not blanket preference for frequentist methods.
- Gelman, Vehtari, McElreath et al. have published "Statistical Workflow" papers (2025) formalizing prior predictive checks as a standard step, making prior evaluation more concrete and teachable.
- The systematic survey on prior sensitivity analysis in clinical trials (BMC 2026) documents that real-world practice falls short of recommended standards — actionable for Chapter 7's discussion of what goes wrong.

---

## 3. Application Domain Examples

**Domain: clinical trials / medicine (primary per TIKTOC.md Chapter 7 scenario)**

1. **Drug trial prior construction (documented regulatory concern).** The FDA's 2026 guidance addresses explicitly how priors should be constructed for efficacy claims in drug trials: pre-specified, with justification, and tested via sensitivity analysis. This anchors Chapter 7's "pharmaceutical company statistician" exercise — it is a real regulatory problem, not a hypothetical.

2. **Three-prior demonstration on a clinical trial dataset (pedagogical).** While no single paper is the archetype, Gelman's BDA3 Chapter 5 contains worked examples showing posterior sensitivity to prior choice on medical data. The chapter should construct its own worked example on a clinical trial scenario (standardly available datasets: the BUGS examples, or simulated data labeled as such).

3. **Pediatric drug trials using informative priors from adult data (documented).** A documented FDA practice: adult trial data used to construct an informative prior for pediatric trials of the same drug (extrapolation). See FDA draft guidance 2026 and PMC9077995 (Bayesian methods for rare disease). Bayesian shrinkage toward the adult posterior is the mechanism. This illustrates "informative prior from prior evidence" — Prior 3 in Chapter 7's demonstration.

4. **Historical controls in Bayesian clinical trials (documented).** Use of informative priors derived from historical control data is documented practice in oncology trials. This is an established application where the "where does your prior come from?" question has a concrete answer: prior clinical evidence. Contrasts cleanly with the speculative or gaming case.

5. **ICH E9(R1) estimand framework (regulatory).** The International Council for Harmonisation's E9(R1) addendum (adopted 2019, implemented by FDA and EMA) formalizes how trial objectives — estimands — determine what assumptions are appropriate. Not a Bayesian document per se, but directly relevant to Chapter 7: regulatory frameworks now require explicit statement of assumptions that frequentist practice often leaves implicit. Useful as evidence that the field is moving toward transparency even in frequentist settings.

---

## 4. The Book's Thesis Connection

Chapter 7 is the hinge of the book's thesis. Every chapter up to this point has noted that frequentist analyses "don't require a prior" without fully examining what that means. Chapter 7 delivers the payoff: the question is not whether to have a prior, but whether to name it. A flat prior on a drug effect size, when three prior Phase II trials showed null effects, is a strong prior — it just doesn't look like one.

The thesis — "neither paradigm is universally correct; competence = choosing per problem/data/decision/audience" — requires Chapter 7 to be genuinely even-handed. The case for frequentist priors-as-feature (regulatory environments, preregistered research, novel phenomena where knowledge doesn't exist) must be stated with as much force as the Bayesian case. If the chapter reads as "frequentist methods have hidden priors therefore Bayesian methods win," it has failed the book's thesis.

What a self-directed student must supply that an algorithm cannot: the judgment of what prior is defensible for their specific domain. An LLM can compute posterior sensitivity to three priors. It cannot tell the student which prior corresponds to the actual state of evidence in their field. That requires domain knowledge, literature review, and epistemic honesty — none of which are computable.

---

## 5. The AI Wayback Machine — Candidate Figures

**Harold Jeffreys (1891–1989)**
Wikipedia page: "Harold Jeffreys"
British mathematician, statistician, seismologist, and geophysicist at Cambridge. Knighted in 1953. Married mathematician Bertha Swirles in 1940; they co-authored Methods of Mathematical Physics. Developed the Jeffreys prior (invariant, noninformative), the Bayesian evidence scale for hypothesis testing, and the foundational text Theory of Probability (1939/1961). His Bayesian work emerged from geophysics problems, not abstract statistics — the prior came from physics, not philosophy. Discipline: statistics/geophysics/seismology. Era: early-mid 20th century. Nationality/gender: British male. Less likely to be a teaching archetype for undergrads but intellectually central.
Anchor prompt: "You are Harold Jeffreys in 1939. A frequentist colleague says that adding a prior to statistical inference makes the results subjective and unrepeatable. You respond by explaining what your 'noninformative' prior is supposed to do and what it doesn't claim."

**Bertha Swirles Jeffreys (1903–1999)**
Wikipedia page: "Bertha Swirles"
British mathematician and physicist. Girton College Cambridge; first class honours in mathematics. Research student of Ralph Fowler alongside Paul Dirac and Subrahmanyan Chandrasekhar. Worked with Max Born and Werner Heisenberg on quantum mechanics. Co-authored Methods of Mathematical Physics with Harold Jeffreys (her husband). President of the Mathematical Association 1969–1970. One of the leading women in 20th-century British mathematics. Discipline: mathematical physics/quantum mechanics. Era: early-mid 20th century. Nationality/gender: British female — significant for gender representation. Note: her connection to Bayesian statistics specifically is via her husband's work and their shared textbook; she is not primarily a Bayesian statistician herself. Use thoughtfully as a representation of women in mathematical sciences connected to the Jeffreys tradition.
Anchor prompt: "You are Bertha Swirles in 1940. You and Harold are working on a textbook about mathematical methods. He believes that scientific inference requires prior probabilities; most physicists around you don't. What do you see as the strongest argument for his position?"

**Andrew Gelman (born 1965)**
Wikipedia page: "Andrew Gelman"
American statistician, Columbia University. Author of Bayesian Data Analysis (BDA3, with Carlin, Stern, Dunson, Vehtari, Rubin) — the standard graduate Bayesian textbook. Primary researcher on weakly informative priors, prior predictive checks, and Bayesian workflow. Known for blunt, applied criticism of both naive Bayesian and naive frequentist practice. Discipline: statistics/political science. Era: contemporary. Nationality/gender: American male. Note: Gelman is a very common textbook citation; consider using one of the less-familiar figures if diversity is the primary criterion. However, his centrality to the "weakly informative prior" concept is hard to replace with a less-known figure.
Anchor prompt: "You are Andrew Gelman in 2006. You've just shown that the inverse-gamma prior for variance, commonly treated as 'noninformative', produces pathological results. A practitioner asks: 'So what should I use instead?' Walk me through your reasoning for the half-t prior."

---

## 6. Pedagogical Delivery Research

**Prior knowledge and common misconceptions:**

The most persistent misconception entering Chapter 7: "Bayesian methods are subjective because they use priors; frequentist methods are objective because they don't." Students entering with frequentist training treat this as settled. The chapter's core pedagogical task is to show that this framing is wrong in both directions: frequentist methods do use priors (implicit flat ones), and having a named prior is not the same as being subjective in a pernicious sense.

A secondary misconception: students believe that "prior ignorance" is representable by a flat/uniform distribution. Gelman's work (and Chapter 7's job) is to show that uniform on the parameter scale is not uniform on the prediction scale. A flat prior on a regression coefficient is a prior that assigns high probability to enormous effects — not ignorance.

Third misconception: once students learn that Bayesian methods require priors, they think the prior choice is arbitrary and therefore the analysis is arbitrary. Prior sensitivity analysis is the corrective: if the conclusion is the same across reasonable priors, the analysis is robust; if not, you need more data or a better-justified prior.

**Instructional sequences that work:**

From pedagogical research (datapedagogy.com, 2024): the "biggest aha moment" for students learning Bayesian statistics is understanding the p-value better after learning the Bayes factor — which suggests Bayesian instruction illuminates frequentist concepts retroactively. Chapter 7 can lean on this: "Now that you've built Bayesian analyses in Chapters 3–6, let's go back and ask: what was the frequentist analysis implicitly assuming?"

The three-prior demonstration (Prior 1: flat, Prior 2: weakly informative, Prior 3: informative centered near zero) should be run before explaining sensitivity analysis. Students seeing the posteriors diverge in tails — but agree near the mode — generates the intuition that sensitivity analysis checks. Show the picture; name the principle after.

"Defend your prior" exercises work well: students must explain why their prior choice is defensible using either domain knowledge, pilot data, or principled ignorance. This forces them to treat prior specification as a design decision, not a nuisance.

**Teaching failure modes:**

The most dangerous teaching failure: presenting the hidden-prior argument as a "gotcha" against frequentism rather than as a clarification of what all analyses assume. If students leave thinking "frequentist methods are dishonest," the book's thesis has been violated. The chapter's tone must be: both paradigms make assumptions; Bayesian methods name theirs, which makes them auditable.

A second failure mode: running the three-prior demonstration but not asking "where do conclusions agree?" If students only see where they diverge, they overestimate prior sensitivity. The pedagogical point is that posteriors usually agree in the bulk and diverge in the tails — and that tails matter for some decisions but not others.

---

## 7. Representation and Display Research

**Frequentist vs. Bayesian side-by-side comparison — worked example:**

Setting: clinical trial data, 40 patients, measuring treatment effect on blood pressure (continuous outcome). True effect approximately -5 mmHg in the data.

| | Frequentist (two-sample t-test) | Bayesian (three priors) |
|---|---|---|
| Model | Two-sample t-test | Normal likelihood, three priors |
| Prior specification | Implicit: flat on true mean difference | Prior 1: Flat/Uniform; Prior 2: Normal(0, 10²); Prior 3: Normal(0, 2²) centered near zero |
| Result | t = 2.1, p = 0.04, "significant" | Prior 1: P(effect < 0) = 2%; Prior 2: P(effect < 0) = 4%; Prior 3: P(effect < 0) = 18% |
| Point estimate | -5.2 mmHg | Posterior means: -5.1, -4.8, -3.2 mmHg |
| Tail behavior | Not modeled | Prior 3 substantially pulls posterior toward zero |
| What it shows | Same data, one answer | Same data, three answers — but point estimates barely move; tails diverge |
| Lesson | "Significance" hides prior assumption | Explicit priors make assumption visible and testable |

*Display note:* The key visual here is a posterior density plot with three curves on it, one per prior. The mode barely moves; the left tails diverge. This is the "tails matter" lesson made concrete. A side-by-side with the frequentist confidence interval added as a vertical band shows where frequentist and Bayesian-flat overlap and where informative priors diverge.

---

## 8. Open Questions and Research Gaps

**The regulatory landscape is shifting fast (likely outdated in 3 years).** The FDA's 2026 draft guidance on Bayesian clinical trials changes the framing of "FDA prefers frequentist" to "FDA accepts Bayesian with appropriate conditions." The chapter should be written to be accurate about current regulatory reality, not the pre-2026 status quo. The guidance (fda.gov/media/190505/download) is a draft as of mid-2026; its final status should be checked before publication.

**EMA position on Bayesian methods (partially unverified).** RAPS coverage indicates EMA issued a public consultation on Bayesian methods in 2020. The author should retrieve the EMA's reflection paper directly (ema.europa.eu) and verify its current status. The EMA's ICH E9 page confirms the E9(R1) addendum (2019) as relevant. The specific regulatory language about frequentist preference needs primary source verification from EMA documents rather than summaries.

**Settled-looking but contested: the "hidden flat prior" argument.** While the argument that frequentist t-tests use an implicit flat prior is accepted in the Bayesian statistics community and appears in Gelman's work, frequentist statisticians dispute that this characterization is fair. The debate is documented on Gelman's blog and in the statistics literature. The chapter should present both framings rather than treating the "hidden prior" as uncontested.

**Paywalled:** Gelman 2006 (Bayesian Analysis 1:515–534) — full text available via Project Euclid and ResearchGate. Gelman et al. 2008 (AoAS 2:1360–1383) — arXiv preprint available (arXiv:0901.4011). Kass & Wasserman 1996 (if used) — JASA, may be paywalled. BDA3 is paywalled as a textbook; free PDF circulated by authors at sites.stat.columbia.edu/gelman/book/BDA3.pdf.

**Open question for the book: does the chapter reference Clayton's Bernoulli's Fallacy?** TIKTOC.md Open Question #5 asks this. Clayton's argument (2021, Columbia UP) is that frequentist statistics systematically confuses P(data|H) with P(H|data) — the core confusion Chapter 7 is designed to address. The book could reference it as supplementary reading without making it central. The framing is polemically anti-frequentist, which cuts against Chapter 7's balanced approach.

---

## 9. Sourcing Notes

- **Jeffreys 1961**: verified via Oxford University Press product page (ISBN 9780198503682). Book, not journal article. MacTutor biography (St Andrews) confirms biography details.
- **Gelman 2006** (Bayesian Analysis, 1:515–534): verified via Project Euclid DOI 10.1214/06-BA117A. ResearchGate and SCIRP references confirm citation details. PDF at sites.stat.columbia.edu/gelman/research/published/taumain.pdf.
- **Gelman et al. 2008** (AoAS, 2:1360–1383): verified via Project Euclid DOI 10.1214/08-AOAS191 and arXiv:0901.4011. PDF at sites.stat.columbia.edu/gelman/research/published/priors11.pdf. Reliable.
- **Kass & Wasserman 1996**: [UNVERIFIED — treat as lead to pursue; verify DOI and pagination before citing].
- **Gelman, Simpson & Betancourt 2017** (American Statistician): preprint confirmed at sites.stat.columbia.edu; journal version needs verification of volume/page numbers before citation.
- **FDA 2026 draft guidance**: confirmed at fda.gov/media/190505/download. Status is draft as of research date; monitor for finalization.
- **BMC 2026 prior sensitivity survey**: confirmed via Springer Nature link (DOI: 10.1186/s12874-026-02803-6). Published; reliable.
- **EMA ICH E9 guideline**: confirmed via ema.europa.eu/en/ich-e9-statistical-principles-clinical-trials-scientific-guideline. Reliable primary source for regulatory context.
- **Clayton 2021** (Bernoulli's Fallacy): verified via Columbia University Press (ISBN 9780231199940). Book; not a primary research source. Polemical framing — cite as supplementary/further reading only, not as evidentiary support.
- **BDA3**: verified via Routledge/CRC Press; PDF at sites.stat.columbia.edu/gelman/book/BDA3.pdf (free for non-commercial use per authors).
