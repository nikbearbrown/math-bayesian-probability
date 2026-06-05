# Research: Chapter 10 — Time and Sequence
## Bayesian Probability
**Chapter one-line:** Time series analysis and sequential updating — where the Bayesian approach is most intuitive, because the posterior from today is the prior for tomorrow.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational Papers and Texts

**Box, G. E. P. & Jenkins, G. M. (1970). Time Series Analysis: Forecasting and Control. Holden-Day, San Francisco. (Revised edition 1976.)**
The original ARIMA framework — the frequentist backbone of the chapter's first solution. Box-Jenkins methodology: identify (ACF/PACF), estimate, check, forecast. Still the most widely implemented time-series approach in econometrics, epidemiology, and operations research. Fifth edition (Box, Jenkins, Reinsel, & Ljung) published 2015 by Wiley; the methodology is unchanged. VERIFIED via multiple academic references and Wiley catalog.

**Kalman, R. E. (1960). "A New Approach to Linear Filtering and Prediction Problems." Transactions of the ASME Journal of Basic Engineering, 82(D), 35–45. doi:10.1115/1.3662552.**
The foundational paper for sequential Bayesian updating in dynamic systems. The Kalman filter is Bayesian updating for linear Gaussian state-space models: the posterior at each time step is Gaussian, and the posterior becomes the prior for the next step. This IS the chapter's "today's posterior is tomorrow's prior" in algorithmic form. All modern structural time series methods (Harvey 1989, Scott & Varian 2014) are extensions. VERIFIED via ASME Digital Collection, UNC "Seminal Kalman Filter Paper" page, multiple reference databases.

**Harvey, A. C. (1989). Forecasting, Structural Time Series Models and the Kalman Filter. Cambridge University Press.**
The bridge text: takes Kalman's recursive filter and frames it as a statistical modeling tool (structural components: trend, seasonal, irregular). Harvey's state-space formulation makes Bayesian structural time series models tractable and interpretable. The chapter's "local level + trend" Bayesian model is Harvey's framework. VERIFIED via Cambridge University Press catalog, Wiley Online Library review, ResearchGate PDF.

**Scott, S. L. & Varian, H. R. (2014). "Predicting the Present with Bayesian Structural Time Series." International Journal of Mathematical Modelling and Numerical Optimisation, 5(1/2), 4–23. doi:10.1504/IJMMNO.2014.059942.**
The applied demonstration that Bayesian structural time series with Google search-query regressors can nowcast weekly initial unemployment claims (US Federal Reserve data). Combines a local linear trend model with spike-and-slab variable selection for a high-dimensional regressor set. This is the chapter's closest empirical anchor: inventory/demand forecasting with Bayesian updating. Authors are from Google; paper is accessible; the `bsts` R package implements the model. VERIFIED via Inderscience, Semantic Scholar, ResearchGate, Scott's Berkeley page.

**Brodersen, K. H., Gallusser, F., Koehler, J., Remy, N., & Scott, S. L. (2015). "Inferring Causal Impact Using Bayesian Structural Time-Series Models." Annals of Applied Statistics, 9(1), 247–274. doi:10.1214/14-AOAS788.**
The CausalImpact paper: uses BSTS to construct a counterfactual and measure whether an intervention (e.g., a marketing campaign) caused a change in a time series. The `CausalImpact` R package at google/CausalImpact is open source. Shows the direct decision-application of Bayesian sequential updating: not just "what will demand be?" but "did our action cause demand to change?" VERIFIED via Project Euclid, arXiv 1506.00356, SCIRP references.

### Key Empirical Cases

**Case 1 — Weekly US Initial Unemployment Insurance Claims (Scott & Varian 2014).**
Documented, published. Federal Reserve economic data (FRED, publicly available). Bayesian structural time series with Google Trends regressors outperforms ARIMA on short-horizon nowcasting. The dataset is available via the `bsts` R package. Reader-accessible; ties directly to the book's BLS data thread.

**Case 2 — Inventory/demand forecasting in operations research (documented structure; specific company case studies are often proprietary).**
HYPOTHETICAL: The chapter's inventory manager scenario is a stylized version of the demand-forecasting problem that companies like Amazon, Walmart, and IKEA solve with state-space models. The structural form (local level + trend + seasonal) is standard and well-documented in Harvey (1989) and Hyndman & Athanasopoulos (2021, *Forecasting: Principles and Practice*, 3rd ed., free online). The specific "52 weeks of weekly demand" problem in TIKTOC is a teaching example, not a documented case — label as illustrative.

**Case 3 — Adaptive clinical trial interim analyses (Bayesian sequential updating in medicine).**
Documented methodology. A 2024 systematic review (BMC Medical Research Methodology) found that ~24% of adaptive clinical trials (2010–2020) used Bayesian methods. The core of these designs is sequential Bayesian updating: after each interim analysis, the posterior on treatment effect becomes the prior for the next stage. The I-SPY 2 breast cancer trial (multi-arm adaptive platform, Bayesian design) is a real, documented example — though specific posterior calculations are not publicly available in reader-friendly form. The methodology is verifiable; the specific numbers are not. Label as documented methodology with an accessible reference pointer.

---

## 2. The Core Concept — State of the Field

### What Is Settled

- **ARIMA remains the dominant frequentist time-series tool** in economics, epidemiology, and operations research. Its theoretical properties (stationarity, identification, maximum-likelihood estimation) are well-understood. Box-Jenkins methodology is taught in essentially every econometrics course.
- **The Kalman filter is Bayesian updating in linear Gaussian state-space models**: this is a mathematical fact, not a contested claim. The connection between the recursive filter and Bayesian inference is exact when observations and state transitions are Gaussian.
- **Bayesian structural time series (BSTS)** as implemented in the `bsts` R package (Scott & Varian 2014) and Stan is a mature, production-level tool. The Google CausalImpact package has many thousands of users.
- **For stationary series with sufficient data**, ARIMA and BSTS produce similar point forecasts. The Bayesian approach adds a full predictive distribution, sequential updating structure, and the ability to incorporate priors on seasonal or trend components.

### What Is Disputed

- **ARIMA vs. state-space models for forecasting accuracy**: Large-scale forecast competitions (M4, M5) generally find that simple methods (including ETS/exponential smoothing, which is a state-space model) outperform complex Bayesian models on aggregate accuracy. The Bayesian advantage is in decision support (P(demand > threshold)) and interpretability of components, not necessarily raw RMSE. The author should not overclaim forecasting accuracy advantages for BSTS.
- **Prior specification for trend and seasonal components**: There is no consensus on weakly informative defaults for structural time series. The literature has several competing recommendations (half-normal on signal-to-noise ratio, diffuse priors, informative priors from pilot data). Flag this as a genuine specification challenge for students.
- **Deep learning vs. statistical models for time series (2020–2026)**: Transformer-based models (PatchTST, TimeGPT, Chronos from Amazon) now match or exceed ARIMA and BSTS on many benchmarks. This chapter should not present BSTS as the accuracy frontier — present it as the Bayesian decision-support tool, which is a different claim. [AGING FLAG: this landscape is changing rapidly; the specific model comparisons cited here may be outdated within 2–3 years.]

### What Has Changed Recently (Last 5 Years)

- **Prophet (Facebook/Meta, Taylor & Letham 2018, JASA)**: Widely-used BSTS-adjacent forecasting tool designed for business time series with strong seasonality. Accessible to non-statisticians; uses Stan for Bayesian estimation. Relevant as a real-world deployment example.
- **Probabilistic forecasting as the mainstream**: The M5 competition (2020, Makridakis et al.) explicitly evaluated probabilistic forecasts, not just point forecasts. This shift in the field directly supports the chapter's argument that predictive distributions matter for decisions.
- **LLM-based time series forecasting (2023–2026)**: Large foundation models fine-tuned on time series are emerging. Chronos (Amazon, 2024), TimeGPT (Nixtla). These are not Bayesian and do not produce calibrated uncertainty — they generate point forecasts or quantile estimates. The chapter's Bayesian approach remains differentiated on decision-theoretic grounds. [AGING FLAG: this landscape is 2–3 years from significant change.]

---

## 3. Application Domain Examples

**1. Weekly unemployment insurance claims (Scott & Varian 2014).**
Documented, published, data available via FRED and `bsts` package. BLS-adjacent; ties directly to the book's companion data. Bayesian updating on weekly data with Google search regressors.

**2. Inventory demand forecasting (BLS/operations context).**
The TIKTOC scenario. Illustrative but structurally documented. The reader can use BLS employment-count time series from the companion website as a stand-in (Ch. 10 Exercise 1 explicitly asks for this). Label the specific "inventory manager" narrative as illustrative; the data structure is real.

**3. Epidemiological nowcasting (COVID-19, Bayesian sequential updating, documented).**
During the COVID-19 pandemic, real-time Bayesian state-space models were used to estimate the effective reproduction number R_t. The EpiNow2 R package (Abbott et al. 2020, Wellcome Open Research) implemented sequential Bayesian updating explicitly: posterior R_t at each time step became the prior for the next. This is a reader-accessible, high-stakes, documented example of exactly the chapter's mechanism. VERIFIED at a methodology level; specific R_t estimates and their decisions are documented in preprint and published literature.

**4. Sports analytics: in-game win probability (documented).**
State-space models for updating win probability in real time — baseball, basketball, football — are widely used and documented in the sports analytics literature. Bayesian updating is the natural framework: prior on win probability updated play by play. Fangraphs (baseball) and ESPN publish in-game probability curves. This is not the chapter's primary domain but is reader-accessible and anchors the "today's posterior is tomorrow's prior" intuition viscerally.

**5. Central bank forecasting (Federal Reserve, Bayesian VAR).**
The Fed's and ECB's BVAR (Bayesian vector autoregression) models are publicly documented in academic papers (Sims 1980 for VAR; Litterman 1986 for Bayesian VAR). Sequential updating of macroeconomic forecasts is the Fed's actual methodology. This is a high-stakes documented example; specific model parameters are published in working papers. Note that BVAR is a multivariate extension beyond the chapter's scope — use as a pointer, not a worked example.

---

## 4. The Book's Thesis Connection

Chapter 10's thesis function is different from all prior chapters: it is where Bayesian inference is *most natural*, because the sequential structure makes the "prior becomes posterior becomes next prior" cycle visible to the reader in real time. The chapter does not need to strain to show why the Bayesian approach is valuable — the updating story is self-evident.

The thesis connection therefore shifts: the chapter must still explain **why anyone uses ARIMA**. The honest answer is that ARIMA is faster, simpler, widely implemented, and for stationary series with adequate data, produces competitive forecasts without the specification burden of choosing priors on trend and seasonal components. The forecasting literature (M4, M5 competitions) consistently finds that simple methods outperform complex Bayesian ones on raw accuracy — a fact the chapter should acknowledge rather than suppress.

**What a self-directed student must supply that an algorithm cannot:** Deciding whether the decision they face requires a full predictive distribution (probability of stocking out, probability of recession) or a point forecast (rough planning estimate). ARIMA produces a point forecast with a growing prediction interval; BSTS produces a calibrated posterior predictive. The student must know which type of output their decision requires before choosing a model. An LLM will fit whichever model is asked for; the human must ask the right question.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Rudolf Emil Kálmán (1930–2016)**
Wikipedia page: "Rudolf E. Kálmán"
Hungarian-American electrical engineer and mathematician. Born Budapest; emigrated to US 1943; PhD Columbia 1957. Invented the Kalman filter (1960) while at the Research Institute for Advanced Study in Baltimore. The filter is used in GPS, the Apollo guidance computer, smartphone navigation, and essentially every modern sequential estimation system. Won the National Medal of Science (2009, presented by Obama). Male, Hungarian-American, engineer by training (not statistician), 20th century. Lesser-known to statistics students despite ubiquity. Anchor prompt: "Explain Rudolf Kálmán's 1960 filter in plain language: what does it mean to say that a Kalman filter is doing Bayesian updating at each time step?"

**Figure 2: Norbert Wiener (1894–1964)**
Wikipedia page: "Norbert Wiener"
American mathematician (MIT). Developed the Wiener filter (1949, *Extrapolation, Interpolation, and Smoothing of Stationary Time Series*) — the frequentist predecessor to the Kalman filter, solving the same optimal linear filtering problem in the frequency domain. Coined the word "cybernetics." Male, American, Jewish heritage, early 20th century. Connects the chapter to the broader history of signal processing and sequential estimation. Lesser-known as a statistician specifically. Anchor prompt: "What problem was Norbert Wiener trying to solve with his 1949 filter, and how does the Kalman filter improve on it?"
Note: This is the first non-standard figure — Wiener is famous in engineering but not as well-known to statistics students.

**Figure 3: Gwilym Jenkins (1933–1982)**
Wikipedia page: "Gwilym Jenkins"
Welsh statistician; co-developed the Box-Jenkins ARIMA methodology. Male, Welsh (British), statistician, mid-20th century. Died young (at 48); the ARIMA framework he co-authored with George Box became the dominant time-series method for decades. His contribution is often overshadowed by Box's (Box is the name that survives in "Box-Jenkins" but also "Box-Cox," "Box plot," etc.). Jenkins represents the "frequentist workhorse" of the chapter and deserves named credit. Relatively obscure as an individual despite the methodology's ubiquity. Anchor prompt: "What did Gwilym Jenkins contribute to the Box-Jenkins ARIMA methodology, and why do we still teach it 50 years later?"

**Diversity note:** All three candidates are male. For the time-series field this is an accurate reflection of the founding generation; the author should be transparent about this in the chapter or add a contemporary female time-series practitioner to the body text. Suggestions: Esther Ruiz (Universidad Carlos III de Madrid, structural time-series models), Francesca Chiaromonte (Penn State/Sant'Anna, high-dimensional time-series), or Hyndman's co-author Yanfei Kang (Beihang University, 2021 IJF paper on time-series feature-based forecasting). These are not Wayback Machine candidates (still active) but merit named citation in the applied examples.

---

## 6. Pedagogical Delivery Research

**Prior knowledge required and common entry misconceptions:**
- Students arriving from Chapter 9 have been introduced to the idea that parameters can have distributions. Chapter 10 extends this to a *sequence* of parameters (state at time t). The conceptual challenge is the hidden state: students must understand that the "true demand level" is not directly observed, only noisy realizations of it.
- The most common misconception about ARIMA: students treat it as a "black box pattern-matcher" rather than a probabilistic model. The ACF/PACF identification step is often memorized without understanding what autocorrelation means. The chapter should motivate ARIMA from first principles (correlated errors, not magic lags).
- Students often confuse "the prediction interval gets wider over time" (ARIMA's growing uncertainty) with "we know less because the model is broken." The correct interpretation — genuine uncertainty about a nonstationary process — needs emphasis.
- For Bayesian sequential updating: students typically understand Bayes' theorem for a fixed dataset. Extending to "now apply it sequentially" is conceptually natural but the notation jump (filtering, smoothing) is steep. The chapter should separate the concept from the notation.

**Instructional sequences that work:**
- Start with a coin-flipping sequential update (Chapter 3's Beta-Binomial model, extended in time) before introducing time series. Show explicitly that the posterior after 10 flips becomes the prior for flip 11. This is the pure Bayesian updating story with no time-series complexity.
- Then transition: "inventory demand is just like coin flips, except the underlying probability changes over time." This motivates the hidden state.
- The ARIMA-first structure in TIKTOC is pedagogically sound: students need the frequentist benchmark before Bayesian updating is introduced as an improvement.
- The "narrowing forecast" visualization (posterior predictive interval shrinking week by week as new data arrives) is the most effective teaching tool for this chapter. Implement as a D3 animation or a simple sequential plot.

**Teaching failure modes:**
- Spending too much time on ARIMA model selection (ACF/PACF interpretation, unit root tests, information criteria for order selection) at the expense of the Bayesian story. ARIMA selection can be delegated to the LLM with verification; the chapter should not become an ARIMA manual.
- Conflating the Kalman filter (a recursive algorithm) with the BSTS modeling framework (a choice of structural components). Students should understand that the Kalman filter is the *algorithm* that solves the BSTS model; the structural model is the *specification*.
- The "sequential updating = online learning" frame is seductive but imprecise. Bayesian sequential updating is exact for Gaussian state-space models; it is approximate (particle filters, variational inference) for nonlinear or non-Gaussian models. The chapter should not overstate the generality.

**Understanding vs. memorizing:**
- Core understanding: "Every Bayesian analysis is implicitly sequential — we could always have stopped earlier and used the posterior as a prior for new data. Time series just makes this explicit." Students who understand this can transfer the concept to any domain.

---

## 7. Representation and Display Research

**Frequentist vs. Bayesian side-by-side for Chapter 10:**

**Frequentist (ARIMA):**
```
Method: ARIMA(1,1,1) — selected by auto.arima or AIC
Point forecast (week 53): 10,840 units
95% Prediction Interval:  [8,200, 14,600]
Interval width: 6,400 units

What the manager can conclude:
- Expected demand is approximately 10,840 units
- The interval will likely contain next week's actual demand
  (frequentist guarantee about the procedure, not this interval)
- P(demand > 10,000)?  Not directly available from this output
```

**Bayesian Structural Time Series (BSTS):**
```
Model: Local level + linear trend
Prior: N(0, 100) on trend slope; Half-N(0, 10) on signal-to-noise ratio
Posterior predictive (week 53):
  Mean:   10,780 units
  SD:     1,560 units
  95% CrI: [7,720, 13,840]
  P(demand > 10,000 | data) = 0.69
  P(demand > 12,000 | data) = 0.23

What the manager can conclude:
- She can directly compute the probability of exceeding the reorder threshold
- Each subsequent week's data will update the posterior predictively
```

**Display recommendation:** The "narrowing funnel" plot is the chapter's hero visual: show the BSTS posterior predictive distribution at week 10, week 26, week 40, and week 52, with the fan narrowing and the center line tracking actual demand. Implement as a D3 animation per the companion website specification.

---

## 8. Open Questions and Research Gaps

1. **Forecasting accuracy of BSTS vs. ARIMA vs. neural networks**: The M4 and M5 competitions are the best empirical evidence, but neither directly evaluated BSTS on short, seasonal demand series like the inventory example. The claim "BSTS produces better decisions, not necessarily better forecasts" needs careful framing. Do not overclaim.

2. **Prior specification for structural components**: No peer-reviewed guidance for introductory-level defaults on trend priors and seasonal priors in BSTS. Hyndman's ETS framework has flat-rate defaults; BSTS requires manual specification. This is a genuine pedagogical gap.

3. **LLM-generated ARIMA code**: Auto-ARIMA (forecast::auto.arima in R, pmdarima in Python) is well-understood and LLMs generate it reliably. LLM-generated BSTS code is more variable — the `bsts` R package is less commonly in LLM training data than ARIMA. The prompting section should acknowledge this asymmetry. [AGING FLAG: likely to improve within 2 years as `bsts` and Stan usage grows in LLM training corpora.]

4. **Real-time Bayesian updating for practitioners**: The gap between "sequential updating is theoretically natural" and "here is how to implement real-time sequential updating in practice" is large. Most practitioners re-fit models on all data rather than truly updating sequentially. The chapter should be honest that the sequential-updating workflow is conceptually clean but computationally non-trivial to implement in production.

5. **BLS data seasonal adjustment**: BLS employment data is pre-seasonally adjusted using X-13ARIMA-SEATS (a frequentist method). Students using BLS data from the companion website may not realize the series is already seasonally adjusted. The chapter or companion dataset documentation should flag this.

---

## 9. Sourcing Notes

- **Box & Jenkins 1970**: Confirmed via SCIRP, ResearchGate; original Holden-Day edition confirmed. Current standard edition is 5th (2015, Wiley; Box, Jenkins, Reinsel, Ljung). Both are citable; the original 1970 edition is the historical reference; the 5th edition is what students will actually access.
- **Kalman 1960**: Confirmed via ASME Digital Collection (doi:10.1115/1.3662552); UNC page hosts the original PDF. Open access via ASME for historical papers.
- **Harvey 1989**: Confirmed via Cambridge University Press catalog, Wiley Online Library review. Not open access; available through university libraries.
- **Scott & Varian 2014**: Confirmed via Inderscience (doi:10.1504/IJMMNO.2014.059942), ResearchGate, Semantic Scholar. Preprint available at Hal Varian's Berkeley page.
- **Brodersen et al. 2015**: Confirmed via Project Euclid (doi:10.1214/14-AOAS788) and arXiv 1506.00356. Open access.
- **COVID-19 EpiNow2**: Abbott et al. (2020). "EpiNow2: Estimate Real-Time Case Counts and Time-Varying Epidemiological Parameters." Wellcome Open Research. Preprint and published versions available; recommended for verification before formal citation.
- **Wiener 1949**: Full citation: Wiener, N. (1949). *Extrapolation, Interpolation, and Smoothing of Stationary Time Series*. MIT Press / Wiley. Verifiable via Google Books and MIT Press catalog.
- **Gwilym Jenkins Wikipedia**: Confirmed "Gwilym Jenkins" page exists on Wikipedia. Born Gwilym Meirion Jenkins, 1933 in Dewsbury, Yorkshire (not Wales as stated above — verify exact birthplace). Died 1982. Correction: sources variously describe him as "English" or note Yorkshire birth. Author should verify nationality description from Wikipedia before citing.
- **Deep learning / foundation model claims (Chronos, TimeGPT)**: These are 2023–2024 preprints/products; verify current status before publication as the field moves fast. Mark as [AGING — verify before print].
