# CLAUDE.md

Agent rules for this repo. For what the project is, the file map and the current deadlines, read `README.md` first. This file does not repeat it.

This is the **group** repo for PCS-33 (ParaShot). It holds notes and source PDFs. There is no application code here yet.

## Before you answer anything about the pitch or report

1. Read `README.md`, then the "Start here" files it lists.
2. Check the status labels in `Final Pitch /final_pitch_content.md`: **AGREED**, **PROPOSED**, **OPEN**.
3. If you do not have enough context to answer properly, say what is missing before you start producing content.

## Source precedence

- **Final pitch content order:** `Final Pitch /teaching_team_clarification.md` (the nine-item MUM flow) only. Do not add items from the generic Monash spec `_Group Final Proposal Presentation (1).pdf`: no use cases, no "5 significant requirements", no testing approach, no WBS, no contribution slide. Add these only if the user asks.
- **Final pitch marks:** the rubric PDF v260915 in `Final Pitch /`.
- **Staff rulings:** `Final Pitch /ed_pitch_threads.md` (verbatim Ed). A later post overrides an earlier one.
- **Supervisor (Dr Sicily):** section 2 of `final_pitch_content.md`.
- **`ParaShot_Pitch_Handover.md`:** September material. It loses to any later note.
- **`Meeting Minutes/`:** often wrong on names, dates and decisions. If a minutes detail looks odd or conflicts with a better source, list it and ask the user. Do not quietly use it.
- **Proposal report (due 2 Nov 2026):** `Group Proposal/teaching_team_ed_clarification.md` and the report rubric in that folder.

## Content rules

- **Labels.** Mark your own suggestions **PROPOSED**. Never relabel anything as **AGREED** unless the user confirms it. When the user decides something, update the label and note who decided it.
- **Product claims.** ParaShot supports screening. It is not a diagnosis tool, and it does not classify host origin (human vs animal). Do not write either claim.
- **Model results.** The team has no trained model results yet. Any accuracy figure must be a published result, cited and labelled as such (for example, Chula-ParasiteEgg-11 / ICIP 2022). Never present one as ours.
- **Detector choice.** The supervisor kickoff list was YOLOv8–v12. YOLO26 and RF-DETR are research suggestions in `model_selection_research.md`. Keep them PROPOSED until the supervisor confirms.
- **Names on slides.** "Victor" is Siow Yee Yang on Allocate+. Use **Siow Yee Yang** on anything staff will see.
- **Conclusion section.** Only reflection on teamwork and project management, plus anticipated team and management problems. Project risks belong in the risk section, not here.
- **Content before slides.** The user wants the content agreed before any slide design. Do not build decks unless asked.
- **Dates.** Write absolute dates (e.g. 20 Oct 2026), not "next week".

## Editing the notes

- Match the existing style: short sections, tables where they help, plain sentences.
- `scoring_focus.md` has a changelog at the bottom. Add a dated line whenever you change that file.
- Mark agent inference as inference. Mark staff guidance as staff guidance.
- `Final Pitch /slide_idea.md` is the user's rough scratch. Read it for intent. Do not tidy or rewrite it unless asked.

## Repo hygiene

- The folder is `Final Pitch ` with a **trailing space**. Quote it in the shell: `"Final Pitch /final_pitch_content.md"`.
- `private/` is gitignored and holds personal notes and individual feedback. Never copy its contents into tracked files. Teammates read this repo.
- Keep staff-issued PDFs under their original names.
- Commit only when the user asks. Write commit messages as one plain sentence describing the change.
- To read `.docx` files on this Mac, use `textutil -convert txt -stdout <file>`.
