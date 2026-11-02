# Copilot in Excel — Participant Exercise Guide
### Formulas & Pivot Tables for DMS (Consumer)
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `DMS_Copilot_Demo.xlsx`

> **Premium licence required.** This guide uses Copilot inside Excel (Agent / Edit with Copilot), which needs a paid Microsoft 365 Copilot licence. On M365 Copilot (Basic), use `Excel_Chat_Guide.md` instead. It produces the same results.
**Mode:** Copilot in Excel (Microsoft 365 Copilot licence). *M365 Copilot (Basic)? Use `Excel_Chat_Guide.md` instead.*

---

## Before You Begin

- Open `DMS_Copilot_Demo.xlsx` from **OneDrive**. Copilot in Excel needs the file saved in OneDrive or SharePoint with AutoSave on.
- Click the **Copilot** button (top-right of the Home ribbon) to open the Copilot pane, and keep it open for every exercise.
- The sheet `DMS Data` has **25 accounts**. Headers are in **row 2**, data runs from **row 3 to row 27**, and the data is as of **30 Sep 2026**.
- Columns **N–Q are intentionally blank**. You will fill them using Copilot. Column M is a blank spacer.

| Column | Field | Column | Field |
|---|---|---|---|
| A | Account ID | G | Call Outcome |
| B | Customer Name | H | PTP Date (blank if no PTP) |
| C | Product | I | PTP Amount (₹) |
| D | DPD | J | Collector Name |
| E | Overdue Amount (₹) | K | Zone |
| F | EMI Amount (₹) | L | Field Visit |

---

## Exercise 1 — Formula Column: DPD Bucket (Column N)

Click cell **N3**, then type into the Copilot pane:

```
In column N, add a formula that classifies each account into a priority
bucket based on DPD in column D:
- "Critical" if DPD is more than 90
- "High" if DPD is 61 to 90
- "Medium" if DPD is 31 to 60
- "Low" if DPD is 30 or less
Apply the formula to all 25 rows of data.
```

**What Copilot will produce:**
```excel
=IF(D3>90,"Critical",IF(D3>60,"High",IF(D3>30,"Medium","Low")))
```

✅ **Check:** 4 Critical, 9 High, 10 Medium, 2 Low.

---

## Exercise 2 — Formula Column: Risk Score (Column O)

Click **O3**, then type:

```
In column O, create a Risk Score for each account by multiplying DPD
(column D) by the Overdue Amount (column E). Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=D3*E3
```

✅ **Check:** the highest score is Vikram Deshpande (BFL-PL-72529) at **46,54,280**. The next highest are Swati Iyer and Deepak Joshi, so Personal Loans hold the top three.

> **Try this:** *"These scores are hard to read. Show them in thousands."* Copilot will divide by 1,000. This is the same scale the Account Priority Matrix in the main dataset uses.

---

## Exercise 3 — Formula Column: Days Since PTP Due (Column P)

Click **P3**, then type:

```
In column P, calculate how many days have passed since the PTP Date in
column H, as of 30 September 2026. If column H is blank, leave the cell
blank. Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=IF(H3="","",DATE(2026,9,30)-H3)
```

✅ **Check:**
- A **positive** number means the promised date has passed. The accounts with a positive number are Pooja Tiwari (6), Mohammed Shaikh (5), Anjali Verma (4), Ganesh Pawar (3) and Rashmi Singh (2).
- **0** means the PTP is due today (Rohan Mishra).
- A **negative** number means the PTP is still in the future.

> **On live data:** replace `DATE(2026,9,30)` with `TODAY()` so the column updates itself every day. The fixed date is used here so everyone in the room gets the same answer.

---

## Exercise 4 — Formula Column: EMIs Overdue (Column Q)

Click **Q3**, then type:

```
In column Q, estimate the number of EMIs overdue by dividing the Overdue
Amount (column E) by the EMI Amount (column F), rounded to the nearest
whole number. Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=ROUND(E3/F3,0)
```

✅ **Check:** Ramesh Patil (row 3) shows **2**, and every Critical account shows **4**. The overdue amount includes a ₹590 bounce charge, which is why the division is rounded.

---

## Exercise 5 — Ask Copilot to Explain a Formula

Click **N3**, then type:

```
Explain this formula in simple terms. What does each part do, and in what
order does it check the conditions?
```

**What Copilot will explain:**
> *"It checks the DPD in D3 from the top down. Over 90 returns Critical. If not, over 60 returns High. If not, over 30 returns Medium. Otherwise it returns Low. Each IF runs only when the one before it was false, so the highest band must be tested first."*

> **Try this:** *"What does this return for a DPD of exactly 90, and exactly 60?"* Because the tests are `>90` and `>60`, 90 lands in **High** and 60 lands in **Medium**. This boundary trap is worth checking on any banded formula.

---

## Exercise 6 — Pivot Table: Overdue by Product and Call Outcome

Click anywhere in the data, then type:

```
Create a pivot table on a new sheet that shows the total Overdue Amount
for each Product, broken down by Call Outcome. I want to see which products
carry the most escalated or unresolved balance.
```

**What Copilot will produce:**
- **Rows:** Product
- **Columns:** Call Outcome
- **Values:** Sum of Overdue Amount (₹)

✅ **Check:** Personal Loan carries the most overdue, **₹1,90,540**, and ₹1,62,160 of it sits in Escalated or Promise Broken accounts. Consumer Durable has the least overdue, **₹28,700**.

---

## Exercise 7 — Pivot Table: Collector Workload by DPD Bucket

Type into the Copilot pane:

```
Now create another pivot table showing the count of accounts for each
Collector Name, broken down by DPD Bucket (column N). I want to see each
collector's workload by priority.
```

**What Copilot will produce:**
- **Rows:** Collector Name
- **Columns:** DPD Bucket (Critical, High, Medium, Low)
- **Values:** Count of Account ID

✅ **Check:** Rajesh Kumar (Personal Loan) has 6 accounts, 3 of them Critical. Amit Tiwari has 4, and 3 of those are High.

> **If Copilot can't use column N:** the blank spacer column M can block range detection. Type `Spacer` into **M2** and ask again.

---

## Copilot Prompts — Quick Reference

| Task | Prompt to use in the Copilot pane |
|------|-------------------------------|
| DPD Bucket | "In column N, classify each account as Critical / High / Medium / Low from DPD in column D: Critical > 90, High 61–90, Medium 31–60, Low 30 or less." |
| Risk Score | "In column O, multiply DPD (column D) by Overdue Amount (column E)." |
| Days Since PTP Due | "In column P, days from the PTP Date (column H) to 30 Sep 2026; blank if no PTP." |
| EMIs Overdue | "In column Q, divide Overdue Amount (E) by EMI Amount (F), rounded to a whole number." |
| Explain a formula | "Explain this formula in simple terms." |
| Pivot — overdue by product | "Pivot: total Overdue Amount by Product and Call Outcome." |
| Pivot — collector workload | "Pivot: count of accounts by Collector Name and DPD Bucket." |
| Highlight broken PTPs | "Highlight rows where Days Since PTP Due (column P) is greater than 0 in amber." |
| Field list | "Filter to Field Visit = Yes and sort by Risk Score, highest first." |

---

*Bajaj Finance Limited | AI Academy — Debt Management Services (Consumer) | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
