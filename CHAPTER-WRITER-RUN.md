# Chapter Writer — Run Report

**Book directory:** `books/math-bayesian-probability/`
**Date:** 2026-06-01
**TIKTOC.md:** found, 14 chapters (Ch 0 + 1–13)
**book.md:** found (no named voice/anatomy → Feynman-textbook voice inferred; comparative anatomy from TIKTOC/chapters-spec)

---

## Chapters written this run (14, ~60,600 words)

| File | Words | Sources | [verify] | Mechanism deep-dived | [contested] |
|---|---|---|---|---|---|
| 00-probability-foundations | 2,453 | 7 | 1 | P(A\|B) ≠ P(B\|A), via the Sally Clark fallacy | 0 |
| 01-the-same-question-two-answers | 3,167 | 9 | 0 | Why the rare-disease false-positive pool swamps true positives | 0 |
| 02-prompting-for-statistics | 3,788 | 7 | 3 | The "correct code / wrong interpretation" LLM failure mode | 0 |
| 03-counting-and-estimating | 4,175 | 5 | 0 | Beta-Binomial conjugate update; CI vs credible interval | 0 |
| 04-comparing-two-groups | 4,765 | 8 | 2 | Ioannidis PPV — replication crisis as structural math | 1 |
| 05-regression-both-ways | 4,954 | 8 | 2 | OLS = MAP under a flat prior; posterior predictive; asymmetry named | 1 |
| 06-model-comparison | 4,198 | 7 | 0 | Bayes factor via marginal likelihood; prior sensitivity vs PSIS-LOO | 1 |
| 07-priors | 4,272 | 7 | 4 | Normal-Normal update under three priors; the hidden flat prior | 0 |
| 08-when-data-is-sparse | 4,534 | 9 | 2 | Type M/S errors, winner's curse, shrinkage | 0 |
| 09-hierarchical-problems | 4,807 | 6 | 0 | Partial pooling via λ = τ²/(τ² + σ²/n) | 0 |
| 10-time-and-sequence | 4,586 | 6 | 3 | Kalman filter as exact Bayesian sequential updating | 0 |
| 11-classification-and-decision | 4,638 | 8 | 3 | Optimal threshold p* = c_FP/(c_FP + c_FN) | 2 |
| 12-a-real-problem-both-ways | 4,653 | 7 | 1 | Six-question scaffold; the P(outcome>threshold) gap | 1 |
| 13-choosing | 5,642 | 15 | 3 | Five-question selection framework; freq/Bayes convergence | 2 |

All chapters carry: Bloom-labeled objectives, the frequentist-first→Bayesian comparative spine, a worked example with lesson + limit, common misconceptions, one AI Wayback Machine figure, "What would change my mind," and "Still puzzling." Ch 0 omits "What would change my mind" by design (prerequisite resolver); Ch 12 has no traditional exercises by design (the chapter is the exercise).

## Chapters skipped (pre-existing)
- `00-frontmatter.md`, `00-introduction.md`, `99-back-matter.md` — **not overwritten**. See blocker note below: the intro/frontmatter are stale and mismatched.

## Blockers
None. All 14 chapters drafted.

## Thin-pantry chapters
None — every chapter had a verified pantry research file.

## [verify] flags requiring author attention (publication-stage checks)
- **Ch 2:** LLM-reliability sources are 2025 preprints (arXiv:2511.04213, 2511.07628) + a Frontiers 2025 paper with unconfirmed author list — all labeled `[CURRENT — flag for revision]`. Highest aging risk in the book.
- **Ch 7:** FDA 2026 draft-guidance status, EMA ICH E9(R1) language, and the Gelman/Simpson/Betancourt 2017 volume/page need confirmation.
- **Ch 10:** M4/M5 competition citation (Makridakis 2020); Chronos/TimeGPT model status; BLS seasonal-adjustment note.
- **Ch 11:** Gelman et al. 2008 weakly-informative-priors cite; Arntz/OECD 2016 full cite; EU AI Act enforcement timeline (`[AGING]`).
- **Ch 13:** FDA 2019 guidance title/URL; Berry 2006 volume/page.
- **Ch 12:** Frey-Osborne 702-occupation table has no confirmed standalone CSV from the authors — companion site must pin a version or use the related Mendeley dataset (not identical).

## Contested claims flagged (handled honestly, not suppressed)
- **Ch 6:** Bayes factors are themselves prior-sensitive (2025 Bayes-Factor-Reversal result) — undercuts the clean "BF gives a probability AIC can't" claim; PSIS-LOO offered as the more defensible tool. `[contested]`
- **Ch 4 / Ch 5:** replication-crisis causation is assumption-dependent; posterior-predictive vs conformal prediction is a live area.
- **Ch 11:** Frey-Osborne 47% vs Arntz 9% automation estimates left unresolved; COMPAS fairness-criteria incompatibility (Chouldechova) stated.
- **Ch 13:** replication crisis as structural-vs-user-error; empirical-Bayes epistemics.

## Mechanism summary (one line each)
See the table above — every chapter names and traces one mechanism on the page rather than gesturing at it.

## AI Wayback Machine figures selected (diversity across the set)
Geiringer (0), [Bayes denominator case] (1), Hopper (2), Mahalanobis (3), Fix (4), Walker (5), Akaike (6), Bertha Swirles Jeffreys (7), Diaconis (8), Rubin (9, with Jennifer Hill credited in a footnote), Kálmán (10), Wald (11), Du Bois (12), Wahba (13). Five women; Indian, Japanese, Hungarian, and Black-American representation. Note: Ch 9–10 founding generation remains male-heavy — the post-draft figure pass should revisit.

---

## Two things that need YOUR decision (not drafting gaps)

1. **The front matter is stale and contradicts the book.** `00-introduction.md` and `00-frontmatter.md` describe a *different* book — a generic "execution vs judgment / using AI well" template. The introduction literally says "Chapter sequence pending" and never mentions frequentist/Bayesian comparison. Now that 14 real chapters exist, these should be rewritten to match. I left them untouched (no `--force`). Want me to rewrite the intro + preface from the actual TIKTOC?

2. **Author attribution is now four-way inconsistent:** `00-frontmatter.md` says "Humanitarians AI Incorporated (501c3)"; planning files variously say "Humanitarians AI," "Nik Bear Brown," and "Bear Brown LLC." Give me the canonical credit and I'll normalize every file in one pass.

## Note on the themes file
Your instruction referenced `97-fundamental-themes.md` (to weave in, then convert to an appendix). **No such file exists** in `chapters/` (either spelling), so there was nothing to weave or convert. If you have one elsewhere, point me to it and I'll fold its themes through the chapters and finalize it as appendix `97-fundamental-themes.md`.

---

**Log:** `logs/log.csv` (14 rows).
**Next step:** author review of `chapters/` before anything leaves that directory. Recommended first passes — (a) the prior-specification gap flagged in the research summary, which touches Ch 3–9; (b) the `[verify]` list above.
