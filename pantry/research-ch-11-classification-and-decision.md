# Research: Chapter 11 — Classification and Decision
## Bayesian Probability
**Chapter one-line:** Classification as statistical inference — where the choice of threshold is a decision under a loss function, and making that loss function explicit is the difference between a model and a decision tool.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational Papers and Texts

**Wald, A. (1950). Statistical Decision Functions. Wiley, New York.**
The foundational monograph establishing the loss-function framework for statistical decisions. Wald defined loss functions, risk functions, Bayes decision rules, admissible rules, and minimax rules — exactly the framework the chapter applies to classification thresholds. The chapter's "what threshold minimizes expected loss given asymmetric costs?" is a direct application of Wald's general theory. VERIFIED via Internet Archive, Semantic Scholar, AbeBooks, Springer reprint edition.

**Berger, J. O. (1985). Statistical Decision Theory and Bayesian Analysis. 2nd ed. Springer (Springer Series in Statistics). ISBN: 0-387-96098-8.**
The modern textbook treatment of Wald's framework applied to Bayesian inference. Chapter 4 covers Bayesian decision theory, loss functions, and admissibility. The key result for this chapter: the Bayes decision rule (threshold that minimizes expected posterior loss) is derived directly from the posterior distribution and the specified loss function. For the loan-default problem, this means the optimal threshold is a direct function of the cost asymmetry ratio and the posterior probability. VERIFIED via Springer Nature (doi:10.1007/978-1-4757-4286-2), AbeBooks, Amazon; 634 pages, 1985.

**Berkson, J. (1944). "Application of the Logistic Function to Bio-Assay." Journal of the American Statistical Association, 39(227), 357–365.**
Berkson coined the term "logit" and established logistic regression as a general statistical model for binary outcomes, in the context of bioassay (dose-response). This is the historical origin of the frequentist first solution in this chapter. The logit is still the standard link function in credit scoring, medical diagnosis, and fraud detection. VERIFIED via JASA archive (via Wikipedia's Joseph Berkson page and multiple secondary references; direct JASA access requires institutional subscription).

**Swets, J. A. (1988). "Measuring the Accuracy of Diagnostic Systems." Science, 240(4857), 1285–1293. doi:10.1126/science.3287615.**
The foundational ROC/AUC paper applied across medical imaging, materials testing, weather forecasting, polygraph testing, and information retrieval. Establishes AUC as a threshold-independent measure of classifier accuracy, and separates diagnostic accuracy from decision bias (where the threshold is set). This directly motivates the chapter's argument: AUC measures the model; the threshold choice is a separate decision. VERIFIED via Science (doi:10.1126/science.3287615), Semantic Scholar (9,510 citations cited), SCIRP references.

**Bernardo, J. M. & Smith, A. F. M. (2000). Bayesian Theory. Wiley (Wiley Series in Probability and Statistics). (Originally 1994; paperback 2000.)**
The rigorous theoretical treatment of Bayesian statistics as a special case of decision theory. Relevant specifically to the chapter's Bayesian logistic regression: posterior predictive probabilities as inputs to a decision function, and the formal derivation of the optimal Bayes classifier under a specified loss function. VERIFIED via Wiley Online Library, AbeBooks, Amazon; ISBN 0-471-49464-X.

### Key Empirical Cases

**Case 1 — COMPAS Recidivism Algorithm (ProPublica 2016; Angwin et al.).**
Documented, published, publicly reproducible. Broward County, Florida, 7,000+ defendants, 2013–2014. The COMPAS algorithm assigns risk scores (0–10) for recidivism; a threshold separates "high" from "low" risk, affecting bail and sentencing. ProPublica (2016) found that the false-positive rate for Black defendants (40.0%) was significantly higher than for white defendants (26.2%). Subsequent work showed that multiple fairness criteria are mathematically incompatible simultaneously (Chouldechova 2017). The case directly demonstrates:
- The threshold is a decision under costs (false positive = wrongful detention; false negative = undetected recidivism)
- Different threshold choices can produce disparate impacts across demographic groups
- Making the loss function explicit reveals which fairness criterion is being implicitly optimized
VERIFIED via ProPublica's public methodology page and PMC 5777393 (Dressel & Farid 2018).

**Case 2 — Credit Scoring / Loan Default Prediction (documented domain, industry standard).**
The TIKTOC chapter problem: loan officer uses a logistic regression model to predict default; the threshold choice determines the false-positive rate (good borrowers declined) vs. false-negative rate (bad borrowers approved). This structure is the industry standard in consumer lending and is documented in:
- Basel III / BCBS risk management guidance (bank regulatory capital frameworks)
- FDIC supervisory guidance on model risk
- Academic literature on credit scoring (Thomas, Edelman, & Crook, 2002, *Credit Scoring and Its Applications*, SIAM)
The specific numbers in TIKTOC (cost of approving a bad loan is 5× the cost of declining a good loan) are illustrative — label as hypothetical example using a real industry structure.

**Case 3 — O*NET Automation Exposure Classification (Frey & Osborne 2013).**
Documented, publicly available data. Frey and Osborne (Oxford Martin School working paper, 2013; published in *Technological Forecasting and Social Change*, 114, 2017, pp. 254–280) used a Gaussian process classifier trained on 70 hand-labeled occupations to assign automation-susceptibility probabilities to 702 O*NET occupations. They applied a threshold of 70% to define "high-risk" occupations, finding ~47% of US employment at risk. This is the chapter's Exercise 3 and a direct application of the loss-function framework: at what probability threshold should an occupation be labeled "at risk," and what does that threshold imply about the relative cost of false alarms vs. missed identifications? VERIFIED: working paper confirmed via SCIRP; journal publication confirmed via IDEAS/REPEC and ResearchGate.

---

## 2. The Core Concept — State of the Field

### What Is Settled

- **Logistic regression as the industry-standard frequentist classifier** is settled. Its theoretical properties (maximum likelihood, consistency, asymptotic normality of coefficients) are well-understood. Regulators (banking, insurance, medicine) treat logistic regression coefficients as the canonical interpretable output.
- **AUC/ROC as the standard threshold-independent evaluation metric** is settled (Swets 1988; Hanley & McNeil 1982 in Radiology). AUC is the expected probability that the model ranks a random positive case above a random negative case; this interpretation is stable and taught across fields.
- **The default 0.5 threshold assumes equal costs**: this is a mathematical fact, not a contested claim. If c(FP) = c(FN), the optimal Bayes threshold is 0.5. The chapter can state this with confidence.
- **Bayesian logistic regression** with flat or weakly informative priors on coefficients produces posteriors that concentrate around the frequentist MLE for large samples. The distinction is in small samples and imbalanced classes, where the prior regularizes and prevents extreme coefficient estimates.

### What Is Disputed

- **Bayesian vs. frequentist logistic regression for prediction accuracy**: For large balanced datasets, they agree on point estimates; the Bayesian advantage is in uncertainty quantification. For small or imbalanced datasets, Bayesian methods with regularizing priors (Gelman et al., "Weakly informative default priors and Bayesian analysis," 2008) perform better. The magnitude of improvement is context-dependent.
- **The calibration problem**: Classifiers that output well-calibrated probabilities (i.e., a prediction of 0.7 is correct 70% of the time) behave differently from those that rank correctly but are not calibrated. Logistic regression is generally well-calibrated; tree ensembles (random forests, gradient boosting) are often not. For the chapter's decision-theoretic application, calibration matters: the threshold calculation assumes the predicted probability is a genuine posterior. The author should note that calibration is a prerequisite, not a given.
- **Algorithmic fairness and threshold choice**: The COMPAS case shows that it is mathematically impossible to simultaneously satisfy multiple fairness criteria (equal false-positive rates, equal false-negative rates, and calibration across groups) when base rates differ. This is Chouldechova's 2017 result. It is settled mathematics but contested in its policy implications.

### What Has Changed Recently (Last 5 Years)

- **Explainability requirements in regulated industries**: The EU AI Act (effective 2026) and US regulatory guidance increasingly require that high-stakes classification models (credit, hiring, medical) be interpretable and have documented threshold rationale. This creates a direct policy argument for making loss functions explicit — exactly the chapter's point. [Note: EU AI Act provisions are in force as of 2026; verify current implementation status.]
- **Conformal prediction**: A recent (2019–2024) alternative to probability calibration that provides prediction sets with valid coverage guarantees without requiring a fully calibrated model. Not Bayesian; relevant as a frequentist alternative to posterior predictive classification.
- **Fairness-aware machine learning**: The FAccT (Fairness, Accountability, and Transparency) community has produced a rich literature (Barocas, Hardt, & Narayanan, *Fairness and Machine Learning*, 2019–2023, free online) on threshold selection under fairness constraints. Directly relevant to the O*NET automation-exposure exercise. [AGING FLAG: this field moves quickly; specific fairness frameworks recommended in 2023 may be outdated by print date.]

---

## 3. Application Domain Examples

**1. Loan default / credit scoring (TIKTOC primary example).**
Industry standard; documented at the regulatory and academic level. Thomas, Edelman, & Crook (2002) is the canonical text. The asymmetric cost structure (5:1 or similar ratios are common in retail lending) is documented in Basel risk-weighting frameworks. The specific worked example is hypothetical; the cost structure is real.

**2. COMPAS recidivism (algorithmic fairness, documented).**
ProPublica (2016) methodology and data publicly available. The false-positive rate disparity is the core teaching case for "what does a threshold decision mean when cost asymmetries differ across groups?" This is the chapter's strongest case for why making loss functions explicit is ethically required, not just analytically helpful.

**3. O*NET automation exposure (Frey & Osborne 2013; Frey & Osborne 2017).**
Data publicly available via O*NET Online and the companion website. The 70% threshold used by Frey & Osborne is the canonical example of a threshold choice that was never explicitly justified as a loss function — and whose consequences (labeling 47% of employment as "at risk") are enormous. Students can recalculate the at-risk fraction under different thresholds (50%, 60%, 80%) and see how the policy implication changes. This is Exercise 3 in TIKTOC and directly ties the chapter to the book's Irreducibly Human series context.

**4. Medical diagnosis (binary diagnostic test, documented).**
The chapter opened in Ch. 1 with a medical test; Ch. 11 can close that loop with logistic regression on multiple predictors (e.g., mammography + age + family history predicting breast cancer). The ROC curve literature originated in radiology; Swets 1988 reports AUC values for medical imaging systems. The threshold choice for cancer screening (high sensitivity → low threshold → many false positives → unnecessary biopsies) is the canonical asymmetric-cost case.

**5. Spam filtering (documented, reader-accessible).**
Bayesian spam filtering (Sahami et al. 1998, AAAI Workshop; Graham's "A Plan for Spam" 2002) is the first high-profile deployment of Bayesian classification at scale. The cost asymmetry: a false positive (legitimate email classified as spam) is more costly than a false negative (spam reaching inbox). This directly motivates a low-false-positive threshold. Historical, well-documented, and reader-accessible without domain expertise.

---

## 4. The Book's Thesis Connection

Chapter 11 is the book's most explicit treatment of the thesis at the decision-making level. The frequentist model (logistic regression) produces a probability — it does not produce a decision. The threshold that converts probability to decision is not a statistical output; it is a decision input. In practice, this threshold is almost always set at 0.5 by default, which assumes equal costs — an assumption that is almost never examined.

The Bayesian framework integrates the probability with an explicit loss function to produce the optimal threshold. The key insight: **the frequentist and Bayesian models agree on the predicted probability; they differ in whether the decision-theoretic optimization is made explicit**. This is the clearest possible argument for the book's thesis: competence means choosing the framework that makes the decision structure visible.

**What a self-directed student must supply that an algorithm cannot:** The loss function. An LLM can fit a logistic regression, compute an ROC curve, and even optimize a threshold — but only if told what the cost ratio is. Determining the actual cost of a false positive (declining a qualified loan applicant) relative to a false negative (approving a defaulter) requires domain knowledge, ethical judgment, and stakeholder input. The algorithm cannot supply these. This is the book's "irreducibly human" judgment call, made maximally explicit.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Abraham Wald (1902–1950)**
Wikipedia page: "Abraham Wald"
Hungarian-born, Jewish, Romanian, American statistician (Columbia University). Escaped Nazi persecution via Vienna to the US in 1938. Founded statistical decision theory (1950 monograph) and sequential analysis (1947). The loss-function framework that underlies the chapter's optimal threshold derivation is directly Wald's. His sequential analysis (stopping rules for sequential tests) has deep connections to the chapter's themes. Died in a plane crash in India in 1950 at age 47. Male, but Central European Jewish heritage in early 20th century — less demographically typical for the US statistics establishment of the era. Anchor prompt: "What did Abraham Wald's 1950 framework of loss functions and risk contribute to the question of how to set a classification threshold?"

**Figure 2: Calyampudi Radhakrishna Rao (C. R. Rao, 1920–2023)**
Wikipedia page: "C. R. Rao"
Indian statistician, born Huvina Hadagali (India); worked at Indian Statistical Institute, Cambridge, Penn State. Developed Cramér-Rao bound, Rao-Blackwell theorem, information geometry. One of the most decorated statisticians of the 20th century; died at 102 in 2023. Male, Indian. Not directly connected to the chapter's classification theme — his contributions are to estimation theory, not classification. CONSIDER for Ch. 4 or Ch. 7 instead; connection to Ch. 11 is weak. [Flagged as weak fit for this chapter specifically.]

**Figure 3: John A. Swets (1928–2012)**
Wikipedia page: "John Swets"
American experimental psychologist and signal detection theorist (MIT Lincoln Laboratory, Bolt Beranek and Newman). Developed the signal detection theory framework for diagnostic decision-making; authored the 1988 Science paper that established ROC/AUC as the standard accuracy measure. Male, American. The ROC curve is the frequentist side of the chapter's model evaluation section; Swets provides the historical and intellectual foundation for why AUC separates discrimination from threshold choice. Anchor prompt: "What insight did John Swets bring from radar signal detection to medical diagnosis, and why does it matter that AUC and threshold choice are separate quantities?"

**Diversity note:** All three strong candidates (Wald, Swets, and the Berkson option) are male and from European/American backgrounds. The fairness angle offers a better diversity opportunity: Joy Buolamwini (Ghanaian-American computer scientist; Gender Shades project, 2018 MIT thesis) documented racial and gender disparities in commercial face recognition classifiers — directly a classification-threshold problem with asymmetric false-positive costs. She is not obscure (widely known in AI ethics circles), but she may be lesser-known to statistics undergraduates. Worth considering as a contemporary connection alongside a historical Wayback figure.

**Revised Candidate 3: Timnit Gebru (born ~1983)**
Wikipedia page: "Timnit Gebru"
Ethiopian-American computer scientist; co-founded the Black in AI organization; led Google's Ethical AI team before her controversial departure in 2020. Co-authored the "Gender Shades" study with Joy Buolamwini (Buolamwini & Gebru, FAccT 2018), showing that commercial face recognition classifiers had error rates up to 34.7% for darker-skinned females versus <1% for lighter-skinned males — a direct consequence of implicit threshold and training-set decisions. Female, Ethiopian-American, contemporary (born ~1983). Strong connection to Ch. 11's loss-function and fairness themes. Not strictly a "historical" Wayback figure but a legitimate "AI Wayback" figure in the sense of documenting a problem the field had created. Anchor prompt: "What did Timnit Gebru and Joy Buolamwini's Gender Shades study reveal about the real-world consequences of classification threshold choices when error costs are not equal across demographic groups?"

---

## 6. Pedagogical Delivery Research

**Prior knowledge required and common entry misconceptions:**
- Students typically arrive knowing logistic regression as a classifier that outputs "0 or 1" — not as a model that outputs a probability. Restoring the probabilistic interpretation is the first conceptual move.
- The most common misconception: "the model gives me the answer (spam or not spam); I don't need to set a threshold." Students must understand that the 0.5 default IS a threshold choice, not a neutral default.
- Students conflate AUC (a property of the model) with the threshold (a choice by the decision-maker). The chapter must separate these cleanly.
- Students often believe that "a more accurate model means a better decision." The COMPAS case shows that a model can be accurate on average and systematically wrong in ways that matter.

**Instructional sequences that work:**
- The "what costs are you accepting?" thought experiment: before any algebra, ask students to consider two scenarios (a) the cost of sending a spam email to the inbox is 0.01 and the cost of misclassifying a real email as spam is 100; (b) the reverse. What threshold do you want? This activates decision-theoretic intuition before formal notation.
- Then: "Your logistic regression already computed the probability. The only question left is: above what probability do you act?" This frames the threshold as the human decision layer above the statistical model.
- The ROC curve as a visualization of the entire space of threshold choices. Walk along the curve: low threshold = high sensitivity/low specificity; high threshold = high specificity/low sensitivity. The AUC integrates over all thresholds.
- The optimal threshold derivation: show that if cost(FP) = c1 and cost(FN) = c2, then the optimal threshold is c1/(c1+c2). This is Berger (1985) applied. Students can derive it from the expected-loss minimization with two lines of algebra.

**Teaching failure modes:**
- Teaching logistic regression as a classification method rather than a probability model. Students who learn it as "classification" never develop the threshold intuition.
- Presenting AUC as "the" measure of model quality without context. For severely imbalanced classes (common in fraud detection, rare events), AUC can look high even for a useless model.
- Skipping the loss-function derivation in favor of "just use the ROC curve to pick a good threshold." Students who skip the derivation cannot defend a threshold choice to a stakeholder.
- Over-emphasizing the math at the expense of the ethical dimension. The COMPAS case is the most powerful teaching tool in the chapter; students who leave without understanding why explicit loss functions have equity implications have missed the point.

**Understanding vs. memorizing:**
- Core understanding: "A classifier doesn't make decisions — it estimates probabilities. Decisions require a threshold. A threshold requires a loss function. A loss function requires human values." Students who understand this can apply it to any classification problem.

---

## 7. Representation and Display Research

**Frequentist vs. Bayesian side-by-side for Chapter 11:**

**Frequentist (logistic regression, threshold = 0.5):**
```
Model output:        Predicted probability of default P(default | features)
Decision rule:       If P(default | x) > 0.5, decline loan
Threshold implies:   Cost(false positive) = Cost(false negative)
                     [rarely true in lending]

Performance at threshold = 0.5:
  Sensitivity (true positive rate): 0.71
  Specificity (true negative rate): 0.85
  False positive rate:              0.15  [15% of good borrowers declined]
  False negative rate:              0.29  [29% of bad borrowers approved]

What the model cannot tell you:
  - Whether 0.5 is the right threshold for your cost structure
  - The posterior distribution of each applicant's default probability
  - How threshold choice interacts with equity across applicant groups
```

**Bayesian logistic regression with explicit loss function:**
```
Model output:        Full posterior on coefficients →
                     Posterior predictive P(default | x, data) for each applicant
Cost structure:      Cost(approve bad loan) = 5 × Cost(decline good loan)
                     → Optimal threshold = 1/(1 + 5) = 0.167

Performance at threshold = 0.167:
  Sensitivity:          0.91  [91% of defaulters identified]
  Specificity:          0.64  [more good borrowers declined, as expected]
  False positive rate:  0.36

Expected cost at threshold 0.167: 142 units
Expected cost at threshold 0.500: 189 units
Reduction in expected cost: 25%

Posterior uncertainty on the optimal threshold:
  Uncertainty in coefficients → uncertainty in predicted probabilities →
  the 0.167 point is itself a distributional result, not a single number.
  95% CrI on optimal threshold: [0.12, 0.22]
```

**Display recommendation:** The ROC curve with three labeled threshold points (0.5 default, cost-optimized 0.167, and a "high-sensitivity" alternative) is the primary comparison visualization. A second visualization: a calibration plot showing that Bayesian logistic regression posteriors are well-calibrated (predicted probability = actual frequency). Both are standard and can be generated by the LLM prompting session.

---

## 8. Open Questions and Research Gaps

1. **Calibration vs. discrimination in practice**: The chapter assumes the logistic regression is well-calibrated, but students using real datasets (including O*NET data) may find models that discriminate well (high AUC) but are poorly calibrated. The chapter needs a paragraph on checking calibration before applying decision-theoretic threshold optimization. No simple pedagogical standard exists for this at the introductory level.

2. **Fairness and the loss-function framework**: Chouldechova (2017) shows that multiple fairness criteria are mutually incompatible when base rates differ across groups. The chapter's framework (optimize expected cost) implicitly chooses one fairness criterion. The author should be explicit about what criterion is being optimized and note the alternatives. [AGING FLAG: the fairness literature is moving rapidly; specific recommendations from 2023 may be outdated by print date.]

3. **Bayesian logistic regression with imbalanced classes**: How to specify priors when one class is rare (fraud, rare disease, automation-susceptible occupations) is not settled at the introductory level. Informative priors on the intercept can improve calibration; the chapter's prompting section should include this specification.

4. **The "47% of jobs at risk" number from Frey & Osborne**: This figure has been widely cited and widely contested. Arntz, Gregory, & Zierahn (OECD, 2016) produced a task-level reanalysis and found only 9% of jobs at high risk. The disagreement is largely about the threshold and the level of analysis (occupation vs. task). This is a direct application of the chapter's threshold-sensitivity lesson — a wonderful teaching opportunity but one where the author should resist asserting which estimate is "correct."

5. **LLM-generated Bayesian logistic regression code**: As of 2026, most LLMs (GPT-4, Claude) will generate PyMC or Stan Bayesian logistic regression code correctly for standard specifications. The prompting section should include a loss-function optimization step (asking the LLM to compute the optimal threshold given a cost ratio) — this is less standard and more likely to require iteration.

6. **The connection between this chapter and EU AI Act high-risk classification systems**: The EU AI Act (2021–2026) explicitly lists credit scoring, employment screening, and other high-stakes classification applications as "high-risk AI" requiring documentation of accuracy, fairness, and error-rate justification. This regulatory context makes the chapter's decision-theoretic framework timely and consequential. [VERIFY current EU AI Act implementation status before print.]

---

## 9. Sourcing Notes

- **Wald 1950**: Confirmed via Internet Archive (free digital copy), Springer reprint (doi listed in search results), AbeBooks physical copies. Public domain in many jurisdictions.
- **Berger 1985**: Confirmed via Springer Nature (doi:10.1007/978-1-4757-4286-2), Amazon, AbeBooks. Still in print. Not open access; available via university libraries.
- **Berkson 1944**: Confirmed via Wikipedia (Joseph Berkson) and multiple academic references. Direct JASA access requires institutional subscription. Year and journal confirmed via multiple secondary sources.
- **Swets 1988**: Confirmed via Science (doi:10.1126/science.3287615), Semantic Scholar. Paywalled at Science; available via university libraries. 9,510 citations per Scispace.
- **Bernardo & Smith 2000**: Confirmed via Wiley Online Library, AbeBooks. Original publication 1994; 2000 is a corrected paperback. ISBN confirmed.
- **COMPAS / ProPublica 2016**: Confirmed via ProPublica's publicly available methodology article ("How We Analyzed the COMPAS Recidivism Algorithm"). The PMC paper (PMID 5777393, Dressel & Farid 2018, Science Advances) is an independent reanalysis, also publicly available.
- **Frey & Osborne 2013 (working paper)**: Confirmed via Oxford Martin School / SCIRP references. Published version: Frey, C.B. & Osborne, M.A. (2017). "The future of employment: How susceptible are jobs to computerisation?" *Technological Forecasting and Social Change*, 114, 254–280. Confirmed via IDEAS/REPEC.
- **Chouldechova 2017**: Chouldechova, A. (2017). "Fair Prediction with Disparate Impact: A Study of Bias in Recidivism Prediction Instruments." *Big Data*, 5(2), 153–163. doi:10.1089/big.2016.0047. Confirmed via Mary Ann Liebert publisher page and multiple secondary citations. Open access version on arXiv: 1703.00056.
- **Buolamwini & Gebru 2018**: Buolamwini, J. & Gebru, T. (2018). "Gender Shades: Intersectional Accuracy Disparities in Commercial Gender Classification." *Proceedings of the 1st Conference on Fairness, Accountability and Transparency (FAccT)*, PMLR 81:77–91. Confirmed via PMLR open access; widely cited. [VERIFY author affiliation details before including in Wayback Machine candidate text.]
- **Note on C. R. Rao as candidate figure**: Connection to Ch. 11 is weak; recommend moving this candidate to a different chapter's research file or dropping.
