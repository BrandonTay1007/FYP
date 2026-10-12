# ParaShot Final Proposal Presentation: Content Working File

Status as of 12 Oct 2026. Follows the MUM teaching-team clarification (`teaching_team_clarification.md`) ONLY. The generic Monash spec PDF is not used.

Legend: **AGREED** = confirmed by user/team/supervisor. **PROPOSED** = agent suggestion, not yet decided. **OPEN** = needs a decision.

---

## 0. Logistics and rules

- Team PCS-33, topic 44 ParaShot. Members (Allocate+ names): Tay Wei Yong (Brandon) 34601066, Liew Yu Hong 34476148, Siow Yee Yang (Victor) 34600701, Hong Zhi Hong 34474994, Kam Joshua 35832312.
- Slot: Tuesday 20 Oct 2026, 1500-1800 session, ALC6316. Fourth of six: PCS22, PDS02, PCS34, PCS33, PCS06, PCS39. Whole team stays for the whole session (individual critiques).
- Time: 14 minutes for 5 members. Q&A not counted. Penalty 5% per minute over for every member. Tutors stopped teams at 1 minute over in mid-sem.
- Presenter name (as on Allocate+) on every slide they speak to.
- Delivery: no phone or laptop for notes (fluency mark capped). Printed or handwritten notes allowed discreetly. Reading word for word fails fluency.
- Submission: slides uploaded to Moodle before the slot. Re-upload allowed any number of times; latest overwrites. Supervisor sign-off not enforced on Moodle; supervisor does nothing on Moodle. Still get supervisor to check content informally. Errors are the team's responsibility.
- Internal deadlines (Meeting 4, 9 Oct): core slide content Mon 12 Oct (Tue if needed). Online practice, then one 2-3 hour physical practice on campus. Brandon books room.
- Supervisor availability: Week 12 wrap-up Thu 4:00-4:30pm online. Away 25 Oct to 7 Nov. No Fridays.
- Proposal report (separate assessment): due Mon 2 Nov 2026 11:55pm, 3500 words, edit-logged Google Doc, authorship statement or -50%.



## 1. Teaching-team rulings (Ed, Soo Wooi King, 29 Sep to 12 Oct)

- Content follows the nine-item MUM flow. Not all items must be present.
- Project plan: Gantt OR RTM, whichever is easier to explain. Gantt preferred, fits one slide. WBS optional. Unchanged Gantt can be repeated and stated as such.
- Requirements: staff do not want an RTM. Show the finalised requirements you will fulfil, not how they were compared or ranked.
- WSM: not re-presented. Decisions should be final by now.
- Critical assumptions and constraints: not needed, unless one explains a particular limitation.
- PM or software development methodology: not needed this semester (returns in Part 2). If shown, goes early, not in conclusion.
- Scope/limitations: basically the mid-sem content, corrected or updated.
- Design: UI wireframe is the mandatory minimum for all teams. Low fidelity only; high fidelity should not exist at proposal stage. Wireframe is a generic template for the whole interface. Describe rather than annotate unless very basic. Other diagrams (UML, sequence, architecture) optional. Figma not needed. Tools with watermarks not penalised. A coded website is NOT accepted in place of a wireframe.
- Frameworks/architecture: may name a few proposed ones, no deep detail.
- Roles mapping to members: optional.
- Changes since mid-sem: may be highlighted to save time.
- Mid-sem reference (12 Oct): optional. This pitch is a follow-up, so you may point back, but the panel may not remember what was said. Anything the rubric scores has to be restated on the slide.
- Risk: all risks the project could encounter, internal or external (#293, 9 Oct). On the slide, name the top 3 and say they are the top 3 of the full set (11 Oct). Impact and mitigation are still the required shape; staff did not add a third topic. Risk register optional. Simple high/medium/low scoring is fine; no formal probability maths.
- Conclusion: reflection on progress thus far, teamwork and PM.
- SMART goals (11 Oct): optional. "Depends on how you view them and how you want to present them." Not required and not forbidden.



## 2. Supervisor rulings (Dr Sicily)

Kickoff 31 Aug: Chula-ParasiteEgg-11 primary (11 species), AI-KFM comparison only. Train YOLOv8-v12 or Faster R-CNN. Motivation is Orang Asli One Health collaboration (Dr Azdayanti, Assoc. Prof. Ogawa). Do not claim host-origin (human vs animal) classification. Screening support, not diagnosis.

27 Aug consultation (Notion): three-tier users recommended: lab manager (super user), senior lab scientist, junior. Juniors upload and screen, seniors validate.

Meeting 3 feedback (17 Sep): build detection pipeline first (highest risk). Basic authentication with case ownership. Produce an architecture plan before implementation.

Early Oct meeting (Notion "Supervisor questions", user-confirmed):

- One species per image acceptable. Multi-species per image is stretch.
- 70% target looks weak; a benchmark on the dataset reportedly ~97%. Compare F1 across papers and Kaggle, not accuracy alone.
- Support multiple formats (PNG, TIFF). Backend converts and resizes. Test for data loss.
- Batch upload of hundreds of field-trip images is an important real use case. Investigate storage and processing.
- Report generation is the most impactful feature: species and egg counts across a batch.
- Two roles: junior uploads and views, senior corrects and labels.
- Five-member team should deliver a feature-rich, production-like app.
- CPU fine for single image, GPU better for batch. Colab for training. Ensemble valid but costly.
- Risks must be realistic with mitigations (client miscommunication, scope change, methodology change). Justified changes not penalised.

Meeting 4 team decisions (9 Oct): single-image detection baseline, multi-species stretch. (12 Oct research note: detectors output a class per box, so multi-species is already produced; the real stretch is a separately validated mixed-image accuracy figure. See 5.4 FR3 and 5.5 wording.) Web app first, mobile only if early. Standardise to one image format, resize required. Colab for now, compare Hugging Face by 22 Oct. Research storage and propose a minimum batch baseline by 22 Oct. Per-feature checklist before implementation.

User confirmations 11 Oct: batch upload and junior/senior roles are IN scope. No model results yet (cite papers). No tech stack chosen. RTM not signed off (no MUM RTM sign-off exists).

12 Oct model research (PROPOSED, `model_selection_research.md`): YOLO26 small as the deployable detector; RF-DETR Small as the CNN-vs-transformer comparison (domain-transfer evidence). YOLO11 only if RF-DETR is too slow on Colab. Confirm YOLO26 with supervisor (kickoff named v8–v12).

## 3. Mid-sem lessons to fix

Team marks: Pitch content D, Visual communication D, Presentation structure and flow D.

- Slide text too small, slides too wordy.
- Exceeded time by a bit.
- Non-presenters moved around and distracted.
- Dress appropriately.
- Wrong handover between speakers; needed more practice.

Pitch feedback: deployment overlapped integration testing with no buffer. Fix in Gantt.

Mid-sem presenters: Yu Hong intro and problem; Wei Yong overview, users, conclusion; Yee Yang requirements and WSM; Zhi Hong SMART goals; Joshua scope, limits, schedule.
Mid-sem deck facts: WSM compared models, YOLO chosen; FR1-FR9 plus NFR >=70% mAP; 3 SMART goals (G1 detection >=70% mAP by Sem1 Wk10; G2 correction and accuracy Sem2 Wk8; G3 case dashboard Sem2 Wk6); open items were YOLO version benchmark, web vs mobile, RBAC gap.

## 4. Section ownership (Meeting 4, AGREED)

Each member updates their own mid-sem section. New: plan and scope = Brandon + Joshua. Design and wireframes = Yu Hong + Zhi Hong. Risk = Victor. Final speaker split: OPEN.

Dev roles: Zhi Hong + Joshua full-stack and test. Yu Hong + Victor AI engineers. Brandon product manager plus development support.

---



## 5. Content by MUM section

Target timing (PROPOSED): roughly 14 min = intro 0:45, problem/overview 1:30, users 1:00, requirements 2:30, scope 1:00, plan 1:15, design 2:00, risk 1:00, conclusion 1:00, buffer 2:00.

### 5.1 Intro material (as per mid-sem pitch)

- Title slide: project name, PCS-33, topic 44, five names and IDs.
- Team introduction slide reused from mid-sem (Meeting 2 fix: give context before diving in).
- One sentence: ParaShot turns a microscope photo into a reviewed, exportable case.
- Do not assume the panel remembers the mid-sem deck (staff, 12 Oct). A one-line "what changed" is enough acknowledgement. Requirements, plan, wireframes and risks still have to stand on their own.



### 5.2 Problem/Opportunity leading to overview and deliverables (WHY it exists, WHAT it solves)

AGREED basis (mid-sem merged statement): identification by eye, scarce expertise, reader variability, no traceable record. Citations: Capuozzo et al. 2024, Keller et al. 2020, Mohammed et al. 2025, Stuyver and Levecke 2021.
PROPOSED additions:

- Field reality: a field trip returns hundreds of images; the expert is the review bottleneck.
- What it solves: drafts boxes and species so the expert reviews rather than searches; every image becomes a case; a batch gets one report.
- Overview workflow: upload batch -> standardise images -> detect (box, species and confidence for every egg) -> senior review and correct -> save cases -> batch report.
- Deliverables: web app, trained detector on Chula-ParasiteEgg-11, case database, batch report.
- OPEN: include a short "changed since mid-sem" panel (batch, roles, report as headline)? Own slide or panel.
- Positioning clause: screening support, not diagnosis, not host-origin classification.



### 5.3 Target end users (WHO will use it)

AGREED (supervisor Oct): junior uploads and views; senior corrects, labels, flags, approves, exports.
Stakeholders not at the keyboard: Dr Azdayanti (UiT parasitology), Assoc. Prof. Ogawa (JCSMHS), Dr Sicily (supervisor). Not users: patients, communities, clinicians making diagnoses.
PARKED: manager tier / organisation model (see section 7 below).

### 5.4 Project Requirements/Goals (WHAT it is expected to do, finalised for now)

Rule: finalised list only. No ranking, RTM or WSM. Must be substantial enough to need all five members, so include an owner column (PROPOSED).

Draft functional requirements (PROPOSED, owners follow Meeting 4 roles):


| ID  | Requirement                                                                  | Owner                         | vs mid-sem                     |
| --- | ---------------------------------------------------------------------------- | ----------------------------- | ------------------------------ |
| FR1 | Upload one or many microscopy images (PNG, TIFF, JPEG) up to a batch cap     | Full-stack (Zhi Hong, Joshua) | Changed: batch added           |
| FR2 | Convert and resize uploads to one standard format, verified for no data loss | Full-stack + Brandon          | New (supervisor)               |
| FR3 | Detect every egg in the image: bounding box, species label and confidence per egg | AI (Yu Hong, Victor)          | Reworded: per-egg species (detectors are per-box multi-class by nature); mixed-image accuracy not separately validated in Sem 1 |
| FR4 | Adjustable confidence threshold with re-run on the same image                | AI + Full-stack               | Unchanged                      |
| FR5 | Senior can relabel, delete a box, flag uncertain, add note                   | Full-stack                    | Unchanged, now senior-only     |
| FR6 | Login with junior and senior roles; cases owned by uploader                  | Full-stack                    | New (supervisor)               |
| FR7 | Case history: every image is a case, grouped by batch                        | Full-stack + Brandon          | Changed: batch grouping        |
| FR8 | Batch report: species and egg counts across all images, exportable           | Brandon + Full-stack          | New, headline feature          |
| FR9 | Agreement summary: model vs senior corrections, per species                  | AI + Brandon                  | Changed: was accuracy summary  |


Draft non-functional (PROPOSED):

- NFR1 detection quality on a held-out Chula split, single model, no ensemble: mAP@0.5 >= 0.90 and F1 >= 0.90 (stretch 0.95), reported per class. The standard Chula test split already contains mixed-species images; a separately curated mixed-image subset is a stretch. Field-image performance is not this semester's target (Heliyon 2024: F1 0.88 → 0.53 out of domain).
- NFR2 batch processing within a stated time per image on CPU; GPU optional.
- NFR3 role security: juniors cannot change labels or access admin functions.
- NFR4 conversion lossless, or loss measured and reported.
- NFR5 a senior can review one image without training.

Goals: staff 11 Oct, optional. PROPOSED: one goals line on this slide (target and date), detail only in Q&A. No separate SMART slide.

Deliberately left out (OPEN to re-add): lowest-confidence-first review queue (agent idea, not supervisor's); senior drawing boxes for missed eggs (never raised with supervisor); manager tier (parked).

OPEN: batch cap number, or "to be set after storage research due 22 Oct".

### 5.5 Project Limitations/Scope (WHAT it is not capable of doing)

Staff: mid-sem content corrected and updated. Keep in-scope brief; spend words on changes.
Not capable of (PROPOSED list): human vs animal origin; clinical diagnosis; mobile app; live video; lab information system integration.
Validated-scope line (PROPOSED wording): "Mixed-species images are detected, but their accuracy is not separately validated in Semester 1; a curated mixed-image evaluation subset is a stretch goal." Do NOT write "the model can only detect one species per image": every candidate detector predicts a class per box, and the Chula benchmark already includes mixed images. This wording still satisfies the supervisor's October ruling; confirm at the wrap-up.
Limitations outside control: trained on Chula faecal smears, not field soil/stool; Colab compute; no guaranteed collaborator images; batch storage limits unknown.
Assumption worth stating (only one): Chula images are representative enough to be useful on lab images.
If organisation model adopted thin: full multi-organisation support listed out of scope with rationale (single-lab deployment is the collaboration context).

### 5.6 Project Plan (HOW executed, WHEN delivered)

- Gantt only, two semesters, milestones marked. No WBS, no methodology, no testing slide.
- Fixes to state out loud: deployment has its own window instead of overlapping integration testing, with fallback if pipeline slips; model training moved from Sem 1 Week 10 to the semester break (AI engineers start then).
- Sequence stays risk-ordered: detection pipeline first.



### 5.7 Project design (UI wireframe minimum, plus other design if needed)

- Low-fidelity wireframes as a template: one layout shell, then login, batch upload, batch overview, single-image review with overlay and correction panel, case history, report preview.
- Walk as a story: junior uploads, senior reviews, report goes out.
- Additional: one architecture diagram (browser, API, inference service, case database, image storage). Candidate technologies named as "candidate, not committed": YOLO26 (deployable, CPU-friendly) and RF-DETR Small (transformer comparison).
- Optional: one pipeline diagram (upload -> convert and resize -> detect -> threshold -> store -> review -> report).
- If manager tier adopted: one admin screen.



### 5.8 Project risk analysis (WHAT may occur, HOW it affects progress, WHAT to do)

Staff (11 Oct): if the register is long, speak to the top 3 and say they are the top 3 of the full set. Columns stay: risk, effect on progress, avoid, recover. High/medium/low is enough.

Spoken slide (PROPOSED), introduced as the top 3:

1. Look-alike species pull per-class accuracy under target (Capillaria hardest; blurred Ascaris vs H. nana). Effect: the detection milestone and batch counts slip. Avoid: per-class metrics, mosaic augmentation. Recover: low-confidence boxes stay visible for the senior to correct.
2. Domain gap: a model that passes the Chula target can still fail on collaborator lab images. Effect: the tool does not help the actual user this year. Avoid: do not claim field performance in Semester 1. Recover: hold any collaborator images for a later check; senior review stays the control.
3. Scope growth from supervisor or collaborator requests (batch upload and roles already arrived after mid-sem). Effect: the five-person plan thins out. Avoid: per-feature checklist; stretch stays stretch. Recover: justified changes are logged, not hidden.

Held for Q&A, not spoken: Colab quota, conversion data loss, batch storage still unknown, team availability, supervisor away 25 Oct to 7 Nov, late AI/web integration, dependence on the two AI engineers.



### 5.9 Conclusion (teamwork and PM lessons; anticipated team and management issues, NOT project risks)

Teamwork, with evidence: mid-sem overtime and wrong handover -> committed to online plus 2-3 hour physical rehearsal; rotating chair and minute-taker keeps everyone active.
Project management, with evidence: deployment-overlap feedback -> Gantt revised; role poll replaced on-the-spot assignment; training slip replanned, not hidden; per-feature checklist adopted.
Anticipated issues: lower availability next semester; supervisor away during report writing; two parallel streams drifting without the shared checklist.

---



## 6. Open decisions

1. NFR1 accuracy target: PROPOSED mAP@0.5 >= 0.90 and F1 >= 0.90 (stretch 0.95). Awaiting team/supervisor.
2. Requirements: keep/cut/reword rows; review queue in or out; missed-egg box drawing in or out; batch cap.
3. Owners per requirement correct?
4. Goals line wording (target and date). Separate SMART slide is closed: staff left it optional, and 14 minutes does not fit one.
5. Section 2: one "what changed" line, not a replay. Scored points are restated (staff, 12 Oct: the panel may not remember mid-sem).
6. Final speaker split.
7. Organisation / manager tier: parked (section 7).
8. Multi-species wording (FR3, 5.5, spoken risk 1) applied 12 Oct per research; confirm with supervisor at wrap-up that "detected but not separately validated" is acceptable under the October ruling.
9. YOLO26 + RF-DETR Small as the two trained models: confirm YOLO26 with supervisor (kickoff list was v8 to v12).



## 7. Parked: organisation and manager tier

Source: 27 Aug supervisor consultation recommended three tiers (manager, senior, junior). Oct ruling named only two. A forked agent proposed an "organisation owns users and roles" model; a second view recommended the thin version only.
Thin version: one implicit organisation; manager only approves sign-ups and assigns junior or senior; one admin screen. Full multi-organisation listed out of scope.
Action if pursued: confirm manager tier with supervisor at Week 12 wrap-up before slides are final.
Status: PARKED by user on 12 Oct. Focus on main content first.

## 8. Sources

- Final Pitch / model_selection_research.md (YOLO26 + RF-DETR, NFR1 numbers)
- Final Pitch / teaching_team_clarification.md (the backbone)
- Final Pitch / Marking Rubric v260915 (weights: fluency 20, content 20, Q&A 5, conduct 5, pitch content 30, visual 5, structure 15; HD needs depth beyond meeting requirements)
- Ed export fit3161-fit3163-mum-s2-2026.csv and Final Pitch / ed_pitch_threads.md
- Mid_semester_pitch / teaching_team_team_feedback.md and general feedback
- Meeting Minutes / Meeting1-4 (treat details with care; confirm odd items)
- ParaShot_Pitch_Handover.md (Sep; superseded by Canva deck and Oct supervisor meeting where they conflict)
- Notion: FYP hub and "Supervisor questions" page (in trash, still readable)

