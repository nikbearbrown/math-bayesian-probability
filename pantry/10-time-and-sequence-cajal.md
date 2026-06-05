# CAJAL Figure Plans — Chapter 10: Time and Sequence

**Chapter:** 10 — Time and Sequence
**Figures planned:** 2
**Plan date:** 2026-06-01

---

## Figure 10.1 — Sequential Updating: Posterior Narrowing Week by Week

**Suggested filename:** 10-sequential-updating-narrowing.svg
**Figure type:** Timeline / progression — multi-stage posterior fan chart

**One-sentence concept:** As each new week of demand data arrives, the Bayesian posterior predictive distribution for future demand narrows and its center tracks the actual series — making concrete the principle that today's posterior is tomorrow's prior.

**S — Specification:** Single-panel wide layout; full textbook column (170 mm wide) × approx. 120 mm tall at 300 DPI; vector SVG.

**C — Content:**
Four time snapshots along a single horizontal time axis (weeks 1–65):
- Snapshot 1 (week 10): wide posterior fan centered near 8,500 units — uncertainty large.
- Snapshot 2 (week 26): narrower fan, center near 9,300 — prior weeks have updated beliefs.
- Snapshot 3 (week 40): narrower still, center near 10,100 — trend becoming clear.
- Snapshot 4 (week 52): tightest observed-period fan, center ≈ 10,780 — posterior well-concentrated.
Plus a 6-item forecast zone (weeks 53–65) showing the widening predictive fan from week 52 forward.
A thin solid line traces the actual weekly demand observations (approximately 8,000 at week 1, rising to ≈ 11,000 at week 52).
A horizontal dashed reference line at the 10,000-unit reorder threshold.

**O — Organization:** Horizontal time axis (week number, left to right); vertical axis = demand in units (6,000–14,000). The four snapshot fans are shaded uncertainty bands (darker center = higher probability density; lighter outer band = lower density). The forecast zone after week 52 expands rightward as a wider shaded fan. The observed series line runs through all fans. The 10,000-unit threshold line runs across the full width. Left-to-right flow encodes time progression. Total labeled elements: 4 snapshot labels + observed-series line + threshold line + forecast zone boundary = 7 labeled components, within the 8-component limit.

**P — Presentation:**
- Observed demand line: Black #000000, weight 1.5 pt.
- Posterior uncertainty bands (inner 50% CrI): Blue #0072B2 at 40% opacity — primary structural anchor.
- Posterior uncertainty bands (outer 95% CrI): Blue #0072B2 at 15% opacity.
- Forecast fan (weeks 53–65, outer 95% CrI): Sky Blue #56B4E9 at 20% opacity — distinct from historical posterior to signal forward projection.
- Forecast fan center line (posterior predictive mean): Blue #0072B2, weight 1 pt, dashed.
- Reorder threshold horizontal dashed line: Vermillion #D55E00, weight 1 pt — marks decision-critical boundary.
- Snapshot week labels: Black #000000, small text outside top of each fan.
- Background: white; no fill panels; bottom and left spines only.

**E — Exclusions:**
- Do not show ARIMA prediction intervals in this figure — this figure is the Bayesian sequential updating story; the ARIMA comparison is text and table.
- Do not show the Kalman gain formula or any mathematical notation.
- Do not plot individual MCMC draws or trace plots.
- Do not show more than four historical snapshots — adding more exceeds the 8-component limit and blurs the "narrowing" message.
- Do not show a separate legend for the two shading levels of the CrI — caption carries this.
- Do not use 3D perspective, gradients other than opacity, or drop shadows.
- Do not add axis tick marks at every week — sparse ticks (weeks 0, 10, 20, 30, 40, 52, 65) only.
- Do not show the posterior for the hidden state (μ_t) separately from the predictive distribution for observed demand (y_t).

**Caption (draft):** Sequential updating of the Bayesian structural time series model on 52 weeks of weekly demand; each fan shows the 50% (darker) and 95% (lighter) posterior uncertainty at that week; the fan narrows as observations accumulate and the underlying trend becomes clear; the dashed red line marks the 10,000-unit reorder threshold; the blue fan beyond week 52 is the posterior predictive distribution for weeks 53–65.

**Accuracy check (figure-checker):**
- The demand series must trend upward from approximately 8,000 (week 1) to approximately 11,000 (week 52) — a downward or flat trend contradicts the chapter's stated data structure.
- The posterior fan at week 52 must be visibly narrower than the fan at week 10 — if they are similar widths, the "narrowing" lesson is lost.
- The forecast fan (weeks 53–65) must widen as it extends further into the future — the opposite (narrowing forecast) would be mathematically wrong.
- The posterior mean at week 53 must fall near 10,780 units (chapter text value) — verifiable at the center of the week-53 forecast.
- The reorder threshold line at 10,000 must intersect the forecast fan, not lie entirely below or above it — the chapter's decision context is that demand is near the threshold.
- Y-axis must start at 0 or at a clearly labeled non-zero value with a break symbol if truncated; if showing only 6,000–14,000, a break must be explicitly marked per the Proportional Ink Rule.

---

## Figure 10.2 — ARIMA Point Forecast vs. Bayesian Predictive Distribution: Week 53 Comparison

**Suggested filename:** 10-arima-vs-bsts-week53.svg
**Figure type:** Comparison panels — two-panel distribution comparison

**One-sentence concept:** The ARIMA model produces a symmetric point-forecast-plus-interval that cannot directly answer the manager's question, while the Bayesian structural time series model produces a full predictive distribution from which P(demand > 10,000) = 0.69 is read directly.

**S — Specification:** Two-panel side-by-side layout; full textbook column (170 mm wide) × approx. 100 mm tall at 300 DPI; vector SVG.

**C — Content:**
Panel 1 — ARIMA forecast display:
- A horizontal number line (x-axis) showing demand from 6,000 to 16,000 units.
- A symmetric bracket or bar marking the 95% prediction interval [8,200, 14,600].
- A single point marker at the point forecast 10,840 units.
- A vertical dashed line at the 10,000-unit threshold.
- The region above 10,000 is not shaded (ARIMA cannot directly assign probability to it).
- Label: "ARIMA(1,1,1)" and "P(demand > 10,000) = ?"

Panel 2 — BSTS predictive distribution display:
- The same horizontal number line scale.
- A smooth bell-shaped predictive density curve centered near 10,780 units with SD ≈ 1,560.
- The area to the right of 10,000 units shaded (= 0.69 of total area).
- The area to the left shaded differently (= 0.31).
- The 10,000-unit threshold vertical dashed line.
- Label: "BSTS posterior predictive" and "P(demand > 10,000) = 0.69"

**O — Organization:** Two panels side by side, sharing the same x-axis scale (6,000–16,000 units) for direct comparison. Panel 1 on the left (ARIMA), Panel 2 on the right (BSTS). Each panel has its own label at the top. The threshold line appears in both panels at the identical x-position. Panels are separated by a narrow gap, not a divider bar.

**P — Presentation:**
- ARIMA interval bracket and point: neutral gray #999999 for the bracket, Black #000000 for the point marker — the ARIMA output is structural but not the answer.
- ARIMA "?" annotation: Vermillion #D55E00 — marks the gap (cannot answer the question).
- BSTS density curve outline: Blue #0072B2, weight 1.5 pt.
- BSTS shaded area right of threshold (P = 0.69): Bluish Green #009E73 at 50% opacity — positive, the answerable region.
- BSTS shaded area left of threshold (P = 0.31): light gray at 30% opacity.
- Threshold line both panels: Vermillion #D55E00, weight 1 pt, dashed.
- Background: white; bottom spine only (no y-axis tick marks needed for Panel 1; Panel 2 y-axis shows relative density with no numerical tick needed, just axis line).

**E — Exclusions:**
- Do not show week-by-week time series in this figure — this is week-53 forecast only; the time series is Figure 10.1.
- Do not show the BSTS posterior on the hidden state μ_53 separately from the predictive distribution for observed demand y_53 — show only the predictive (observable) distribution.
- Do not add numerical tick marks on the y-axis of Panel 2 (relative density axis) — only the shape and shaded area matter.
- Do not show the Kalman filter update equations.
- Do not show ARIMA model-selection diagnostics (ACF, PACF).
- Do not label the 0.69 and 0.31 areas both with percentages and fractions — one form only (decimals: 0.69, 0.31).
- Do not use 3D, gradients, or drop shadows.
- Do not put the BSTS predictive mean label (10,780) on the figure — caption carries it.

**Caption (draft):** Week-53 forecast comparison: the ARIMA(1,1,1) prediction interval [8,200–14,600] with point forecast 10,840 (left panel) cannot directly state P(demand > 10,000), while the Bayesian structural time series posterior predictive distribution (right panel, mean 10,780, SD 1,560) yields P(demand > 10,000) = 0.69 by direct integration over the shaded region.

**Accuracy check (figure-checker):**
- The ARIMA bracket endpoints must match the chapter text exactly: [8,200, 14,600]; point forecast 10,840.
- The BSTS curve mean must lie near 10,780, visually to the right of the 10,000 threshold — if the mean is to the left of the threshold, the 0.69 probability cannot be correct.
- The shaded right-of-threshold area must appear to be roughly 69% of the total density area — a rough visual check: the center (10,780) is slightly above the threshold (10,000), so slightly more than half the area falls to the right; 0.69 is consistent with this geometry.
- Both panels must use the same x-axis scale; the threshold line must appear at the same x-position in both panels.
- The ARIMA bracket center (10,840) and BSTS mean (10,780) must be visually close but not identical — they are different models, not the same estimate.
- BSTS curve must be bell-shaped and unimodal — a bimodal or skewed-left curve would misrepresent a normal predictive distribution.
