# Excel with M365 Copilot (Basic) — No Agent Required
### Formulas & Pivot Tables for DMS (Consumer), using M365 Copilot chat + Meta-Prompting
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `DMS_Copilot_Demo.xlsx`
**Companion guides:** `MetaPrompting_Guide.md` · `Excel_Agent_Guide_Premium.md` (Agent version)

---

## Who This Guide Is For

`Excel_Agent_Guide_Premium.md` uses **Edit with Copilot** in Excel, in which Copilot writes formulas into your cells and builds pivot tables for you. It needs a **paid Microsoft 365 Copilot licence**.

This guide produces **the same results** with **M365 Copilot (Basic)**:

- **Copilot does the thinking.** It writes the formula, explains the logic and gives you the pivot layout.
- **You do the clicking.** You paste the formula and build the pivot in Excel yourself, which takes about 30 seconds per exercise.

| Your licence | What works for you |
|---|---|
| **M365 Copilot (Premium)** | Either guide. The Agent guide is faster. |
| **M365 Copilot (Basic)** | **This guide.** Run the prompts in M365 Copilot chat. Copilot will not edit the workbook for you. |

---

## How Every Exercise Works

```
Step 1 → Paste the Excel Meta Prompt with that exercise's TASK filled in
Step 2 → Read the Working Prompt Copilot generates
Step 3 → Attach DMS_Copilot_Demo.xlsx and run the Working Prompt
Step 4 → Apply Copilot's answer in Excel yourself (paste formula / build pivot)
Step 5 → Verify against the expected numbers in this guide
```

> 💡 **Why Step 5 matters:** without an agent, nobody checks the result but you. The expected numbers below let you spot a wrong formula in seconds.

---

## Before You Begin

1. Open `DMS_Copilot_Demo.xlsx` in **Excel** (desktop or web) and go to the **DMS Data** sheet.
2. Open **M365 Copilot** chat in a second window, either the M365 Copilot app or `m365copilot.com`.
3. Keep both windows side by side.

### What's in the file

- Row 1 is a title and **row 2 holds the headers**. **Data runs in rows 3–27** (25 accounts, as of **30 Sep 2026**). Row 28 is a note.
- **Column M is a blank spacer.** Columns **N–Q already have headers** (`➕ DPD Bucket`, `➕ Risk Score`, `➕ Days Since PTP Due`, `➕ EMIs Overdue`) and empty cells below them. You will fill those cells.
- **PTP Date (H) holds real Excel dates** and is blank where there is no promise. Unlike some other workbooks in this programme, there is no text-date trap here.
- The "as of" date is fixed at **30 Sep 2026**, so everyone in the room gets the same answer.

| Column | Field | Column | Field |
|---|---|---|---|
| A | Account ID | H | PTP Date *(blank if no PTP)* |
| B | Customer Name | I | PTP Amount (₹) |
| C | Product | J | Collector Name |
| D | DPD | K | Zone |
| E | Overdue Amount (₹) | L | Field Visit (Yes / No) |
| F | EMI Amount (₹) | M | *(blank spacer)* |
| G | Call Outcome | N–Q | **You fill these** |

---

## ⚡ The Excel Meta Prompt — Your Starting Point

This follows the RTCFT pattern from `MetaPrompting_Guide.md`, adapted for Excel. The file layout is already filled in, so for each exercise you only replace **[TASK]**.

```
Act as a Microsoft Copilot prompt expert specialising in Excel for debt management services.

Role:    I am a DMS Collections Analyst at Bajaj Finance Limited. I use M365 Copilot chat,
         which cannot edit my workbook — I will apply the result in Excel myself.
Task:    I need to: [TASK]
Context: Sheet "DMS Data" in DMS_Copilot_Demo.xlsx. Data as of 30 Sep 2026.
         Headers are in row 2; data is in rows 3 to 27 (25 accounts).
         Columns: A Account ID, B Customer Name, C Product, D DPD, E Overdue Amount,
         F EMI Amount, G Call Outcome, H PTP Date (blank if no PTP), I PTP Amount,
         J Collector Name, K Zone, L Field Visit. Column M is a blank spacer.
Format:  The prompt must ask Copilot for:
         1. The exact result (formula for row 3, or pivot/table layout) ready to copy
         2. Step-by-step instructions to apply it manually in Excel
         3. How to handle blanks (accounts with no PTP)
         4. A quick way to verify the result is correct
Tone:    Clear and step-by-step, for a collections user who is not an Excel expert.

Write me a detailed, ready-to-use Copilot prompt I can use in M365 Copilot chat with this file attached.
```

> ✏️ **Short on time?** Once you've done this for Exercise 1, reuse the Working Prompt Copilot gave you and swap in the new task for the later exercises.

---

---

# Exercise 1 — Formula Column: DPD Bucket (N)
**Time:** ~8 minutes

### Step 1 — [TASK] to paste into the Meta Prompt
```
write a formula for column N ("DPD Bucket") that classifies each account from DPD in column D:
"Critical" if DPD is more than 90, "High" if 61 to 90, "Medium" if 31 to 60, "Low" if 30 or
less, for rows 3 to 27
```

### Step 2 — Check the Working Prompt
- [ ] Does it mention row 3 and filling down to row 27?
- [ ] Does it ask for manual steps and a verification check?

### Step 3 — Attach the file and run
Attach `DMS_Copilot_Demo.xlsx` → paste the Working Prompt → send.

### Step 4 — Apply in Excel
1. Click **N3** and paste the formula Copilot gave you.
2. Fill it down to **N27**: select **N3:N27** and press **Ctrl + D**, or double-click the fill handle at the bottom-right corner of N3.

### Step 5 — Verify
Type this in any empty cell, such as **U3**:
```excel
=COUNTIF(N3:N27,"Critical")
```
**Expected: 4 Critical · 9 High · 10 Medium · 2 Low.** The four Critical accounts are BFL-CD-40633, BFL-PL-70741, BFL-PL-71529 and BFL-PL-72529.

<details><summary>Reference formula (open only if stuck)</summary>

```excel
=IF(D3>90,"Critical",IF(D3>60,"High",IF(D3>30,"Medium","Low")))
```
</details>

> **Discussion Point:** Three of the four Critical accounts are Personal Loans with an escalated outcome. What does that say about where field-visit effort should go first?

---

# Exercise 2 — Formula Column: Risk Score (O)
**Time:** ~5 minutes

### Step 1 — [TASK]
```
write a formula for column O ("Risk Score") that multiplies DPD (D) by Overdue Amount (E),
for rows 3 to 27
```

### Steps 2–4
Same as Exercise 1, but paste in **O3** and fill down to **O27**.

### Step 5 — Verify
```excel
=MAX(O3:O27)
```
**Expected: 46,54,280** (4,654,280), for Vikram Deshpande (BFL-PL-72529). The next two are Swati Iyer (42,39,690) and Deepak Joshi (40,58,580), so Personal Loans hold the top three.

<details><summary>Reference formula</summary>

```excel
=D3*E3
```
</details>

> **Try this:** *"These scores are hard to read. Show them in thousands."* Copilot will divide by 1,000, the same scale the Account Priority Matrix in the main dataset uses.

---

# Exercise 3 — Formula Column: Days Since PTP Due (P)
**Time:** ~8 minutes

### Step 1 — [TASK]
```
write a formula for column P ("Days Since PTP Due") that returns the number of days from the
PTP Date in column H to 30 September 2026, and leaves the cell blank when H is blank,
for rows 3 to 27
```

### Steps 2–4
Paste in **P3** and fill down to **P27**.

### Step 5 — Verify
- **10 rows are blank**: the accounts with no PTP date.
- **Positive** means the promised date has passed: Pooja Tiwari 6, Mohammed Shaikh 5, Anjali Verma 4, Ganesh Pawar 3, Rashmi Singh 2.
- **0** means the PTP is due on 30 Sep: Rohan Mishra.
- **Negative** means the PTP is still in the future, for example Harish Kulkarni (-6).

<details><summary>Reference formula</summary>

```excel
=IF(H3="","",DATE(2026,9,30)-H3)
```
If the result shows as a date instead of a number, set the column format to **Number**.
</details>

> **On live data:** replace `DATE(2026,9,30)` with `TODAY()` so the column updates every day. The fixed date is used here so everyone gets the same answer.

> **Discussion Point:** Five accounts have a promise that has already lapsed. Which of them is carrying the largest overdue amount, and so needs a broken-PTP follow-up first?

---

# Exercise 4 — Formula Column: EMIs Overdue (Q)
**Time:** ~5 minutes

### Step 1 — [TASK]
```
write a formula for column Q ("EMIs Overdue") that divides Overdue Amount (E) by EMI Amount (F)
and rounds to the nearest whole number, for rows 3 to 27
```

### Steps 2–4
Paste in **Q3** and fill down to **Q27**.

### Step 5 — Verify
**Expected:** Ramesh Patil (row 3) shows **2**, and every Critical account shows **4**.

> 💡 The overdue amount includes bounce charges, so the raw division is rarely a whole number. For example, Ramesh Patil's 12,990 ÷ 6,200 is 2.1. That is why the formula rounds.

<details><summary>Reference formula</summary>

```excel
=ROUND(E3/F3,0)
```
</details>

---

# Exercise 5 — Ask Copilot to Explain a Formula
**Time:** ~3 minutes

No meta prompt or attachment is needed. Copy the formula from **N3** and paste it into M365 Copilot chat:
```
Explain this Excel formula in simple terms for a collections user. What does each part do,
and in what order are the conditions checked?
[paste formula here]
```

**What to look for:**
- The explanation should state that the conditions are checked **in order**, so the highest band must be tested first.
- Follow up with: *"What does this return for a DPD of exactly 90, and exactly 60?"* Because the tests are `>90` and `>60`, 90 lands in **High** and 60 lands in **Medium**. Check boundaries on any banded formula.

---

# Exercise 6 — Pivot Table: Overdue by Product and Call Outcome
**Time:** ~8 minutes

### Step 1 — [TASK]
```
design a pivot table showing the total Overdue Amount (₹) for each Product (rows) broken down by
Call Outcome (columns). Give me the exact field placement and click-by-click steps to build it
in Excel, plus the expected result table so I can check my pivot.
```

### Steps 2–3
Run the Working Prompt with the file attached, as before.

### Step 4 — Build it in Excel
1. On **DMS Data**, select **A2:Q27** exactly. Don't include the title in row 1 or the note in row 28.
2. Go to **Insert → PivotTable → New Worksheet → OK**.
3. Place the fields:
   - **Product** → Rows
   - **Call Outcome** → Columns
   - **Overdue Amount (₹)** → Values. If it shows *Count*, change it to **Sum** in **Value Field Settings**.

### Step 5 — Verify (₹)

| Product | Callback Requested | Dispute | Escalated | No Response | PTP Confirmed | Partial PTP | Promise Broken | Total |
|---|---|---|---|---|---|---|---|---|
| Consumer Durable |  | 8,390 | 7,940 |  | 12,370 |  |  | 28,700 |
| Digital Product | 8,990 |  | 14,090 | 8,190 | 18,180 |  |  | 49,450 |
| Lifestyle Finance |  |  |  |  | 11,790 | 52,470 |  | 64,260 |
| Personal Loan |  |  | 136,970 |  | 28,380 |  | 25,190 | 190,540 |
| Two-Wheeler |  |  |  | 9,290 | 26,160 |  |  | 35,450 |
| **Grand Total** | **8,990** | **8,390** | **159,000** | **17,480** | **96,880** | **52,470** | **25,190** | **368,400** |

*Excel sorts rows and columns alphabetically by default, so your order may differ. Your Excel may show Indian digit grouping, for example 1,90,540.*

> **Discussion Point:** Personal Loan carries ₹190,540, and ₹162,160 of it sits in Escalated or Promise Broken accounts. Consumer Durable carries the least. Where would you deploy field visits first?

---

# Exercise 7 — Pivot Table: Collector Workload by DPD Bucket
**Time:** ~8 minutes

### Step 1 — [TASK]
```
design a pivot table showing the count of accounts for each Collector Name (rows) broken down by
DPD Bucket (columns: Critical, High, Medium, Low). Give me the field placement, click-by-click
steps, and the expected row totals.
```

### Step 4 — Build it in Excel
1. Select **A2:Q27** → **Insert → PivotTable → New Worksheet**.
2. Place the fields:
   - **Collector Name** → Rows
   - **DPD Bucket** → Columns
   - **Account ID** → Values (*Count of Account ID*)
3. If Excel cannot see column N, the blank spacer column M may be breaking range detection. Type `Spacer` in **M2** and rebuild the pivot.

### Step 5 — Verify

| Collector Name | Critical | High | Medium | Low | Total |
|---|---|---|---|---|---|
| Amit Tiwari |  | 3 | 1 |  | 4 |
| Pooja Sharma | 1 | 1 | 2 | 1 | 5 |
| Rajesh Kumar | 3 | 1 | 2 |  | 6 |
| Ravi Patil |  | 2 | 2 | 1 | 5 |
| Sunita Rao |  | 2 | 3 |  | 5 |
| **Grand Total** | **4** | **9** | **10** | **2** | **25** |

> **Discussion Point:** Rajesh Kumar holds 3 of the 4 Critical accounts, all Personal Loans. Is the workload balanced by count but not by risk?

> 💡 **No pivot tables allowed on your machine?** Ask Copilot for the same result as a `COUNTIFS` formula grid instead. For example, `=COUNTIFS(J3:J27,"Rajesh Kumar",N3:N27,"Critical")` returns **3**.

---

# Exercise 8 — Bonus: Ask Copilot for Insights
**Time:** ~5 minutes

This works directly in M365 Copilot chat with the file attached. No manual steps are needed.

```
Look at the DMS Data sheet in the attached file. Which collectors hold the most Escalated
accounts, and what do those accounts have in common (product, DPD, zone)? Summarise the key risk
areas for the DMS team in 3 bullet points, quoting Account IDs as evidence.
```

**Expected:**
- **Rajesh Kumar holds 3 of the 5 Escalated accounts**: BFL-PL-70741, BFL-PL-71529 and BFL-PL-72529. All are Personal Loans with DPD of 91 to 102 and field visits marked Yes.
- The other two are Pooja Sharma (BFL-CD-40218) and Sunita Rao (BFL-DP-52307).
- **Escalated accounts by zone:** Pune 2, Mumbai 2, Nagpur 1.

> 💡 **Lesson:** check any "top" claim against the data. If Copilot names a single collector, confirm it with a `COUNTIFS`.

---

## Reference: What Your Results Should Show

| Check | Expected |
|---|---|
| Total accounts | 25 |
| DPD Bucket | 4 Critical · 9 High · 10 Medium · 2 Low |
| Highest Risk Score | Vikram Deshpande, 4,654,280 (BFL-PL-72529) |
| Days Since PTP Due | 10 blank · 0 for Rohan Mishra · 5 positive (2 to 6) · 9 negative |
| EMIs Overdue | Every Critical account shows 4 |
| Largest overdue by product | Personal Loan, ₹190,540 |
| Collector with most Critical | Rajesh Kumar, 3 |

---

## Agent vs M365 Copilot (Basic) — What Changes

| | Edit with Copilot (Agent) | M365 Copilot chat + Meta Prompt (this guide) |
|---|---|---|
| Licence | M365 Copilot (Premium) | M365 Copilot (Basic) |
| Writes formula into cells | ✅ Automatic | ✍️ You paste and fill down |
| Builds pivot table | ✅ Automatic | ✍️ You build it using Copilot's layout |
| Explains formulas, gives insights | ✅ | ✅ Same |
| Handles errors | Agent retries | You paste the error back and ask for a fix |
| What you learn | Prompting | Prompting **plus** checking the formula logic yourself |

---

## Troubleshooting

| Problem | What to do |
|---|---|
| Formula refers to row 1 or the wrong column | Remind Copilot: *"Headers are row 2, data starts row 3."* |
| Days Since PTP Due shows a date | Set the column format to **Number**. |
| `#NAME?` after pasting | Curly quotes crept in. Retype the `"` characters in Excel. |
| Pivot shows *Count* instead of *Sum* | Change it in **Value Field Settings**. |
| Pivot includes the title or note text | Rebuild it from **A2:Q27** only. |
| Pivot cannot see column N | Type `Spacer` in **M2** and rebuild. |
| Copilot says it can't open the file | Re-attach it from OneDrive, or paste the relevant rows as text. |

---

*Bajaj Finance Limited | AI Academy — Debt Management Services (Consumer) | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India***
