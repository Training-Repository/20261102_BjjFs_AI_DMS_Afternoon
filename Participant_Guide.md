# BFL DMS (Consumer) — M365 Copilot Participant Guide
### Meta Prompts for Call Documentation, Account Prioritisation, DMS Reporting, Recovery Strategy & Agency Review

**Programme:** Microsoft Copilot for Debt Management Services (Consumer)
**Organisation:** Bajaj Finance Limited
**Interface:** M365 Copilot Chat (m365.cloud.microsoft/chat or Teams)
**Dataset:** `DMS_Copilot_Dataset.xlsx` — West Zone, data as of 30 Sep 2026 (synthetic)

---

## How Each Exercise Works — The 3-Step Rhythm

| Step | What You Do | What It Shows |
|------|-------------|----------------|
| **Step 1 — Meta Prompt** | Fill in the template and paste it into Copilot Chat | Copilot generates a tailored, role-specific working prompt |
| **Step 2 — Generated Prompt** | Review the prompt Copilot created | How your context shaped the output |
| **Step 3 — Live Apply** | Attach the Excel file using `/` and run the generated prompt | Copilot produces a real DMS insight or summary |

> 💡 BFL's Copilot allows **up to 3 file attachments per prompt**. Every exercise below stays within that limit. To work across more files at once, see `Copilot_Notebooks_Guide.md`.

---

## The Meta Prompt Template (used in every stage)

```
Act as a Microsoft Copilot prompt expert.

I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

## RTCFT Quick Reference

Every prompt Copilot generates from the template follows RTCFT:

| Element | What It Means | Example (DMS Context) |
|---------|---------------|-------------------------------|
| **R** — Role | Who are you? | "You are a tele-collections officer in DMS (Consumer) at Bajaj Finance Limited" |
| **T** — Task | What do you need? | "Summarise this call and extract the PTP details" |
| **C** — Context | What is the situation? | "A 65-DPD Personal Loan account; second broken promise" |
| **F** — Format | How should it look? | "Structured summary: Bounce Reason, Outcome, PTP Date, Amount, Next Action" |
| **T** — Tone | What register? | "Professional, factual, CRM-ready" |

---

## Your Dataset at a Glance

`DMS_Copilot_Dataset.xlsx` has six sheets. In every sheet the title is in row 1, headers are in row 4 and data starts in row 5.

| Sheet | What it holds |
|---|---|
| Call Interaction Log | 20 calls, 21–30 Sep 2026 (CL-02601 to CL-02620), with call time, bounce reason, caller, outcome and PTP |
| Account Priority Matrix | The same 20 accounts ranked by Risk Score (DPD × Overdue Amount ÷ 1,000) |
| DMS Performance | Monthly KPIs, Apr–Sep 2026, with targets in the sub-title row |
| Bucket Trend Analysis | DPD bucket counts and ₹ Cr by product, Jul–Sep 2026, with roll-forward and resolution rates |
| Recovery Strategy Tracker | 10 segments with strategy, channel, target vs actual resolution, gap and status |
| Agency & Conduct Tracker | 5 collection agencies (fictional names) with certification, contact-hour exceptions, complaints and audit scores |

---

## Stage 1 — Customer Interaction Documentation

**Use case:** Summarising call notes, extracting PTP details and producing CRM-ready entries.
**Sheet to use:** `Call Interaction Log`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Tele-Collections Officer in DMS (Consumer) at Bajaj Finance Limited.
I need to summarise customer call interactions and produce structured
documentation — bounce reason, call outcome, promise-to-pay details and
next action — for entry into our DMS CRM.
My audience is my DMS supervisor and the CRM team.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

*(Typical output. Yours will be worded differently.)*

```
You are a Tele-Collections Officer in DMS (Consumer) at Bajaj Finance Limited
documenting customer calls for the CRM.

Task: Review the call log provided and generate a structured CRM entry for
each call.

Context: These are calls to customers whose EMI bounced or is overdue on
Consumer Durable, Digital Product, Lifestyle Finance, Personal Loan and
Two-Wheeler loans. Calls may end in a PTP, a partial PTP, an escalation,
a dispute, a callback or no response.

Output format — use these labelled fields for each entry:
- Customer Name & Account ID
- Product & DPD
- Overdue Amount (₹) & Bounce Reason
- Called By
- Call Outcome
- PTP Date & PTP Amount (if any)
- Action Taken
- Next Follow-up Date & Method

Constraints: Use only what is in the log. Do not invent dates or amounts.
Tone: Factual, professional, CRM-ready. No filler.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our DMS dataset. Use only the "Call Interaction Log" sheet.

1. For Call ID CL-02601 (Ramesh Patil), generate a structured CRM entry
   using the format above.
2. List every call with outcome "Escalated" or "Dispute", with the reason
   and the recommended next step.
3. Calculate the share of calls that ended in a PTP (full or partial).
   List the PTPs falling due between 1 and 7 October 2026.
4. Flag any call made outside 08:00–19:00.

Format the output as a supervisor-ready report.
```

**What a good answer contains:**
- **Escalated / Dispute:** CL-02602 Sunita Mehta (product returned to dealer, sent to the Dispute Desk), CL-02606 Priya Kulkarni (dispute over a foreclosure not reflected), CL-02607 Deepak Joshi (legal notice, third escalation) and CL-02615 Swati Iyer (moved to 90+, legal team notified).
- **PTP rate:** 9 full + 3 partial PTPs out of 20 calls, so **60%** (45% if only full PTPs are counted).
- **Due 1–7 Oct:** 6 PTPs — Suresh Nair (1 Oct), Santosh More (2 Oct), Anil Sharma and Farhan Shaikh (3 Oct), Meena Rao (4 Oct) and Ramesh Patil (5 Oct).
- **Outside hours:** CL-02610 at **19:42** (Konkan Collect Associates) and CL-02618 at **07:35** (DigiReach Tele-Collect).

> If Copilot misses item 4, follow up: *"Check the Call Time column again against 08:00–19:00."* Catching what the first answer missed is part of the skill.

---

## Stage 2 — Account Prioritisation

**Use case:** Identifying which overdue accounts need action today, ranked by risk.
**Sheet to use:** `Account Priority Matrix`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a DMS Team Lead at Bajaj Finance Limited.
I need to prioritise overdue Consumer loan accounts and decide which need
immediate action today — tele-calling, a field visit or legal review —
based on DPD bucket, overdue amount and risk score.
My audience is my tele-collections team and our field agencies.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a DMS Team Lead at Bajaj Finance Limited reviewing the daily
account priority matrix.

Task: Produce a prioritised recovery action list for the tele-collections
team and the field agencies.

Context: Accounts fall into four DPD buckets — 1–30, 31–60, 61–90 and 90+ —
mapped to Low, Medium, High and Critical priority. Risk Score = DPD ×
Overdue Amount ÷ 1,000. Some accounts are flagged for a field visit.
Accounts under dispute must not be sent for a field visit.

Output format:
- All Critical accounts ranked by risk score, with the recommended action
- High accounts not contacted in the last 5 days
- Summary table: account count and overdue amount (₹) by priority tier
- Field visit list with a suggested sequence, excluding disputed accounts

Tone: Direct, action-oriented, suitable for a morning huddle.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our DMS dataset. Use the "Account Priority Matrix" sheet,
as of 30 Sep 2026.

1. List every Critical account ranked by Risk Score, with the recommended
   immediate action.
2. From the High accounts, flag those last contacted before 25 Sep 2026.
3. Create a summary table: account count and total overdue amount (₹) for
   each priority tier.
4. List the accounts where Field Visit? = Yes and suggest a visit sequence.
   Check the Call Interaction Log sheet too: flag any of these accounts that
   are under dispute.

Present this as a morning DMS action brief.
```

**What a good answer contains:**
- **Critical (3):** Swati Iyer (Risk Score 4,240), Deepak Joshi (4,059), Priya Kulkarni (789).
- **High, stale contact:** Rohan Mishra (last contact 23 Sep) and Mohammed Shaikh (21 Sep).
- **By tier:** Critical 3 accounts / ₹94,770 · High 8 / ₹1,16,770 · Medium 7 / ₹59,530 · Low 2 / ₹5,480.
- **Field visits (7):** Swati Iyer, Deepak Joshi, Rohan Mishra, Meena Rao, Priya Kulkarni, Sunita Mehta, Kavita Deshmukh. **Priya Kulkarni** and **Sunita Mehta** are in dispute, so their visits should go on hold.

---

## Stage 3 — DMS Performance Reporting

**Use case:** Preparing the monthly performance summary for the Head of DMS.
**Sheet to use:** `DMS Performance`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a DMS MIS Analyst at Bajaj Finance Limited.
I need to prepare a monthly performance summary for the Consumer portfolio —
collection efficiency, NACH bounce rate, PTP kept %, escalations, conduct
complaints and GNPA — for April to September 2026.
My audience is the Head of DMS (Consumer) and the zonal leadership team.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a DMS MIS Analyst at Bajaj Finance Limited preparing the monthly
management review.

Task: Analyse six months of DMS (Consumer) performance and write a
management summary.

Context: Data covers April–September 2026 for West Zone. Targets: Collection
Efficiency 97.5%, GNPA ceiling 1.50%, conduct complaints no more than 15 a month.

Output format:
1. Executive summary (200–250 words): efficiency trend, September vs August,
   GNPA status, conduct complaints
2. Comparison table for Jul / Aug / Sep: Collection Efficiency %, NACH Bounce
   Rate %, PTP Kept %, Accounts Escalated, Conduct Complaints
3. Three key observations
4. Two recommended actions for October 2026

Tone: Professional, data-driven, ready for leadership.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our DMS dataset. Use the "DMS Performance" sheet.

Generate the full management summary as described — executive summary,
Jul/Aug/Sep comparison table, three observations and two October actions.

Also check:
- Collection efficiency rose every month from April to August, then fell in
  September. Confirm this, and say whether the 97.5% target was met in any month.
- September looks like a stress month. Name every metric that moved the
  wrong way from August, with both values.
```

**What a good answer contains:**
- **Efficiency:** 95.8% (Apr) rising to **97.0%** (Aug), then **96.2%** (Sep). The 97.5% target was not met in any month.
- **September vs August:**
  - NACH bounce rate rose from 11.9% to **13.8%**.
  - PTP kept fell from 74% to **68%**.
  - Escalations rose from 184 to **263**.
  - Conduct complaints rose from 12 to **27**, above the limit of 15.
  - New delinquencies rose from 9,390 to **11,260**.
  - Bucket-1 resolution fell from 90.3% to **87.6%**.
- **GNPA:** 1.36%, up slightly from 1.33% but still within the 1.50% ceiling.

---

## Stage 4 — Bucket Roll-forward and Recovery Strategy

**Use case:** Finding which products and segments are slipping, and what to change in October.
**Sheets to use:** `Bucket Trend Analysis` + `Recovery Strategy Tracker` (both in the same file)

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a DMS Strategy Lead at Bajaj Finance Limited.
I need to analyse bucket roll-forward by product for July–September 2026 and
recommend differentiated recovery strategies by segment for October.
My audience is the senior DMS leadership team.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a DMS Strategy Lead at Bajaj Finance Limited conducting the monthly
portfolio review.

Task: Analyse roll-forward and resolution rates by product, evaluate each
recovery segment against target, and recommend October actions.

Context: Two sheets are provided — Bucket Trend Analysis (Jul–Sep 2026, by
product) and Recovery Strategy Tracker (Sep 2026, target vs actual resolution
with status). Roll-forward is the share of accounts moving into a higher DPD
bucket in the month.

Output format:
1. Roll-forward analysis — the worst product and its 3-month trend
2. Every segment marked At Risk, with one corrective action each
3. Best-practice insight — what the best-resolving product or segment does
   differently, and where else it could apply
4. A 150-word portfolio health summary to open the strategy meeting

Tone: Analytical, strategic, actionable.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our DMS dataset. Use the "Bucket Trend Analysis" and
"Recovery Strategy Tracker" sheets.

1. Which product has the worst roll-forward rate in September? How has it
   moved since July? What could explain it?
2. List every segment with Status "At Risk". Suggest one specific corrective
   action for each in October 2026.
3. Consumer Durable has the best resolution rate, and its Dealer Dispute
   segment is ahead of target. What could explain this? Can any of it apply
   to Personal Loan?
4. Write a 150-word portfolio health summary for the start of the review.
```

**What a good answer contains:**
- **Worst roll-forward:** Personal Loan, at 11.2% (Jul), 11.9% (Aug) and **13.1%** (Sep), so it is worsening every month. Its resolution rate fell from 80.9% to **78.6%**.
- **At Risk segments (3):**
  - Severely Overdue: target 40%, actual 33.5%.
  - Promise Broken: target 55%, actual 47.2%.
  - Personal Loan — Hardship: target 66%, actual 59.3%.
- **Best practice:** Consumer Durable resolves at **91.2%** in September. The Dealer Dispute segment is at 86.0% against a target of 85%. Small tickets, digital payment links and early dispute handling with the dealer are the likely reasons. Copilot should present these as hypotheses, not facts from the data.

---

## Stage 5 — Agency Performance and Conduct Review

**Use case:** A monthly scorecard of collection agencies against the conduct standard.
**Files to attach:** `DMS_Copilot_Dataset.xlsx` + `Fair_Collection_Practices_Standard.pdf` (2 attachments)

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am an Agency Manager in DMS (Consumer) at Bajaj Finance Limited.
I need a monthly review of our collection agencies — resolution, DRA
certification of agents, calls outside permitted hours, complaints and audit
scores — checked against our Fair Collection Practices Standard.
My audience is the Head of DMS (Consumer).

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are an Agency Manager in DMS (Consumer) at Bajaj Finance Limited.

Task: Review each collection agency for September 2026 against the Fair
Collection Practices Standard and recommend an action per agency.

Context: The Agency & Conduct Tracker gives allocation, resolution, agents
deployed vs DRA-certified, calls outside 08:00–19:00, complaints and audit
scores. The Standard sets the rules: clause 3.1 (contact hours), 5.1 (100%
DRA certification), 5.2 (audit bands), 5.3 (complaints per 1,000 accounts)
and 5.4 (reporting of contact-hour exceptions).

Output format:
1. Scorecard table: Agency | Resolution % | Certified % | Outside-hours calls |
   Complaints per 1,000 | Audit score | Status
2. Breach table: Agency | Clause | What the data shows | Required action
3. One recommendation per agency: continue / improvement plan / show-cause /
   reduce allocation
Quote the clause number for every rule you apply. Use only the two files.

Tone: Factual, firm, audit-ready.
```

---

### Step 3 — Live Apply (attach both files via `/`)

```
I am attaching our DMS dataset and the DMS Fair Collection Practices Standard.
Use the "Agency & Conduct Tracker" sheet for September 2026.

Produce the scorecard, the breach table and one recommendation per agency.
Then tell me which agency the Head of DMS should discuss first, and why.
```

**What a good answer contains:**
- **Konkan Collect Associates (Mumbai):**
  - Clause 5.1: 52 of 58 agents certified (89.7%).
  - Clause 3.1: 9 calls outside permitted hours.
  - Clause 5.3: 6.8 complaints per 1,000 accounts, above the limit of 5.
  - Clause 5.2: audit score 71, so an Improvement Plan.
  - This is the agency to discuss first.
- **Godavari Credit Assist (Nashik):**
  - Clause 5.1: 24 of 27 agents certified (88.9%).
  - 3 calls outside hours.
  - Clause 5.3: 6.6 complaints per 1,000 accounts.
  - Audit score 78, so an Improvement Plan.
- **DigiReach Tele-Collect:**
  - Clause 3.1: **14** calls outside hours, the highest of any agency.
  - Clause 5.1: 117 of 120 agents certified.
  - Audit score 82, Satisfactory.
- **Sahyadri Recovery Services** and **Vidarbha Field Solutions** have no breaches.

---

## Stage 6 — Bonus: Outlook Copilot for a Broken-PTP Follow-Up

**Use case:** A firm but respectful email to a customer whose PTP was not honoured.
**No file needed. Use Outlook → Draft with Copilot.**

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Tele-Collections Officer at Bajaj Finance Limited.
I need to draft a follow-up email to a customer whose promise to pay (PTP)
was not honoured on the agreed date, asking for payment or a revised
commitment.
My audience is the customer.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a Tele-Collections Officer at Bajaj Finance Limited drafting a
customer-facing follow-up for a PTP that was not honoured.

Task: Write a professional email reminding the customer of the missed
commitment and asking for payment or a revised date.

Context: The customer agreed a specific PTP date and amount, which has not
been received. Payment can be made only through the BFL payment link, UPI or
a branch. If it stays unpaid, the account will be referred for a field visit.

Output format:
- Subject line
- Opening: acknowledge the earlier commitment
- Body: the agreed PTP date and amount, and that it has not been received
- Request: payment by [revised date] via the payment link, or a new commitment
- Next step: a field visit if it stays unpaid
- Sign-off: DMS Team, Bajaj Finance Limited

Tone: Professional, firm, respectful. Never threatening.
```

---

### Step 3 — Live Apply (in Outlook → Draft with Copilot)

```
Draft a follow-up email to Rashmi Singh (Account BFL-CD-41307), who agreed
to pay ₹4,790 on 28 September 2026. The payment has not been received.

Ask for payment by 3 October 2026 through the BFL payment link [LINK], or a
revised commitment in writing. Mention that continued non-payment will
lead to a field visit.

Use the format and tone above. Include a subject line.
```

> ⚠️ Read the draft before sending. Remove anything that could read as a threat, and never add account details beyond what the customer already has.

---

## All Exercises at a Glance

| Stage | Use Case | Sheet / Tool | Output |
|-------|----------|--------------|--------|
| 1 | Call documentation | Call Interaction Log | CRM entry + PTP tracker + contact-hour flags |
| 2 | Account prioritisation | Account Priority Matrix | Morning action brief |
| 3 | DMS performance reporting | DMS Performance | Management summary |
| 4 | Roll-forward & recovery strategy | Bucket Trend + Strategy Tracker | Segment strategy brief |
| 5 | Agency & conduct review | Agency & Conduct Tracker + Standard PDF | Agency scorecard with clause references |
| 6 *(Bonus)* | Broken-PTP follow-up | Outlook — no file | Customer-ready email |

---

## ⚠️ Data Handling

The dataset is **synthetic**, so it is safe to attach. Live DMS data is not. On real accounts:

- Use Copilot signed in with your **BFL work account** (look for the enterprise data protection indicator).
- Don't paste customer PII (names, phone numbers, account numbers, PAN) into any tool outside BFL's approved Copilot.
- Attach only the sheets and columns the question needs.

---

*Bajaj Finance Limited | AI Academy — Debt Management Services (Consumer) | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
