# Chapter Research Pass — Orientation Summary

**Book:** Bayesian Probability (with LLMs) — Bear Brown LLC
**Date:** 2026-06-01
**Files produced:** 14 — `pantry/research-ch-00…13-*.md`, one per chapter, all 9 sections, 21–32 KB each.

*This is author orientation before drafting. It is not a pantry artifact. Every primary source was web-verified before citation; items the agents couldn't confirm are tagged `[UNVERIFIED — confirm]` in the files.*

---

## Coverage: strongest → weakest

**Strongest** (dense, fully-verified primary sources):
- **Ch 1** (medical test): Casscells 1978, Eddy 1982, Gigerenzer & Hoffrage 1995, ASA p-value statement (Wasserstein & Lazar 2016), Ioannidis 2005 — all DOI-verified; real legal cases (Sally Clark, *People v. Collins*).
- **Ch 4** (two groups): the replication-crisis literature is the richest in the book — Ioannidis 2005, Open Science Collaboration 2015, Kruschke 2013, Cohen 1988.
- **Ch 6** (model comparison): Akaike 1974, Schwarz 1978, Kass & Raftery 1995, Jeffreys 1961, Vehtari 2017 — all verified.
- **Ch 11** (classification/decision): Wald 1950, Berger 1985, Berkson 1944, Swets 1988; documented cases (COMPAS, Frey & Osborne).
- **Ch 12** (capstone): real, public, verified BLS/O*NET datasets with URLs.

**Weakest** (need author attention before drafting):
- **Ch 2** (prompting): no peer-reviewed evidence base exists for undergraduates using LLMs for comparative Bayesian/frequentist analysis. The chapter is original pedagogical design assembled from adjacent literature. Genuinely novel — and the fastest-aging chapter in the book.
- **Ch 5** (regression): math is solid (Gelman & Hill 2007), but the "advertising→sales" worked example has no documented real-world case; it's necessarily hypothetical.
- **Ch 7** (priors): two key sources unverified (Kass & Wasserman 1996; Gelman/Simpson/Betancourt volume); regulatory (EMA/FDA) positions need direct document retrieval.
- **Ch 10** (time series): ARIMA + Kalman are solid, but Bayesian-structural-time-series cases lack "real numbers a student can look up" (best anchor: Scott & Varian 2014).
- **Ch 13** (choosing): theory is well-sourced (Bayarri & Berger 2004, Efron 2005, Gelman & Shalizi 2013), but there's no published research on how *students* fail at writing method-justifications — the chapter's main deliverable.

---

## Cross-chapter patterns

- **Recurring sources** (build these into the bibliography as load-bearing): Ioannidis 2005 (Ch 1, 4, 8); Gelman & Hill 2007 (Ch 5, 9); Open Science Collaboration 2015 (Ch 4, 8); Gelman across the Bayesian chapters.
- **The prior-specification thread** runs through every Bayesian chapter — see top gap below.
- **Aging concentrates** in Ch 2 and every chapter's prompting section, plus the fairness material in Ch 11 (EU AI Act / FAccT in flux — flagged `[AGING]`). Keep this material structurally separable so it can be revised without touching the statistical core.

## The single highest-priority gap

**What a "weakly informative prior" concretely looks like, per problem, for an undergraduate.** Raised independently by three agents. It recurs in Ch 3 (a proportion on 0–1), Ch 4 (a mean on 0–100), Ch 5 (a regression slope in business units), Ch 7, Ch 8, Ch 9. Gelman's guidance lives on his blog and in Stan docs; no peer-reviewed, undergraduate-accessible consolidation exists. This is exactly where students will get stuck and where different LLMs will give inconsistent answers — so it's both the biggest pedagogical risk and, given the book's LLM-implementation premise, the place the thesis is most tested. Recommend the author write worked prior-specifications for each chapter rather than leaving them to student judgment.

### Other gaps worth pre-empting
1. **Ch 6 claim needs softening.** A 2025 preprint on Bayes-factor prior sensitivity undercuts the TOC's "Bayes factors give a probability AIC can't" framing. Present the dispute; PSIS-LOO is the more defensible practical tool.
2. **Ch 2 needs empirical validation** and will need rapid revision — treat as living content.
3. **Ch 12 action item:** the Frey-Osborne 702-occupation table has no confirmed standalone CSV from the authors. The companion site must host a digitized version or point to the related Mendeley dataset (not identical). Resolve before Ch 12 ships.

---

## AI Wayback Machine — diversity balance across all 14 chapters

The agents proposed ~40 candidates. Aggregate balance is decent but uneven:

- **Women surfaced (~10):** Hilda Geiringer (0), Florence Nightingale (1, 12), Grace Hopper (2), Gertrude Mary Cox (3), Evelyn Fix (4), Janet Norwood (4, 12), Helen M. Walker (5), Bertha Swirles Jeffreys (7), Timnit Gebru (11), Grace Wahba (13).
- **Non-Western / underrepresented:** Kolmogorov, Mahalanobis (×2), Akaike, Kálmán, Wald, Du Bois (Black American), Gebru (Ethiopian-American).

**Two problems to fix when figures are finally selected (post-draft pass):**

1. **Ch 9 (hierarchical) and Ch 10 (time series) skew entirely male** in the founding generation. For Ch 9 the agent suggests crediting **Jennifer Hill** in body text even if not the Wayback figure; Ch 10 needs a deliberate diverse pick.
2. **Jerzy Neyman is proposed in four chapters** (1, 3, 8, 13). Use him once at most; diversify the rest.

Best high-diversity, well-connected picks to prioritize: Cox (3), Norwood (4 or 12), Walker (5), Bertha Swirles Jeffreys (7), Gebru (11), Wahba (13), Du Bois (12).

*Figure selection is deliberately deferred to the post-draft Wayback pass — this is the curated shortlist for it.*
