<!--
    outline.md
    TABLE OF CONTENTS — your chapter-level planning document.

    This is NOT the auto-generated TOC that appears in the EPUB
    (pandoc handles that via --toc in build.sh). This file is YOUR
    working outline: chapter titles, one-line descriptions, and the
    order of arguments before you start drafting.

    Keep it in sync with the actual chapter files in chapters/.
    When the outline diverges from the drafts, update one or the other —
    don't let them drift.

    Back-filled from TIKTOC.md (the completed /g1 full TOC).
-->

# Bayesian Probability — Outline

**Author:** Nik Bear Brown  
**Publisher:** Bear Brown LLC

---

## Front Matter

- **Copyright**
- **Dedication** *(optional)*
- **Preface** — why solve everything twice; the comparative method and the $1 / Kindle Unlimited intent

## Introduction

Statistics is usually taught inside one paradigm. This book teaches the
choice between two by solving every problem both ways. Maps the comparative
chapter anatomy, the explicit-asymmetry rule, and the LLM-implementation
approach the reader will use throughout.

## Chapters

**Chapter 0 — Probability Foundations** *(prerequisite resolver; Week 0, not in the semester budget)* — conditional probability, Bayes' theorem as arithmetic, nothing more.

1. **The Same Question, Two Answers** — the medical-test problem shows what a p-value can't say and introduces the Bayesian answer to the question the test actually asks.
2. **Prompting for Statistics** — using an LLM as a statistical implementation partner: describe precisely, verify critically, iterate. The skill every later chapter assumes.
3. **Counting and Estimating** — the binomial/proportion problem both ways; the first full side-by-side and the cleanest contrast between confidence and credible intervals.
4. **Comparing Two Groups** — the t-test and its Bayesian analog; a first encounter with why significant results don't always replicate (Ioannidis).
5. **Regression, Both Ways** — OLS vs. Bayesian regression; the lines converge, the decision-relevant outputs diverge. The asymmetry is named here.
6. **Model Comparison** — AIC / likelihood-ratio vs. Bayes factors; ranking versus probability, and what to do when models are close.
7. **Priors: Where Does Your Assumption Come From?** — every analysis has priors; frequentist methods hide theirs, Bayesian methods name theirs. Same data, three priors.
8. **When Data Is Sparse** — small samples, rare events, the winner's curse, and Bayesian shrinkage as principled regularization.
9. **Hierarchical Problems** — grouped data and partial pooling; the sharpest divergence and the most pronounced Bayesian asymmetry (flagged at chapter open).
10. **Time and Sequence** — time series and sequential updating, where Bayesian inference is most intuitive: today's posterior is tomorrow's prior.
11. **Classification and Decision** — classification as inference under a loss function; the threshold is a decision under costs, not a statistic.
12. **A Real Problem, Both Ways** — guided capstone: one self-selected real dataset, both frameworks, a written comparison answering six required questions.
13. **Choosing** — not a verdict but a framework for selecting an approach based on the problem, the data, the decision, and the audience.

## Back Matter

- **Acknowledgments**
- **About the Author**
- **Notes** *(if using endnotes)*
- **References** — incl. McElreath (*Statistical Rethinking*) as the next step; D'Agostini, Bernardo & Smith; Clayton (*Bernoulli's Fallacy*) if cited
- **Index** *(print only)*

---

## Notes on Order

The order is doing real work; chapters are not swappable.

- **Ch 0 → 1:** Ch 1's Bayesian solution needs conditional probability and Bayes' theorem. Ch 0 closes that gap before Ch 1 opens.
- **Ch 1 → 2:** Ch 1 deliberately leaves implementation open ("do it by hand for three prevalences"); Ch 2 then teaches LLM-assisted implementation so every later chapter can lean on it.
- **Ch 2 is load-bearing:** every chapter from 3 on includes a prompting section that assumes the Ch 2 skill. Skipping Ch 2 breaks the rest of the book.
- **Act One (1–4)** establishes that the paradigms answer different questions on simple, well-specified models. **Act Two (5–9)** introduces methods where the Bayesian solution returns answers the frequentist one structurally cannot, building to hierarchical models (the complexity/payoff peak). **Act Three (10–13)** applies the toolkit and ends on judgment.
- **Asymmetry rule:** from Ch 5 on, chapters spend more space on the Bayesian solution because the frequentist analog is simpler. Named as evidence, not apology — first at Ch 5, most pronounced at Ch 9.
- **Transition Act One→Two:** reader can run and interpret both a frequentist and a Bayesian analysis of a simple problem and state what each leaves unanswered.
- **Transition Act Two→Three:** reader can specify priors, compare models, and handle sparse/grouped data — i.e., make the modeling choices the capstone requires.
