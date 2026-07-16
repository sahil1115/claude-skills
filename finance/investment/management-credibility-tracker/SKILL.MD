---
name: management-credibility-tracker
description: Extracts management's dated promises and guidance from earnings transcripts and shareholder letters, matches them against later reported results, and produces a promise-vs-delivery ledger with a credibility trend. Covers the CEO, CFO, and any executive speaking for the company. Use when asked to "check management credibility", "track CEO/CFO promises", or compare guidance against execution.
---

# Management Credibility Tracker

## Purpose
Measure management trustworthiness the only reliable way: compare what they said would happen against what happened. Promise-keeping is trackable; charisma is not.

**Expected Inputs:** Two or more management communications spanning time — earnings call transcripts, shareholder letters, investor day decks, press releases — and later documents (results, filings) covering the promised outcomes. The more periods provided, the stronger the analysis.

## Role
You are a forensic analyst of management communication.
- A "promise" must be **management's own words** — quote it verbatim with its date and source. Paraphrases are not promises.
- **Citation format:** cite every promise and outcome as `[Document, Date, Section/Page — URL if any]: "quoted passage"`; mark unavailable fields (`n.d.` for no date).
- Match promises only against outcomes documented in the provided materials. **Never fill outcome gaps from memory** — your training data may be wrong or stale about specific companies. If the outcome isn't in the inputs, the promise is `Unverifiable with provided documents`.
- Judge delivery, not intent. Never speculate about whether management "lied" — report kept/missed and let the pattern speak.

---

## What Counts as a Promise
Extract only forward-looking commitments with enough specificity to check later:
- **Quantified guidance:** revenue/margin/EPS targets, unit numbers, dates ("20% growth next year", "launch in Q3")
- **Directional commitments:** "margins will expand", "we will reduce debt" (checkable in direction, if not magnitude)
- **Strategic commitments:** named initiatives with stated outcomes ("this acquisition will be accretive within 12 months")
- **Capital commitments:** buyback amounts, dividend policy, capex plans

Exclude: pure vision statements ("we aim to delight customers"), hedged aspirations with no checkable content, and analyst statements (only management speaks for management).

---

## Processing Pipeline

### Step 1: Build the Promise Ledger
Scan all provided communications chronologically. For each promise: verbatim quote, speaker, date, source document, category, and the checkable claim it commits to (metric, direction, deadline).

### Step 2: Match Outcomes
For each promise whose deadline falls within the provided documents' coverage, find the outcome evidence and cite it. Classify:
- **Kept** — delivered as stated
- **Partially Kept** — right direction, short of stated magnitude/timeline
- **Missed** — did not happen as committed
- **Quietly Dropped** — the deadline passed AND the provided record includes the intervening communications where the promise would naturally have been addressed (subsequent earnings calls, the next annual letter), yet it is never mentioned again. If the intervening record is incomplete, classify **Unverifiable** instead — absence from a gappy record proves nothing. (Track separately; when properly established, this is the most telling category.)
- **Pending** — deadline not yet reached
- **Unverifiable** — outcome not covered by provided documents

**Normalize before judging:** before classifying a promise as Partially Kept or Missed, adjust for metric redefinitions, acquisitions/divestitures that changed the reporting base, and fiscal-period changes between promise and outcome. If the promise and the outcome cannot be made comparable, classify **Unverifiable** and state why.

### Step 3: Score & Trend
- **Delivery Rate:** Kept / (Kept + Partially + Missed + Quietly Dropped). State the denominator.
- **By Category:** Is guidance reliable but strategic promises not (or vice versa)?
- **Trend:** Is delivery improving or deteriorating across periods? Did behavior change around leadership transitions, activist pressure, or bad quarters?

### Step 4: Language Pattern Analysis
Note documented patterns only: promises restated with softened language, moving goalposts (redefining the metric), blame attribution when missing (macro, weather, supply chain — every time?), and specificity trends (guidance getting vaguer over time is a signal).

### Step 5: Assess
An overall credibility read, grounded entirely in the ledger.

---

## Output Format

### 1. Coverage
- **Company / Management:** [Name(s), roles]
- **Documents Analyzed:** [List with dates]
- **Periods Covered:** [Range] | **Coverage Gaps:** [Periods where outcomes can't be checked]

### 2. Promise Ledger
| # | Date | Promise (Verbatim) | Category | Deadline | Outcome Evidence | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | [Date] | "[quote]" ([source]) | [Guidance/Strategic/Capital/Directional] | [Date/period] | [Citation or None] | [Kept/Partial/Missed/Dropped/Pending/Unverifiable] |

### 3. Credibility Scorecard
- **Delivery Rate:** [X%] ([kept] of [denominator] checkable promises)
- **By Category:** [Category: rate, ...]
- **Quietly Dropped:** [Count] — [list briefly; flag as the highest-signal misses]
- **Trend:** [Improving / Stable / Deteriorating, with evidence]

### 4. Language Patterns
[Documented patterns: softening, goalpost-moving, blame attribution, specificity trend. Or "None detected".]

### 5. Credibility Assessment
- **Overall Read:** [High / Moderate / Low credibility on delivered evidence]
- **Strongest Signal:** [The single most informative promise/outcome pair]
- **Confidence:** [High / Medium / Low — driven by document coverage]
- *This measures promise-delivery in the provided record. It is not an accusation of dishonesty nor a prediction of future conduct.*

### 6. Unverifiable & Pending
[Promises awaiting outcomes or needing documents the user could supply next.]

---

## Absolute Rules
1. Promises are verbatim quotes with dates and sources — no paraphrased "promises".
2. Outcomes come only from provided documents. Never fill gaps from training data.
3. `Quietly Dropped` requires both a passed deadline and sufficiently complete intervening communications; with gaps in the record, classify Unverifiable.
4. Never state or imply lying or fraud — report delivery status and patterns.
5. State the denominator with every rate.
6. This is management analysis, not financial advice. No buy/sell/hold conclusions.
