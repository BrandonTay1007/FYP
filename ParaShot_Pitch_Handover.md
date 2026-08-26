# ParaShot — Mid-Semester Pitch Handover Document

> **Purpose of this file:** A complete context handover so another agent (or team member) can continue preparing the mid-semester project pitch deliverable without re-reading all the source PDFs. It captures the unit requirements, the assigned project, and the content drafted so far.
>
> **Working hub:** [Notion FYP](https://app.notion.com/p/3c83a300c24f806bbbd0ff2cdfabbac7) (Monash → Y3S1 → FYP). Prefer that for navigation; keep this file as the long-form dump.

---

## 1. Project at a glance

- **Unit(s):** FIT3161 Computer Science Project Part 1 / FIT3163 Data Science Project Part 1 / FIT3188 Cyber Security Project Part 1 (Monash University Malaysia — MUM)
- **Team size:** 5 members
- **Assigned topic:** ParaShot — Parasite Egg Detection and Case Logging App (Topic #44; topic open to 1 team, now assigned and locked — no swaps allowed as Moodle setup is complete)
- **Deliverable type:** This is a Final Year Project (FYP). Current focus is the **Mid-Semester Project Pitch**.



### Topic brief (verbatim intent)

ParaShot is an interactive application supporting laboratory screening for parasite eggs in microscope images. Users upload a microscopy photo, adjust a detection-confidence threshold, and trigger on-demand analysis that highlights detected eggs with bounding boxes and species labels. Each analysis becomes a case record in a personal history log, where users can review results, correct mislabelled detections, flag uncertain cases, and re-run analysis with updated settings — with corrections feeding back into a running accuracy summary. Records can be exported as case reports. Development covers a case-management database, a configurable detection pipeline, and an interface supporting upload, threshold control, manual correction, and reporting — spanning data handling, algorithm integration, and interactive system design rather than a single-shot prediction display.

- **Deliverable(s) stated in brief:** A working web/mobile app with image upload, detection overlay, and species labels.
- **Additional requirements:** None stated.

---



## 2. The Mid-Semester Pitch assessment — what's required

The pitch has **two strictly sequential parts**. Part 2 cannot start until Part 1 is signed off.

### Part 1 — Pitch draft sign-off + documentation (Grade: Satisfactory/Unsatisfactory)

- Handled by **your own team supervisor**, during/around Week 5.
- Requires at least **one completed group meeting + submission** before sign-off.
- **Sign-off gate = no sign-off means the later presentation is invalid and scores zero, even if delivered.**
- Slides must be **uploaded to Moodle under the sign-offs**, then ping the supervisor to sign off. Teams may keep updating slides until the actual presentation.

**Three focus areas the supervisor signs off on:**

1. **Project Scope** — feasible, sufficiently challenging, well outlined. Items reasonably assumed in-scope but excluded must be explicitly identified with rationale.
2. **Weighted Scoring Model (WSM)** — project compared against a variety of other options using a WSM.
3. **Project Goals** — clearly and simply stated as a bullet list.



### Part 2 — Pitch presentation (Grade: 0–100%)

- Live presentation + Q&A in a later studio session (scheduling TBA in a separate post).
- **Time limit:** 5 members = **14 minutes** (3–4 members = 12 min). Q&A is separate; TAs stop the clock during Q&A.
- **Time penalty:** 5% points off *each* team member's mark for *every minute* over the limit.

---



## 3. Supervisor-specified slide flow (MUM-adjusted)

The team supervisor overrode the generic worksheet flow with this **9-slide structure** (adjust as needed per topic):

1. **Introduction slide**
2. **Problem statement / Opportunity statement** — what the project solves or the opportunity it explores
3. **Project overview** — general summary of what the project does, in reference to (2)
4. **Analysis of Option and Recommendation** — implement WSM and show at least one example to decide on project direction
5. **Preliminary project requirements / objectives** — extracted from supervisor, decided upon, planned to use
6. **Project goals (SMART) / deliverables** — the final output at the very end of the project (after Part 2)
7. **Project limitations / scope** — scope = what you set to achieve (in-scope/achievable vs out-of-scope/not achievable); limitations = restrictions/constraints often outside your control; these may overlap
8. **Schedule estimate / timeline**
9. **Conclusions** — what is still pending, needs further investigation or elaboration

> Note: the original worksheet's business-case-heavy flow (Introduction/Background, Business Objective, Current Situation, Critical Assumptions & Constraints, Analysis of Option & Recommendation, Preliminary Requirements, Schedule Estimate) is *informative* but the supervisor's 9-slide flow above takes precedence for MUM.

---



## 4. Marking rubric summary (Part 2 — the graded pitch)

Each criterion is marked /10 then scaled to its weight. General bands: HD 8–10, D 7–7.9, C 6–6.9, P 5–5.9, N 0–4.9. **Note: meeting all requirements without weakness is NOT enough for HD — HD needs substantial depth/quality beyond expectations.**


| Criterion                       | Type       | Weight |
| ------------------------------- | ---------- | ------ |
| Presentation fluency            | Individual | 20     |
| Content and contribution        | Individual | 20     |
| Response to questions           | Individual | 5      |
| Professional conduct            | Individual | 5      |
| Pitch content                   | Team       | 30     |
| Visual communication            | Team       | 5      |
| Presentation structure and flow | Team       | 15     |




### Key rubric implications to design for

- **Fluency (20%, individual):** Reading text word-for-word fails fluency. No phones/tablets/laptops for speaking notes (phone OK for timekeeping only) or the individual fluency mark is capped. Printed/handwritten notes or discreet cards are allowed. Looking at the audience-visible slides on a lectern/room screen is fine. Rubric also scores pace, voice, non-verbal communication, and audience engagement — not only notes.
- **Content & contribution (20%, individual):** Depth of project-specific understanding, clearly connected to the wider project. Familiarity with own material.
- **Response to questions (5%, individual):** Staff aim to ask each member ≥1 question. If not asked (time), you get the team average. Justify decisions with project-specific evidence, trade-offs, and acknowledge limitations. **A question may be directed to one member; others may supplement only after that member has answered.** Polished/confident delivery alone is not HD.
- **Professional conduct (5%, individual):** Respectful, attentive, constructive; don't interrupt/dominate/undermine. **Merely avoiding bad behaviour is not HD** — HD needs mature judgement that actively helps the room.
- **Pitch content (30%, team):** Comprehensive, project-specific coverage of business problem/opportunity, objectives, users/stakeholders, assumptions, constraints, requirements, SMART goals, feasible scope, option analysis, planning, and **supporting research/evidence** — connected into a coherent, persuasive case. There is **no separate “references” criterion**. Citations are how you show that evidence on slides 2 and 6 and in Q&A.
- **Visual communication (5%, team):** Readable, organised, consistent, purposeful visuals.
- **Structure & flow (15%, team):** Strong opening + conclusion, seamless speaker transitions, time management, unified team coordination.
- **Presenter name** must appear (as on Allocate+) on every slide that presenter speaks to.



### GenAI policy for the pitch

GenAI is permitted for producing **visual materials** (mock-ups, look-and-feel, brainstorming interfaces). BUT every student will be asked to explain and justify their material in detail and is graded on understanding. GenAI must not come at the expense of understanding, reasoning, or communication.

---



## 5. Content drafted so far



### 5.1 Project Scope

**In scope — core features**

- Image upload (microscopy photos)
- Confidence threshold control (adjustable detection sensitivity)
- On-demand detection (user-triggered, not automatic)
- Detection overlay (bounding boxes + species labels + confidence scores)
- Case record creation (each analysis → case in personal history log)
- Review and correction (correct mislabelled detections, flag uncertain cases)
- Re-run analysis (with updated settings; corrections feed a running accuracy summary)
- Case report export (downloadable per record)

**In scope — system components**

- Case-management database (case records, corrections, flags, accuracy metrics)
- Configurable detection pipeline (model integration + adjustable threshold)
- Frontend interface (upload, threshold, overlay, correction, history log, export)
- Running accuracy summary (tracks how corrections affect performance over time)

**In scope — non-functional**

- Clear, usable interface for lab users (not just developers)
- Responsive design (web and/or mobile — CONFIRM with supervisor)
- Reasonable single-image detection response time

**Out of scope (unless supervisor says otherwise) — with rationale**

- Training a model from scratch → prohibitively data/compute-heavy for one semester; fine-tune or integrate a pre-trained model instead
- Real-time video or simultaneous batch processing → adds complexity beyond core value of single-image screening
- Integration with external lab systems (LIS/LIMS) → out of team control, no access to real lab infrastructure
- User authentication / multi-user access control → CONFIRM; may be simplified to single-user if not required
- Automated diagnosis / clinical decision-making → this is a screening *support* tool, not a diagnostic device; clinical validation is out of scope

**Limitations / constraints (largely out of team control)**

- Model accuracy limited by availability/quality of labelled training data
- Detection speed constrained without guaranteed GPU access
- One-semester timeline, 5 student developers, varying availability/skills
- Prototype/proof-of-concept, not production/clinical-grade



### 5.2 Weighted Scoring Model (WSM)

**Framing:** Because the topic was assigned from a list, present the WSM as the team evaluating candidate topic options before committing to ParaShot. **The scores below are an EXAMPLE — the team must replace them with their own reasoning, since they will be asked to justify every number in Q&A.**


| Criteria                                      | Weight   | ParaShot | Alt 2 (e.g. generic CRUD app) | Alt 3 (e.g. data dashboard tool) |
| --------------------------------------------- | -------- | -------- | ----------------------------- | -------------------------------- |
| Technical challenge / learning value          | 25%      | 90       | 50                            | 65                               |
| Feasibility within semester                   | 20%      | 75       | 90                            | 80                               |
| Real-world impact / usefulness                | 20%      | 90       | 55                            | 70                               |
| Team skill fit (ML, web, DB)                  | 15%      | 80       | 70                            | 75                               |
| Data / resource availability                  | 10%      | 65       | 85                            | 70                               |
| Scope for individual contribution (5 members) | 10%      | 85       | 60                            | 70                               |
| **Weighted total**                            | **100%** | **82.5** | **65.0**                      | **71.5**                         |


- Weighted total = Σ(weight × score).
- Narrative: ParaShot wins on challenge, impact, and giving 5 members separable meaningful work; honest trade-off is its lower data-availability score.
- **TODO:** replace Alt 2 / Alt 3 with the actual alternative topics the team considered, and re-derive scores as a team.



### 5.3 Project Goals (SMART)

- **G1:** Build a working web app that detects parasite eggs in uploaded microscopy images and displays bounding boxes with species labels, achieving a defined baseline detection accuracy (e.g. ≥70% precision or F1 on a held-out test set) by end of semester.
  - *Why 70% is SMART, not random:* Published detectors on Kato-Katz images report much higher in-distribution scores (Ward et al., 2022: weighted precision 94.9% / recall 96.1%; Oyibo et al., 2025: weighted precision 95.9% / F-score 94.0%). A ≥70% FYP baseline is **conservative and achievable** with a pretrained/fine-tuned model and a small test set. We are not claiming clinical SOTA. Mohammed et al. (2025) also show performance can drop out-of-distribution (different camera, unseen species) — so a modest target plus human correction (G3) is the honest FYP design.
- **G2:** Implement a case-management system that stores each analysis as a reviewable case record with a personal history log, supporting create, view, and export of individual case reports.
  - *Why this goal:* Manual microscopy is typically a one-shot readout with no structured record of what was seen or corrected (the gap in §5.4). Field AI-pathology prototypes explicitly pair detection with **verification and reporting**, not boxes alone (Ward et al., 2022). ParaShot is the student-scale version: one image → one case → export.
- **G3:** Provide an interactive correction workflow allowing users to adjust the confidence threshold, correct mislabelled detections, and re-run analysis, with corrections updating a running accuracy summary.
  - *Why this goal:* Kato-Katz results depend on reader skill and experience, and microscopy expertise is increasingly scarce (Keller et al., 2020). Automated systems are intended to **support** trained readers and reduce human-induced error, not replace them (Mohammed et al., 2025). Correction + accuracy summary is how we keep a human in the loop and measure disagreement.
- **G4:** Deliver a usable, responsive interface tested with ≥3 representative user scenarios (upload → detect → review → correct → export) before end of project.
  - *Why this goal:* The topic is an interactive system, not a single-shot display. If users cannot complete the loop, G1–G3 never leave a notebook demo.

Each is Specific, Measurable, Achievable, Relevant, Time-bound. Put **2–3 citations on slide 6** (G1–G3); do not read DOIs aloud.

### 5.3b Background research (use on slides 2 and 6)

**What the rubric actually says.** Pitch content (30%) asks for *supporting research/evidence* next to the business problem, goals, and planning. Q&A (5%) asks you to justify decisions with project-specific evidence. There is no extra mark for a bibliography — but unjustified claims sit at Pass/Credit.

**Problem (slide 2) — claims → sources**

| Claim on the slide | Source (say in Q&A) |
|---|---|
| Egg ID is still done by microscopy; WHO still treats Kato-Katz as the programmatic standard for soil-transmitted helminths | Stuyver & Levecke (2021) |
| Reading the slide is slow and needs scarce expertise; results vary with the reader | Mohammed et al. (2025) — slide exam ≈ 80% of time-to-result, needs expertise; Keller et al. (2020) — readings depend on skill; expertise increasingly rare |
| Opportunity: detectors can draft boxes + species labels, with a human still checking | Ward et al. (2022); Oyibo et al. (2025) |
| We are not a diagnostic device | Same papers frame AI as *support* for screening/control programmes, plus our out-of-scope clinical validation |

**References (copy onto a tiny slide-6 footer or backup slide)**

1. Keller, L., Patel, C., Welsche, S., Schindler, T., Hürlimann, E., & Keiser, J. (2020). Performance of the Kato-Katz method and real time polymerase chain reaction for the diagnosis of soil-transmitted helminthiasis… *Parasites & Vectors*. https://doi.org/10.1186/s13071-020-04401-x
2. Stuyver, L. J., & Levecke, B. (2021). The role of diagnostic technologies to measure progress toward WHO 2030 targets for soil-transmitted helminth control programs. *PLOS Neglected Tropical Diseases, 15*(6), e0009422. https://doi.org/10.1371/journal.pntd.0009422
3. Ward, P., Dahlberg, P., Lagatie, O., Larsson, J., Tynong, A., Vlaminck, J., … Stuyver, L. J. (2022). Affordable artificial intelligence-based digital pathology… Kato-Katz stool thick smears. *PLOS Neglected Tropical Diseases, 16*(6), e0010500. https://doi.org/10.1371/journal.pntd.0010500
4. Mohammed, M. A., Anzaku, E. T., Ward, P. K., Levecke, B., Krishnamoorthy, J., De Neve, W., et al. (2025). Detecting soil-transmitted helminth and *Schistosoma mansoni* eggs… YOLOv7 variants. *PLOS Neglected Tropical Diseases, 19*(7), e0013234. https://doi.org/10.1371/journal.pntd.0013234
5. Oyibo, P., Meulah, B., Oyibo, W., Diehl, J.-C., Agbana, T., van Lieshout, L., & Vdovin, G. (2025). Deep learning-based automated detection and multiclass classification of soil-transmitted helminths and *Schistosoma mansoni* eggs in fecal smear images. *Scientific Reports*. https://doi.org/10.1038/s41598-025-02755-9

**Honest limits (say if asked).** These papers are about Kato-Katz / STH control programmes, often in endemic settings. ParaShot is an FYP screening-support prototype (one uploaded photo, not a field whole-slide scanner). Cite them for *why the problem exists* and *why detect+correct is plausible*, not as proof that we will hit 95% in a Malaysian teaching lab.

### 5.4 Problem / Opportunity statement (slide 2)

**Problem.** Identifying parasite eggs in microscope images is still done largely by eye. A reader must both *find* eggs on a cluttered slide and *name* the species from shape. WHO still treats Kato-Katz microscopy as the programmatic standard for soil-transmitted helminths (Stuyver & Levecke, 2021). That work depends on scarce skill, slows as volume or fatigue rises, and readings vary with the reader (Keller et al., 2020; Mohammed et al., 2025). Each screen is usually a one-shot judgement — nothing structured is kept about what was seen, missed, or corrected.

**Opportunity.** Object-detection models can already draft boxes and species labels on Kato-Katz images at high in-distribution accuracy (Ward et al., 2022; Oyibo et al., 2025), but published systems still pair AI with **human verification**, not fully automatic diagnosis. ParaShot explores that human-in-the-loop alternative at FYP scale: upload one microscopy photo, run detection on demand, set a single confidence threshold, and get proposed bounding boxes plus species labels. The user can correct mistakes. Each analysis is saved as a **case** in a personal history log, so the image becomes a reviewable record rather than a discarded glance.

**Positioning.** This is screening *support* — a draft for a human to confirm — not a diagnostic device and not a replacement for a trained reader.

**Slide bullets (3–5, for sign-off):**
- By eye today: find eggs *and* name the species; scarce skill; slower with volume and fatigue (Keller et al., 2020; Mohammed et al., 2025)
- No saved record — each screen is a one-shot judgement
- Opportunity: on-demand detect → proposed species label → human corrects → case log (Ward et al., 2022)
- One photo = one case (not a one-shot demo that disappears)
- Screening support, not diagnosis

**Spoken (~45s):**
“Egg ID on microscope images is still mostly done by eye. You have to find the eggs and name the species from shape. The literature on Kato-Katz screening is clear that this needs scarce skill and that reading the slide is the slow, expert step. We’re exploring a human-in-the-loop alternative: upload one photo, run detection on demand, set a confidence threshold, get boxes and species labels, correct mistakes, and save that as a case. Support for screening — not a diagnostic device.”

Keep flags, re-run, accuracy summary, and export off this slide — they belong on slide 3.

### 5.4b Business case (informative, per original worksheet — maps into supervisor slides 2–5)

- **Introduction / Background:** Manual microscopy screening for parasite eggs is slow, expertise-dependent, and prone to inconsistency and fatigue-based error; labs face high sample volumes with limited specialist staff.
- **Business Objective:** Assist screening readers by drafting egg detection and species labels — speeding the first pass while keeping a human in the loop for correction and final judgement.
- **Current Situation & Problem/Opportunity:** See **§5.4** (slide 2 draft).
- **Critical Assumptions & Constraints:** Assumes a labelled dataset or fine-tunable pre-trained model exists; prototype (non-clinical) scope. Constrained by one semester, 5 developers, no guaranteed GPU, no clinical validation.
- **Analysis of Options & Recommendation:** Summarise WSM; recommend ParaShot as maximising learning value + impact while feasible.
- **Preliminary Requirements:** upload, configurable detection pipeline, detection overlay, case DB, correction/re-run, accuracy summary, report export, responsive UI.
- **Schedule Estimate (high-level phases):** Requirements & design (Wk 1–5) → Core detection + upload (Wk 6–9) → Case management + correction (Wk 9–11) → Reporting + polish + testing (Wk 11–13). Present as a simple Gantt.



### 5.5 Users / stakeholders (slide 3b)

**Working default for the pitch** (team can still swap “lab tech” vs “trainee” as the operator — do not list both as equal primaries).

**Primary user (operator):** a **screening reader** — lab technician or trainee — who looks at a microscopy photo of a parasite-egg slide. Job: find eggs, name the species, keep a record. They upload, set the threshold, run detection, correct/flag, re-run, save the case, export.

**Secondary users / stakeholders (they care; they are not at the slider):**
- Lab supervisor / lecturer — quality of screening, corrections, exported reports, accuracy summary
- Project supervisor + unit — academic FYP stakeholders (scope, deliverable, marks)
- **Not users:** patients and clinical decision-makers — screening *support*, not diagnosis

**On-slide (3–5 bullets):**
- Operator: screening reader (tech or trainee) — upload → detect → correct → log
- Stakeholder: supervisor/lecturer — history, reports, accuracy
- Academic stakeholders: FYP supervisor and unit
- Not in scope: patient / diagnostic user

**Spoken (~30s):**
“The person using the app is whoever is reading the slide. They get a draft of *where* the eggs are and *what species they look like*, then they confirm. A supervisor might open the history or an exported report. We are not building a tool for the patient or for an official diagnosis.”



### 5.6 Core user workflow (simple)

`Upload → Set Threshold → Run Detection → Review Results → Correct if needed → Re-run if needed → Save as Case → Export Report`

Running in the background throughout: the **accuracy summary** updates whenever corrections are made.

Step-by-step:

1. Upload a microscopy image
2. Set confidence threshold
3. Run detection (on-demand)
4. View results (bounding boxes + species labels)
5. Review & correct (fix wrong labels, flag uncertain)
6. Re-run optionally with updated settings; corrections feed accuracy summary
7. Save as case record in personal history log
8. Export case as downloadable report



### 5.7 Proposed work breakdown (5 members)

Functional slices for role assignment (individual or pairs on harder pieces):

- Case-management database (schema, CRUD)
- Detection pipeline (model integration, configurable threshold) — harder
- Upload & threshold UI (web/mobile frontend)
- Correction & history log (manual correction, re-run, accuracy tracking)
- Reporting / export (case report generation)
- Integration & system architecture — harder



### 5.8 Proposed speaker split (14 min, ~2.5–3 min each)


| Slide(s) | Content                                                   | Presenter                   |
| -------- | --------------------------------------------------------- | --------------------------- |
| 1        | Title (project title, group #, topic, all names + IDs)    | —                           |
| 2        | Introduction + Problem/Opportunity                        | Member 1                    |
| 3        | Project overview (a) + users/stakeholders (b)             | Member 1 → Member 2         |
| 4        | Analysis of Option & Recommendation (WSM)                 | Member 2                    |
| 5        | Preliminary requirements / objectives                     | Member 3                    |
| 6        | Project goals (SMART) / deliverables + research citations | Member 4                    |
| 7        | Project limitations / scope (in/out + rationale)          | Member 5                    |
| 8        | Schedule estimate / timeline                              | Member 5                    |
| 9        | Conclusions (pending items, next steps)                   | Member 3 → Member 1 (recap) |


Adjust to balance time evenly and match each member's owned work area.

---



## 6. Questions to ask the supervisor (still open / to confirm)

**Detection model & data**

- Train our own model or use/fine-tune a pre-trained one (e.g. YOLOv8)?
- Specific dataset provided, or source our own microscopy images?
- Which parasite species must be supported — minimum set or team-defined?
- Reasonable baseline accuracy target at this stage?

**Scope & deliverable**

- Web AND mobile, or is one sufficient?
- Preferred case report export format (PDF / CSV / structured report)?
- Personal history log per-user with auth, or session-based acceptable?
- Priority of re-run/correction loop vs core detection?

**Technical constraints**

- Preferred/required tech stack (Python/Flask, React, specific DB)?
- Detection in-browser or on backend server?
- Performance expectation for single-image analysis?

**PM & expectations**

- What does a successful MVP look like this semester vs Part 2?
- Check-in cadence outside team meetings?
- Milestones/deadlines beyond the meeting recordings?

---



## 7. Outstanding TODOs for the next agent / team

- [ ] **Users / stakeholders:** §5.5 is now a slide-ready default (screening reader + supervisor). Team still lock operator = lab tech vs trainee before the deck is final.
- [ ] Confirm the open supervisor questions in Section 6 (especially web-vs-mobile, dataset, species set, tech stack) — several scope decisions depend on these.
- [ ] Replace WSM example alternatives + scores with the team's real considered options and agreed reasoning.
- [x] Add cited background research to justify SMART goals and problem statement — see **§5.3b** (five papers). Still put 2–3 of them on slides 2/6; do not overclaim we are a field diagnostic device.
- [ ] Fill in real team member names + IDs (as per Allocate+) and finalise the speaker split; map §5.7 work slices to named presenters.
- [ ] Build the actual 9-slide draft deck once content is locked (put presenter name on every slide they speak to; add 3–5 plain-text bullets per content slide for the draft sign-off requirement).
- [ ] Upload draft deck to Moodle under sign-offs and ping supervisor for sign-off BEFORE the presentation session.
- [ ] Rehearse to hit 14 min total (time penalty is severe and hits every member).
- [ ] Ensure at least one group meeting + submission is completed before sign-off (prerequisite).

---



## 8. Source documents referenced

- Group Project Meeting Minutes & Videos — assessment details + marking guide (V10082026)
- Mid-Semester Project Pitch — Individual and Group Sign-off, Group Presentation (v10082026 / v12082026)
- Mid-Semester Project Pitch marking rubric (v17082026)
- Meeting minutes template (fit316x-meeting-minutes-template.docx)
- ParaShot topic brief (topic #44, image)
- Supervisor's Week 4 Moodle post specifying the 9-slide flow and sign-off process

