# Copilot Notebooks — Participant Guide
### One workspace, all your files, no re-attaching
**Bajaj Finance Limited | M365 Copilot Training — Debt Management Services (Consumer)**
**Files used:** `DMS_Copilot_Demo.xlsx`, `DMS_Copilot_Dataset.xlsx`, `Fair_Collection_Practices_Standard.pdf`, and the guides in this repo

---

## Why Notebooks?

In a normal Copilot Chat, every new conversation starts from zero. You attach the file again, explain your role again and restate the format you want. You are also limited to **3 attachments per prompt**.

A **Copilot Notebook** is a saved workspace for one piece of work. You add your files to it once, as **references**, and write your standing instructions once. After that, every chat you start inside the notebook is grounded on those references, across sessions and days.

| | Regular Copilot Chat | Copilot Notebook |
|---|---|---|
| Files | Attached per prompt (max **3** in BFL) | Added once as **references**, then available to every chat in the notebook |
| Context | Lost when you open a new chat | Kept in the notebook across chats and days |
| Instructions (role, tone, format) | Re-typed in every prompt (the RTCFT block) | Set once in the notebook's **Copilot instructions** |
| Grounding | Your prompt + attachments (+ wider M365 / web, depending on settings) | **Only** the references you added, so answers stay focused on your files |
| Outputs | Chat replies | Chat replies, saved pages, and (where enabled) Word / PowerPoint drafts, mind maps, study guides |

> 💡 **Rule of thumb:** use one notebook per piece of work, such as the October agency review, the September bucket review or the monthly DMS MIS pack. Don't create a new notebook for every question.

---

## ⭐ Going Beyond the 3-Attachment Limit

This is the most useful reason to use Notebooks at BFL.

- The 3-file limit applies to **attachments in a chat prompt**.
- Notebook **references** are added separately, through the notebook's *Add references* panel rather than the chat box. Copilot then grounds its answers on **all** of them together.
- According to Microsoft's documentation:
  - **Copilot Chat** users can add up to **50 references**, and all 50 are used for grounding.
  - **Microsoft 365 Copilot** (licensed) users can add more than 300 references. The first **300** are used for grounding.
- A **OneDrive or SharePoint folder** can be added as a single reference. Every file you put in that folder later becomes available to the notebook without any extra steps.

**In practice:** one question can draw on the call log, the agency tracker, the monthly KPIs and the conduct standard at once, with nothing attached to the prompt.

> ⚠️ **Check in your own tenant:** the 3-attachment cap is BFL's setting for chat. If notebook references also appear capped, tell your trainer or IT, because the admin policy may differ. Exercise 2 below is a simple way to test it.

---

## Before You Begin

- [ ] You can sign in to the **M365 Copilot** app (desktop or web) with your BFL work account, and you see **Notebooks** in the left navigation.
- [ ] You have copied the files from this repo to your **OneDrive**, in a folder such as `OneDrive › Copilot-Training-DMS`.
- [ ] You have made `.txt` copies of three Markdown guides. Notebooks accept `.docx, .pptx, .xlsx, .pdf, .loop, .page, .txt, .rtf` and OneNote pages, but **not `.md`**. Download the guides, then rename them:

| Original in repo | Rename to |
|---|---|
| `MetaPrompting_Guide.md` | `MetaPrompting_Guide.txt` |
| `Participant_Guide.md` | `Participant_Guide.txt` |
| `Excel_To_PowerPoint.md` | `Excel_To_PowerPoint.txt` |

`Fair_Collection_Practices_Standard.pdf` needs no renaming, because PDFs are accepted as they are.

Your OneDrive folder should now contain **6 files**:

```
Copilot-Training-DMS/
├── DMS_Copilot_Demo.xlsx                   (25 accounts, as of 30 Sep 2026)
├── DMS_Copilot_Dataset.xlsx                (Call Interaction Log, Account Priority Matrix,
│                                                DMS Performance, Bucket Trend Analysis,
│                                                Recovery Strategy Tracker, Agency & Conduct Tracker)
├── Fair_Collection_Practices_Standard.pdf  (conduct standard — training sample)
├── MetaPrompting_Guide.txt
├── Participant_Guide.txt
└── Excel_To_PowerPoint.txt
```

That is already **twice the 3-attachment limit**, which is intentional for these exercises.

---

# Exercise 1 — Create Your Notebook
**Time:** ~5 minutes

### Step 1 — Create it
1. In the M365 Copilot app, select **Notebooks** → **New notebook**.
2. Name it: `BFL DMS Consumer — Sep 2026 Review`

### Step 2 — Add references
1. Select **Add references** (at the top of the content pane in the Copilot app, or the **+** next to *References* in OneNote).
2. Choose **one** method:
   - **Option A: files.** Select all 6 files from your OneDrive folder, or use **Upload** to add them from your computer.
   - **Option B: folder (recommended).** Select the `Copilot-Training-DMS` **folder** as a single reference.
3. Select **Add**.

> 💡 **Option B scales better.** When October's call log or agency audit lands in the folder, the notebook can use it without any extra step.

### Step 3 — Set the Copilot instructions (your RTCFT Role, Format and Tone, written once)
Open the notebook's **Copilot instructions** and paste:

```
I work in Debt Management Services (DMS) — Consumer, West Zone, at Bajaj Finance Limited (an NBFC).
Products: Consumer Durable, Digital Product, Lifestyle Finance, Personal Loan, Two-Wheeler.
Currency is ₹. Overdue amounts are in ₹ unless a column says ₹ Cr. The data is as of 30 September 2026;
the performance sheet covers April–September 2026 and the bucket trend covers July–September 2026.
The conduct rules are in Fair_Collection_Practices_Standard.pdf (a training sample).

When you answer:
- Use only the references in this notebook. Name the file and sheet (or the clause number, for the
  Standard) for every number or rule you quote.
- If something is not in the references, say "not in the data" — do not estimate.
- Lead with a 3-line summary, then a table, then recommendations with a suggested owner.
- Tone: factual, firm and audit-ready — suitable for the Head of DMS (Consumer).
- Use Red / Amber / Green where a target, limit or audit band exists.
```

### ✅ Check
Your notebook shows **6 references** (or 1 folder), and the instructions are saved.

---

# Exercise 2 — Validate the Notebook Can See Everything
**Time:** ~5 minutes

Before you rely on any analysis, confirm that Copilot has read every reference. This is the same idea as Step 1 of the 9-Step Flow.

Start a chat **inside the notebook** and type:

```
List every reference in this notebook. For each one, give:
- the file name
- what it contains (sheets / sections, row counts, periods covered)
- one fact from it that proves you have read it
Then tell me if any file looks incomplete or could not be read.
```

### ✅ Check
- [ ] All **6 files** are listed. That is more than you could attach to one chat prompt.
- [ ] For `DMS_Copilot_Dataset.xlsx`, it names all **six** sheets.
- [ ] For `DMS_Copilot_Demo.xlsx`, it mentions 25 accounts as of 30 Sep 2026.
- [ ] For the PDF, it identifies the Fair Collection Practices & Recovery Conduct Standard (ref DMS-CON-FCP-07) and notes that it is a training sample.

> If a file is missing, open **References**, confirm it is listed, and check that you can open it in OneDrive.

---

# Exercise 3 — Ask Across Files (the payoff)
**Time:** ~15 minutes

Neither question below could be answered in one regular chat prompt without going past the 3-attachment limit or re-attaching. In the notebook, you don't attach anything.

### 3a — One conduct theme, every source

```
Collection conduct appears in several places:
- Call Interaction Log (DMS_Copilot_Dataset.xlsx) — the Call Time and Called By columns
- Agency & Conduct Tracker (same workbook) — certification, outside-hours calls, complaints, audits
- DMS Performance (same workbook) — monthly Conduct Complaints
- Fair_Collection_Practices_Standard.pdf — the rules

Build a one-page conduct view for September 2026:
1. Calls in the log made outside the permitted hours, with caller and time
2. Agencies with outside-hours calls, uncertified agents, a complaint rate above
   the limit, or an audit score below 80
3. The monthly conduct complaints trend, against the limit in the Standard
4. Link: do the outside-hours calls in the log come from the same agencies the
   tracker flags?
Quote the clause number for every rule. Recommend 3 actions with owners.
```

**What a good answer contains:**
- **Call log:** two calls fall outside 08:00–19:00 (clause 3.1).
  - CL-02610 at 19:42, by Konkan Collect Associates (Anita Bhatt).
  - CL-02618 at 07:35, by DigiReach Tele-Collect (Kiran Desai).
- **Agencies:**
  - Konkan: 9 outside-hours calls; 52 of 58 agents certified; 6.8 complaints per 1,000; audit score 71 (Improvement Plan).
  - Godavari: 3 outside-hours calls; 24 of 27 agents certified; 6.6 complaints per 1,000; audit score 78 (Improvement Plan).
  - DigiReach: 14 outside-hours calls; 117 of 120 agents certified.
  - In total, **12 uncertified agents** are deployed against the 100% rule (clause 5.1).
- **Trend:** conduct complaints were 10–14 a month from April to August, then **27** in September. That is above the limit of 15 in clause 10.2, so the matter goes to the Zonal Business Head with a remediation plan.
- **Link:** yes. Both outside-hours calls in the log were made by agencies the tracker also flags. Clause 5.4 requires each exception to be reported within 2 working days.

### 3b — Policy against practice

```
Check the 20 accounts in the Call Interaction Log and the Account Priority Matrix
against clauses 3.1, 6.1, 6.3 and 7.1 of the Standard.
Give me a gap table: Clause | Requirement | Accounts affected | Evidence (file + sheet) |
Compliant? | Suggested action | Owner.
If the data cannot show whether a clause was followed, say so.
```

**What a good answer contains:**
- **Clause 7.1 (field contact on hold during a dispute):**
  - **Priya Kulkarni** (Dispute) still has Field Visit = Yes. This is a breach.
  - **Sunita Mehta** (escalated to the Dispute Desk, product returned to dealer) also has Field Visit = Yes. This is a breach.
- **Clause 3.1:** CL-02610 and CL-02618, as in 3a.
- **Clause 6.3 (broken PTP escalated within 24 hours):** Anita Bhatt (CL-02610) was escalated to a senior collector, so this is compliant.
- **Clause 6.1 (PTP confirmed by SMS within 24 hours):** Copilot should say this is **not in the data**. The log does not record whether the confirmation SMS was sent, so a check of the SMS records is needed.

### ✅ Check
- [ ] Every figure is quoted with its **file and sheet**, and every rule with its **clause number**.
- [ ] 3a draws on the PDF **and** three sheets of the workbook.
- [ ] 3b says "not in the data" for at least one clause rather than guessing.
- [ ] You did **not** attach a single file.

> 💡 **Tip:** Copilot may paraphrase a clause. Open the PDF and read the clause yourself before you quote it in a note or a report.

---

# Exercise 4 — Re-run the Use Cases Without Re-attaching
**Time:** ~10 minutes

In `Participant_Guide.md`, every stage asks you to attach the file before pasting the prompt. In the notebook, you skip the attach step.

Pick any two and use these short versions. The notebook instructions already supply the role, tone and format.

| Stage | Prompt inside the notebook |
|---|---|
| 1 — Call documentation | `From Call Interaction Log: a CRM entry for CL-02601, every Escalated or Dispute call with next step, and the PTPs due 1–7 Oct 2026.` |
| 2 — Account prioritisation | `From Account Priority Matrix: Critical accounts by Risk Score, count and overdue by tier, and the field-visit list excluding disputed accounts.` |
| 3 — DMS reporting | `From DMS Performance: Jul/Aug/Sep comparison, every metric that worsened in September, and two October actions.` |
| 4 — Recovery strategy | `From Bucket Trend Analysis and Recovery Strategy Tracker: worst roll-forward product with 3-month trend, and every At Risk segment with one action.` |
| 5 — Agency review | `From Agency & Conduct Tracker and the Standard: agency scorecard, breaches with clause numbers, one recommendation per agency.` |

**Quick checks:**
- **Stage 4:** Personal Loan is worst at 13.1% roll-forward in September. Three segments are At Risk: Severely Overdue, Promise Broken and Personal Loan — Hardship.
- **Stage 5:** Konkan Collect Associates is the first agency to discuss.

### ✅ Check
Compare the output with the regular-chat version from earlier. The format and tone should match **without** you retyping the RTCFT Role, Format and Tone.

---

# Exercise 5 — The 9-Step Flow, Inside One Notebook
**Time:** ~10 minutes

`Excel_To_PowerPoint.md` uses three separate chats (A: Discovery, B: Execution, C: PowerPoint) and asks you to **attach the file again** in Chat B. In a notebook:

1. Start **Chat A** in the notebook and run Steps 1–4 on one sheet, for example **DMS Performance** or **Agency & Conduct Tracker**. Copy the Working Prompt from Step 4.
2. Start a new chat in the **same notebook** (Chat B) and paste the Working Prompt. The file is already there.
3. Save the useful output as a **page** in the notebook, so it doesn't sit only in a chat.
4. If your notebook shows **create options** (Word document / PowerPoint deck), generate the Step-6 document or the Step-9 deck from the notebook. Otherwise, continue with the PowerPoint agent as in the workbook.

> 💡 **Why this helps:** the chats stay separate, which keeps the output clean, while the files and instructions are shared.

---

## Optional Extras (if visible in your tenant)

Microsoft is rolling out Notebook features in stages, so some of these may not appear for you yet.

| Feature | Try this |
|---|---|
| **Mind map** | Map how agencies, outside-hours calls, complaints and Standard clauses connect. |
| **Study guide** | Generate a quiz from `MetaPrompting_Guide` to test yourself on RTCFT. |
| **Word / PowerPoint from notebook** | Turn your Exercise 3a output into a Word brief or a 5-slide agency review deck. |
| **Share the notebook** | Share with a colleague so they work from the same references and instructions. |

---

## Efficiency Rules — Quick Reference

| Do | Avoid |
|---|---|
| One notebook per piece of work (e.g. "Oct agency review", "Sep bucket review") | One giant notebook for everything, because the grounding gets noisy |
| Put role, period, units, tone and format in **Copilot instructions** | Re-typing the RTCFT block in every prompt |
| Add a **folder** reference when logs and reports keep arriving | Re-uploading each new version by hand |
| Remove outdated references (last month's tracker, an old Standard) | Keeping v1, v2 and v3 of the same file, because Copilot may quote the wrong one |
| Ask Copilot to **name file + sheet or clause** for every number or rule | Accepting figures you can't trace |
| Treat a cross-file match as a lead and verify it | Acting on a match as if it were proof |
| Save good outputs as **pages** | Leaving key results only in chat history |
| Start a **new chat in the same notebook** for each new task | One endless chat, where earlier answers leak into later ones |

---

## Troubleshooting

| Problem | What to do |
|---|---|
| `.md` file can't be added | Rename it to `.txt`, or copy the content into a notebook page. |
| Copilot says it can't find a number | Check the file is in **References** and that you can open it. Ask: *"Which sheet contains X?"* |
| Copilot mixes periods (Sep calls vs Apr–Sep KPIs) | Name the sheet and period in the prompt: *"Use only the Call Interaction Log (21–30 Sep 2026)."* |
| A clause or figure looks wrong | Open the source, check it yourself, then ask Copilot to quote the exact text. |
| Answer uses the wrong file version | Remove old versions from References. |
| Notebooks not in the left navigation | Your licence or tenant setting may not include Notebooks yet. Tell your trainer. |
| Folder reference returns partial results | Very large folders are ranked for relevance, so name the specific file in your prompt. |

---

## Further Reading

- [How Microsoft Copilot Notebooks works](https://support.microsoft.com/en-us/microsoft-365-copilot/how-microsoft-365-copilot-notebooks-works)
- [Add references to your Copilot Notebook](https://support.microsoft.com/en-us/microsoft-365-copilot/add-references-to-your-microsoft-365-copilot-notebook)
- [Microsoft 365 Copilot release notes](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)

---

## 📝 Notes

**What I would put in a notebook at work:**

&nbsp;

**My standing Copilot instructions:**

&nbsp;

---

*Bajaj Finance Limited | M365 Copilot Training — Debt Management Services (Consumer)*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
