<!--
    book.md
    BOOK DESCRIPTION & HIGH-LEVEL OUTLINE — your planning document.

    This file is for YOU, not the reader. It does not get compiled into
    the EPUB. Use it to think clearly about what the book is before you
    write it, and to keep yourself honest as you draft.

    Update freely as the book takes shape. Earlier versions belong in
    git history, not in this file.

    Back-filled from TIKTOC.md (the completed /g1 full TOC) so this
    planning file matches the authoritative spec. Where the TOC did not
    settle something, it is marked [NEEDS HUMAN INPUT].
-->

# Bayesian Probability

**Author:** Nik Bear Brown  
**Publisher:** Bear Brown LLC
<!-- Author attribution disagrees across planning files (Humanitarians AI /
     Nik Bear Brown / Bear Brown LLC). TIKTOC.md uses "Bear Brown LLC";
     adopted here for consistency. Confirm the canonical credit. -->

---

## One-Sentence Pitch

A hands-on statistics book that solves every problem twice — frequentist
first, then Bayesian, side by side — so the reader learns not just how to
run each analysis but how to choose between them.

## The Argument

Most introductory statistics is taught inside a single paradigm. Students
learn the frequentist machinery — p-values, confidence intervals,
significance tests — as if it were simply "statistics," and never see the
questions it structurally cannot answer. This book argues that competent
statistical practice requires holding both paradigms at once: solving the
same real problem both ways, seeing exactly where the frequentist approach
strains, and understanding what the Bayesian approach buys and what it costs.

The reader changes from someone who applies a default method to someone who
chooses a method. By the end, the answer to "frequentist or Bayesian?" is
never reflexive — it depends on what the decision-maker needs, whether prior
information exists and is defensible, how much data there is, and who will
receive the result. The book treats that judgment, not either paradigm, as
the skill worth building.

Implementation runs through LLM-generated code throughout (taught explicitly
in Chapter 2), so the reader spends cognitive effort on statistical reasoning
and verification rather than on coding from scratch — while learning to catch
the plausible-looking wrong answers an LLM will produce.

## The Gap

Single-paradigm intro texts (the standard frequentist sequence) never show
the reader what they're missing; pure Bayesian texts assume the reader has
already rejected frequentism. Neither teaches the *choice*. This book's gap
is the explicit, problem-by-problem comparison plus LLM-based implementation
at a $1 / Kindle Unlimited price point.

Candidate comparables (drawn from the pantry/ sources — confirm and sharpen):

- *Bayesian Statistics the Fun Way* (Kurt) — accessible Bayesian intro, but single-paradigm.
- *Statistical Rethinking* (McElreath) — referenced as the next step for full MCMC; graduate-level, code-heavy.
- *Bernoulli's Fallacy* (Clayton) — argues against frequentism polemically; not a how-to.
- *Bayesian Reasoning in Data Analysis* (D'Agostini); *Bayesian Theory* (Bernardo & Smith) — reference-grade, not teaching-first.

[NEEDS HUMAN INPUT — confirm the 3 comparables to position against and what each gets wrong.]

## The Reader

Primary: an undergraduate (or self-learner) taking applied statistics who
knows basic algebra and a little probability, can follow a formula, and
wants to analyze real data — but has only ever seen the frequentist toolkit.
They are trying to make defensible decisions from data and don't yet know
that the method they reach for is a choice.

After the book they can take a real dataset, implement both a frequentist
and a Bayesian analysis of the same question, articulate what each assumes
and where each fails, and justify a choice between them to a skeptic.

[NEEDS HUMAN INPUT — pin one specific named reader/course for the intake.]

## High-Level Outline

**Act One — Establish (Ch 1–4, plus Ch 0 prerequisites)**
The same question asked two ways. Establishes that the two paradigms answer
different questions, teaches LLM-assisted implementation, and runs the first
full side-by-side comparisons (proportions, two-group).

**Act Two — Build (Ch 5–9)**
The methods that make the divergence matter: regression, model comparison,
priors made explicit, sparse data, and hierarchical models — where the
Bayesian solution earns its added complexity.

**Act Three — Apply (Ch 10–13)**
Sequential/time-series updating, classification as decision under a loss
function, a full both-ways analysis of a self-chosen real dataset, and a
framework for choosing an approach — which is not always "Bayesian."

## Open Questions

(From the TIKTOC Open Questions Log.)

- [ ] Working title for the Kindle listing (cover, SEO, series positioning)
- [ ] Companion website URL and launch timeline (Chapter 12 depends on it; data downloaded)
- [ ] Which data-preparation reference book to point to (Ch 12)
- [ ] Does Ch 13 ship a printable decision-guide artifact?
- [ ] Does the book cite Clayton's *Bernoulli's Fallacy* explicitly?
- [ ] Does this carry the Irreducibly Human series mark?
- [ ] Canonical author credit (see attribution note above)
