# Meta-Prompting Guide — Debt Management Services (Consumer)
**Microsoft Copilot Training | Bajaj Finance Limited**

---

## What Is Meta-Prompting?

Instead of writing a prompt yourself, you ask Copilot to write the prompt for you. You tell it your role, your task and who will read the output.

In effect, you are saying:

> *"You are a prompt expert. You know how to talk to AI. Write me a prompt I can use for my actual work."*

The output becomes your **reference prompt**: something you refine once and reuse across DMS workflows, from tele-calling notes to agency reviews and monthly MIS.

---

## The Core Meta-Prompt Formula

```
Act as a Microsoft Copilot prompt expert.
I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].
Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

## Meta-Prompts for DMS (Consumer) — Bajaj Finance

Use these as your starting point. Copy, paste and run them in Copilot, then use the output as your working prompt for the exercises.

---

### 1. Customer Interaction Documentation

```
Act as a Microsoft Copilot prompt expert.
I am a Tele-Collections Officer in Debt Management Services (Consumer) at Bajaj Finance
Limited, an NBFC. I call customers whose EMI has bounced or is overdue on Consumer Durable,
Digital Product, Lifestyle Finance, Personal Loan and Two-Wheeler loans. After each call I
document the interaction in the DMS CRM — the bounce reason, call outcome, promise-to-pay
(PTP) details, action taken and the next follow-up step.

My audience is my DMS supervisor and the CRM team who use this data for daily recovery
tracking and escalation decisions.

Write me a detailed, structured Copilot prompt I can use to produce a CRM-ready call
summary from my call notes. The prompt should specify: my role, the task, what input I will
provide, the exact output format for each field (bounce reason, outcome, PTP date, PTP
amount, action taken, next follow-up), and a factual, professional tone.
```

---

### 2. Account Prioritisation

```
Act as a Microsoft Copilot prompt expert.
I am a DMS Team Lead at Bajaj Finance Limited. Every morning I review an account priority
matrix for overdue Consumer loans across four DPD buckets — 1–30, 31–60, 61–90 and 90+ —
with overdue amounts, risk scores, last contact dates and field visit flags. I need a
prioritised daily action list: which accounts to call first, which need a field visit today,
and where the overdue exposure is highest.

My audience is my tele-collections team and the field agencies we allocate to.

Write me a Copilot prompt I can use to produce this prioritised action list. The prompt
should tell Copilot how to rank accounts, what to flag (stale contacts, disputed accounts
that must not get a field visit, critical exposure), and the tone (direct, action-oriented,
ready for a morning huddle).
```

---

### 3. DMS Performance Reporting

```
Act as a Microsoft Copilot prompt expert.
I am a DMS MIS Analyst at Bajaj Finance Limited. I maintain a monthly performance dashboard
for the Consumer portfolio in West Zone — EMI demand, amount collected, Collection Efficiency %,
NACH bounce rate, Bucket-1 resolution, PTP count and PTP kept %, escalations, field visits,
conduct complaints, GNPA % and new delinquencies — for April to September 2026. I need a
management summary: the efficiency trend, a comparison of the last three months, and
recommended actions for October.

My audience is the Head of DMS (Consumer) and the zonal leadership team in their monthly
review meeting.

Write me a structured Copilot prompt that will produce this summary from my dashboard. The
prompt should specify the format (executive narrative + comparison table + action
recommendations), the tone (professional, data-driven, management-ready), and the signals to
surface (efficiency against the 97.5% target, the September bounce spike, GNPA against the
1.50% ceiling, conduct complaints against the limit of 15).
```

---

### 4. Bucket Roll-forward and Recovery Strategy Analysis

```
Act as a Microsoft Copilot prompt expert.
I am a DMS Strategy Lead at Bajaj Finance Limited. I track bucket movement every month across
five Consumer products — Consumer Durable, Digital Product, Lifestyle Finance, Personal Loan
and Two-Wheeler — with DPD bucket counts, overdue amounts, roll-forward rates and resolution
rates. I also maintain a Recovery Strategy Tracker with segment-wise strategies, channels,
target vs actual resolution %, and status. I need to identify which products and segments
are underperforming, explain the roll-forward pattern, and recommend differentiated actions
for October.

My audience is the senior DMS leadership team, who use this for monthly strategy and
allocation decisions.

Write me a Copilot prompt that will produce this analysis from my two datasets. The prompt
should specify the format (roll-forward analysis + underperforming segments + corrective
actions + portfolio health summary), the tone (analytical, strategic, actionable), and the
patterns to surface (worst roll-forward product, segments marked At Risk, what the best
performing segment does differently).
```

---

### 5. Agency Performance and Conduct Review

```
Act as a Microsoft Copilot prompt expert.
I am an Agency Manager in DMS (Consumer) at Bajaj Finance Limited. I oversee the collection
agencies we allocate overdue accounts to. Each month I review their allocation and
resolution, agent DRA certification, calls made outside permitted hours, customer complaints
and quarterly audit scores against our Fair Collection Practices Standard.

My audience is the Head of DMS (Consumer), who decides on allocation changes, improvement
plans and show-cause notices.

Write me a Copilot prompt I can use to produce a monthly agency review. The prompt should
specify the format (agency scorecard table + breaches against named policy clauses +
recommended action per agency), the tone (factual, firm, audit-ready), and what to flag
(uncertified agents, contact-hour breaches, complaint rates, audit status).
```

---

### 6. Broken-PTP Customer Communication

```
Act as a Microsoft Copilot prompt expert.
I am a Tele-Collections Officer at Bajaj Finance Limited. I need to draft follow-up emails
and WhatsApp templates for customers whose promise to pay (PTP) was not honoured on the agreed
date. The message must state the PTP amount and date, ask for payment through the BFL payment
link or a revised commitment, and explain what happens next if the amount stays unpaid —
without being threatening or aggressive.

My audience is the customer receiving the message.

Write me a Copilot prompt I can use to draft this communication. The prompt should specify
the format (subject line + opening + body + request + next step + sign-off), the tone
(professional, firm, respectful — never threatening), and the details to personalise
(customer name, account ID, PTP date, PTP amount, revised date, payment link placeholder).
```

---

## Still Not Right? Run This.

If the prompt Copilot wrote doesn't feel right (too generic, wrong format, wrong tone), don't rewrite it yourself. Use this follow-up instead:

```
The prompt you wrote is a good start, but I need you to adjust it.
Here is what I want to change:

- [What felt off — e.g., "the format doesn't match what my supervisor expects"]
- [What's missing — e.g., "it doesn't tell Copilot to keep disputed accounts off the field list"]
- [The tone issue — e.g., "it sounds too formal for a morning huddle"]

Please rewrite the prompt with these corrections.
Keep the same structure (Role / Task / Context / Format / Tone) but fix the parts I've described.
```

---

## What to Do With the Output

Once Copilot gives you a well-structured prompt:

1. **Read it.** Does it reflect your actual DMS role and portfolio?
2. **Replace the placeholders** with your real bucket, product, agency or account details.
3. **Run it** on the exercise dataset provided in this session.
4. **Save it.** This is your reusable reference prompt for that task.

---

*Bajaj Finance Limited | AI Academy — Debt Management Services (Consumer) | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
