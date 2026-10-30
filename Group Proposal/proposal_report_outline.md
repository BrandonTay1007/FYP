# ParaShot Project Proposal Report: Outline and Content Guide

Drafted 31 Oct 2026. Due **Mon 2 Nov 2026, 11:55 PM**. Worth 10%.

This file is a guide for writers, not the report. Each heading says what the marker wants, what we should put there, where the material already lives, a word budget, and a status.

Legend: **AGREED** = decided by the user, team or supervisor. **PROPOSED** = agent suggestion, not yet decided. **OPEN** = we do not have the content or the decision yet.

Owners use the pitch split from Meeting 4 (9 Oct) and are **PROPOSED** for the report. Confirm in the team chat.

---

## Rules that shape the whole report

Sources: `Project Proposal Report .pdf` (the worksheet, V22092026), `Marking rubric for project proposal report.pdf`, `ed_proposal_threads.md`. When the worksheet and rubric differ, follow the worksheet (staff, Ed 3685039, 29 Oct).

| Rule | Detail | Source |
|---|---|---|
| Marks | Intro 10, Lit review 15, PMP 50, Methodology 10, Conclusion 5, References 5, Style 5 | Worksheet; staff confirmed worksheet split (Ed 3672668, 25 Oct) |
| Word limit | 3500 ±10%, so 3850 hard cap. Aim for about 3500 | Ed 3681417, 3686256 |
| What counts | Body text and headings in chapters 1–5 | Ed 3685641 |
| What does not count | Front matter (cover, TOC, authorship statement), figure and table labels, references, appendices, code. Other tables: see the next row | Ed 3684559, 3688593 |
| Tables (unclear) | Staff gave mixed answers. Ed 3679445 (28 Oct): "List of requirements are still counted. Labels are not." A student then asked if only the requirements table counts, and staff replied "Items in tables are not counted" (that could mean all tables, or "other tables"). Ed 3684559 (29 Oct): "Labels and things in tables do not count." **Safest reading (PROPOSED): count the requirements table, do not count other tables** | Ed 3679445, 3684559 |
| References | At least 15 for a 3-person team, more for larger teams. We have 5, so aim for **about 25**. Any citation anywhere in the report counts. APA | Ed 3676563; worksheet 8b |
| Reference check | Messy or wrong references can be treated as GenAI misuse. Any member may be asked what a cited source says. Every writer must have opened what they cite | Worksheet 8d |
| Authorship statement | Missing = automatic 50% penalty. Both the worksheet layout and a table layout are fine | Worksheet; Ed 3641037 |
| Edit log | Draft in an edit-logged online doc. Other word processors are allowed, but keep a version history in case staff ask for it | Worksheet; Ed 3648882 |
| Submission | Every member clicks SUBMIT on Moodle | Worksheet |
| Not needed | Sample code (removed from the updated rubric) | Ed 3673486 |

**Biggest lever (PROPOSED):** put the scope list, roles, WSM, communication plan and resource list into tables, which do not count toward the limit. Body text then explains and justifies them. This frees words for the literature review and the risk process, which carry the marks.

**The requirements table is the exception:** budget it as counted, about 250 words (see 3.1.3). Keep each row to one short line (ID, requirement, type, priority). Put rationale, owner, acceptance criteria and status in the RTM in Appendix A, which is not counted. If staff later confirm that every table is excluded, those 250 words become spare.

**Product claims, everywhere in the report:** ParaShot supports screening. It is not a diagnosis tool and does not classify host origin (human vs animal). We have no trained model results. Any accuracy figure is a published result, cited as such (e.g. Chula-ParasiteEgg-11, ICIP 2022). Use "Siow Yee Yang", not "Victor".

### Word budget (PROPOSED, split by marks)

| Chapter | Marks | Budget |
|---|---|---|
| 1 Introduction | 10 | 320 |
| 2 Literature review | 15 | 650 |
| 3 Project management plan | 50 | 1760 (includes ~250 for the requirements table) |
| 4 Methodology | 10 | 550 |
| 5 Conclusion | 5 | 150 |
| Headings | | ~100 |
| **Total** | | **~3530** (about 320 under the 3850 cap) |

---

## Front matter (0 marks, not counted, but the 50% penalty sits here)

- Title page: "ParaShot: Human-in-the-loop parasite egg screening" (PROPOSED title), team PCS-33, topic 44, unit codes, supervisor Dr Sicily, date.
- Member names and IDs (Allocate+ names): Tay Wei Yong 34601066, Liew Yu Hong 34476148, Siow Yee Yang 34600701, Hong Zhi Hong 34474994, Kam Joshua 35832312.
- **Total word count** on the cover.
- Table of contents, list of figures, list of tables.
- **Authorship statement:** for each member's initials, (i) the sections they drafted and finalised and (ii) the figures and tables they led. Fill in from the "Who writes" lines below once owners are confirmed.

Who writes: OPEN. The worksheet suggests electing one proof editor and style wrangler; that person can own the front matter.

---

## 1 Introduction (10 marks, ~320 words)

The rubric wants: the project and team, the background and problem, the expected outcome, and a map of the report.

### 1.1 Project background and problem (~140)

- Parasite egg identification in stool smears is still done by eye. WHO still treats Kato-Katz microscopy as the standard for soil-transmitted helminth programmes (Stuyver & Levecke, 2021).
- It needs scarce expertise, results vary with the reader, and nothing structured is kept about what was seen or corrected (Keller et al., 2020; Mohammed et al., 2025).
- Field reality: a field trip returns hundreds of images, and the expert becomes the bottleneck.
- Motivation: the supervisor's One Health collaboration with Orang Asli communities (Dr Azdayanti, Assoc. Prof. Ogawa). Say it is the context, not a labelled task.
- Source: `Final Pitch /final_pitch_content.md` 5.2; `ParaShot_Pitch_Handover.md` problem/opportunity text (Sep, reword it).

### 1.2 Aims and expected outcome (~110)

- One sentence: ParaShot turns a microscope photo into a reviewed, exportable case.
- Workflow: upload a batch → standardise images → detector drafts box, species and confidence for every egg → senior reviews and corrects → cases saved → batch report.
- Deliverables: web app, detector trained on Chula-ParasiteEgg-11, case database, batch report.
- Positioning clause: screening support, not diagnosis, not host-origin classification.
- Introduce the team in one line (five members, roles in 3.2.2).

### 1.3 Report structure (~70)

- One sentence per chapter: 2 literature review, 3 project management plan, 4 methodology, 5 conclusion, appendices A–D.

Who writes: PROPOSED Liew Yu Hong (did intro and problem at mid-sem).
Status: problem statement AGREED (mid-sem). Field-trip bottleneck, workflow and deliverables PROPOSED (pitch 5.2).

---

## 2 Literature review (15 marks, ~650 words)

The worksheet wants intro, body and conclusion as subsections. Critique previous work and tools, synthesise themes, and justify the project by a gap. The rubric adds: academic **and** grey literature, competing tools, and PM methodologies. Staff say the "critical analysis of PM methodologies" means **using a WSM to pick the methodology** (Ed 3679373, 29 Oct). The 6 Oct structure post says the WSM "can go here".

### 2.1 Introduction (~60)

- What the review covers and why: problem context, detection methods, existing tools, delivery methodology.

### 2.2 Body (~470)

Write by **theme**, not paper by paper. Synthesis is what the HD band asks for.

**2.2.1 The screening problem (~80)**
- Kato-Katz is still the standard, it depends on skill, and expertise is getting scarce. Sources: Stuyver & Levecke 2021; Keller et al. 2020; Mohammed et al. 2025.

**2.2.2 Automated egg detection (~150)**
- Public datasets: Chula-ParasiteEgg-11 (Anantrasirichai et al., 2022) and AI-KFM (Capuozzo et al., 2024).
- Published results, labelled as published: ICIP 2022 winners used multi-model ensembles (F1 about 0.99). Single lightweight YOLO models report mAP@0.5 of 0.96–0.99 on Chula (YAC-Net, Parasites & Vectors 2024; Intelligence-Based Medicine 2025; INJET 2025).
- Version differences are about one point, so the choice rests on speed, ecosystem and maintenance (feeds 4.1).
- Weakness theme: performance drops out of domain. F1 fell from 0.88 to 0.53 on new images (Heliyon 2024). This is why senior review stays in the loop.
- Source: `Final Pitch /model_selection_research.md` sections 1–3, 5 and the addendum.

**2.2.3 Existing and competing tools (~120)**
- Ward et al. 2022: affordable AI digital pathology for Kato-Katz smears, still paired with human verification.
- Oyibo et al. 2025: multiclass detection of STH and *S. mansoni*.
- Commercial and grey-literature tools: **OPEN.** The repo has no review of commercial parasitology software yet. Someone must find 2–3 real ones (vendor pages, product docs), check what they do, and note that they are scanner-bound or closed. Do not name a product nobody on the team has looked at.
- Critique point for every tool: does it keep a reviewed, traceable case record and a batch report? That is the gap ParaShot fills.

**2.2.4 Delivery methodology and the WSM (~120)**
- Compare 3–4 methodologies (e.g. predictive/waterfall, Scrum, Kanban, hybrid iterative-incremental) in a **WSM table** (does not count toward words). Criteria (PROPOSED): handles changing requirements (batch and roles arrived after mid-sem), fits a part-time student team, supports risk-first ordering (detector first), works across two semesters with a break, supervisor checkpoints.
- Cite 2–3 PM sources (e.g. the Scrum Guide, PMBOK or a software engineering text, plus the unit's seminar material).
- Body text states the winner and the one or two criteria that decided it. Section 3.2 then applies it without repeating the comparison.
- **OPEN:** the team has not recorded a methodology WSM. The mid-sem WSM compared models and topic options, not methodologies. Scores need team agreement, since members may be asked to justify them.

### 2.3 Conclusion and rationale (~120)

- The gap: detectors are accurate on benchmark data, but published systems and tools stop at detection. They do not provide a reviewed case record, role-based approval or a batch report for field screening, and they still need human checking out of domain.
- ParaShot's answer: human-in-the-loop review, an approval gate, and a per-sample and per-batch report.
- One line linking to the chosen methodology.

**Reference pool already in the repo (19, need ~25):** Keller 2020; Stuyver & Levecke 2021; Ward 2022; Mohammed 2025; Oyibo 2025; Anantrasirichai 2022; Capuozzo 2024 (all in `ParaShot_Pitch_Handover.md`); YAC-Net 2024; Intelligence-Based Medicine 2025; INJET 2025; Heliyon 2024; Diagnostics 2023; Sci Rep 2023 CoAtNet; RF-DETR paper (arXiv 2511.09554); RF-DETR urine microscopy 2025; Ultralytics YOLO26 docs; Frontiers in Microbiology 2024; Dacal et al. (phone JPG); IEEE DataPort Chula record (all in the two research files). Missing: PM methodology sources (2–3) and competing tools (2–3). Every URL needs a full APA entry. Open each one before citing it.

Who writes: PROPOSED split by theme across members, so each member contributes about 5 references.
Status: themes and source choice PROPOSED; competing tools and the methodology WSM OPEN.

---

## 3 Project management plan (50 marks, ~1760 words, including the requirements table)

Half the marks. The rubric lists: scope statement, requirements and RTM, team organisation and roles, management process, schedule, resources. The 6 Oct staff post: "finalised (as of end of semester) project requirements, scope, limitations etc."

### 3.1 Scope and requirements (~590, including the requirements table)

**3.1.1 Scope statement (~80 + table)**
- Table: in scope vs out of scope, each with a **priority** (must / should / stretch). The HD band asks for high and low priority items.
- In scope: batch upload, detection, three box states and review, junior and senior roles, case history, batch report, settings page.
- Stretch: separately validated accuracy on mixed-species images; mobile app (only if early).
- Out of scope: diagnosis, host-origin classification, mobile app (baseline), live video, lab information system integration, proprietary microscope files (VSI, ND2, LIF, CZI) and whole-slide DICOM, multi-organisation support.
- Source: `final_pitch_content.md` 5.5, 5.4d, section 7.

**3.1.2 How requirements were obtained (~100)**
- Supervisor kickoff (31 Aug), 27 Aug consultation (three-tier users), Meeting 3 (17 Sep, pipeline first, authentication), early Oct supervisor meeting (batch, report, two roles, formats, accuracy target), team review on 12 Oct (sample level, review status, missed eggs, confirmed negatives), literature (accuracy target, format choice).
- This is what the rubric means by "discussion of how requirements are obtained".

**3.1.3 Functional and non-functional requirements (~60 text + ~250 table, counted)**
- Table of finalised FRs and NFRs as of end of semester. **Budget it as counted** (staff, Ed 3679445: "List of requirements are still counted"). Keep rows to one short line: ID, requirement, type, priority. About 18 rows at ~14 words each = ~250 words. Body text explains what changed since mid-sem: batch, roles, report as the headline, review flow.
- **Use the numbering and ★ markers on Canva pages 11–12** (15 Oct); do not use the 5.4 table numbers in `final_pitch_content.md`, which were renumbered in Canva. **OPEN**.
- NFRs: NFR1 mAP@0.5 ≥ 0.90 and F1 ≥ 0.90 on the held-out Chula test split, stretch 0.95 (PROPOSED, `model_selection_research.md`). NFR2 per-image time still "≤ N s" (**OPEN**). NFR6 Chrome and Edge (PROPOSED).
- **OPEN:** copy the full FR/NFR list from Canva pages 11–12 into the report. The repo has only part of it.

**3.1.4 Acceptance criteria (~40 + separate table)**
- One testable criterion per key requirement, e.g. "a senior can approve a case only when no box is in the check state", "the batch report counts approved cases only", "NFR1 met on the held-out split".
- Staff: acceptance criteria are what the stakeholder deems satisfactory (Ed 3679990). Say ours come from the supervisor's stated priorities, then confirm with her. She is away 25 Oct to 7 Nov, so mark them as pending her review.
- Put them in their own table or in the Appendix A RTM, not as a column in the requirements table, so they stay outside the count (PROPOSED).

**3.1.5 Limitations and assumptions (~60)**
- Limitations we cannot fix or propose away: trained on Chula faecal smears, not field images; Colab compute; no guaranteed collaborator images; no validation with real lab staff.
- One assumption: Chula images are representative enough to be useful on lab images.
- Source: `final_pitch_content.md` 5.5.

Who writes: PROPOSED Brandon + Joshua (plan and scope owners).
Status: in-scope items AGREED (user, 11 Oct: batch upload and roles in). Out-of-scope list and limitations PROPOSED (pitch 5.5, 5.6), including "no validation with real lab staff". Acceptance criteria and full NFR list OPEN.

### 3.2 Project organisation (~450)

**3.2.1 Development lifecycle model (~300)**
- State the model and why. Hybrid models are allowed (Ed 3678154). PROPOSED: **hybrid iterative-incremental**. Semester 1 was mostly up-front (requirements, design, risk), Semester 2 delivers increments (detector → review → history/report → settings → deploy), with supervisor review at each.
- Justify from our facts: requirements changed after mid-sem (batch, roles); risk-first ordering (detector first, supervisor Meeting 3); the web team builds on a stand-in model so AI delays do not block them; the per-feature checklist before each feature is built.
- Adaptations to a student team: part-time hours, the semester break, the supervisor away 25 Oct to 7 Nov.
- Refer back to the WSM in 2.2.4; do not repeat it.
- **OPEN:** confirm the team actually uses this model, and whether we run sprints (length?) or a Kanban flow.

**3.2.2 Team roles and responsibilities (~150 + table)**
- Table: member, development role, PM responsibility, report section owned.
- Dev roles (Meeting 4, AGREED): Hong Zhi Hong and Kam Joshua full-stack and test; Liew Yu Hong and Siow Yee Yang AI engineers; Tay Wei Yong product manager and development support.
- Add the rotating chair and minute-taker (pitch 5.9).
- Stakeholders not on the team: Dr Sicily (supervisor), Dr Azdayanti and Assoc. Prof. Ogawa (collaborators). They are not users.

Who writes: PROPOSED Brandon.

### 3.3 Schedule and resources (~250)

**3.3.1 Schedule overview (~130)**
- Summarise phases and milestones in text and point to the Gantt (Appendix D) and WBS (Appendix C).
- Milestones (AGREED, pitch 5.6): M1 detector meets the 0.90 target; M2 MVP feature-complete (Sem 2 W8); M3 deployed (W10); M4 final demo and report (W12).
- Dependencies: M1 → threshold tuning; detection API → upload/detect/display; M2 → integration testing → M3.
- Fixes since mid-sem: deployment no longer overlaps integration testing; training moved to the semester break; M1 fallback ("continue with the best model so far").
- Source: Canva Gantt (page 15/16 is current, not the local `Final Pitch /gantt/` SVGs).

**3.3.2 Resources (~120 + table)**
- Table: human (5 members, roles, hours per week **OPEN**), compute (Colab for training; Hugging Face compared; CPU fine for single-image inference, GPU better for batch), software (Ultralytics, RF-DETR, web stack **OPEN**, Git/GitHub, Canva, Notion), data (Chula-ParasiteEgg-11 primary, AI-KFM comparison), storage for batches (**OPEN**, research was due 22 Oct), people outside the team (supervisor time, collaborators).
- Note what we do not have: real lab testers. The usability test uses team and peers role-playing junior and senior.

Who writes: PROPOSED Joshua.
Status: milestones AGREED; hours, web stack and storage OPEN.

### 3.4 Management process (~470)

The biggest single chunk of marks inside the PMP (20 of 50 in the worksheet split). The rubric wants: risk management with an extensive register covering PM **and** technical risks, a communication plan, monitoring, and review and audit.

**3.4.1 Risk management process (~200)**
- Describe the cycle: identify (team brainstorm, supervisor feedback, literature), analyse (likelihood × impact, high/medium/low), respond (avoid, mitigate, recover), monitor (register reviewed at each meeting, owner per risk).
- Name the top 3 in text, with the full register in Appendix B:
  1. Look-alike eggs keep per-class accuracy under 0.90 (Capillaria; blurred Ascaris vs *H. nana*). Technical.
  2. Domain gap: passes on Chula, fails on lab images. Technical.
  3. Scope growth from supervisor or collaborator requests. PM.
- Source: `final_pitch_content.md` 5.8. Owner at the pitch: Siow Yee Yang.

**3.4.2 Communication plan (~110 + table)**
- Table: who, channel, frequency, purpose. Team (weekly meeting, chat), supervisor (meetings; away 25 Oct to 7 Nov; no Fridays), collaborators (through the supervisor), teaching team (Ed).
- **OPEN:** the actual channels and meeting cadence. Fill in from what the team really does.

**3.4.3 Monitoring and control (~90)**
- Progress against milestones on a task board (tool **OPEN**: Notion, GitHub Projects, Trello?).
- Per-feature checklist before implementation (Meeting 4).
- Change control: justified scope changes are logged, not hidden.

**3.4.4 Review and audit (~70)**
- Meeting minutes with rotating chair and minute-taker; Git version control with branches and reviews; edit-logged report doc; supervisor check-ins.

Who writes: PROPOSED Siow Yee Yang (risk) + Brandon (communication, monitoring).
Status: top 3 risks PROPOSED (wording from the pitch); communication plan and tools OPEN.

---

## 4 Methodology (10 marks, ~550 words)

The worksheet wants algorithms and ML approach, an architecture diagram with integration, and data source and pre-processing. The rubric wants enough detail that another team could repeat it: software, tools, libraries, data steps, development steps. The 6 Oct staff post adds "proposed solution + software designs".

### 4.1 Detection approach (~180)

- Detector: YOLO26 small as the deployable model, RF-DETR Small as the CNN vs transformer comparison. Both **PROPOSED**. The supervisor's kickoff list was YOLOv8–v12, so say "pending supervisor confirmation" unless she has confirmed since 22 Oct (**OPEN**).
- Why: single YOLO versions differ by about one point on Chula; YOLO26 is faster on CPU; RF-DETR has published domain-transfer evidence.
- Training: fine-tune from COCO weights, held-out test split, report mAP@0.5, mAP@0.5:0.95 and F1, per-class metrics, mosaic augmentation.
- Inference: run once per image at a low floor (~0.05), store all boxes. Thresholds are browser-side filters giving three box states (counted / check / hidden), never a re-run.
- Short pseudocode for the threshold filter and approval gate (optional; code does not count toward words).
- Source: `model_selection_research.md`; `final_pitch_content.md` 5.4b.

### 4.2 Data source and pre-processing (~140)

- Chula-ParasiteEgg-11 (11 species, primary); AI-KFM comparison only.
- Upload accepts `.jpg`, `.jpeg`, `.png`, `.tif`, `.tiff`. Each file is decoded once and stored as one 8-bit RGB PNG, keeping the original filename. The detector works on a resized RGB tensor. JPEG sources and the resize are declared loss. The lossless check applies only to PNG and uncompressed or LZW TIFF.
- Sample metadata (sample ID, site, date) entered at upload, recorded as given.
- Source: `image_format_research.md`; `final_pitch_content.md` 5.4d. JPEG acceptance still needs supervisor confirmation (**OPEN**).

### 4.3 System architecture and integration (~140 + figure)

- Architecture diagram: browser → API → job queue → inference service → case database + image storage. Label the stored model version.
- Text: how the parts connect, why batch detection runs as a background job, why model output is immutable and corrections are a separate layer (who, when). That layer is what makes the traceable-record claim true.
- **OPEN:** the diagram does not exist in the repo yet. Draw it.

### 4.4 Software design (~50 + figures)

- Low-fidelity wireframes: login, batch upload, batch overview, single-image review (solid and dashed boxes, "show hidden" toggle, approve button), case history, report preview, settings.
- Source: `Final Pitch /wireframes/requirement_wireframes.html` and the Canva deck.

### 4.5 Tools and development steps (~40 + table)

- Table: languages, libraries (Ultralytics, RF-DETR), training environment (Colab), web framework and database (**OPEN**, no stack chosen as of 11 Oct), version control, design tools.
- Development steps in order: environment setup → baseline training → detection API with a stand-in model → review UI → history and report → settings → integration testing → deployment.

Who writes: PROPOSED Liew Yu Hong + Siow Yee Yang (4.1, 4.2); Hong Zhi Hong + Joshua (4.3–4.5).
Status: detector and format PROPOSED; architecture diagram and tech stack OPEN.

---

## 5 Conclusion (5 marks, ~150 words)

- One or two paragraphs that **summarise the report**: the problem, the gap, what ParaShot will deliver, how it will be managed (lifecycle, milestones, top risks), and the method.
- No new material.
- PROPOSED: the worksheet and rubric ask for a summary, so this differs from the pitch conclusion (teamwork reflection). A one-sentence nod to teamwork is fine; do not turn it into a reflection.

Who writes: PROPOSED Tay Wei Yong (did the mid-sem conclusion).

---

## References (5 marks, not counted)

- APA 7th, only works cited in the text, about 25 entries.
- Use Zotero or similar. Everyone checks their own entries against the source.

---

## Appendices (not counted)

| Appendix | Content | Source | Status |
|---|---|---|---|
| A RTM | The full RTM **from the time of the pitch** (worksheet 4a ii). Body 3.1.3 holds the finalised list | Canva pages 11–12; staff did not want an RTM on the pitch slides, so the full matrix may need building from them | **OPEN** |
| B Risk Register | All 10 risks: the top 3, plus Colab quota, declared JPEG and resize loss, unknown batch storage, team availability, supervisor away 25 Oct to 7 Nov, late AI and web integration, dependence on the two AI engineers. Columns: ID, risk, type (PM or technical), likelihood, impact, rating, avoid, recover, owner | `final_pitch_content.md` 5.8 | PROPOSED (ratings are agent suggestions) |
| C WBS | Module-level tree: management, detector, web app (upload, review, history, report, settings), deployment, testing, documentation. Staff: the Gantt already contains the WBS if done right, but the worksheet lists both (Ed 3682111, 3685481) | Derive from the Gantt | **OPEN** |
| D Gantt | Both semesters, milestones and dependency arrows. Use landscape pages for the wide chart (Ed 3689275 is unanswered; landscape is the safe choice) | Canva Gantt pages | AGREED (user, 15 Oct); dependency arrows PROPOSED (16 Oct) |

---

## Open items to settle before writing (by 1 Nov 2026)

1. Confirm section owners (this file's "Who writes" lines are PROPOSED).
2. Anything decided at the 20 Oct pitch or the 22 Oct supervisor wrap-up? This outline uses notes up to 16 Oct. In particular: YOLO26, JPEG acceptance, the 0.90 target, review status, missed-egg boxes, confirmed negatives.
3. Methodology WSM: options, criteria and scores (2.2.4).
4. Competing tools: find and read 2–3 (2.2.3).
5. Full FR and NFR list from Canva pages 11–12, plus the NFR2 time figure.
6. Acceptance criteria per key requirement.
7. Communication channels, meeting cadence and task-board tool.
8. Weekly hours, web stack and batch storage for the resources table.
9. Architecture diagram, WBS and pitch-time RTM.
10. Lifecycle: confirm hybrid iterative-incremental and sprint length.
11. Table counting: optionally ask on Ed whether the requirements table counts. Until staff answer, budget it as counted.
