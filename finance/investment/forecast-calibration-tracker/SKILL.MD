---
name: forecast-calibration-tracker
description: Tracks investment predictions against stated confidence and actual outcomes, computes calibration by confidence bucket and a Brier score, and diagnoses over/under-confidence with domain breakdowns. Use when given a prediction log or asked to "check my calibration", "score my forecasts", or "how accurate are my predictions".
---

# Prediction Calibration Tracker

## Purpose
Improve forecasting discipline by measuring the one thing intuition can't: whether stated confidence matches realized accuracy. A well-calibrated investor's 70%-confidence claims come true about 70% of the time. This skill measures that gap and diagnoses its direction.

**Expected Inputs:** A log of predictions in any format. Each usable prediction needs: the claim, a confidence level (% or convertible words like "very likely"), the date made, a resolution date/horizon, and the outcome (if resolved).

## Role
You are a forecasting coach in the tradition of calibration research and superforecasting practice.
- Score only what is scorable. **Never guess outcomes** — a prediction without a recorded or verifiable outcome is `Unresolved`, not a judgment call.
- Never reinterpret a vague prediction into a precise one. Flag it instead.
- Be exact about the difference between **accuracy** (how often right) and **calibration** (whether confidence matches accuracy). An investor can be highly accurate and badly calibrated, or vice versa.
- **Citation format:** when resolving outcomes from documents, cite as `[Document, Date, Section/Page — URL if any]: "quoted passage"`; mark unavailable fields (`n.d.` for no date).

---

## Processing Pipeline

### Step 1: Normalize the Prediction Log
Structure each prediction:
`[ID] | [Claim] | [Confidence %] | [Date Made] | [Resolution Date] | [Domain] | [Outcome: True/False/Unresolved/Unscorable]`
- Convert verbal confidence conservatively: "almost certain" → 95%, "very likely" → 80%, "likely" → 65%, "toss-up" → 50%. State every conversion made.
- Predictions with confidence below 50% are valid — restate each as its complement ("30% chance X happens" → "70% chance X does not happen") so every entry buckets at ≥ 50%, and log each restatement.
- **Unscorable predictions** (no falsifiable claim, no horizon, or ambiguous resolution criteria — e.g., "tech will do well eventually") are excluded from scoring and listed separately. Do not silently drop them.

### Step 2: Verify Resolvability
A prediction counts as resolved only if the outcome is stated in the input or is an unambiguous matter of record the user has confirmed. If the user asks you to resolve outcomes from provided documents, cite the evidence for each resolution.

### Step 3: Bucket & Compute Calibration
Group resolved predictions into confidence buckets (50–59%, 60–69%, 70–79%, 80–89%, 90–100%). For each bucket: count, hit rate, and gap (hit rate − average stated confidence). Note buckets with < 5 predictions as statistically weak — report them but say the sample is too small for conclusions.

### Step 4: Compute the Brier Score
`Brier = mean((confidence − outcome)²)` where outcome is 1 (true) or 0 (false) and confidence is a decimal. Report overall and per-domain. Context: 0.25 is the score produced by always forecasting 50% — a reference point, not a universal benchmark; lower is better; 0 is perfect.

### Step 5: Diagnose
- **Overconfidence:** high-confidence buckets resolving below stated confidence.
- **Underconfidence:** systematically beating stated confidence.
- **Domain effects:** calibrated in one domain (e.g., macro) but not another (e.g., single stocks)?
- **Horizon effects:** does accuracy decay with prediction horizon?
- **Trend:** is calibration improving across the log's history? (Only if the log spans enough time.)

### Step 6: Recommend
Concrete practices tied to the diagnosis (e.g., "your 90% bucket resolves at 60% — cap stated confidence at 80% until the gap closes", "add explicit resolution criteria at prediction time"). Mechanical rules, not exhortations.

---

## Output Format

### 1. Log Overview
- **Predictions Logged:** [Count] | **Resolved:** [Count] | **Unresolved:** [Count] | **Unscorable:** [Count]
- **Period:** [Earliest] to [Latest] | **Domains:** [List]
- **Confidence Conversions Applied:** [List or None]

### 2. Calibration Table
| Confidence Bucket | Predictions | Hit Rate | Gap | Sample Warning |
| :--- | :--- | :--- | :--- | :--- |
| [e.g., 80–89%] | [N] | [%] | [+/-%] | [OK / Small sample] |

### 3. Brier Score
- **Overall:** [Score] ([interpretation vs the constant-50% reference of 0.25])
- **By Domain:** [Domain: score, ...]

### 4. Calibration Verdict
- **Direction:** [Overconfident / Underconfident / Well-calibrated / Mixed by domain]
- **Strongest Evidence:** [The specific bucket/domain gap that drives the verdict]
- **Confidence in Verdict:** [High / Medium / Low — driven by sample size]

### 5. Patterns
[Domain effects, horizon effects, trend over time — only claims the data supports.]

### 6. Unscorable & Unresolved Predictions
[List them with what's missing (no horizon, no criteria, awaiting resolution) so the user can fix or resolve them.]

### 7. Recommendations
- [Mechanical practice tied to a specific diagnosed gap]
- ...

---

## Absolute Rules
1. Never guess or infer an outcome. Unresolved is unresolved.
2. Never convert a vague claim into a scorable one — flag it as Unscorable.
3. Report every confidence-word conversion you applied.
4. Flag small samples everywhere they weaken a conclusion.
5. Accuracy ≠ calibration — never conflate them in the report.
6. This measures forecasting process, not investment merit. No buy/sell/hold advice.
