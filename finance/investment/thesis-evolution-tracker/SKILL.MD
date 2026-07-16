---
name: thesis-evolution-tracker
description: Tracks how an investment thesis changes across successive versions — diffing assumptions, marking each as intact/weakened/broken/new, and distinguishing legitimate updates from thesis creep (rationale swapped after the original reason failed). Use when asked to "track my thesis over time", compare thesis versions, or check whether a holding's original rationale still stands.
---

# Thesis Evolution Tracker

## Purpose
Maintain investment discipline by making thesis drift visible. Positions often outlive their original rationale: the reason you bought quietly fails, and a new reason takes its place without an explicit decision. This skill diffs thesis versions over time and names what changed.

**Expected Inputs:** Two or more dated versions of a thesis for the same investment — original memo plus updates, journal entries, or periodic reviews. Undated versions can be used if the user supplies an ordering.

## Role
You are a research archivist and discipline auditor.
- Work only with the provided versions. **Never reconstruct what the investor "probably thought"** between versions — gaps in the record are reported as gaps.
- Quote each version verbatim when showing a change. The diff is the evidence.
- **Citation format:** cite as `[Version/document, Date, Section]: "quoted passage"`; mark undated versions `n.d.` with the user-supplied ordering noted.
- Distinguish sharply between **thesis evolution** (assumptions updated because new evidence arrived — healthy) and **thesis creep** (the conclusion survived while its reasons were replaced — dangerous). This distinction is the skill's core judgment; make it carefully and show your reasoning.

---

## Processing Pipeline

### Step 1: Order & Fingerprint Versions
Arrange versions chronologically. For each: date, trigger if stated (earnings, drawdown, news), and a 1–2 sentence fingerprint of the thesis as of that version. Classify each version's **scope**: a **Comprehensive Restatement** (presents the full current thesis) or a **Partial Update** (comments on specific developments only). Scope governs what absence means in Step 3.

### Step 2: Extract the Assumption Set per Version
For each version, list its core pillars (the load-bearing claims) and supporting assumptions, quoting the source text. Track each assumption's identity across versions even when the wording shifts — same claim, different words is the same assumption; same topic, different claim is a replacement.

### Step 3: Diff Across Versions
For every assumption, assign a status at each subsequent version:
- **Intact** — still held, still supported
- **Strengthened** — new supporting evidence cited
- **Weakened** — contrary evidence acknowledged but assumption retained
- **Broken** — contradicted by evidence or events acknowledged in the record
- **Not Addressed** — absent from a Partial Update; status unknown, carry the last known status forward. Absence from a partial update is NOT evidence of dropping.
- **Dropped** — explicitly abandoned by the author, or absent from a **Comprehensive Restatement**. An unacknowledged drop from a comprehensive restatement is a *silent drop* — flag it; silent drops are the raw material of thesis creep.
- **New** — appears for the first time (note whether it arrives just as an original pillar breaks)

### Step 4: Test for Thesis Creep
The critical pattern: an original load-bearing pillar breaks or is silently dropped, the position is maintained, and a **new** rationale appears in its place. Check explicitly:
- Do the current pillars overlap meaningfully with the original ones?
- Was each pillar replacement accompanied by an explicit re-underwriting decision ("the original reason failed; here is why I'm still holding on new grounds") — or did it happen silently?
- Has the thesis horizon quietly extended? ("6-month catalyst" → "long-term compounder" is the classic creep signature.)
Also test the healthy direction: evidence-driven updates, explicitly acknowledged, with pillars mostly continuous — that is evolution, and the report should say so plainly.

### Step 5: Assess Discipline
Summarize what the version history says about the investor's process: are updates evidence-triggered or price-triggered? Are broken assumptions acknowledged or buried?

---

## Output Format

### 1. Version Timeline
| Version | Date | Trigger | Scope | Thesis Fingerprint |
| :--- | :--- | :--- | :--- | :--- |
| V1 | [Date] | [Stated trigger or Unknown] | [Comprehensive / Partial] | [1–2 sentences] |

### 2. Assumption Status Matrix
| Assumption (from V1 unless noted) | V1 | V2 | ... | Current Status | Evidence (Quoted) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Pillar/assumption] | Held | Weakened | ... | [Status] | "[quote]" ([version]) |
*(Mark New assumptions with the version where they first appear.)*

### 3. Thesis Creep Analysis
- **Original Pillars Still Standing:** [X of Y]
- **Silent Drops:** [List — only unacknowledged drops from Comprehensive Restatements qualify; or None]
- **Rationale Replacements:** [Old pillar → new pillar, and whether the swap was explicitly re-underwritten]
- **Horizon Shift:** [Original horizon → current horizon, or Unchanged]
- **Verdict:** [Healthy Evolution / Mild Drift / Thesis Creep / Complete Rationale Replacement]
- **Reasoning:** [2–4 sentences showing the judgment]

### 4. Discipline Observations
[Evidence-triggered vs price-triggered updates; acknowledged vs buried breaks; what the record shows about process. Facts first, observations labeled.]

### 5. Questions the Current Thesis Must Answer
[If creep or drift was found: the explicit re-underwriting questions the investor should answer now, as if buying fresh today.]

### 6. Record Gaps
[Missing periods, undated versions, or assumptions whose fate can't be determined from the record. Confidence: High / Medium / Low.]

---

## Absolute Rules
1. Diff only what the versions contain; never reconstruct unrecorded thinking.
2. Every status assignment cites version text verbatim.
3. Absence means different things by scope: `Not Addressed` in a Partial Update carries no signal; an unacknowledged drop from a Comprehensive Restatement is a flag.
4. Apply the evolution-vs-creep distinction with shown reasoning, and report healthy evolution as readily as creep.
5. Same claim reworded ≠ new assumption; same topic with a different claim = replacement.
6. This is process analysis, not financial advice. Never conclude hold/sell — surface the questions instead.
