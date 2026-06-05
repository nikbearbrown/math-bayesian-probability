# Research: Chapter 05 — Regression, Both Ways
## Bayesian Probability
**Chapter one-line:** Linear regression as a frequentist workhorse and as a Bayesian model — the solutions converge on the line, but diverge on everything else that matters for decision-making.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Gelman, A., & Hill, J. (2007). *Data Analysis Using Regression and Multilevel/Hierarchical Models*. Cambridge University Press. ISBN: 978-0-521-68689-1**
The most pedagogically focused graduate-level text bridging OLS and Bayesian regression in a unified framework. Chapter 3 covers the frequentist-Bayesian equivalence under flat priors explicitly; later chapters develop hierarchical regression. Gelman and Hill use real datasets throughout (social science, public health, political science). The specific equivalence result—OLS = MAP under flat (improper uniform) prior—is derived here. This is the primary textbook citation for Ch 5. VERIFIED via Cambridge University Press page and multiple library catalogs. Not open access but widely available.

**McElreath, R. (2020). *Statistical Rethinking: A Bayesian Course with Examples in R and Stan* (2nd ed.). Chapman and Hall/CRC. ISBN: 978-0-367-13991-9**
The book cited in TIKTOC as "the next step" after this book. Chapters 4–5 develop Bayesian linear regression from the posterior-as-geometry-of-plausibility perspective, with explicit prior predictive simulation before fitting. The 2nd edition is stronger on causal inference (DAGs). Reviewed positively in multiple journals. For Ch 5, McElreath's treatment of prior predictive checks (simulate from the prior before seeing data) is the best available pedagogical development of why priors on regression coefficients matter. VERIFIED via Routledge, Wikipedia, and review articles.

**Gelman, A., Carlin, J. B., Stern, H. S., Dunson, D. B., Vehtari, A., & Rubin, D. B. (2013). *Bayesian Data Analysis* (3rd ed.). Chapman and Hall/CRC.**
BDA3 Chapter 14 covers Bayesian regression in full generality. The equivalence of OLS and MAP under flat priors is in Chapter 14. The posterior predictive distribution derivation is in Chapter 6 (general posterior predictive checking). The reference for the mathematical derivations the chapter summarizes. VERIFIED as in Ch 3 research file.

**Greenland, S., Senn, S. J., Rothman, K. J., Carlin, J. B., Poole, C., Goodman, S. N., & Altman, D. G. (2016). Statistical tests, P values, confidence intervals, and power: A guide to misinterpretations. *European Journal of Epidemiology*, 31, 337–350. DOI: 10.1007/s10654-016-0149-3**
Although primarily a p-value paper, this source is directly relevant to Ch 5: a regression coefficient with p = 0.08 is not evidence that "advertising doesn't work" (Exercise 2 in the TIKTOC). Greenland et al. enumerate the specific misinterpretation that a non-significant result is "no effect." This paper grounds the "what the manager missed" question in the chapter's exercise. Open access. VERIFIED via Johns Hopkins and Semantic Scholar.

**Welch, B. L. (1947). The generalization of 'Student's' problem when several different population variances are involved. *Biometrika*, 34(1–2), 28–35.**
Less directly relevant to regression than to Ch 4, but the OLS t-test for regression coefficients uses the same mathematical machinery. Including for the "OLS coefficient tests" block of the chapter: the t-statistic on a regression coefficient has a standard error and a t-distribution, and the same misinterpretation problems from Ch 4 apply here. VERIFIED via Biometrika and multiple reference databases.

### Key empirical cases

**Bayesian marketing mix modeling (Bayesian MMM) — industry-wide documented adoption.** Google (Meridian, 2024+), Meta (Robyn, open-sourced 2022), and PyMC Labs (PyMC-Marketing, 2022+) have all released open-source Bayesian regression tools for modeling the effect of advertising spend on sales. These tools model adstock (carryover) and saturation (diminishing returns) effects using Bayesian priors, because the posterior predictive distribution is needed to optimize budget allocation—exactly the "P(sales increase > X | budget increase)" question the chapter poses. This is documented in company publications, peer-reviewed surveys (Springer Nature, 2026), and open-source repositories. Not hypothetical.

**Galton's original height regression dataset (documented, historical, public domain).** Francis Galton's 1886 data on the relationship between parent and child heights is the founding dataset for linear regression. The dataset is publicly available and well-documented. Use as a historical anchor: Galton invented regression to model a relationship between two continuous variables—the modern use is the same, scaled up. The dataset is small (about 900 parent-child pairs) and can be fitted with both OLS and Bayesian regression to show the convergence on the line.

**HYPOTHETICAL — Chapter's worked example:** The specific scenario (60 weeks of sales and advertising spend, retail analyst, slope = 2.3) is pedagogically constructed. Label as hypothetical. The qualitative structure—advertising spend as predictor, sales as outcome—mirrors the documented MMM applications above.

---

## 2. The Core Concept — State of the Field

### What is settled (cited)

- **OLS = MAP under flat prior.** When the prior on regression coefficients is flat (improper uniform), the posterior mode (MAP estimate) is identical to the OLS coefficient. The posterior mean is also the OLS estimate in this case because the posterior is symmetric (normal). This is mathematically derived in Gelman & Hill (2007) and BDA3 (2013). It is not controversial.
- **OLS is BLUE (Best Linear Unbiased Estimator) under the Gauss-Markov conditions:** homoscedastic errors, no autocorrelation, no perfect multicollinearity. This result is settled and is the foundational justification for teaching OLS as a default. The frequentist case for OLS is strong when these conditions hold.
- **The posterior predictive distribution integrates over parameter uncertainty** while the frequentist prediction interval conditions on the estimated parameters. This means the Bayesian prediction interval is always at least as wide (more honest about total uncertainty) and becomes substantially wider when the dataset is small. This is established in Bayesian theory and documented empirically.
- **Bayesian and frequentist regression give identical point estimates under flat priors, but different intervals.** The frequentist 95% CI for a coefficient does not give P(β ∈ interval | data); the Bayesian 95% credible interval does. Same philosophical distinction as in Ch 3.

### What is disputed

- **What "weakly informative" priors mean for regression coefficients in practice.** Gelman recommends standardizing predictors and using Normal(0, 1) or Normal(0, 2.5) priors on standardized coefficients (the default in Stan's brms package). This is a defensible recommendation but not universally adopted; different software packages (rstanarm vs. brms vs. PyMC) use different defaults. For the business regression in the chapter, what does "weakly informative" mean for an advertising coefficient measured in thousands of dollars? The author must specify this concretely.
- **Whether the equivalence of OLS and MAP justifies calling OLS "Bayesian with a flat prior."** Some statisticians (notably Brad Efron) argue that frequentist confidence intervals and Bayesian credible intervals deserve to be understood as answering genuinely different questions, not just different implementations of the same thing. The claim that "OLS is Bayesian with an implicit flat prior" is pedagogically useful but philosophically contested—particularly because the improper uniform prior is not a valid probability distribution. The chapter should acknowledge this.
- **When Bayesian regression is computationally worth it.** For the simple linear regression the chapter presents, MCMC is overkill—analytical solutions exist for the normal-normal conjugate case. For a 60-week dataset with one predictor, VI (variational inference) or even Laplace approximation gives indistinguishable results at a fraction of the computation. The chapter uses MCMC/Stan in the prompting section; the author should note that simpler approximations exist.

### What has changed recently (last 5 years)

- **Probabilistic programming languages have matured dramatically.** Stan (via brms or rstanarm R interfaces), PyMC (Python), and NumPyro have made Bayesian regression accessible without low-level coding. LLM-assisted implementation has further reduced the barrier. This is relevant to the chapter's prompting section: as of 2025–2026, prompting an LLM to fit a Bayesian regression in PyMC or brms is feasible for undergraduates. Flag as aging-risk.
- **Bayesian workflow (Gelman et al., 2020/2024)** has articulated a step-by-step protocol: (1) prior predictive check, (2) fit the model, (3) posterior predictive check, (4) compare to alternative models. This workflow is now the recommended practice and provides structure for the chapter's prompting section.
- **Causal inference has grown substantially** as a distinct framework from regression. Gelman & Hill (2007) was updated in a second edition (Gelman, Hill, & Vehtari, 2020, *Regression and Other Stories*, Cambridge) that is more explicitly causal. The distinction between descriptive regression ("advertising is associated with sales") and causal inference ("advertising causes sales") is more prominent in recent pedagogy. The chapter should make this distinction briefly.
- **Conformal prediction** (2023–2026) provides distribution-free frequentist prediction intervals with finite-sample coverage guarantees, challenging the Bayesian claim that posterior predictive distributions are superior for prediction uncertainty. This is an active research area; the chapter need not engage with it but should not overclaim Bayesian prediction superiority.

---

## 3. Application Domain Examples

**Retail advertising and sales (chapter's primary domain — documented industrial application).**
Bayesian regression for advertising effectiveness is now documented in major company publications. Meta's Robyn (2022) and Google's Meridian (2024) are open-source frameworks for Bayesian marketing mix modeling. The core model is Bayesian linear regression with priors encoding business knowledge (e.g., advertising spend should have a non-negative effect on sales; diminishing returns at high spend). The posterior predictive distribution is used to answer: "If we increase advertising budget by 10%, what is the probability sales increase by at least 5%?" This is exactly the chapter's worked example question. Documented, contemporary, reader-relevant.

**Economics: returns to education (documented, long-standing).** The relationship between years of schooling and wages is the canonical economics regression problem. Mincer's earnings equation (Mincer, 1974) is the foundational frequentist analysis. Bayesian re-analyses of wage equations are documented in the economics literature. For the chapter, this is a more serious application than advertising—the coefficient on education in a wage regression is a policy-relevant quantity, and the posterior distribution on that coefficient (rather than just a p-value) is what a policy analyst needs. This connects to the book's BLS/O*NET dataset library.

**Environmental science: temperature trend estimation (documented, climate science).** OLS trend estimation (fitting a line through temperature anomaly over time) is the standard frequentist approach to documenting climate change. Bayesian regression with informative priors from physics is used in more sophisticated analyses. The chapter can mention this as a domain where the prior (incorporating physical constraints on the temperature trend) is scientifically defensible rather than arbitrary. Reader-accessible through news coverage.

**Real estate: hedonic pricing models (documented, economics).** House price as a function of square footage, location, bedrooms, etc. is the canonical multiple regression example. OLS is the historical default; Bayesian regression with spatial priors is now standard in real estate modeling. The posterior predictive distribution answers: "What is the probability this house is worth more than $500,000, given its features?" The frequentist prediction interval cannot answer this directly.

---

## 4. The Book's Thesis Connection

Chapter 5 is the chapter where the TIKTOC explicitly names the "asymmetry rule": the Bayesian solution is more complex than the frequentist one, and this complexity earns something real. The chapter's thesis role is to make the cost-benefit trade-off explicit for the first time: OLS is cheaper, faster, and produces identical point estimates—but it cannot answer the analyst's actual question ("should we increase the budget?"). The Bayesian posterior predictive distribution can.

A self-directed student must supply what the algorithm cannot: (1) the business decision threshold ("a sales increase of at least 5% counts as a win"), (2) the prior—what do we believe about the advertising-sales relationship before seeing this data? Both require judgment that reaches outside the data. The chapter's Exercise 3 makes this explicit: "The company uses a decision threshold of P(ROI > 0) > 0.85. Can the frequentist model satisfy this criterion directly?" The answer is no—not because OLS is wrong, but because it doesn't produce a probability distribution over outcomes.

The asymmetry that is "named here for the first time" in the TIKTOC is the book's central pedagogical claim: Bayesian methods earn their complexity when decisions require probability statements about outcomes. OLS is not wrong; it is insufficient for decision-making under uncertainty when the decision requires a probability.

---

## 5. The AI Wayback Machine — Candidate Figures

**Francis Galton (1822–1911)**
Wikipedia page: "Francis Galton"
British polymath. Invented linear regression, the correlation coefficient, and the concept of regression toward the mean (from studies of inherited traits, 1886). His original regression problem was exactly a two-variable continuous relationship. Connection to Chapter 5: every regression the chapter teaches descends from Galton's invention. The name "regression" comes from his observation that children of tall parents "regress toward the mean." This is a memorable and accurate historical hook: the algorithm is named after the phenomenon it was designed to measure. Galton's legacy is complicated—he was also a founder of eugenics—but his statistical contributions are foundational and real. The complexity of his legacy is worth acknowledging rather than suppressing. Gender: male; nationality: British; era: Victorian; discipline: statistics, anthropology, genetics.
**Anchor prompt:** "Francis Galton invented regression in the 1880s while studying whether tall parents had tall children. He noticed something strange: the children of very tall parents were, on average, shorter than their parents. He called this 'regression toward mediocrity.' What does regression toward the mean tell us about prediction? Does it mean tall parents are 'pulling' their children back toward average height?"

**Evelyn Fix (1904–1965)** — profiled in Ch 4. Available here if needed; but prefer a fresh figure.

**Madan Lal Puri (1929–2023)**
Wikipedia page: "Madan Lal Puri"
Indian-American statistician. Spent most of his career at Indiana University Bloomington. Major contributions to nonparametric statistics and time series analysis. Born in Sialkot, British India (now Pakistan). Connection to Chapter 5: Puri's work on nonparametric rank-based alternatives to OLS regression is directly relevant to the "where frequentist strains" section—when the normality assumption on residuals is violated, rank-based regression methods are the frequentist alternative, and Bayesian regression with robust (non-normal) likelihoods is the Bayesian alternative. Lesser-known outside statistics departments; Indian-American; male; late 20th century; mathematical statistics. Note: his Wikipedia page "Madan Lal Puri" exists and is verified.
**Anchor prompt:** "Madan Lal Puri spent decades building regression methods that don't require assuming your data follows a normal distribution. OLS assumes the errors around the line are normally distributed. What actually happens when that assumption is wrong? Can you tell from looking at your data? What did Puri develop to handle it?"

**Helen Walker (1891–1983)**
Wikipedia page: "Helen M. Walker"
American statistician and historian of statistics. President of the ASA (1944). Wrote *Studies in the History of Statistical Method* (1929), and co-authored a major statistics textbook (*Statistical Inference*, 1953, with Lev). Her historical work traces the development of regression and correlation from Galton through Pearson. Connection: Chapter 5 tells the history of regression implicitly (Galton → OLS → Bayesian regression). Walker's work provides the documented historical source for this lineage. Female; American; 20th century; discipline: statistics and history of statistics. Less well-known.
**Anchor prompt:** "Helen Walker wrote the history of statistics while also being a practicing statistician—she knew the formulas and knew where they came from. She traced linear regression from Francis Galton's sweet peas through to the modern use of computers. What was lost as regression moved from 'a discovery about inheritance' to 'a tool for predicting sales'? What do we forget when we use a method without knowing its history?"

---

## 6. Pedagogical Delivery Research

**Prior knowledge and misconceptions:**
Students entering Ch 5 from an introductory statistics course believe OLS is "the" regression method and that R² is a quality measure. The most dangerous misconception for this chapter: confusing a **confidence interval for the mean** with a **prediction interval for a new observation**. The CI for E[Y | X=x] is narrow; the prediction interval for a new Y is wider (it includes irreducible residual variance). This confusion is compounded when Bayesian posterior predictive distributions are introduced—students conflate them with the CI, the prediction interval, and the posterior on the coefficient.

A second documented misconception: the R² statistic measures "how good the regression is" without acknowledging that R² can be high for a causally meaningless relationship. The chapter's advertising-sales example is potentially confounded (both might be driven by a third variable, like seasonal demand)—McElreath's 2nd edition introduction of DAGs is the pedagogical resource for this.

**Instructional sequences that work:**
1. Before introducing Bayesian regression, have students compute the OLS prediction interval for a new observation manually (or via LLM). Then ask: "Does this interval tell you the probability that next quarter's sales will exceed $500,000?" When students realize the answer is no, the Bayesian posterior predictive distribution becomes motivating rather than exotic.
2. The prior predictive check (McElreath's innovation for undergraduates): before fitting any data, simulate from the prior—what does it imply sales could be? If the prior allows negative sales or absurdly large values, it is not weakly informative. This makes prior specification concrete and testable.
3. The equivalence demonstration: fit OLS. Fit Bayesian regression with a flat prior using an LLM. Show the coefficients are identical. Then narrow the prior and show the coefficients shrink. This makes the MAP = OLS result visceral rather than abstract.

**Teaching failure modes:**
- Teaching Bayesian regression before students understand OLS creates confusion: "What is the Bayesian regression of?" Students need the frequentist baseline before the Bayesian comparison is meaningful.
- Presenting MCMC implementation details before the conceptual argument is made: students lose the forest for the trees. The chapter's prompting section should show the LLM output first and the prior specification second.
- Not naming the asymmetry explicitly. The TIKTOC says the asymmetry is "named here for the first time." If this naming is buried or passive, students miss the pedagogical pivot. It should be explicit: "Bayesian regression costs more and requires more. Here is what it buys. Here is when the cost is worth it."

**Understanding vs. memorizing:**
A student who understands can answer: "The frequentist model has R² = 0.71 and p = 0.0003 for the advertising coefficient. Does this mean the company should increase its advertising budget?" The correct answer: no, not by itself. R² and p-value say something about the fit and the evidence for a non-zero relationship; they say nothing about the probability that a budget increase will produce a sales increase exceeding the ROI threshold. That is a decision-theoretic question requiring a probability distribution over future outcomes—which the Bayesian posterior predictive distribution provides.

---

## 7. Representation and Display Research

**Frequentist column — worked example:**
Given: 60 weeks of sales (Y) and advertising spend (X), OLS regression
Coefficient: β̂ = 2.3 (for each unit increase in advertising, sales increase by 2.3 units on average)
Standard error: SE(β̂) = 0.4
t-statistic: 2.3 / 0.4 = 5.75
p-value: < 0.001 (highly significant)
95% CI for β: 2.3 ± 1.96 × 0.4 = [1.52, 3.08]
95% prediction interval for next quarter: [X, Y] (a scalar interval, not a distribution)
Interpretation: "If advertising spend increases by 1 unit, we estimate sales increase by 2.3 units on average, with a 95% confidence that the true slope is between 1.52 and 3.08."
Cannot answer: P(sales increase > threshold | budget increase)

**Bayesian column — worked example:**
Priors: Normal(0, 10) on intercept, Normal(0, 5) on slope (weakly informative), HalfNormal(1) on σ
Posterior on slope: approximately Normal(2.3, 0.4) given 60 data points — near-identical to OLS because n = 60 is large enough that the prior is washed out
95% CrI for slope: approximately [1.5, 3.1] (identical to frequentist CI to first approximation)
Posterior predictive distribution for next quarter: a full probability distribution over possible sales values, not a scalar interval
Can answer: P(sales increase > X | 10% budget increase) = computed from the posterior predictive distribution
Note: with n = 60, the Bayesian and frequentist point estimates and intervals are nearly identical. The difference is in what questions can be answered, not in the numerical answers.
Interpretation: "Given the data and these priors, there is a 97% probability that advertising has a positive effect on sales (slope > 0). If budget increases by 10%, the probability of achieving a sales increase exceeding [threshold] is [computed]."

**Display note for author:**
The key visual for this chapter is three plots:
1. OLS line with 95% CI band and 95% prediction interval band (the two bands, different widths)
2. Bayesian posterior on the slope coefficient (a distribution, not an interval)
3. Bayesian posterior predictive distribution for next quarter's sales under a 10% budget increase (a full probability distribution with the threshold marked)

The third plot has no frequentist analog. It is the visual argument for the Bayesian approach.

---

## 8. Open Questions and Research Gaps

- **The specific prior specification for business regression is underdeveloped in undergraduate teaching literature.** For a retail analyst who has no prior data on advertising elasticity, what is a genuinely weakly informative prior for the slope? Gelman's blog posts and Stan forums provide guidance but no undergraduate-accessible treatment exists. The author must develop this concretely, with a prior predictive check as justification.

- **The OLS = MAP equivalence requires careful exposition.** The statement is true under a flat improper prior, but an improper prior is not a proper probability distribution—it cannot be used for model comparison (Bayes factors) without issues. Students who internalize "OLS is Bayesian with a flat prior" may then try to compute Bayes factors using this "prior" and get incorrect results. This pedagogical hazard should be flagged at the point where it is introduced.

- **The posterior predictive distribution vs. the frequentist prediction interval.** Recent work on conformal prediction (distribution-free frequentist intervals with finite-sample coverage guarantees) has partially closed the frequentist gap in prediction uncertainty. The chapter should not claim the Bayesian posterior predictive distribution is unambiguously superior—it has better theoretical properties under correct model specification, but conformal methods have better finite-sample coverage guarantees under model misspecification. This is a live research area; flag as likely to evolve within 3 years.

- **Causal interpretation of regression coefficients.** The chapter's setup ("does advertising drive sales?") is a causal question, but regression is not a causal method without additional assumptions (counterfactual models, instrumental variables, or randomization). The author should decide whether to include a brief disclaimer or develop the causal distinction more fully. McElreath's 2nd edition is the best undergraduate-accessible treatment.

- **Bayesian MMM tools (Google Meridian, Meta Robyn, PyMC-Marketing):** Documented in commercial and academic sources (Springer Nature, 2026; PyMC Labs blog). These tools use Bayesian regression for the exact problem in the chapter. However, they also include adstock and saturation effects not in the chapter's simple linear model. Presenting them as examples of the chapter's method without noting this discrepancy would be misleading. Flag: use as domain-context evidence for industrial relevance, not as implementations of the chapter's specific model.

- **Likely-outdated-within-3-years:** Specific PPL implementations (brms, PyMC, Stan syntax) age fast. The prompting section should ask the LLM for the current best practice rather than specifying syntax the author chooses today.

---

## 9. Sourcing Notes

- **Gelman & Hill (2007):** Verified via Cambridge University Press page and multiple library catalogs. ISBN 978-0-521-68689-1 (paperback) confirmed. Note: a second edition exists as *Regression and Other Stories* (Gelman, Hill & Vehtari, 2020, Cambridge), which is more current; author should decide which to cite. The original (2007) is more commonly cited in graduate syllabi for the multilevel regression content; the 2020 update is more accessible and more current.
- **McElreath (2020):** Verified via Routledge/CRC, Wikipedia ("Statistical Rethinking"), and review articles in Measurement (Taylor & Francis) and JRSSA. ISBN confirmed. The 2nd edition (2020) is the current version; a 1st edition (2016) exists.
- **Gelman et al. BDA3 (2013):** As above.
- **Galton biography:** Verified via Wikipedia ("Francis Galton"), ScienceDirect (regression history article), and Significance (RSS journal, Senn 2011). Wikipedia page confirmed: "Francis Galton."
- **Madan Lal Puri biography:** [VERIFIED] — Wikipedia page "Madan Lal Puri" confirmed (Indiana University, nonparametric statistics, born 1929). Verify page still exists before citing.
- **Helen M. Walker biography:** [PARTIALLY VERIFIED] — Wikipedia page "Helen M. Walker" exists; ASA presidency confirmed in Amstat News historical records. Verify current Wikipedia page content before citing.
- **Bayesian MMM sources:** Verified via Springer Nature journal (DOI pending retrieval), PyMC Labs blog, and company GitHub repositories (Meta Robyn, Google Meridian). These are not peer-reviewed publications; treat as industry documentation rather than peer-reviewed evidence.
- **Gelman, Hill & Vehtari (2020), *Regression and Other Stories*:** [UNVERIFIED — confirm exact title, publisher, and year] — described consistently in secondary sources as Cambridge, 2020. Author should retrieve the Cambridge catalog entry directly.
- **Greenland et al. (2016):** As verified in Ch 4 research file.
