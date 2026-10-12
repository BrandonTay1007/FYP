# ParaShot (PCS-33)

Working notes for team PCS-33, topic 44 ParaShot, FIT3161 / FIT3163 at Monash University Malaysia. This repository holds assessment notes, staff rulings, and source PDFs. The application itself is not in this repo.

ParaShot is a lab screening tool: a microscopist uploads a faecal-smear image, a detector drafts bounding boxes and species labels, and a senior reviewer corrects the result before it is saved as a case and rolled into a batch report. It supports screening. It is not a diagnosis tool, and it does not classify host origin.

Supervisor: Dr Sicily. Teaching-team contact for pitch content: Soo Wooi King.

## Current work

The live task is the **final proposal presentation**.

| | |
|---|---|
| When | Tuesday 20 Oct 2026, 15:00–18:00 |
| Where | ALC6316 |
| Length | 14 minutes for five members. Q&A is not counted. |
| Order | Fourth of six: PCS22, PDS02, PCS34, **PCS33**, PCS06, PCS39 |

The proposal report is a separate assessment, due Monday 2 Nov 2026, 23:55. Notes for it live under `Group Proposal/`.

## Start here

Read these in order when preparing the final pitch:

1. [`Final Pitch /scoring_focus.md`](Final%20Pitch%20/scoring_focus.md) — where the marks are, and what to spend time on.
2. [`Final Pitch /teaching_team_clarification.md`](Final%20Pitch%20/teaching_team_clarification.md) — the nine-item MUM content flow. This is the content spec.
3. [`Final Pitch /final_pitch_content.md`](Final%20Pitch%20/final_pitch_content.md) — the working script. **AGREED** is decided. **PROPOSED** is a suggestion. **OPEN** still needs a decision.
4. [`Final Pitch /model_selection_research.md`](Final%20Pitch%20/model_selection_research.md) — detector choice (YOLO26 and RF-DETR). Confirm YOLO26 with the supervisor before it is treated as agreed. The kickoff list was YOLOv8–v12.

Logistics, the slot, and submission rules are in section 0 of `final_pitch_content.md`. They are not repeated in `scoring_focus.md`.

The folder name is `Final Pitch` with a trailing space. Quote it in the shell: `"Final Pitch /scoring_focus.md"`.

## What overrides what

- Pitch **content** follows `teaching_team_clarification.md`, not the generic Monash worksheet PDF in `Final Pitch /`.
- Pitch **marks** follow the rubric PDF in that same folder, version v260915. Check Moodle before the slot in case a newer rubric is posted.
- [`ParaShot_Pitch_Handover.md`](ParaShot_Pitch_Handover.md) is the September mid-semester dump. Where it conflicts with `final_pitch_content.md` or the October supervisor meeting, the later note wins.
- [`Final Pitch /ed_pitch_threads.md`](Final%20Pitch%20/ed_pitch_threads.md) is the pitch-related extract of Ed threads (through 12 Oct 2026). [`fit3161-fit3163-mum-s2-2026.csv`](fit3161-fit3163-mum-s2-2026.csv) is the full export that extract was taken from. Threads added on 12 Oct came from a later pull and are marked as such at the top of the extract.

## Repository map

| Path | What it is |
|---|---|
| `Final Pitch /` | Final presentation. Working notes, MUM content flow, rubric, spec PDF, Ed extract, model research. |
| `Mid_semester_pitch/` | PCS-33 grades and the cohort feedback from the mid-semester pitch. |
| `Group Proposal/` | Proposal-report worksheet clarification, the report rubric, and a report PDF. The report itself is the edit-logged Google Doc due 2 Nov. |
| `Meeting Minutes/` | Minutes for meetings 1–4 (Word). |
| `ParaShot_Pitch_Handover.md` | September context dump for the mid-semester pitch. Superseded for the final pitch where the two disagree. |
| Root PDFs | Mid-semester pitch spec, mid-semester rubric, and the group meeting-minutes instructions. |

Root files kept as staff issued them, including the spaced names:

- `Mid-Semester Project Pitch - Individual and Group Sign-off, Group Presentation-FIT3161-63-3188 v12082026 (2).pdf`
- `Marking Rubric - Mid-Semester Project Pitch - Individual and Group Sign-off, Group Presentation-FIT3161-63-3188 v17082026.docx.pdf`
- `Group Project Meeting Minutes  Videos (5).pdf`

## What stays off GitHub

`private/` is gitignored. Personal notes and individual feedback stay there. Do not commit them.
