# Investment Analysis Skills

Ten decision-support skills for investors. They share the same design rules: evidence-cited findings, `Unknown` instead of guesses, confidence levels on judgments, and **no buy/sell/hold advice** — they improve your process, not replace your judgment.

## Installation

Copy a skill's folder into your Claude Code skills directory (e.g., `.claude/skills/` in your project or `~/.claude/skills/` globally), then invoke it by name (e.g., `/investment-thesis-red-team`) or just describe the task — the trigger phrases in each skill's description let Claude pick it up automatically.

---

## How to Use Each Skill

### 1. investment-thesis-red-team
**What it does:** Attacks your investment thesis like a professional short seller — steelmans it first, then audits every load-bearing assumption, builds the strongest bear case, and defines observable kill criteria.

**How to use:**
1. Write your thesis down (a memo, or even rough notes — but the more explicit your assumptions, the better the audit).
2. Attach supporting research you relied on: annual reports, transcripts, industry data. The skill only attacks with evidence from what you provide — it will not invent market data.
3. Invoke the skill with the thesis and materials.
4. Read the Assumption Audit table first (which assumptions are Solid vs Unsupported), then the Kill Criteria — those become your monitoring checklist.

**Inputs:** thesis + supporting documents. **Output:** assumption audit, bear case, kill criteria, 1–10 risk score with survivability band.

### 2. investment-bias-auditor
**What it does:** Reads your trading/decision journal and finds documented behavioral biases (loss aversion, FOMO, revenge trading, anchoring, and 6 more), each backed by your own quoted words, plus a 0–100 tilt score and mechanical guardrails.

**How to use:**
1. Keep a journal — even brief dated entries ("Sold X today because…") are enough. Ten or more entries gets you a numeric score; fewer gets a qualitative rating.
2. Optionally include your trade history (dates, sizes, entries/exits) — it unlocks the severity component of the score.
3. Invoke the skill with the journal. Account numbers and personal identifiers get masked automatically.
4. Adopt the guardrails table — each is a checkable rule (cooling-off periods, size caps), not vague advice.

**Inputs:** journal entries, optional trade history. **Output:** evidence-quoted bias table, tilt score with components, guardrail rules.

### 3. forecast-calibration-tracker
**What it does:** Compares your predictions' stated confidence against how often they actually came true. Reports calibration by confidence bucket, a Brier score, and whether you're systematically over- or under-confident.

**How to use:**
1. Log predictions as you make them: the claim, a confidence % (sub-50% is fine — it gets restated as the complement), the date, and a resolution deadline. Vague claims with no deadline are flagged Unscorable, so write falsifiable ones.
2. Record outcomes as predictions resolve (or provide documents the skill can resolve them from — it will cite each resolution).
3. Invoke the skill with the log. Re-run quarterly as more predictions resolve.
4. Act on the verdict: if your 90% bucket resolves at 60%, cap your stated confidence until the gap closes.

**Inputs:** prediction log with confidence and outcomes. **Output:** calibration table by bucket, Brier score, over/under-confidence verdict, unscorable list.

### 4. investment-decision-reviewer
**What it does:** Scores the *process* behind a decision independent of its outcome — 8 dimensions (information gathering, alternatives, base rates, sizing, pre-commitment, …) — then places it on the skill/luck matrix. Stops you learning the wrong lesson from a lucky win or an unlucky loss.

**How to use:**
1. Write down what you knew and reasoned **at decision time** — the skill quarantines everything learned afterward.
2. Include the outcome if known (it's used only for the matrix quadrant, never the process score).
3. Invoke the skill. Undocumented dimensions score `Unknown` — a high Unknown count is itself the finding that your decisions aren't documented enough.
4. Watch for the "Dumb luck" quadrant (bad process, good outcome) — that's the most expensive one to misread as skill.

**Inputs:** decision rationale, decision-time context, optional outcome. **Output:** 8-dimension process scorecard, quadrant classification, transferable lessons.

### 5. investment-memo-reviewer
**What it does:** Grades an investment memo section-by-section (A–F) against an institutional committee rubric — thesis & variant perception, valuation, risks & pre-mortem, sizing, exit criteria — and simulates the questions a committee would ask.

**How to use:** Submit the finished memo (state the audience — personal, club, professional — to calibrate strictness). Fix the `Missing` sections first (they're graded worse than F), then the load-bearing ones (thesis, valuation, risks), then resubmit for a re-grade.

### 6. management-credibility-tracker
**What it does:** Extracts management's verbatim, dated promises from transcripts and letters, matches them against later reported results, and produces a promise-vs-delivery ledger with delivery rate and trend. Tracks "Quietly Dropped" promises separately.

**How to use:** Provide communications spanning multiple periods (the promise documents AND the later documents where outcomes appear). More consecutive quarters = stronger analysis; the skill downgrades to `Unverifiable` when the record has gaps, so completeness matters.

### 7. capital-allocation-auditor
**What it does:** Grades how management deployed cash — capex, R&D, M&A, buybacks, dividends, debt — each lever graded on evidence and dollar-weighted into an overall report card. Buybacks are judged on valuation info available at the time, never hindsight.

**How to use:** Provide several years of annual reports (cash flow statements are the backbone), plus proxy statements and acquisition announcements if you have them. Every computed metric shows its formula and inputs, so you can check the arithmetic.

### 8. company-narrative-auditor
**What it does:** Tests a company's specific claims against evidence the company doesn't control — reviews, news, industry data — weighted by a 5-tier evidence hierarchy, producing claim-by-claim corroborated/contradicted verdicts.

**How to use:** Provide the company materials making the claims AND the external evidence (or let it fetch, if web tools are enabled). Forum/review evidence only ever corroborates patterns — it never establishes a finding alone, so include higher-tier sources where possible.

### 9. thesis-evolution-tracker
**What it does:** Diffs your thesis versions over time, tracks each assumption's status (intact / weakened / broken / dropped / new), and calls the big one: healthy evolution vs. thesis creep — a position whose original rationale quietly died and got replaced.

**How to use:** Save dated versions of your thesis whenever you update it, and feed the full sequence in. Label whether each update was a full restatement or a quick note if you can — absence from a quick note means nothing, absence from a full restatement is a flag.

### 10. investment-postmortem-analyzer
**What it does:** Reviews completed trades against their original theses, attributes each to skill vs. luck (thesis-right/wrong × outcome-good/bad), finds cross-trade patterns, and extracts lessons as forward-looking rules.

**How to use:** Provide closed positions with entry/exit data and the original thesis for each (no recorded thesis is itself a finding). Run it on batches — the cross-trade patterns (sizing asymmetries, exit discipline) are where the real lessons live.

---

## Worked Examples (First 4 Skills)

### Example 1 — investment-thesis-red-team

**You provide:**
> /investment-thesis-red-team
>
> Thesis: Acme Robotics (fictional) will double in 3 years. Warehouse automation demand is growing 30%/yr, Acme has the best gripper technology, and at 18x earnings it's cheap for the growth. Attached: FY2025 annual report, Q1 earnings transcript.

**You get back (abridged):**
> **Assumption Audit**
>
> | # | Assumption | Load-Bearing? | Evidence Against | Verdict |
> |---|---|---|---|---|
> | 1 | 30%/yr demand growth persists | Yes | Annual report p.12 shows backlog growth slowing to 14% YoY | Contested |
> | 2 | Gripper tech is a durable moat | Yes | No patent or switching-cost evidence provided | Unsupported |
> | 3 | 18x is cheap for the growth | Yes | No supplied valuation comparison — moved to Unanswered Questions | Unsupported |
>
> **Kill Criteria:** backlog growth < 15% for two consecutive quarters; a top-3 customer dual-sourcing grippers; gross margin below 38%.
>
> **Risk Score: 7/10 (Fragile)** — two of three load-bearing assumptions are unsupported by the provided materials.

### Example 2 — investment-bias-auditor

**You provide:**
> /investment-bias-auditor
>
> Journal excerpts:
> - Mar 4: "Sold half my index fund — market feels toppy, everyone on r/investing is bearish."
> - Mar 18: "Bought back in 6% higher. Can't keep missing this rally."
> - Apr 2: "TechCo down 30% since I bought. Not selling until I'm back to even."
> - Apr 9: "Doubled position in TechCo to lower my average. It owes me."

**You get back (abridged):**
> | Bias | Evidence (Quoted) | Confidence |
> |---|---|---|
> | Herding | "everyone on r/investing is bearish" (Mar 4) | High |
> | FOMO | "Can't keep missing this rally" (Mar 18) | High |
> | Anchoring / Loss Aversion | "not selling until I'm back to even" (Apr 2) | High |
> | Sunk Cost | "Doubled… to lower my average. It owes me." (Apr 9) | High |
>
> **Tilt Score:** qualitative — **High tilt** (4 entries is below the 10-entry minimum for a numeric score).
>
> **Guardrails:** (1) No position changes within 24h of reading social sentiment. (2) Averaging down requires a re-written thesis first. (3) Pre-committed exit price at entry, in writing.

### Example 3 — forecast-calibration-tracker

**You provide:**
> /forecast-calibration-tracker
>
> My 2025 predictions:
> 1. "Rate cut by June" — 80% — resolved TRUE
> 2. "GadgetCorp beats Q2 earnings" — 90% — FALSE
> 3. "Oil above $95 by year end" — 70% — FALSE
> 4. "My biotech pick gets FDA approval" — 85% — FALSE
> 5. "Index up on the year" — 60% — TRUE
> 6. "Housing will correct eventually" — 75% — ?

**You get back (abridged):**
> **Calibration Table**
>
> | Bucket | Predictions | Hit Rate | Gap | Sample Warning |
> |---|---|---|---|---|
> | 60–69% | 1 | 100% | +40% | Small sample |
> | 70–79% | 1 | 0% | −70% | Small sample |
> | 80–100% | 3 | 33% | −52% | Small sample |
>
> **Brier Score:** 0.42 (worse than the constant-50% reference of 0.25)
> **Verdict:** Overconfident (Low confidence — 5 resolved predictions is a very small sample).
> **Unscorable:** #6 — "eventually" has no deadline; add a resolution date.
> **Recommendation:** cap stated confidence at 70% until your 80%+ bucket resolves near 80%.

### Example 4 — investment-decision-reviewer

**You provide:**
> /investment-decision-reviewer
>
> Decision (Jan 2025): Put 20% of my portfolio into ShipFast Logistics (fictional) at $42. Reasoning at the time: freight rates were rebounding, the CFO bought shares in December, and the stock was at 9x earnings vs peers at 14x. I didn't write down an exit plan. Outcome: sold at $58 in May (+38%).

**You get back (abridged):**
> **Process Scorecard** (outcome quarantined until Step 3)
>
> | Dimension | Score | Evidence |
> |---|---|---|
> | Information Gathering | 3/5 | Three real signals cited, but no disconfirming-evidence search documented |
> | Base Rates | Unknown | Undocumented — no outside view recorded |
> | Risk Sizing | 2/5 | 20% position with no documented downside analysis |
> | Pre-Commitment | 1/5 | "I didn't write down an exit plan" |
>
> **Overall Process Score:** 2.4/5 (Unknowns excluded, 3 of 8 dimensions undocumented)
> **Quadrant:** Bad process + good outcome = **Dumb luck** — the +38% must not validate the 20% sizing.
> **Transferable Lesson:** cap any single position without a written downside case; write exit criteria at entry.

---

*All examples use fictional companies. These skills produce process analysis and decision support — not investment, tax, or legal advice.*
