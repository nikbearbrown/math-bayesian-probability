# Research: Chapter 08 — When Data Is Sparse
## Bayesian Probability
**Chapter one-line:** Small samples, rare events, and underpowered studies — where frequentist methods break down, produce inflated estimates, or simply refuse to run, and where Bayesian priors do their most important work.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Gelman, A., & Carlin, J. (2014). "Beyond power calculations: Assessing Type S (sign) and Type M (magnitude) errors." Perspectives on Psychological Science, 9(6), 641–651. DOI: 10.1177/1745691614551642**
Introduces Type S (sign error: concluding the effect is in the wrong direction) and Type M (magnitude error: exaggeration ratio — how much the estimated effect exceeds the true effect) as additions to the Type I/II framework. Argues that in noisy, low-power settings, statistically significant results are systematically misleading about both direction and magnitude. Provides the `retrodesign()` R function for computing these errors post hoc. Directly anchors Chapter 8's "winner's curse" section. Peer-reviewed; published in a top psychology methods journal.

**Clayton, A. (2021). Bernoulli's Fallacy: Statistical Illogic and the Crisis of Modern Science. New York: Columbia University Press. ISBN: 9780231199940.**
Argues that frequentist statistics systematically commits a logical error by treating P(data|H₀) as evidence about P(H₀|data) — the central confusion behind the winner's curse. Clayton traces this error to the foundational work of Fisher, Pearson, and Neyman, and argues for Bayesian inference as the resolution. Relevant to Chapter 8 as a framing source: the book asks whether this is labeled a hypothetical in TIKTOC.md Open Question #5. Note: polemic book by a mathematics instructor at Harvard Extension — not a peer-reviewed primary research paper. Use as framing/further reading; do not cite as evidence of empirical claims.

**Gelman, A., Carlin, J. B., Stern, H. S., Dunson, D. B., Vehtari, A., & Rubin, D. B. (2013). Bayesian Data Analysis (3rd ed.). Boca Raton: CRC Press.**
The standard graduate Bayesian reference. Chapters on informative priors and prior construction from existing literature are directly relevant to Chapter 8's "prior from published literature" technique. Chapter 5 covers hierarchical models as a regularization device; Chapter 17 covers robust regression. The core reference for Bayesian shrinkage as principled regularization.

**Ioannidis, J. P. A. (2005). "Why most published research findings are false." PLOS Medicine, 2(8), e124. DOI: 10.1371/journal.pmed.0020124**
Demonstrated using a Bayesian framework that when prior probability of true effects is low and statistical power is low, most significant findings are false positives. Chapter 8's "winner's curse" is the same phenomenon at the effect-size level: if most published significant results from underpowered studies are inflated, this is the expected outcome, not a research misconduct problem. The Bayesian framing of what NHST produces under low power.

**Stein, C. (1956). "Inadmissibility of the usual estimator for the mean of a multivariate normal distribution." In Proceedings of the Third Berkeley Symposium on Mathematical Statistics and Probability, 1:197–206.**
[UNVERIFIED — confirm proceedings year and page numbers before citing; this is a well-known reference but should be verified against primary databases. May be better cited via James & Stein 1961.]
Foundational paper showing that the ordinary least squares estimator is inadmissible in dimensions ≥ 3, motivating shrinkage estimators. The James-Stein estimator that followed directly connects to Bayesian shrinkage: shrinking toward a prior mean is the Bayesian formalization of what shrinkage estimators do heuristically.

### Key empirical cases

**Surgical complication rate monitoring — hospital quality improvement (partially documented; TIKTOC scenario is pedagogical).**
The TIKTOC.md scenario (3 complications in 200 procedures) is constructed for the chapter but reflects a real clinical quality improvement problem. The published literature on Bayesian quality monitoring in healthcare is documented: hospital surgical site infection detection using Bayesian networks (PMC5391146, documented). Bayesian approaches to rare surgical complication monitoring are used in healthcare quality programs, though the specific 3/200 numbers are illustrative, not drawn from a published dataset. Label the worked example as illustrative when writing the chapter; the phenomenon is documented.

**Underpowered psychology studies and effect size inflation (documented).**
The winner's curse in psychology is extensively documented. Quantitative studies (e.g., Lakens & Etz, documented via statistical-solutions.com and ScienceDirect) show that initial effect estimates from studies powered between 8–31% are inflated by 25–50%. The Open Science Collaboration's 2015 psychology replication project (Science, 349:aac4716) found that 61 of 100 published significant psychology findings failed to replicate — a landmark empirical case of what Type M errors look like in practice. [UNVERIFIED — confirm Open Science Collaboration 2015 citation details before citing.]

**Tracking disease outbreaks from sparse data with Bayesian inference (documented).**
Osthus et al. (2021, AAAI Proceedings, article 16621) demonstrate Bayesian inference for disease outbreak detection when only 0.05% of the population is tested daily. Bayesian methods with appropriate priors perform well even with extremely sparse data. This is a documented, peer-reviewed case directly relevant to the chapter's sparse-count context.

---

## 2. The Core Concept — State of the Field

### What is settled

- The "winner's curse" is a statistical phenomenon with a mathematical derivation: when the significance threshold acts as a selection filter, only studies that overestimate the effect by chance clear the threshold when power is low. This is not disputed (Gelman & Carlin 2014; Button et al. 2013 Nature Reviews Neuroscience).
- Bayesian shrinkage — pulling sparse-data estimates toward a prior mean — is equivalent to regularization (ridge regression / L2 penalty) in the non-hierarchical case. The connection between Bayesian priors and regularization is well established.
- The Beta-Binomial model for rare proportion estimation is solved analytically (conjugate pair) and is the standard Bayesian approach to counts data in Chapter 8's setting.
- For counts this small (3/200), the normal approximation underlying frequentist proportion tests is unreliable; exact binomial methods or Bayesian Beta-Binomial are the appropriate tools.

### What is disputed

- **When is Bayesian shrinkage "helpful" vs. "misleading"?** If the prior is mis-specified — centered on the wrong value — Bayesian shrinkage pulls estimates in the wrong direction and can be worse than the noisy frequentist estimate. This is the honest answer to the chapter's Exercise 3 and must be stated without sugarcoating.
- **Publication bias vs. winner's curse:** Whether the replication crisis is primarily caused by the winner's curse (a statistical artifact of low power + significance threshold) or by publication bias (selective reporting) or by questionable research practices (p-hacking) is an active area of metascience. Gelman & Carlin 2014 locates the mechanism in the threshold; others emphasize researcher behavior. Chapter 8 should present the statistical mechanism without pretending it exhausts the explanation.
- **James-Stein paradox and shrinkage:** Shrinkage toward a global mean is provably optimal in the mean squared error sense for ≥ 3 dimensions, but what it means to shrink unrelated estimates together (heights of people in different cities, for example) is philosophically awkward. Bayesian hierarchical models resolve this by shrinking toward a shared hyperparameter that is itself estimated from the data — but this requires a modeling assumption about exchangeability.
- **The "sparse data means you should wait" counterargument:** Frequentist analysis that reports "the data are too sparse to conclude anything" is sometimes the honest scientific answer. Chapter 8 must not suggest that Bayesian methods always solve the sparse-data problem — they solve it by importing prior knowledge, and if that prior knowledge is wrong, you've imported bias.

### What has changed recently (last 5 years)

- **Digital twins and synthetic controls** are being used in rare disease clinical trials to augment small samples — related to Bayesian borrowing of external information. FDA guidance 2026 addresses this.
- **Type M and Type S error analysis** has moved from statistical theory into methodological guidance. Multiple psychology journals now recommend retrodesign analysis (using Gelman & Carlin's framework) as part of study reporting.
- **Bayesian adaptive trials** for rare diseases are increasingly FDA-approved in practice, not just advocated theoretically. The Xenpozyme pediatric trial example (FDA approval, using 20-patient study with digital twin extrapolation) is documented (fierecbiotech.com; clinicalleader.com, 2026).
- Tracking disease outbreaks from sparse data (Osthus 2021) has become more visible post-COVID-19, when public health agencies frequently faced exactly the Chapter 8 scenario: rare-event counts under partial observability.

---

## 3. Application Domain Examples

**Domain: public health / clinical quality improvement (primary per TIKTOC.md)**

1. **Hospital surgical complication rate monitoring (partially documented; illustrative numbers).** The phenomenon — rare complication counts, need to assess whether rate is acceptable or changing — is real and documented in healthcare quality improvement literature. Bayesian monitoring with informative priors from published complication rate benchmarks is used in practice (e.g., surgical site infection monitoring, PMC5391146). The specific 3/200 scenario in TIKTOC.md is pedagogically constructed; label as "illustrative case based on documented practice."

2. **Rare disease clinical trials (documented).** Pediatric and rare disease trials routinely face n < 30 with sparse outcome events. FDA guidance (2026) and published methodology (PMC9077995) document Bayesian approaches using informative priors from adult trials or published literature. The Xenpozyme example (20-patient pediatric study) is a concrete, named, recent case.

3. **COVID-19 early outbreak detection from sparse data (documented).** Osthus et al. (2021, AAAI): Bayesian framework for tracking disease outbreaks when testing is sparse. Shows that Bayesian methods with appropriate Gaussian process priors maintain performance at extremely low data density. Directly connects to Chapter 8's "rare events" framing.

4. **Psychology replication crisis — effect size inflation in underpowered studies (documented).** The Open Science Collaboration (2015, Science) demonstrated that 61% of published psychology findings failed to replicate. Gelman & Carlin's Type M framework provides the statistical mechanism: low-power studies reporting significant effects systematically overestimate effect sizes. Chapter 8's Exercise 2 (n=20 study d=0.8 vs. n=200 replication d=0.2) is directly motivated by this empirical pattern.

5. **Genome-wide association studies (GWAS) and winner's curse (documented).** In genetic epidemiology, the winner's curse is so well-documented that GWAS reporting standards now require independent replication. Effect sizes from discovery cohorts are routinely inflated; subsequent replication studies find smaller effects. Documented in PMC9713380 (modeling replication rates in GWAS accounting for winner's curse). This domain provides a domain-diverse example of the same mechanism the chapter discusses.

---

## 4. The Book's Thesis Connection

Chapter 8 is where the Bayesian approach earns its complexity cost most directly. The frequentist approach to 3/200 complications does what it is supposed to do — it produces a wide confidence interval that accurately represents the data's uncertainty. That honest representation is sometimes the right answer. But when a decision (is this hospital's accreditation at risk?) must be made now with these data, Bayesian shrinkage toward the known distribution of complication rates provides a more actionable estimate — at the cost of importing prior assumptions.

The chapter serves the book's thesis by making the tradeoff concrete: Bayesian methods solve the sparse-data problem by importing information (prior). If that information is good, the estimate improves. If that information is wrong, the estimate worsens. The prior is not free. This is the chapter where a student who has been impressed by Bayesian methods should feel the vertigo: Bayesian shrinkage is powerful, but power is not always virtue.

What a self-directed student must supply that an algorithm cannot: the judgment of whether the prior is well-justified for this particular sparse-data problem. An LLM can compute a Beta-Binomial posterior. It cannot tell the student whether the published complication rates used as a prior are applicable to this hospital's patient mix, surgical volume, and era. That requires clinical domain knowledge.

---

## 5. The AI Wayback Machine — Candidate Figures

**Charles Stein (1920–2016)**
Wikipedia page: "Charles M. Stein"
American mathematical statistician, Stanford University. Proved in 1956 that the maximum likelihood estimator of a multivariate normal mean is inadmissible in dimensions ≥ 3 — a counterintuitive result that motivated all subsequent work on shrinkage estimation. The James-Stein estimator (with Willard James, 1961) formalized shrinkage toward the prior mean. Stein's result connects Bayesian priors and regularization at a foundational level. Taught at Stanford for decades; known for demanding standards and minimalist writing style. Discipline: mathematical statistics. Era: mid-20th century. Nationality/gender: American male (Jewish background — underrepresented in some textbook contexts).
Anchor prompt: "You are Charles Stein in 1956, presenting a result that says the standard estimator for three or more means is inadmissible — that you can always do better by shrinking toward zero. Your audience is skeptical. Why should they believe this, and what does it mean for how statisticians should think about estimation?"

**Jerzy Neyman (1894–1981)**
Wikipedia page: "Jerzy Neyman"
Polish-American statistician; co-developed the Neyman-Pearson hypothesis testing framework with Egon Pearson. His framework formalized Type I and Type II errors — the very framework that Gelman & Carlin's Type S / Type M analysis critiques. Neyman's work is the target of Chapter 8's critique, not its hero; but using him as an AI Wayback figure allows the chapter to animate the critique from the inside. Born in Bendery (now Moldova), educated in Poland, fled to England, then the US; founded the statistics department at Berkeley. Discipline: statistics/probability. Era: early-mid 20th century. Nationality/gender: Polish-American male.
Anchor prompt: "You are Jerzy Neyman in 1933, explaining to a colleague why you and Egon Pearson chose to define statistical error in terms of long-run frequency properties rather than the probability of a specific hypothesis. What are you trying to achieve, and what are you deliberately setting aside?"

**Persi Diaconis (born 1945)**
Wikipedia page: "Persi Diaconis"
American mathematician, former professional magician, Mary V. Sunseri Professor of Statistics and Mathematics at Stanford. Left home at 14 to travel with a magician; self-educated; returned to academia at 24; became a MacArthur Fellow in 1982. Known for mathematical analysis of randomness (card shuffling), Bayesian statistics (with David Freedman), and empirical Bayes methods. His trajectory — magician to statistician — is pedagogically compelling for showing that intuitions about randomness and rare events are reliably wrong. Discipline: statistics/probability/combinatorics. Era: contemporary. Nationality/gender: American male (Greek descent). Notable for unusual background.
Anchor prompt: "You are Persi Diaconis, teaching a student who has just learned that random-looking events in small samples are often not random — that the winner's curse means significant findings in small studies are probably inflated. The student asks: 'How do we develop good intuitions about rare events?' What do you tell them?"

---

## 6. Pedagogical Delivery Research

**Prior knowledge and common misconceptions:**

Students entering Chapter 8 from frequentist training have learned to interpret "not significant" as "no effect" — a direct consequence of not thinking about power. The winner's curse is initially counterintuitive: "if the study found a significant result, isn't that good evidence the effect is real?" The pedagogical challenge is explaining why selection on significance inflates apparent effect sizes.

A common misconception about Bayesian shrinkage: students initially believe the prior "overrides" the data. The correct intuition is that with sparse data, the likelihood is flat and the prior dominates; with abundant data, the likelihood dominates. This is not the prior overriding data — it's the data not having much to say. Show this visually with a sequence of posteriors as n increases.

Another misconception: "Bayesian methods always give better estimates than frequentist in small samples." This is false when the prior is mis-specified. The chapter must address this directly: Bayesian shrinkage helps when the prior captures real prior knowledge; it hurts when it doesn't.

**Instructional sequences that work:**

The retrodesign demonstration is highly effective: take a published significant result with small n and compute what the Type M exaggeration ratio is. Students are surprised that a study they would intuitively trust (p < 0.05, significant!) is likely to be inflated by 50% or more.

Run the Beta-Binomial example before teaching the theory. Show students the prior, the data (3 events), and the posterior numerically. Then ask: "where did the tighter estimate come from?" The answer — from the prior encoding what we know about complication rates in general — makes the mechanism transparent.

The "two hospitals" comparison is effective: Hospital A has 200 procedures and 3 complications (same as TIKTOC). Hospital B has 20 procedures and 3 complications (15% rate). Show that the frequentist CI for Hospital B is [3%, 38%] — almost uninformative — and the Bayesian posterior using the same prior gives a much tighter estimate. Students see the gain directly.

**Teaching failure modes:**

Presenting the winner's curse only as a "problem with frequentist methods" misses the point. The problem is with significance filtering combined with low power — which is a problem with how researchers use frequentist methods, not an intrinsic failure of frequentist logic. Chapter 8 should be clear: a frequentist researcher who honestly reports "the data are too sparse to conclude anything" has done the right thing.

Presenting Bayesian shrinkage without the caveat about prior misspecification is dangerous. Students who leave Chapter 8 thinking "Bayesian always better for sparse data" will eventually use a bad prior and trust their inflated-shrinkage estimate more than they should.

---

## 7. Representation and Display Research

**Frequentist vs. Bayesian side-by-side comparison — worked example:**

Setting: hospital tracks surgical complications. 3 complications in 200 procedures over 2 years. Accreditation threshold: complication rate < 2.5%.

| | Frequentist (exact binomial / proportion test) | Bayesian (Beta-Binomial with informative prior) |
|---|---|---|
| Estimate | 3/200 = 1.5% | Posterior mean ≈ 1.49% |
| Interval | 95% CI: [0.31%, 4.35%] (exact binomial) | 95% CrI: [0.55%, 3.18%] |
| Interval width | 4.04 percentage points | 2.63 percentage points |
| Prior used | None (implicit flat) | Beta(3, 200): "published rate ≈ 1.5%" |
| Answers "Is rate < 2.5%?" | Not directly | P(rate < 0.025 \| data) = directly computable |
| Year-over-year comparison | p = 0.71 (not significant; nearly no power) | Posterior on change: P(rate improved) = direct |
| Honest caveat | "CIs are technically correct but wide; test has almost no power" | "Posterior tightened because of prior — verify prior is applicable to this hospital" |

*Display note:* The key pedagogical display is showing two posterior density plots — one from a flat prior (nearly indistinguishable from the frequentist CI) and one from the informative prior — and annotating that the tighter estimate came entirely from importing prior knowledge. The display makes the prior's contribution visible.

A secondary display: the winner's curse diagram. A simple simulation showing effect size estimates from 1000 underpowered studies (true effect = 0.2, n = 20), marking the significance threshold, and showing that only the overestimated studies cross the line. Students should be able to trace the mechanism visually.

---

## 8. Open Questions and Research Gaps

**The winner's curse / Type M and Type S errors: likely increasingly outdated in application.** Gelman & Carlin 2014 is well-established but the software (retrodesign R function) and application norms are evolving. As power analysis and pre-registration become more standard in psychology, some of the worst cases the paper describes are becoming less common. Chapter 8 should note that these practices are improving without overstating how much.

**Open Science Collaboration 2015** (if cited): this is a landmark paper (Science, 349:aac4716) but its interpretation is disputed. Some meta-researchers argue the replication rate is better than 61% suggests when methodological differences between original and replication are accounted for. The author should present the documented replication failure rate as an empirical finding while noting the interpretive debate. [UNVERIFIED — confirm exact citation before citing.]

**Bayesian adaptive trials for rare diseases (aging quickly).** The FDA 2026 guidance and specific approved trial examples (Xenpozyme, digital twins) represent the cutting edge as of mid-2026. This material will age faster than any other section of Chapter 8; flag for annual review.

**James-Stein and Stein's paradox for Chapter 8 scope:** Whether to include James-Stein as background is a judgment call. It is intellectually foundational (shrinkage estimators as Bayesian analog) but requires explaining multidimensional estimation theory, which may exceed the reader's mathematical background. Consider presenting the intuition (shrinking toward a group mean improves estimates when data is sparse) without deriving the admissibility result.

**Unresolved: the prior construction problem for real sparse-data analyses.** The chapter shows how to use Beta(3, 200) as a prior by assuming the published literature says "rate ≈ 1.5%." In practice, identifying the right published literature, extracting a beta prior from reported means and confidence intervals, and assessing whether the prior is applicable to this specific context requires substantial domain expertise. No algorithmic solution exists. This is genuinely hard and should be treated as such.

**Paywalled:** Gelman & Carlin 2014 (Perspectives on Psychological Science) — paywalled; PDF circulated widely and available at sites.stat.columbia.edu/gelman/research/published/retropower_final.pdf. Ioannidis 2005 (PLOS Medicine) — open access by design.

---

## 9. Sourcing Notes

- **Gelman & Carlin 2014** (Perspectives on Psychological Science, 9(6):641–651): verified via SAGE Journals (journals.sagepub.com/doi/10.1177/1745691614551642) and multiple reference databases (ResearchGate, Columbia PDF). DOI: 10.1177/1745691614551642. PDF at sites.stat.columbia.edu/gelman/research/published/retropower_final.pdf. Reliable.
- **Clayton 2021** (Bernoulli's Fallacy, Columbia UP): verified via Columbia University Press (ISBN 9780231199940) and Amazon. Book; not peer-reviewed research. Author bio: Clayton teaches philosophy of probability at Harvard Extension School (confirmed via book description). Use as framing/further reading only.
- **Ioannidis 2005** (PLOS Medicine, 2(8):e124): verified via PLOS Medicine journal (journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124). Open access. DOI: 10.1371/journal.pmed.0020124. Reliable.
- **Open Science Collaboration 2015** (Science, 349:aac4716): [UNVERIFIED — confirm DOI and exact citation before citing; well-known paper but page-level details need verification].
- **Stein 1956 inadmissibility paper**: [UNVERIFIED — the 1956 proceedings paper is foundational but the proceedings are not always well-indexed. Better to cite James & Stein 1961 "Estimation with Quadratic Loss" (Proceedings of 4th Berkeley Symposium) which is more accessible and directly introduces the James-Stein estimator. Both need verification.]
- **Osthus et al. 2021** (AAAI Proceedings, article 16621): verified via AAAI digital library (ojs.aaai.org/index.php/AAAI/article/view/16621). Open access. Reliable.
- **BDA3**: see Ch 07 sourcing notes — same reference.
- **PMC5391146** (surgical site infection detection, Bayesian network): verified via PubMed Central (open access). Reliable for documented clinical case.
- **PMC9713380** (GWAS winner's curse): verified via PubMed Central. Open access. Reliable.
- **FDA 2026 draft guidance**: see Ch 07 sourcing notes.
- **Button et al. 2013** (Nature Reviews Neuroscience, power in neuroscience): not searched above; [UNVERIFIED — if the author wants a second empirical source for underpowered-studies-and-inflation, this is the standard reference; verify: Button KS et al., "Power failure: why small sample size undermines the reliability of neuroscience," Nature Reviews Neuroscience 14:365–376, 2013.]
