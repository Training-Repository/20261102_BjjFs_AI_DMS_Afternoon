# M365 Copilot Training — Debt Management Services, Consumer (Bajaj Finance Limited)

Training materials for a Microsoft 365 Copilot enablement session for the Bajaj Finance Limited (BFL) **Debt Management Services (DMS) — Consumer** team, delivered by Technizer India under the **GenAI for Enterprise Teams** program.

The session covers prompt engineering (meta-prompting and the RTCFT framework), Excel formulas and pivot tables with Copilot, checking practice against a conduct standard in PDF, the end-to-end flow from a raw data file to a leadership-ready deck, using Copilot Notebooks to work across more files than the chat attachment limit allows, and turning a large document into a formatted PDF.

> All data in this repository is **synthetic** and safe to use in training. Customer names, account numbers and agency names are fictional. `Fair_Collection_Practices_Standard.pdf` is a **training sample**, not a BFL policy or a regulatory text.

The session follows the Inspect → Plan → Execute workflow shown in [`Workflow.png`](Workflow.png).

## Which guide do I use?

| You have | Use |
|---|---|
| M365 Copilot (Basic), the default | `Excel_Chat_Guide.md` for the Excel exercises |
| M365 Copilot (Premium) licence | `Excel_Agent_Guide_Premium.md` for the same Excel exercises, done by Copilot inside Excel |

Every other guide works on both.

## Contents

| File | Description |
|---|---|
| [`MetaPrompting_Guide.md`](MetaPrompting_Guide.md) | Introduces meta-prompting: asking Copilot to write your prompt for you. Includes six ready-to-use meta-prompts for DMS work. |
| [`Participant_Guide.md`](Participant_Guide.md) | Main hands-on guide. Six stages, each following the Meta Prompt → Generated Prompt → Live Apply rhythm: call documentation, account prioritisation, DMS performance reporting, roll-forward and recovery strategy, agency and conduct review, and a broken-PTP email in Outlook. |
| [`Excel_Chat_Guide.md`](Excel_Chat_Guide.md) | **Default Excel guide.** DPD bucket, risk score, days since PTP due and EMIs overdue formula columns, explaining a formula, and two pivot tables, using an RTCFT meta-prompt in M365 Copilot, applied by hand, with expected results to check against. |
| [`Excel_Agent_Guide_Premium.md`](Excel_Agent_Guide_Premium.md) | **Premium only.** The same exercises, with Copilot writing the formulas and building the pivots inside Excel. |
| [`Excel_To_PowerPoint.md`](Excel_To_PowerPoint.md) | "AI at Work" workbook describing a 9-step Copilot flow, across three chats (Discovery, Execution, PowerPoint), for turning any file into an analysis, a Word document, and a leadership deck. |
| [`Copilot_Notebooks_Guide.md`](Copilot_Notebooks_Guide.md) | Using Copilot Notebooks as a persistent workspace: add all files once as references, set standing instructions, and query across more files than the 3-attachment chat limit. |
| [`PDF_Playbook.md`](PDF_Playbook.md) | Repeatable process for turning a large document into a formatted PDF using Copilot and Word. |
| [`Fair_Collection_Practices_Standard.pdf`](Fair_Collection_Practices_Standard.pdf) | Conduct standard (training sample) covering contact hours, agent conduct, agency governance, PTP handling, disputes, grievances and reporting. Used in Stage 5 and in the Notebooks exercises. |
| [`DMS_Copilot_Dataset.xlsx`](DMS_Copilot_Dataset.xlsx) | Practice dataset for the meta-prompt stages. Sheets: Call Interaction Log, Account Priority Matrix, DMS Performance, Bucket Trend Analysis, Recovery Strategy Tracker, Agency & Conduct Tracker. |
| [`DMS_Copilot_Demo.xlsx`](DMS_Copilot_Demo.xlsx) | Practice dataset for the Excel exercises: 25 accounts as of 30 Sep 2026, with columns N–Q left blank for Copilot-generated formulas. |
| [`Workflow.png`](Workflow.png) | The Inspect → Plan → Execute workflow diagram. |
| [`Contact.md`](Contact.md) | Trainer contact details. |

## How to use this material

1. Start with `MetaPrompting_Guide.md` and `Participant_Guide.md` to learn the RTCFT framework and generate working prompts against `DMS_Copilot_Dataset.xlsx`.
2. Move to the Excel exercises on `DMS_Copilot_Demo.xlsx`: `Excel_Chat_Guide.md` by default, or `Excel_Agent_Guide_Premium.md` if you have a Premium licence.
3. Finish with `Excel_To_PowerPoint.md` to practise the full 9-step flow from raw file to analysis, document, and deck.
4. Use `Copilot_Notebooks_Guide.md` to move all of the above into a single Copilot Notebook, with no re-attaching and no 3-file limit.
5. Keep `PDF_Playbook.md` for when a review pack or report needs to go out as a PDF.

## Requirements

- M365 Copilot (Basic) is enough for everything except `Excel_Agent_Guide_Premium.md`
- Access to Copilot Notebooks in the M365 Copilot app (for `Copilot_Notebooks_Guide.md`)
- Excel files uploaded to OneDrive so they can be attached in M365 Copilot

---

*Delivered by Technizer India | GenAI for Enterprise Teams*
