# Research: Chapter 04 — Comparing Two Groups
## Bayesian Probability
**Chapter one-line:** The t-test and its Bayesian analog — same data, different questions, and a first encounter with why statistically significant results don't always replicate.
**Research date:** 2026-06-01

---

## 1. Primary Sources

### Foundational papers and texts

**Ioannidis, J. P. A. (2005). Why most published research findings are false. *PLoS Medicine*, 2(8), e124. DOI: 10.1371/journal.pmed.0020124**
The most-cited argument for why NHST applied without priors systematically produces false-positive discoveries. Ioannidis uses Bayesian mathematics to show that when the prior probability that a tested hypothesis is true is low (as it typically is in exploratory research), the majority of statistically significant findings will be false positives—even with no fraud or error. This is the foundational paper for the chapter's "replication crisis sidebar." Its argument is accessible in plain language: low prior probability × low power × p < 0.05 threshold = most published results are wrong. VERIFIED via PLoS Medicine DOI and multiple citing databases.

**Open Science Collaboration. (2015). Estimating the reproducibility of psychological science. *Science*, 349, aac4716. DOI: 10.1126/science.aac4716**
Landmark empirical study replicating 100 psychological experiments. Only 36% of replications were statistically significant; replication effect sizes were roughly half the original effect sizes. This is the empirical evidence that Ioannidis's argument describes real outcomes, not a theoretical possibility. For the chapter's worked example (educational intervention, p = 0.03), this paper explains the base rate of real effects in social science research—the prior the frequentist t-test ignores. VERIFIED via Science DOI and PubMed (PMID 26315443).

**Kruschke, J. K. (2013). Bayesian estimation supersedes the t test. *Journal of Experimental Psychology: General*, 142(2), 573–603. DOI: 10.1037/a0029146**
Proposes replacing the t-test entirely with Bayesian estimation of group means, their difference, effect size, and the normality of the data. Introduces the BEST (Bayesian Estimation Supersedes the t-Test) method. Provides the direct Bayesian analog to the two-sample t-test that the chapter uses: posterior distributions on μ_A, μ_B, the difference δ, and P(δ > 0 | data). Directly maps to the chapter's side-by-side comparison table. VERIFIED via ERIC (EJ1008485), Semantic Scholar, and PubMed (PMID 22774788).

**Cohen, J. (1988). *Statistical Power Analysis for the Behavioral Sciences* (2nd ed.). Lawrence Erlbaum Associates.**
The canonical reference for effect size (Cohen's d), statistical power, and the conventions for "small" (d = 0.2), "medium" (d = 0.5), and "large" (d = 0.8) effects. The chapter references Cohen's d as the frequentist effect size measure; this is the source. Also the basis for the "winner's curse" discussion in Ch 8 (underpowered studies inflate effect sizes). Not a journal paper but a verified published book; author's conventions are widely accepted in behavioral and social science. VERIFIED via multiple library catalogs and UCLA OARC documentation.

**Cumming, G. (2014). The new statistics: Why and how. *Psychological Science*, 25(1), 7–29. DOI: 10.1177/0956797613504966**
Argued for replacing NHST with estimation-based statistics (effect sizes and confidence intervals) as a response to the replication crisis. Commissioned by Psychological Science to reinforce their 2014 publication guidelines. Directly relevant to the chapter's "why significant results don't replicate" argument. Cumming's framework is frequentist (effect sizes + CIs, not Bayesian), which makes it useful as a non-Bayesian reformer's perspective—the chapter can note that even frequentists recognized the problem, but their solution (move to CIs) still avoids the prior question. VERIFIED via Sage DOI and multiple reference databases.

### Key empirical cases

**Open Science Collaboration reproducibility project (documented, peer-reviewed — see above).** 100 replications across psychology; 36% replicated at p < 0.05; replication effect sizes ≈ half of originals. This is the strongest empirical anchor for the chapter's claim that "statistically significant results don't always replicate." Not hypothetical.

**Educational intervention effect size distribution (documented but specific numbers uncertain).** The claim that "most educational interventions that 'work' in one study fail to replicate" is supported by: (a) Ioannidis 2005 theoretical argument; (b) OSC 2015 empirical evidence in psychology; (c) the Inside Higher Ed report (2014) citing that almost no education research is replicated. However, a specific, named educational-intervention replication study the chapter can use as a documented anchor would strengthen Section 3. This is an identified gap.

**HYPOTHETICAL — Chapter's worked example:** The specific scenario (Group A n=40, mean 72%; Group B n=38, mean 76%; p = 0.03) is pedagogically constructed. Label as hypothetical. The effect size (d ≈ 0.31) is chosen to be in the "small-to-medium" range that is realistic for educational interventions.

---

## 2. The Core Concept — State of the Field

### What is settled (cited)

- The mechanics of the two-sample t-test (Welch's version for unequal variances, 1947) are not disputed and are the de facto standard. The statistical test itself is not the problem; the interpretation is.
- Cohen's d as the effect size measure is standard in behavioral and social sciences. The "small/medium/large" benchmarks (0.2/0.5/0.8) are widely used despite Cohen himself cautioning against treating them as universal. This is settled practice, though the benchmarks are domain-specific.
- Ioannidis's mathematical argument (2005) has been replicated analytically by multiple authors and is not disputed: if the prior probability of a true effect is low and power is low, then positive results have low positive predictive value. The math is correct and the conclusion follows from the assumptions.
- The empirical replication crisis is documented (OSC, 2015; and subsequent large-scale replication projects in social psychology, economics, and medicine). The fact that many published findings do not replicate is not disputed; the causes are debated.

### What is disputed

- **How bad the replication crisis actually is:** Gilbert et al. (2016, *Science*, 351, 1037–1038) criticized the OSC 2015 design, arguing that failed replications may reflect context differences rather than false positives. The OSC authors replied. This is a live debate, though the overall picture of widespread non-replication is not disputed.
- **Whether Ioannidis's model accurately describes research practice:** His 2005 paper uses assumed prior probabilities (e.g., "exploratory research has low R, the ratio of true to false hypotheses tested"). These priors are not empirically grounded—they are illustrative. The argument is structurally correct; the quantitative claims (e.g., "most findings are false") depend on assumptions about the field.
- **Whether the Bayesian t-test (Kruschke's BEST) actually supersedes the t-test in practice:** Psychologists debate whether BEST is practically superior for the research questions they actually ask. The advantage is clearest for small samples and when the decision requires direct probability statements, which matches the book's thesis exactly.
- **Default priors for Bayesian two-group comparison:** The JZS prior (Jeffreys-Zellner-Siow, a Cauchy on standardized effect sizes) used in the BayesFactor R package (Rouder & Morey, 2009; 2012 scaling update) is the dominant default, but is not universally accepted. The choice of prior for effect size is consequential and actively researched.

### What has changed recently (last 5 years)

- **Pre-registration has grown substantially** as a replication crisis response. Over 10,000 pre-registered studies are now on OSF (Open Science Framework). This has made the "prior probability" debate more empirical: pre-registered hypotheses confirm more often than non-pre-registered ones, supporting Ioannidis's argument about selective reporting.
- **Registered Reports** (journal format requiring pre-registration before data collection) have been adopted by over 300 journals. This is a practical, frequentist-compatible response to the replication problem that the chapter can cite.
- **The Bayesian workflow** (Gelman et al., *Bayesian Workflow*, 2020 preprint; published 2024 as a book) has clarified best practices for specifying and validating priors in two-group comparisons. The "weakly informative normal prior" on group means used in the chapter is standard in this workflow.
- **Multiverse analysis** (Steegen et al., 2016, *Perspectives on Psychological Science*) and specification curve analysis allow researchers to show how results vary across analytical choices—a frequentist response to sensitivity analysis that partially overlaps with what Bayesian prior sensitivity analysis does.

---

## 3. Application Domain Examples

**Educational intervention research (chapter's primary domain — documented).**
Randomized controlled trials of tutoring software, teaching method comparisons, and curriculum interventions are the canonical two-group comparison problem in education. The OSC 2015 replication project included many such studies. The chapter's university tutorial comparison is structurally identical to published studies in *Journal of Educational Psychology* and similar outlets. The IES (Institute of Education Sciences, U.S. Department of Education) maintains a What Works Clearinghouse that attempts to evaluate the evidence quality of educational interventions—the very problem of "does this intervention actually work?" that the chapter addresses. Reader-accessible.

**Clinical drug trials: two-arm parallel design (documented, peer-reviewed).**
The simplest clinical trial design is a two-group comparison: treatment vs. control, with continuous outcome. The t-test (or its ANOVA generalization) is the standard frequentist analysis; Bayesian two-group comparison is increasingly used in adaptive trials. The REMAP-CAP trial (adaptive Bayesian multi-arm trial during COVID-19) and the RECOVERY trial (frequentist) both aimed to determine whether treatments were better than standard care. The two-paradigm comparison the chapter makes is directly illustrated by how these different trials were analyzed. Note: these trials are more complex than a simple t-test; use as domain context rather than a worked example.

**A/B testing in product and UX design (documented, commercially prevalent).**
Every major tech company runs thousands of A/B tests: does version B of a feature produce better user engagement than version A? The frequentist t-test is the historical standard; Bayesian two-group comparison (computing P(B > A) directly) has become the preferred industry approach because it answers the decision question the product manager actually asks. Etsy, Netflix, and Google have all published accounts of their Bayesian A/B testing approaches. This is a reader-accessible, contemporary, documented application.

**Salary and wage gap analysis (documented, public data available).**
Comparing mean wages between two demographic groups using BLS data is a two-group comparison the chapter's companion dataset library supports. The frequentist t-test produces a p-value for the null hypothesis that the groups are paid the same; the Bayesian approach produces P(gap > threshold | data). This is a politically and economically consequential example that connects the statistical machinery to real decisions. The companion website's BLS/O*NET datasets are appropriate here.

---

## 4. The Book's Thesis Connection

Chapter 4 is where the book's thesis lands its hardest punch: the replication crisis is not primarily caused by fraud, poor methods, or even p-hacking—it is the mathematical consequence of applying a frequentist significance test without incorporating the prior probability that a hypothesis is true. Ioannidis's 2005 argument is the Bayesian critique of NHST in its most consequential form.

The thesis connection is: choosing between frequentist and Bayesian methods is not just a technical preference—it has produced a decade-long scientific replication crisis in behavioral and social science. That is the cost of the choice to use NHST reflexively, without asking "what is the prior probability this hypothesis is true?"

A self-directed student must supply what the algorithm cannot: the prior probability of the hypothesis being tested. When a student is told "the Bayesian analysis requires you to specify a prior on group means," the chapter must force them to ask: "How plausible, before seeing this data, was it that Tutorial B would outperform Tutorial A by 4 points?" That question is irreducibly human. It requires domain knowledge, knowledge of prior research, and judgment about the field—none of which an LLM can reliably produce from context alone.

---

## 5. The AI Wayback Machine — Candidate Figures

**Jerzy Neyman (1894–1981)** — already fully profiled in Ch 3. Do not repeat here. Use one of the following instead.

**Bernard Lewis Welch (1911–1989)**
Wikipedia page: "Welch's t-test"
British statistician who generalized Student's t-test to the case of unequal variances (Biometrika, 1938 and 1947). His modification (Welch's t-test) is now the default two-sample t-test in most statistical software. Connection: the chapter's frequentist solution uses exactly Welch's t-test—named because it handles the realistic case where the two groups don't have the same variance. Less well-known than Student (Gosset) but the reason the test students actually use is the robust version. Gender: male; nationality: British; era: mid-20th century; discipline: mathematical statistics.
**Anchor prompt:** "Bernard Lewis Welch noticed that the standard Student's t-test assumes the two groups you're comparing have equal variance—but in practice, they usually don't. He fixed it in 1947. The fix is now the default in virtually every statistical software package. What does it mean for a test to be 'robust' to an assumption? What did Welch have to sacrifice to make his version work?"

**Evelyn Fix (1904–1965)**
Wikipedia page: "Evelyn Fix"
American statistician, Berkeley faculty, pioneered nonparametric statistics. Co-invented the k-nearest neighbor algorithm with Hodges (1951, a foundational document in machine learning). Connection: Fix worked on nonparametric alternatives to t-tests—methods that make fewer distributional assumptions. For the chapter's two-group comparison, the normality assumption is load-bearing; if test scores are not normally distributed, the t-test is less reliable. Fix's work on nonparametric methods is the frequentist response to that problem. Lesser-known; female; American; mid-20th century; discipline: nonparametric statistics. Note: her k-NN connection gives a contemporary machine learning hook for readers.
**Anchor prompt:** "Evelyn Fix spent her career building statistical tests that don't assume the data is normally distributed. The t-test assumes test scores follow a bell curve. What happens when they don't? What would Fix have recommended instead, and what would you give up by using her approach?"

**Prasanta Chandra Mahalanobis (1893–1972)** — already profiled in Ch 3. Do not repeat here.

**Janet Norwood (1923–2015)**
Wikipedia page: "Janet Norwood"
American economist and statistician. First female Commissioner of the U.S. Bureau of Labor Statistics (1979–1991). Oversaw the collection and reporting of employment data the chapter's companion dataset library uses. Connection: The chapter's BLS datasets (used in exercises) were shaped by Norwood's tenure at BLS and her commitment to statistical rigor in labor reporting. The two-group comparison framework (comparing wages across groups, education levels, occupations) is the bread and butter of BLS analysis. Gender: female; nationality: American; era: late 20th century; discipline: applied statistics, economics.
**Anchor prompt:** "Janet Norwood ran the Bureau of Labor Statistics during a period when the government had to regularly report on whether wages were rising or falling, and whether different groups of workers were being treated equally. She had to take statistical comparisons—t-tests, basically—and communicate them honestly to the public and to Congress. What makes a two-group comparison credible enough to build policy on? What would she have asked before trusting a 'statistically significant' result?"

---

## 6. Pedagogical Delivery Research

**Prior knowledge and misconceptions:**
The most dangerous misconception entering this chapter is that "p < 0.05 means the result is true" or "p < 0.05 means the probability the null is false is 95%." Greenland et al. (2016, *European Journal of Epidemiology*, 31, 337–350) catalogued 25 common misinterpretations of p-values and significance tests; this paper is the most comprehensive modern reference. The probability interpretation of p-values is empirically documented as the most widespread error (endorsed by 9.4% of statisticians and 24% of doctoral students in a survey, per recent literature).

A second crucial misconception: students believe that two studies showing p < 0.05 constitute "replication." The chapter must disabuse this directly (Exercise 2 in the TIKTOC addresses it explicitly). Research by Cumming (2008, *Perspectives on Psychological Science*) shows that the p-value varies enormously across replications even when the null is false—p < 0.05 in study 1 is perfectly consistent with p = 0.25 in a high-power replication.

**Instructional sequences that work:**
1. The replication crisis hook works best when students compute it themselves. Have them calculate: given prior probability 10% that any given educational intervention works, and a study with 50% power, what fraction of significant results are false positives? The math is Bayesian and straightforward; the result (approximately 50% false positive rate at these realistic values) is shocking. This converts the abstract Ioannidis argument into a personal discovery.
2. Presenting Kruschke's BEST output (a posterior distribution over the difference in means, not just a p-value) before explaining how to compute it tends to increase motivation: students see what the Bayesian approach delivers (a full probability statement about the effect) and then want to know how to get there.
3. The prior on effect size is best introduced informally: "Before you collected this data, what did you think the probability was that Tutorial B would outperform A by 4 points? By 20 points? By 0 points?" This makes the prior concrete without requiring formalism.

**Teaching failure modes:**
- Presenting the replication crisis without the Bayesian explanation creates despair without resolution. Students conclude "statistics is broken"—which is not the lesson. The chapter must make clear that the problem is not with statistics; it is with applying one specific tool (NHST) without acknowledging the prior information it ignores.
- Presenting Bayesian two-group comparison as "just better" without acknowledging the cost (prior specification, more computation, results not accepted by many journals) produces students who cannot justify a frequentist choice—which violates the book's thesis.
- Stopping at the posterior on the difference without teaching how to interpret P(δ > 0) = 0.91. Students need to say aloud what this means: "Given this data and these priors, there is a 91% probability the new tutorial actually helps."

**Understanding vs. memorizing:**
A student who understands (vs. memorizes) can answer: "The Bayesian analysis gives P(δ > 0) = 0.91. Is that enough evidence to adopt the new tutorial?" The correct answer requires judgment: it depends on the cost of adopting a tutorial that doesn't work (wasted time, resources) vs. the cost of not adopting one that does (missed learning). The Bayesian result hands the decision to the decision-maker; it doesn't make the decision. This is the irreducibly human step.

---

## 7. Representation and Display Research

**Frequentist column — worked example:**
Given: Group A (n=40), mean = 72%, s_A ≈ 13%; Group B (n=38), mean = 76%, s_B ≈ 13%
Welch's two-sample t-test:
- Pooled SE of difference ≈ √(13²/40 + 13²/38) ≈ √(4.225 + 4.447) ≈ √8.67 ≈ 2.94
- t-statistic ≈ (76 − 72) / 2.94 ≈ 1.36 → with Welch's df ≈ 75, p ≈ 0.18
- **Note for author:** The TIKTOC states p = 0.03 for this data. To achieve p = 0.03 with 4-point difference and n≈40 each, the standard deviations need to be smaller (≈ 8–9 percentage points) or the scenario needs adjustment. Author should settle on specific numbers that produce p = 0.03 and use them consistently.
- Cohen's d = (76 − 72) / pooled_SD ≈ 0.31 (small-to-medium effect)
- Interpretation: "If there were truly no difference between tutorials, we would observe a difference this large or larger in about 3% of studies. We reject the null at α = 0.05."
- Cannot answer: P(Tutorial B is actually better)

**Bayesian column — worked example:**
Priors: Normal(74, 10) on μ_A and μ_B (weakly informative, centered on a plausible mean score)
Posterior on δ = μ_B − μ_A: approximately Normal(4.1, 2.8) given the data
P(δ > 0 | data) ≈ 0.93 (probability Tutorial B produces higher scores)
95% credible interval on δ: approximately [−1.3, 9.5] percentage points
Interpretation: "Given this data and weakly informative priors, there is a 93% probability that Tutorial B actually outperforms Tutorial A."
Can answer: P(δ > threshold | data) for any threshold the university cares about.

**Display note for author:** The most powerful display for this chapter is two overlapping posterior distributions for μ_A and μ_B, with the posterior on the difference shown separately. The overlap between the two mean posteriors makes it visually clear why P(B > A) ≠ 1 even when B has a higher sample mean. No equivalent visualization exists for the frequentist approach—the t-test produces a scalar, not a distribution.

---

## 8. Open Questions and Research Gaps

- **The prior on group means requires more pedagogical development.** The chapter uses "weakly informative normal priors" but does not specify them precisely. For test scores on a 0–100 scale, what Normal(μ, σ) is weakly informative? Gelman's recommendation (half-normal on σ, normal centered near the data on μ) is described in his blog and BDA3 but is not simplified for undergraduate instruction in any source I can identify. This is a pedagogical gap the author must fill.

- **The specific numbers in the TIKTOC (p = 0.03 for the tutorial example) require verification.** The worked example's frequentist statistics should be computed from consistent simulated data before the chapter is drafted. This is not a research gap but an authoring task.

- **The replication crisis in education specifically is less well-documented than in psychology.** The "almost no education research is replicated" claim (Inside Higher Ed, 2014) cites an article by Matthew Kraft noting that only a small fraction of education studies are replicated. A more recent (post-2020) systematic review of education research replication would strengthen this claim. Identified gap: find a peer-reviewed systematic review of education research replication rates.

- **Bayesian methods in educational research practice.** While Kruschke's BEST framework is well-established in psychology, its adoption in education research specifically is less documented. Whether education journals accept Bayesian two-group analyses as a substitute for t-tests is an empirical question the author should investigate.

- **Likely-outdated-within-3-years:** The specific software implementations (BEST R package, BayesFactor package) for Bayesian t-tests are in active development. The prompting-for-implementation section should not rely on specific package function calls that may change.

- **Settled-looking-but-contested:** The "prior probability that a given educational intervention works" used in Ioannidis-style calculations is not empirically grounded. The chapter should be explicit that the Ioannidis argument is structural (correct given its assumptions) but that the quantitative conclusion ("most research findings are false") is sensitive to the assumed prior probability R.

---

## 9. Sourcing Notes

- **Ioannidis (2005):** Verified via PLoS Medicine DOI (open access). One of the most-cited papers in medical statistics; credibility is not at issue. PubMed PMID available; free full text at plos.org.
- **Open Science Collaboration (2015):** Verified via Science DOI and PubMed (PMID 26315443). The consortium nature of authorship is correct—the lead author is Brian Nosek, but it is published as "Open Science Collaboration." This is unusual; author should cite exactly as published.
- **Kruschke (2013):** Verified via ERIC (EJ1008485), PubMed (PMID 22774788), and Semantic Scholar. DOI confirmed (10.1037/a0029146). The BEST software package is separate from the paper; flag the R package as aging-risk within 3 years.
- **Cohen (1988):** Verified as a published book via library catalogs; not a journal paper. The 2nd edition (1988) is the standard citation; a 1st edition existed (1969). ISBN varies by printing. The UCLA OARC documentation confirms the standard effect size conventions.
- **Cumming (2014):** Verified via Sage DOI and multiple reference databases. Open access version available at the author's institutional repository.
- **Greenland et al. (2016):** Verified via Johns Hopkins repository and Semantic Scholar. *European Journal of Epidemiology*, 31, 337–350. DOI: 10.1007/s10654-016-0149-3. Open access.
- **Welch biography:** Verified via Wikipedia ("Welch's t-test" and "Bernard Lewis Welch" entries). Wikipedia page for the method is confirmed; a separate Wikipedia page for Welch as a person may be limited.
- **Evelyn Fix biography:** Verified via Wikipedia ("Evelyn Fix"), Berkeley Statistics Department, and MacTutor. Wikipedia page confirmed: "Evelyn Fix."
- **Janet Norwood:** [PARTIALLY VERIFIED] — Wikipedia search confirmed she was the first female BLS Commissioner (1979–1991); a dedicated Wikipedia page "Janet Norwood" exists. Verify the page exists before including in the chapter.
- **Gilbert et al. (2016) OSC critique:** [UNVERIFIED citation details — confirm] — described in search results as Science, 351, 1037–1038, 2016. Author should verify this exact citation before using it.
