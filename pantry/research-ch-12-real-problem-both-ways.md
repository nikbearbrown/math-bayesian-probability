# Research: Chapter 12 — A Real Problem, Both Ways
## Bayesian Probability
**Chapter one-line:** One real dataset, one real question, both frameworks deployed completely — the deliverable is not which approach won but a written comparison that demonstrates statistical judgment.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**BLS Occupational Employment and Wage Statistics (OEWS) Program Documentation**
U.S. Bureau of Labor Statistics, annual, bls.gov/oes/
The authoritative technical documentation for the OEWS program. Describes survey methodology (rolling 6-panel design, ~1.1 million establishments, two semiannual panels per year), occupational coding (SOC system, ~830 occupations), and the structure of the public-use flat files. Directly governs how to interpret and prepare OEWS data for student analysis. Essential reading before assigning any OEWS-based dataset exercise.

**O*NET 30.3 Database Technical Documentation**
O*NET Resource Center (U.S. Department of Labor), onetcenter.org/database.html, current release 30.3 (2024–25)
Describes all content model files: Task Statements, Work Activities, Work Context (including the "Degree of Automation" scale, descriptor code 4.C.3.b.2), Skills, Knowledge, Interests. Database is distributed as flat text/CSV files freely downloadable from onetcenter.org. The Work Context file and Task Statements file are the two most useful for capstone analysis. Covers ~900 O*NET-SOC occupations. Students need the data dictionary to interpret scale anchors.

**Frey, C.B. & Osborne, M.A. (2013/2017). "The Future of Employment: How Susceptible Are Jobs to Computerisation?" Working paper, Oxford Martin School; published in *Technological Forecasting and Social Change*, 114, 254–280.**
The foundational automation-probability dataset: Gaussian process classifier applied to 702 O*NET occupations, each scored 0–1 on probability of computerization. The full paper PDF is publicly available at oxfordmartin.ox.ac.uk/downloads/academic/The_Future_of_Employment.pdf. The appendix contains the per-occupation probability scores. The Mendeley Data repository (data.mendeley.com/datasets/czbvhmzwm3/1) hosts a related dataset of "Probability of Automation of Occupations 2036." Direct CSV of the original 702-occupation table: the main paper appendix is the definitive source; several GitHub repositories have reformatted it (search GitHub for "Frey Osborne automation data"). This dataset is central to the Ch 11–12 O*NET thread and is the single best dataset for a Bayesian vs. frequentist comparison on automation exposure because it has both a continuous outcome (probability score) and a categorical one (high/medium/low risk).
*Aging flag: The specific numeric predictions are widely critiqued and now dated; use as a classification/regression exercise, not as a policy claim.*

**Gelman, A., Vehtari, A., Simpson, D., et al. (2020). "Bayesian Workflow." arXiv:2011.01808.**
The most comprehensive reference for the full Bayesian analysis lifecycle: prior predictive checks, iterative model building, posterior predictive checks, model comparison. Not a textbook; a practical guide to what "doing Bayesian analysis properly" looks like end-to-end. Chapter 12 students implicitly follow a simplified version of this workflow. The six-question comparison scaffold in the chapter maps onto sections of this paper. Freely available at arxiv.org/abs/2011.01808.

**Wasserstein, R.L. & Lazar, N.A. (2016). "The ASA's Statement on p-Values: Context, Process, and Purpose." *The American Statistician*, 70(2), 129–133. DOI: 10.1080/00031305.2016.1154108**
The ASA's first-ever position statement on a statistical topic. Directly relevant to Ch 12 as the authoritative description of what p-values do and do not mean — which students must articulate in their comparative write-up. Freely available via Taylor & Francis.

### Key empirical cases

**Case 1 (documented): Wage distribution analysis using OEWS national data.**
BLS published a May 2024 OEWS national flat file covering ~830 occupations with median, mean, and percentile wages (10th, 25th, 75th, 90th). Students can ask: (a) Does the wage distribution within a major occupational group (e.g., "Healthcare Support") follow a log-normal distribution? (frequentist goodness-of-fit test vs. Bayesian posterior on distribution parameters); (b) Is the mean wage for a selected occupation cluster significantly different from the national all-occupations median? (frequentist t-test vs. Bayesian posterior on the difference). Dataset accessible at bls.gov/oes/2024/may/featured_data.htm. Direct flat file downloads from bls.gov/oes/tables.htm.

**Case 2 (documented): Automation exposure classification using O*NET Work Context + Frey-Osborne scores.**
Students can merge the O*NET Work Context "Degree of Automation" scale (4.C.3.b.2, available for all ~900 occupations from onetcenter.org) with the Frey-Osborne automation probability appendix. Questions: (a) Does the O*NET automation scale score predict Frey-Osborne high-risk classification? (frequentist logistic regression vs. Bayesian logistic regression with prior on slope); (b) What is the posterior probability that an occupation scoring above the median on the O*NET automation scale has a Frey-Osborne risk score above 0.5? Both questions have clean frequentist and Bayesian solutions.

**Case 3 (documented): Educational attainment and earnings using BLS CPS-derived data.**
BLS publishes annual "Education pays" data from the Current Population Survey: median weekly earnings and unemployment rates by eight education levels, age 25+. Available at bls.gov/careeroutlook/2025/data-on-display/education-pays.htm (2024 data). Questions: (a) Is there a statistically significant linear relationship between education level and median weekly earnings? (frequentist OLS vs. Bayesian linear regression with weakly informative prior on slope); (b) What is the posterior probability that a college graduate earns more than $1,500/week? Both are tractable with data that fits on a single page.

---

## 2. The Core Concept — State of the Field

### What is settled

The basic mechanics of both frameworks are well-established and not controversial at the textbook level. For real data analysis: (1) frequentist OLS and Bayesian regression with flat priors produce identical point estimates — this is textbook (e.g., Gelman & Hill 2007, *Data Analysis Using Regression and Multilevel/Hierarchical Models*); (2) the confidence interval / credible interval distinction is clearly documented in the ASA statement (Wasserstein & Lazar 2016) and in Bayarri & Berger (2004); (3) the Gaussian process classifier methodology underlying Frey-Osborne is documented in their paper and is replicable.

### What is disputed

**Whether Frey-Osborne scores are valid measures of automation risk at all.** Multiple papers have argued the methodology inflates risk: Arntz, Gregory & Zierahn (2016, OECD) found much lower automation risk when analyzing task heterogeneity *within* occupations rather than treating occupations as homogeneous; Dengler & Matthes (2018) replicated the method for Germany with markedly different results. The data is still useful as a *pedagogical exercise in statistical methodology* — the point is not whether the scores are correct, but what frequentist and Bayesian methods reveal about the distribution of those scores and their predictors.

**The "right" prior for wage data.** Labor economists generally use log-normal priors for wage distributions; some prefer Pareto tail models for high earners. For a capstone exercise, either weakly informative or uniform priors are acceptable, but the choice should be documented and defended.

### What has changed recently (last 5 years)

The O*NET database now releases updates more frequently (currently at version 30.3, with releases approximately 3 times per year), incorporating new task-level AI exposure measures. A 2024 Upjohn Research report (research.upjohn.org) explicitly applies O*NET Work Activities to derive AI exposure scores using a methodology different from Frey-Osborne, offering a more current comparison dataset. The OEWS program renamed itself from "Occupational Employment Statistics (OES)" to "Occupational Employment and Wage Statistics (OEWS)" in 2021; older citations use OES. The 2024–2034 Employment Projections released by BLS (August 2024, bls.gov/emp/) are now the current projection cycle, superseding 2023–2033.

---

## 3. Application Domain Examples — Vetted Dataset List

Each entry: dataset name, URL, the 2–3 pre-specified analysis questions it supports, and why it works both ways. All verified as publicly accessible as of June 2026.

---

**Dataset A: OEWS May 2024 National Occupational Employment and Wage Estimates**
- **URL:** https://www.bls.gov/oes/2024/may/featured_data.htm (overview); flat files at https://www.bls.gov/oes/tables.htm
- **Format:** Excel/CSV downloadable flat file; ~830 occupational rows; columns include employment (thousands), mean wage, median wage, wage percentiles (10th–90th), SOC code, occupation title
- **Access:** Freely public; no registration required
- **Pre-specified questions:**
  1. *Distribution question:* Within Healthcare Support occupations (SOC major group 31-0000), is the median hourly wage distribution consistent with a log-normal model? Frequentist approach: Kolmogorov-Smirnov or Shapiro-Wilk test on log(wages). Bayesian approach: posterior on log-normal parameters (μ, σ); posterior predictive check against observed distribution.
  2. *Comparison question:* Is the mean wage for Computer and Mathematical occupations (SOC 15-0000) different from the national cross-occupation median? Frequentist: one-sample t-test. Bayesian: posterior on the difference between group mean and population median, with weakly informative normal prior on the mean.
- **Why it works both ways:** The frequentist test answers "is this result surprising if the null is true?" The Bayesian approach answers "what is the probability the true mean is above/below a threshold?" — exactly the thesis contrast. The data is clean, pre-aggregated, domain-agnostic, and requires no data wrangling beyond filtering by SOC major group.
- **Tractability:** One work session easily covers both questions. Students can complete data prep with a single LLM-prompted import.

---

**Dataset B: O*NET 30.3 Work Context — Degree of Automation (Scale 4.C.3.b.2)**
- **URL:** https://www.onetcenter.org/database.html (download "Work Context" file from the database ZIP); individual descriptor page at https://www.onetonline.org/find/descriptor/result/4.C.3.b.2
- **Format:** CSV flat file from the database download; columns include O*NET-SOC code, occupation title, element ID (4.C.3.b.2 for "Degree of Automation"), scale ID (IM = Importance, CT = Context), data value (1–5 scale), standard error, sample size
- **Access:** Freely public; database download at onetcenter.org; no registration required
- **Pre-specified questions:**
  1. *Correlation question:* Does the O*NET "Degree of Automation" score correlate with the Frey-Osborne automation probability score (from the paper appendix, ~702 occupations matched by SOC code)? Frequentist: Pearson r or Spearman rank correlation with significance test. Bayesian: posterior on correlation coefficient ρ using a Beta or LKJ prior.
  2. *Classification question:* Does a high "Degree of Automation" score (above the scale midpoint of 3) predict high Frey-Osborne risk (probability > 0.5)? Frequentist: logistic regression, coefficient significance test, ROC/AUC. Bayesian: logistic regression with weakly informative normal prior on slope; posterior on P(high-risk | automation score).
- **Why it works both ways:** The logistic regression comparison is the cleanest possible demonstration of the Ch 11 thread applied to real data; the frequentist model gives significance and odds ratios, the Bayesian model gives the posterior probability that automation score is a meaningful predictor — two different questions, same data.
- **Tractability:** Matching O*NET to Frey-Osborne requires an SOC-code merge (manageable with LLM help in one session). Both questions are answerable with the merged dataset.
- **Dataset merge caveat:** O*NET uses O*NET-SOC codes (8-digit); Frey-Osborne uses the older 2010 SOC system (6-digit). A crosswalk file is available from onetcenter.org/crosswalks.html. Note this in the student data-prep prompt.

---

**Dataset C: BLS Education Pays 2024 — Earnings and Unemployment by Educational Attainment**
- **URL:** https://www.bls.gov/careeroutlook/2025/data-on-display/education-pays.htm (2024 data); underlying CPS data table at https://www.bls.gov/emp/chart-unemployment-earnings-education.htm
- **Format:** Small table (8 rows × education level; columns: median weekly earnings, unemployment rate); data derives from the Current Population Survey
- **Access:** Freely public; directly readable from the BLS website; downloadable as chart data
- **Pre-specified questions:**
  1. *Regression question:* Is there a linear relationship between years of education implied by degree level (mapped to approximate years: e.g., less than high school ≈ 10, bachelor's ≈ 16, doctoral ≈ 22) and median weekly earnings? Frequentist: OLS regression, coefficient significance test, R². Bayesian: Bayesian linear regression, posterior on slope and intercept, posterior predictive interval for a given education level.
  2. *Threshold question:* What is the probability that a worker with a bachelor's degree earns more than $1,500/week? Frequentist: cannot directly compute this probability; can construct a prediction interval and note the limitation. Bayesian: directly compute P(earnings > $1,500 | bachelor's degree) from posterior predictive distribution.
- **Why it works both ways:** The threshold question is the sharpest single demonstration of the frequentist/Bayesian contrast in the entire dataset library — the frequentist approach structurally cannot answer the question the student wants answered. Ideal for students in any major; the domain is immediately relatable.
- **Tractability:** The dataset has only 8 data points — unusually small, which makes the prior choice consequential and forces the student to confront and defend it. This is pedagogically valuable, not a limitation.
- **Note:** The small N means confidence intervals are wide and the normal approximation may be questionable. This is an instructive feature: students using the Bayesian approach with an informative prior (from prior years' data, also on the BLS site) can demonstrate shrinkage.

---

**Dataset D: BLS Employment Projections 2024–2034 — Occupational Growth Rates**
- **URL:** https://www.bls.gov/emp/tables/occupational-projections-and-characteristics.htm; interactive at https://data.bls.gov/projections/occupationProj; downloadable files at https://www.bls.gov/emp/data/occupational-data.htm
- **Format:** CSV/Excel, ~830 occupations; columns include base employment (2024), projected employment (2034), change (thousands and percent), median annual wage, typical education entry requirement
- **Access:** Freely public; no registration required; released August 2024
- **Pre-specified questions:**
  1. *Comparison question:* Do occupations requiring a bachelor's degree or higher show significantly different projected growth rates than those requiring less than a bachelor's? Frequentist: two-sample t-test on percent change. Bayesian: Bayesian two-group comparison, posterior on the difference in mean growth rates, posterior P(bachelor's-required group grows faster).
  2. *Regression question:* Does current median wage predict projected growth rate? Frequentist: OLS regression with significance test on slope. Bayesian: Bayesian linear regression with weakly informative prior; posterior predictive interval for a high-wage occupation.
- **Why it works both ways:** The two-group comparison is the direct Ch 4 structure applied to real data; students have already seen the machinery. Adding the "actual growth data vs. prior knowledge" angle makes the prior-choice discussion concrete — if a student knows healthcare is growing, what prior should they place on healthcare occupations' growth rate?
- **Tractability:** Data is pre-cleaned and SOC-organized; one filtering step by education requirement column completes data prep. Easily manageable in one session.

---

**Dataset E (Optional / Advanced): BLS OEWS Metropolitan Area Wage Estimates — Regional Variation**
- **URL:** https://www.bls.gov/oes/current/oessrcma.htm (current MSA-level estimates)
- **Format:** One file per metro area OR a combined cross-MSA file; columns as in Dataset A
- **Access:** Freely public
- **Pre-specified questions:**
  1. *Hierarchical question:* Do software developer wages vary significantly across metropolitan areas? This is the Ch 9 question in real data form: complete pooling vs. no pooling vs. partial pooling. The Bayesian hierarchical model is more appropriate here than for the other datasets; the frequentist approach (metro-by-metro t-tests or one-way ANOVA) misses the partial-pooling insight.
  2. *Distribution question:* Within a single metro area (student's choice), is the wage distribution for a selected occupation consistent with the national distribution for that occupation?
- **Why it works both ways:** Best suited for students who have engaged strongly with Ch 9 and want to revisit the hierarchical thread in a capstone setting.
- **Tractability caveat:** This dataset is larger and messier than A–D; recommend as an advanced option only. Data wrangling is non-trivial. Not recommended for students who struggled with data prep in earlier chapters.

---

## 4. The Book's Thesis Connection

Chapter 12 is not an argument about methodology — it *is* the thesis enacted. Every prior chapter has shown the two frameworks applied to a textbook problem. Here, the student applies them to a dataset they chose, answering questions they were given, writing a comparison that requires them to supply what no algorithm can: judgment about which framework better serves the analysis goal given what the decision-maker actually needs.

The six-question scaffold makes this concrete. Questions 1–4 are retrievable from the analysis outputs. Questions 5 and 6 require judgment:
- Question 5 ("Which approach better serves the analysis goal, and why?") requires the student to state what the decision-maker needs — a probability statement, a significance test, a point estimate — and match that to the framework. An algorithm asked this question will produce a generic answer; a student who has worked through Chapters 1–11 can give a specific one.
- Question 6 ("What would change your conclusion?") requires epistemic honesty about the analysis's limits — about sample size, prior choice, model assumptions — that only a human author can supply for their specific dataset and question.

The deliverable (4–6 pages of written comparative analysis) is not replicable by prompting an LLM with the dataset, because it requires the student to defend choices. The LLM is a tool for implementation; the judgment is irreducibly human. This is the capstone version of the series theme.

---

## 5. The AI Wayback Machine — Candidate Figures

**Figure 1: Florence Nightingale (1820–1910)**
- Wikipedia: "Florence Nightingale"
- Connection: Nightingale's rose diagrams (polar area charts) of Crimean War mortality data (1858) are among the earliest documented cases of statistical visualization used to drive a policy decision — a real problem, both ways, avant la lettre. She compared mortality rates across cause categories and used the visual comparison to argue for sanitary reform. For Ch 12, she exemplifies the communicative half of the capstone: the analysis is not finished until it supports a written argument about action.
- Attributes: British, female, 19th century, nursing/public health/statistics
- Anchor prompt: "Florence Nightingale used statistical graphics to compare mortality data across conditions and drive a policy argument. Describe how she structured that comparison and what made it persuasive to a non-statistical audience."

**Figure 2: W.E.B. Du Bois (1868–1963)**
- Wikipedia: "W. E. B. Du Bois"
- Connection: Du Bois and his students at Atlanta University produced a series of statistical infographics for the 1900 Paris Exposition displaying data on Black American social and economic conditions — employment, wages, education, property ownership. These are documented comparative analyses of real labor market data, using visualization to make the comparison legible to a general audience. The datasets Du Bois used (Census, labor surveys) are precursors to the BLS/O*NET data the chapter uses. His work demonstrates domain-agnostic statistical communication at the capstone level.
- Attributes: American, Black, male, sociologist/statistician, late 19th–early 20th century
- Anchor prompt: "W.E.B. Du Bois created statistical visualizations of labor market and educational data for the 1900 Paris Exposition. Describe what data he used, how he structured the comparisons, and why these are considered early examples of data communication."

**Figure 3: Janet Norwood (1923–2015)**
- Wikipedia: "Janet Norwood"
- Connection: Norwood was the first woman to serve as Commissioner of the Bureau of Labor Statistics (1979–1991), overseeing the agency that produces the exact datasets used in Ch 12 (OEWS, CPS, Employment Projections). Under her leadership, BLS navigated major methodological and political pressures around labor statistics while maintaining the credibility and public accessibility of the data. For a chapter built around BLS data, she is the most direct historical connection to the provenance of the datasets.
- Attributes: American, female, economist/statistician, 20th century, government
- Anchor prompt: "Janet Norwood served as BLS Commissioner from 1979 to 1991. Describe the methodological and institutional challenges she managed and how her tenure shaped the public availability and credibility of U.S. labor market data."

---

## 6. Pedagogical Delivery Research

### How to teach comparative statistical writing (capstone-specific)

The core failure mode in statistics capstone projects is **output narration without argument**: students report what each analysis found but never answer "which approach better serves this goal and why." The six-question scaffold is designed to force past this failure mode by making question 5 the only one that cannot be answered by reading off output.

Research on capstone rubrics (Assessing a Capstone Research Project, *Academic Medicine*, PMC8883397; Rubrics in Capstone Design Courses, *ResearchGate*) consistently identifies two rubric dimensions that differentiate strong from weak capstone work: (1) evidence of integration across the analysis (not just listing results), and (2) explicit acknowledgment of limitation. The Ch 12 six-question scaffold directly operationalizes both.

A 2024 post in the *Data Pedagogy* blog (datapedagogy.com, "Updating Beliefs on Bayesian Education") notes that students who learn both frameworks simultaneously — as this book does — demonstrate better conceptual understanding of both, because seeing the contrast makes each framework's assumptions visible.

**Specific failure modes in two-paradigm capstones (compiled from pedagogy literature and practitioner experience):**
1. **The false symmetry error:** Student treats both analyses as equally valid for the goal, declines to choose, writes "both approaches have merits." Cure: the six-question scaffold requires a stated preference in question 5.
2. **The prior cop-out:** Student chooses a flat/uniform prior "because I don't have prior knowledge" without checking whether prior knowledge actually exists. Cure: require students to search for at least one published study or BLS prior-year data before declaring ignorance.
3. **The p-value restatement:** Student interprets the Bayesian credible interval as if it were a confidence interval, or the posterior probability as if it were a p-value. Cure: question 4 of the scaffold ("where do the analyses agree / diverge?") forces a comparison of outputs that exposes conflation.
4. **The implementation pass-through:** Student accepts LLM output without verifying it against the structure of the analysis. Cure: the "what prior did you use and why?" sub-question in question 3 forces engagement with the Bayesian setup, which an LLM can only answer generically without student input.

### Worked partial example guidance

The chapter's worked partial example (one dataset analyzed halfway) should ideally use Dataset C (Education Pays, 8 rows) because it is small enough that the entire analysis fits on one page and the threshold question (P(earnings > $1,500 | bachelor's)) is the clearest single-page demonstration of the frequentist/Bayesian contrast in the book.

---

## 7. Representation and Display Research

### The six-question comparison scaffold as a display table

The chapter already specifies the six questions. The author should render them as a two-column table where the right column is an explicit prompt to the student (what to write, not just what question to answer):

| # | Question | What your answer must include |
|---|---|---|
| 1 | What is the data generating process? What does each framework assume about it? | Name the assumed distribution; name the assumed sampling procedure; say whether those assumptions are met |
| 2 | What did the frequentist analysis find? What can it not tell you? | State the test statistic, p-value or CI, and the specific question the frequentist method cannot answer |
| 3 | What did the Bayesian analysis find? What prior did you use and why? | State the posterior mean/median and CrI; name the prior distribution and defend its parameters |
| 4 | Where do the analyses agree? Where do they diverge? | At minimum: compare point estimates and intervals; identify any case where the two approaches recommend different actions |
| 5 | Which approach better serves the analysis goal, and why? | State the decision-maker's actual need; map it to a framework; acknowledge what the other framework could add |
| 6 | What would change your conclusion? | At least one: more data, different prior, different model specification |

### Dataset-selection prompt template

A single-page table listing the five verified datasets (A–E above) with three columns: Dataset name / domain, Analysis type supported, Recommended for students who... This should appear early in the chapter as the first decision point.

---

## 8. Open Questions and Research Gaps

1. **Frey-Osborne data exact CSV provenance.** The original 702-occupation automation probability table is in the paper appendix as a PDF table, not a clean CSV. Several GitHub repositories have digitized it, but none are the authoritative release; the original authors have not published a standalone data file. The author should either (a) locate or create a clean CSV of the appendix data and host it on the companion website, or (b) use the Mendeley dataset (data.mendeley.com/datasets/czbvhmzwm3/1) as a proxy, documenting the difference. [UNVERIFIED — confirm exact source before publishing]

2. **O*NET version alignment.** O*NET releases approximately 3 updates per year; the "Degree of Automation" scale values change slightly across releases. The companion website should pin to a specific version (currently 30.3) and note the download date. Any student downloading a different version may get slightly different values. The author should decide whether to freeze a specific version file on the companion site.

3. **BLS OEWS file format changes.** The OEWS flat file structure changed in 2021 (from OES to OEWS naming). Older tutorials will reference column names that no longer match. The data prep reference materials on the companion website must use the current (post-2021) file format.

4. **"Education pays" small-N problem.** Dataset C has only 8 data points (one per education level), which is too small for many frequentist tests to be reliable. The author should decide whether to use the underlying CPS microdata (available from census.gov/programs-surveys/cps/data/datasets.html) for a fuller analysis, or treat the small N as a pedagogical feature (making prior choice consequential). If the latter, note it explicitly in the data-selection guide.

5. **LLM prompting for Bayesian analysis is aging fast.** The prompting section of this chapter is the most time-sensitive material in the book. Which LLMs can reliably execute a Bayesian logistic regression with a specified prior? As of 2025–2026, this varies by model and prompt structure. Flag this section as requiring annual review before each course offering.

6. **Acemoglu-Restrepo automation dataset.** Acemoglu & Restrepo (2018, NBER w23285, *Journal of Political Economy* 2020) studied industrial robot penetration by commuting zone — this is a different kind of automation data (robot adoption, not task-level susceptibility) and would support a two-group or regression capstone. However, the data requires merging IFR (International Federation of Robotics) robot data with BLS industry employment data, which is non-trivial for a one-session capstone. Not recommended for the standard dataset library; flag as advanced.

---

## 9. Sourcing Notes

- **BLS OEWS:** Verified public access June 2026. URL: bls.gov/oes/. The program runs continuously; data is updated annually (May release). The May 2025 data is the most recent release as of this writing. Use the specific year's URL for a stable citation.
- **O*NET 30.3:** Verified public access June 2026. URL: onetcenter.org/database.html. No registration required. Database ZIP includes all flat files. The "Work Context" file contains the Degree of Automation scale. Individual occupation data browsable at onetonline.org.
- **Frey-Osborne paper PDF:** Verified available at oxfordmartin.ox.ac.uk/downloads/academic/The_Future_of_Employment.pdf as of June 2026. The appendix table (702 occupations, automation probability) is in the PDF; no standalone CSV from the authors has been confirmed. The Mendeley dataset at data.mendeley.com/datasets/czbvhmzwm3/1 is a related but not identical dataset ("Probability of Automation of Occupations 2036"). [CONFIRM before assigning — verify the specific CSV the companion website will host.]
- **BLS Education Pays 2024:** Verified at bls.gov/careeroutlook/2025/data-on-display/education-pays.htm. Data derives from the CPS; the 8-row table is directly readable from the BLS site. Underlying CPS microdata at census.gov/programs-surveys/cps/data/datasets.html.
- **BLS Employment Projections 2024–2034:** Verified at bls.gov/emp/data/occupational-data.htm. Released August 2024. CSV download available. Interactive browser at data.bls.gov/projections/occupationProj.
- **Wasserstein & Lazar 2016:** Verified at tandfonline.com/doi/full/10.1080/00031305.2016.1154108. Open access.
- **Gelman et al. 2020 "Bayesian Workflow":** Verified at arxiv.org/abs/2011.01808. Free preprint.
- **Ioannidis 2005:** Verified at journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124. Open access, PLOS Medicine.
- **Acemoglu & Restrepo (2018/2020):** Verified at nber.org/papers/w23285 (working paper). Published in *Journal of Political Economy*. Dataset not independently verified as public download. [UNVERIFIED for direct data access — do not assign without confirming data availability.]
