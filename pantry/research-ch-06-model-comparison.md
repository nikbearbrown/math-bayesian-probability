# Research: Chapter 06 — Model Comparison
## Bayesian Probability
**Chapter one-line:** How do you choose between two models? Frequentist model comparison requires choosing a test; Bayesian model comparison produces a probability — and the difference matters most when the models are close.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Akaike, H. (1974). "A new look at the statistical model identification." IEEE Transactions on Automatic Control, 19(6), 716–723.**
Introduces the Akaike Information Criterion (AIC), derived from information theory (Kullback-Leibler divergence). Proposes selecting models that minimize expected information loss, with a penalty of 2 per estimated parameter. Foundational for Chapter 6's frequentist column: AIC ranks models by predictive accuracy without requiring priors. Highly cited (50,000+).

**Schwarz, G. (1978). "Estimating the dimension of a model." Annals of Statistics, 6(2), 461–464.**
A three-page paper that derives a different model selection criterion from Bayesian principles. BIC uses penalty ln(n) per parameter (heavier than AIC for n > 7), making it more conservative with large samples. BIC approximates twice the log Bayes factor, bridging frequentist and Bayesian approaches. Directly connects to Chapter 6's question of what each criterion actually measures.

**Kass, R. E., & Raftery, A. E. (1995). "Bayes factors." Journal of the American Statistical Association, 90(430), 773–795. DOI: 10.1080/01621459.1995.10476572**
The canonical reference for Bayesian model comparison via Bayes factors. Reviews the Jeffreys evidence scale, discusses computation methods, and addresses practical use cases. Provides the calibration table (BF > 100: decisive; 10–100: strong; 3–10: moderate; 1–3: anecdotal) that Chapter 6's epidemiology example uses. Clearly written; primary source for the chapter's Bayesian column.

**Jeffreys, H. (1961). Theory of Probability (3rd ed.). Oxford: Oxford University Press.**
Jeffreys's 1939/1961 treatise introduced the Bayesian approach to hypothesis testing, including the evidence scale for Bayes factors. The classification scheme (substantial, strong, decisive) that Kass & Raftery 1995 standardized originates here. Represents the intellectual lineage from geophysics/Bayesian inference to modern model comparison.

**Vehtari, A., Gelman, A., & Gabry, J. (2017). "Practical Bayesian model evaluation using leave-one-out cross-validation and WAIC." Statistics and Computing, 27(5), 1413–1432. DOI: 10.1007/s11222-016-9696-4**
Introduces PSIS-LOO as a robust, computationally efficient alternative to Bayes factors for model comparison. WAIC (Widely Applicable Information Criterion) and LOO cross-validation measure out-of-sample predictive accuracy without requiring proper prior specification. Critical for the chapter's "recent developments" and directly relevant to Chapter 6's prompting section since the `loo` R package implements these methods.

### Key empirical cases

**COVID-19 epidemic curve model comparison (documented, 2020–2021).** Multiple published studies applied Bayesian model comparison to COVID-19 incidence data to choose between exponential growth, logistic, and SIR compartmental models. One study (PMC7928884) compared stochastic growth variants vs. ARIMA under a Bayesian framework using rolling cross-validation across 20 countries. Demonstrates Chapter 6's epidemiology scenario concretely: different models fitting early data well, Bayes factors and LOO used to pick a forecast model for public health communication.

**SARS 2003 super-spreading model comparison (documented).** Bayesian modelling framework with model comparison applied to SARS outbreak data to distinguish homogeneous transmission from super-spreading models (Bayesian modelling framework, bioRxiv/PLOS Computational Biology 2025, DOI pending). Used Bayes factors via importance sampling; identifies the same model structure across different time series. Directly anchors Chapter 6's epidemiology setting.

**Species abundance distribution models in ecology (documented).** Comparison of four statistical models across 16,000+ ecological communities using AIC, BIC, and Bayesian methods (Baldridge et al., PMC5183127). Shows that AIC and BIC often disagree on the "winning" model and that model averaging is appropriate when no single model dominates. Illustrates Chapter 6's ΔAIC < 4 ambiguity case in a real published dataset.

---

## 2. The Core Concept — State of the Field

### What is settled

- AIC (Akaike 1974) and BIC (Schwarz 1978) are the dominant frequentist model comparison criteria; their derivations, properties, and failure modes are well understood.
- Bayes factors (Jeffreys 1961; Kass & Raftery 1995) provide the Bayesian analogue: a ratio of marginal likelihoods that directly quantifies relative evidence.
- For large samples and well-specified models, AIC and Bayes factors often agree on the winner (Burnham & Anderson 2002).
- Model averaging — weighting predictions by posterior model probabilities — is the principled Bayesian response to uncertainty about which model is correct; this is well established (Hoeting et al. 1999 "Bayesian Model Averaging" *Statistical Science*).

### What is disputed

- **Prior sensitivity of Bayes factors:** Bayes factors are highly sensitive to the spread of the prior on model parameters in ways that posteriors are not. A weakly informative prior ideal for inference can yield Bayes factors that swing from "moderate" to "strong" evidence with small changes in prior width (Lindley-Bartlett paradox; Bayes Factor Reversal Paradox, arxiv 2511.22152, 2025). This is not fully resolved; practitioners disagree on whether Bayes factors or LOO cross-validation better captures model evidence.
- **AIC vs. BIC:** AIC targets predictive accuracy; BIC approximates Bayes factors under a unit information prior and is consistent (selects the true model as n → ∞). Whether "predictive accuracy" or "true model selection" is the right goal is genuinely contested in applied statistics.
- **DIC (Spiegelhalter et al. 2002, JRSS-B) vs. WAIC vs. LOO:** Multiple Bayesian model comparison criteria exist; the field has not converged on one default. DIC has theoretical problems with non-normal posteriors; WAIC/LOO are preferred by the Stan/Bayesian workflow community.

### What has changed recently (last 5 years)

- **PSIS-LOO has become the de facto standard** for model comparison in Bayesian workflows using Stan, replacing DIC and competing with WAIC. The `loo` R package (Vehtari et al.) is widely used.
- The FDA released draft guidance in January 2026 explicitly addressing Bayesian model comparison in clinical trial design, signaling regulatory recognition of these methods.
- The "Bayes Factor Reversal Paradox" (arXiv:2511.22152, 2025) formalizes a known instability: two analysts with different priors on the same data can reach opposite conclusions using Bayes factors at realistic sample sizes. This is a live controversy.
- Efficient prior sensitivity analysis for Bayesian model comparison is an active area (arXiv:2601.15132, 2026).

---

## 3. Application Domain Examples

**Domain: epidemiology/public health (primary per TIKTOC.md)**

1. **COVID-19 growth model selection (documented).** Early in the pandemic, public health agencies used exponential, logistic, and SIR models to project cases. Published comparisons (Shea et al., PMC7928884) used Bayesian frameworks and showed that AIC and Bayes factors often disagreed on the winning model, with no single model dominating all regions. Chapter 6's scenario — "which model for the next 30 days?" — is directly grounded here.

2. **SARS 2003 super-spreading vs. homogeneous transmission (documented).** Model comparison using Bayes factors was used to determine whether heterogeneous (super-spreading) or homogeneous transmission models better fit SARS case data. The same model won consistently across different SARS time series. Demonstrates Bayesian model comparison's ability to make a stable inference where frequentist model selection would require a different test for each comparison.

3. **Influenza seasonal forecasting model comparison (documented).** Epidemic forecasting literature consistently uses AIC, BIC, and increasingly LOO to compare SIR variants, ARIMA, and mechanistic transmission models. Centers for Disease Control forecasting challenges (2016–2022) produced large comparative literature showing AIC and predictive cross-validation sometimes disagree.

4. **Ecological species abundance (documented, secondary domain).** Baldridge et al. PMC5183127: comparing four models across 16,000+ communities. When no model clearly wins by AIC (ΔAIC < 4), model averaging assigns probabilistic weight across models — a case study of Chapter 6's "close call" scenario.

5. **Model comparison in financial econometrics (documented).** Bayesian model averaging of exchange rate prediction models (documented academic literature) shows that BMA consistently outperforms single-model selection when models are close. Finance is a secondary domain but useful as contrast to epidemiology.

---

## 4. The Book's Thesis Connection

Chapter 6 is the pivot where the frequentist-Bayesian comparison becomes most consequential for communication. AIC says "exponential fits better by 4.2 units." A Bayes factor says "the data are 8.3 times more consistent with exponential growth." These are not the same claim: one is a rank, the other is a probability ratio. The chapter serves the book's thesis — "competence = choosing per problem/data/decision/audience" — by showing that model comparison is also a choice: when the communicative goal is "how confident should we be in this model?", a Bayes factor or posterior model probability is the right tool; when the goal is simply "which model predicts best?", AIC or LOO suffices.

What a self-directed student must supply that an algorithm cannot: the judgment of what kind of communicability is required. An epidemiologist briefing politicians needs to say "there is an 85% probability the exponential model is correct" — a Bayesian output. An ecologist comparing models for a paper in a field that reads AIC tables needs AIC. The algorithm can compute both; the student must decide which question their audience is actually asking.

---

## 5. The AI Wayback Machine — Candidate Figures

**Hirotugu Akaike (1927–2009)**
Wikipedia page: "Hirotugu Akaike"
Japanese statistician and time series analyst at the Institute of Statistical Mathematics, Tokyo. Developed AIC from information-theoretic foundations in 1974; received the Kyoto Prize in 2006 — one of Japan's highest academic honors. Rarely discussed in Western statistics textbooks relative to his global influence. Discipline: statistics/time series/information theory. Era: mid-20th century. Nationality/gender: Japanese male — underrepresented country of origin in standard Western pedagogy.
Anchor prompt: "You are Hirotugu Akaike in 1974, just after submitting the AIC paper. A colleague asks you why you used Kullback-Leibler information loss rather than a classical goodness-of-fit test. Explain your reasoning in plain language."

**Gideon Schwarz (1933–2007)**
Wikipedia page: "Gideon Schwarz" (via Bayesian information criterion page; individual Wikipedia page may not exist — verify before use)
[UNVERIFIED — confirm individual Wikipedia page exists; if not, use BIC page citation only]
Israeli-American statistician, Hebrew University of Jerusalem and Princeton. Derived BIC in a three-page 1978 Annals of Statistics paper by solving a Bayesian model selection problem. The paper spawned a criterion used in nearly every statistical software package, despite its Spartan length. Discipline: mathematical statistics. Era: late 20th century. Nationality/gender: Israeli male.
Anchor prompt: "You are Gideon Schwarz in 1978. You have just derived BIC from Bayesian model selection principles. Explain in plain language why your penalty term — ln(n) per parameter — is larger than Akaike's penalty of 2, and what that difference means for how aggressively each criterion eliminates complex models."

**David Spiegelhalter (born 1953)**
Wikipedia page: "David Spiegelhalter"
British statistician, Winton Professor of the Public Understanding of Risk at Cambridge. Co-developed the Deviance Information Criterion (DIC) for Bayesian model comparison (2002 JRSS-B paper, third most cited in mathematical sciences 1998–2008). Also known for communicating statistics to public audiences and for Bayesian clinical trial methodology. Discipline: Bayesian statistics/medical statistics/public communication. Era: contemporary. Nationality/gender: British male.
Anchor prompt: "You are David Spiegelhalter in 2002, explaining to a clinician why you invented DIC. The clinician says 'I already have AIC — why do I need another criterion?' What do you tell them?"

---

## 6. Pedagogical Delivery Research

**Prior knowledge and common misconceptions:**
Students from frequentist-only backgrounds understand model comparison as "which model has lower AIC wins." The concept that AIC produces a ranking (not a probability) is initially invisible — students treat ΔAIC as if it were a probability or p-value. The move from "ranks" to "probability of being the right model" requires explicit instruction.

A subtler misconception: BIC is often called the "Bayesian" criterion, leading students to conflate it with Bayes factors. They are derived from different principles and measure different things. BIC approximates the log Bayes factor only under a unit information prior; in practice, BIC and Bayes factors can disagree substantially (documented in model selection literature).

**Instructional sequences that work:**
- Start with a concrete close call (ΔAIC < 4, or BF ≈ 2–4) and ask "what would you do?" before introducing any theory. This surfaces the "I'd pick the winner" instinct that both criteria resist.
- Use the epidemiology framing from TIKTOC: the communicative stakes (briefing officials) make the probability/ranking distinction feel real rather than technical.
- Present the AIC column and BF column side by side on the same dataset before asking students to state which they'd report to a public health official. The asymmetry in how each criterion's output reads aloud is the teaching moment.
- Model averaging should be introduced as the answer to genuine uncertainty: when BF ≈ 2–4, use both models weighted by posterior probability. Students find this counterintuitive but compelling.

**Teaching failure modes:**
- Teaching AIC rules of thumb (ΔAIC < 2 = indistinguishable; ΔAIC > 10 = decisive) without grounding them in what the criterion measures produces formulaic application.
- Presenting Bayes factors as "the Bayesian version of AIC" obscures the prior sensitivity problem; students then feel betrayed when they learn that prior choice can reverse the winner.
- Conflating model comparison with parameter estimation: students sometimes ask "which model is true?" as if model comparison resolves this. Chapter 6 should be explicit that model comparison identifies which model better fits the data given specific priors/assumptions — neither approach tells us which model is "true."

**Understanding vs. memorizing:**
The deep understanding target: a student should be able to explain why a Bayes factor of 8 is more informative than ΔAIC = 4, even though both favor the same model — and why that statement has qualifications. Memorizing the Jeffreys evidence scale without understanding its prior-sensitivity is insufficient.

---

## 7. Representation and Display Research

**Frequentist vs. Bayesian side-by-side comparison — worked example:**

Setting: epidemiologist comparing linear trend model (M1) vs. exponential growth model (M2) on 30 days of disease case counts.

| | Frequentist (AIC/LRT) | Bayesian (Bayes Factor) |
|---|---|---|
| Computation | AIC(M1) = 142.3, AIC(M2) = 138.1; ΔAIC = 4.2 | BF₂₁ = P(data\|M2) / P(data\|M1) = 8.3 |
| Interpretation | Exponential model fits better by 4.2 AIC units | Data are 8.3× more consistent with exponential growth |
| Communicable as probability? | No — "fits better" is a ranking, not a probability | With equal model priors: P(M2\|data) = 8.3/9.3 ≈ 89% |
| Close-call guidance (ΔAIC < 4) | "Models are approximately equivalent" | BF < 3: anecdotal evidence; BF 3–10: moderate |
| Model averaging | Not standard; sometimes done via AIC weights | Natural: weight predictions by posterior model probability |
| When to prefer | Fast; no prior needed; standard in epidemiology | When communicating probability of model correctness |

*Display note:* The side-by-side should include a "ΔAIC = 1.8" sub-case to show that frequentist guidance ("approximately equivalent") and Bayesian guidance ("anecdotal evidence for one model") say the same thing but in different registers. The display value is in showing that the two approaches aren't always saying different things — just translating differently.

---

## 8. Open Questions and Research Gaps

**Prior sensitivity of Bayes factors (unresolved).** The Bayes Factor Reversal Paradox (2025, arXiv:2511.22152) formalizes that at realistic sample sizes (n = 20–100), two analysts using different priors on the same data can reach opposite conclusions with Bayes factors. This is not yet in textbooks. For Chapter 6, the honest treatment must flag that Bayes factor answers depend on prior choices in ways AIC does not — making Bayes factors a double-edged tool.

**PSIS-LOO vs. Bayes factors for model comparison: no settled consensus.** Gelman and the Stan community favor PSIS-LOO because it uses the posterior predictive distribution rather than the prior predictive distribution, making it less prior-sensitive. But Bayes factors retain defenders (especially in psychology via BayesFactor R package). The field has not converged. Authors should present WAIC/LOO as the emerging practical standard while acknowledging the philosophical dispute.

**Likely outdated in 3 years:** Any specific guidance on R packages (loo, BayesFactor, bridgesampling) and their default settings. The `loo` package API, default diagnostics, and WAIC/LOO computation methods are actively evolving.

**Paywalled sources:** Kass & Raftery 1995 (JASA) is paywalled but the PDF is widely circulated; author should verify access. Spiegelhalter et al. 2002 (JRSS-B) is paywalled.

**Unverifiable cases:** The specific ΔAIC = 4.2 / BF = 8.3 numbers in TIKTOC.md are hypothetical (labeled in TIKTOC). No real dataset is provided; the chapter will need a real or simulated dataset for exercises. The companion website dataset will need to be created.

**Settled-looking but contested:** The "ΔAIC > 10 = decisive" rule of thumb is widely cited but its derivation is from Burnham & Anderson 2002 (an ecology text), not from statistical theory. In medicine, a ΔAIC of 4 may matter enormously; in ecology, it may not. Context-dependence is underemphasized in teaching.

---

## 9. Sourcing Notes

- **Akaike 1974** (IEEE TAC, 19:716–723): verified via Semantic Scholar, ADS, multiple reference databases. Full PDF available (eclass.uoa.gr link). DOI: 10.1109/TAC.1974.1100705. Reliable.
- **Schwarz 1978** (Annals of Statistics, 6:461–464): verified via Project Euclid (projecteuclid.org/journals/annals-of-statistics). Full PDF available (sites.stat.washington.edu). DOI: 10.1214/aos/1176344136. Reliable.
- **Kass & Raftery 1995** (JASA, 90:773–795): verified via multiple reference databases (SCIRP, colorado.edu hosted PDF, perso.amse-aixmarseille.fr hosted PDF). DOI: 10.1080/01621459.1995.10476572. Reliable; PDF available.
- **Jeffreys 1961** (Theory of Probability, Oxford): verified via Oxford University Press product page and MacTutor biography. 3rd edition confirmed. Not a journal article — book citation. The "evidence scale" is attributed to Chapter V of the 1961 edition; page numbers should be confirmed from a library copy.
- **Vehtari, Gelman & Gabry 2017** (Statistics and Computing, 27:1413–1432): verified via Springer Nature Link and Aalto University research portal. arXiv preprint: 1507.04544. DOI: 10.1007/s11222-016-9696-4. Reliable.
- **Burnham & Anderson 2002** (Model Selection and Multimodel Inference, Springer): verified via ResearchGate, Springer Nature link. Not page-level verified; treat as secondary confirmation for AIC ecology context.
- **Spiegelhalter et al. 2002 DIC paper** (JRSS-B): verified via Wiley Online Library (rss.onlinelibrary.wiley.com/doi/10.1111/1467-9868.00353). Paywalled; full citation confirmed via multiple sources.
- **Bayes Factor Reversal Paradox (2025)**: arXiv:2511.22152 — not yet peer-reviewed. Flag as preprint if cited.
- **COVID-19 model comparison** (PMC7928884): verified open-access via PubMed Central. Reliable for empirical case.
