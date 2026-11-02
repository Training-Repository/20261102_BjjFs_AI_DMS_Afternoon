# Copilot-Assisted Document-to-PDF Playbook
**Bajaj Finance Limited | M365 Copilot Training — Debt Management Services (Consumer)**

## Purpose

This guide describes a robust, repeatable process for transforming large amounts of content and images into a professionally formatted PDF using Microsoft Copilot and Microsoft Word.

In DMS, typical uses are the monthly DMS review pack, a quarterly agency audit report, or a conduct-training handout for empanelled agencies.

The process is designed for:

- Up to 50 pages of content
- Up to 30 images
- Upload-constrained environments
- Users with minimal document-engineering experience
- Situations where content completeness is critical

---

# Choose Your Route

| Route | Use it when | What you do |
|---|---|---|
| **A — Notebook (default)** | Copilot Notebooks is available to you | Add your files to a notebook as references (up to 50 on M365 Copilot (Basic); 300+ licensed), then run the Phase 6 prompt in that notebook, replacing "the uploaded document" with "the sources in this notebook". Phases 7 to 9 apply as written. Notebooks accept `.docx, .pptx, .xlsx, .pdf, .txt` but not `.md`. Check that your figures carry through; if any are missing, use Route B. |
| **B — Single source document** | No Notebooks, or figure placement must be guaranteed | Follow Phases 1 to 5 to consolidate everything into one `SOURCE.docx`, then continue from Phase 6. |

The rest of this playbook describes Route B in full. Route A skips Phases 1 to 5.

---

# Core Principle

Do not ask Copilot to create a document from scattered source files.

Instead:

1. Consolidate all content into a single source document.
2. Provide sufficient structure and metadata.
3. Use Copilot to transform and enhance the document.
4. Export the validated result to PDF.

This minimizes content loss and reduces dependency on upload limits.

---

# Target Workflow

```text
Source Content
      +
Images
      ↓

SOURCE.docx
      ↓

Upload to Copilot
      ↓

Transform to FINAL.docx
      ↓

Validate
      ↓

Export PDF
      ↓

FINAL.pdf
```

---

# Phase 1 – Prepare Source Material

Gather:

- All textual content
- All images
- Existing headings
- Existing tables
- Existing appendices

Create a working folder.

```text
Project
│
├── Images
│
├── SOURCE.docx
│
├── FINAL.docx
│
└── FINAL.pdf
```

---

# Phase 2 – Assign Image Identifiers

Every image must receive a unique identifier.

Use this format:

```text
FIG-001
FIG-002
FIG-003
...
FIG-030
```

Do not use:

```text
Image 1
Image A
Screenshot
Chart Final
Diagram Latest
```

Identifiers must remain stable throughout the process.

---

# Phase 3 – Build the Source Document

The source document becomes the single source of truth.

Create:

```text
SOURCE.docx
```

---

# Recommended Source Document Structure

## Cover Page

Example:

```text
Document Title

Version 1.0

Source Document for Copilot Transformation
```

---

## Image Manifest

Create a master catalog of all images.

Example:

| Figure ID | Title |
|------------|---------|
| FIG-001 | Collection Efficiency Trend, Apr–Sep 2026 |
| FIG-002 | Bucket Roll-forward by Product |
| FIG-003 | Agency Audit Scores, Q2 FY2026-27 |

Purpose:

- Tracks all images
- Simplifies validation
- Reduces accidental image loss

---

## Main Content

For each image use the following structure.

### Example

```text
Section Title

Paragraph content.

FIGURE REFERENCE:
FIG-001

Purpose:
Shows the monthly Collection Efficiency % against the 97.5% target.

<INSERT IMAGE>

Caption:
Collection Efficiency Trend, Apr–Sep 2026
```

---

# Image Placement Standard

Every image should contain four components:

```text
1. Figure Identifier
2. Purpose Statement
3. Embedded Image
4. Caption
```

Example:

```text
FIGURE REFERENCE:
FIG-007

Purpose:
Shows contact-hour exceptions by agency for September 2026.

<IMAGE>

Caption:
Outside-Hours Calls by Agency
```

This creates sufficient context for Copilot even if the image itself contains complex information.

---

# Table Standard

Important tables should also receive identifiers.

Example:

```text
TABLE REFERENCE:
TBL-001

<INSERT TABLE>

Caption:
Agency Scorecard — September 2026
```

Use:

```text
TBL-001
TBL-002
TBL-003
...
```

---

# Phase 4 – Source Document Quality Check

Before uploading to Copilot verify:

## Images

- Every image has a Figure ID
- Every image has a caption
- Every image has a purpose statement
- Every image appears in the manifest

## Tables

- Every important table has a Table ID
- Every table has a caption

## Content

- All sections are present
- No duplicate sections
- No placeholder text remains

---

# Phase 5 – Upload to Copilot

Upload:

```text
SOURCE.docx
```

Only.

Treat this document as the authoritative source.

---

# DMS Example — Monthly Agency Review Pack

A worked outline you can reuse every month.

```text
SOURCE.docx
│
├── Cover: "DMS (Consumer) West Zone — Agency Review, September 2026"
├── Image manifest (FIG-001 … FIG-004)
├── 1. Summary (from your Copilot agency review — Stage 5 of the meta-prompt guide)
├── 2. Agency scorecard ............ TBL-001
├── 3. Breaches by clause .......... TBL-002  (clauses 3.1, 5.1, 5.2, 5.3)
├── 4. Outside-hours calls ......... FIG-001
├── 5. Complaint rate per 1,000 .... FIG-002
├── 6. Audit scores ................ FIG-003
├── 7. Actions and owners .......... TBL-003
└── Appendix: source sheets and the conduct standard reference
```

Build the tables and charts in Excel first, paste them into SOURCE.docx with their IDs, then run the Production Prompt below unchanged.

> The production prompt forbids new factual content. That matters here: an audit pack must contain only figures you can trace to the tracker.

---

# Phase 6 – Transformation Prompt

Use the following prompt as-is.

---

## Production Prompt

```text
The uploaded document is the complete source of truth.

Transform the document into a professional publication-ready Word document.

Requirements:

1. Preserve all content.
2. Do not summarize.
3. Do not omit any content.
4. Do not create new factual content.
5. Preserve every section.
6. Preserve every appendix.
7. Preserve all figure identifiers.
8. Preserve all table identifiers.
9. Preserve figure-to-content relationships.
10. Preserve table-to-content relationships.
11. Maintain all captions.
12. Create a professional heading hierarchy.
13. Create a table of contents.
14. Improve typography and spacing.
15. Improve consistency of styles.
16. Improve visual presentation.
17. Ensure the document remains suitable for PDF publication.
18. Treat the uploaded document as authoritative and complete.

Output a complete transformed document.

Before finalizing, verify:

- Every section is present.
- Every figure identifier is present.
- Every image is present.
- Every table identifier is present.
- No content has been removed.
```

---

# Phase 7 – Validate the Result

Validation is mandatory.

Never export directly to PDF.

---

## Structural Validation

Verify:

- All sections exist
- All appendices exist
- Table of contents is generated

---

## Figure Validation

Search:

```text
FIG-
```

Compare:

```text
Source Document Count
vs
Final Document Count
```

Both should match.

Example:

```text
Source: 27 Figures
Final: 27 Figures
```

---

## Table Validation

Search:

```text
TBL-
```

Compare counts.

Both should match.

---

## Spot Review

Review:

- First section
- Middle section
- Final section

This catches most transformation errors quickly.

---

# Phase 8 – Recovery Prompt

Use this only if content is missing.

```text
Compare the output document against the uploaded source document.

Identify every missing:

- Section
- Figure
- Table
- Appendix
- Caption
- Paragraph

Restore all missing content.

Do not modify correctly preserved content.
```

---

# Phase 9 – Export to PDF

Once validation succeeds:

```text
File
→ Save As
→ PDF
```

or

```text
File
→ Export
→ Create PDF
```

---

# PDF Quality Checklist

Before distribution confirm:

- Title page correct
- TOC correct
- Images render correctly
- Captions present
- Tables render correctly
- Page breaks correct
- No blank pages
- Appendices present
- PDF opens correctly

---

# Best Practices

## Do

- Use one source document
- Use stable figure identifiers
- Use figure captions
- Use purpose statements
- Validate before PDF export
- Keep the document as the single source of truth

## Don't

- Upload dozens of independent files
- Depend on image filenames
- Ask Copilot to recreate content from memory
- Skip validation
- Export directly to PDF without review

---

# Golden Rule

Ask Copilot to transform and improve a complete document.

Do not ask Copilot to reconstruct a document from fragmented inputs.

Document transformation is significantly more reliable than document generation.

---

*Bajaj Finance Limited | M365 Copilot Training — Debt Management Services (Consumer)*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
