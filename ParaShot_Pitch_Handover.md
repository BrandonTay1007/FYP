# ParaShot — Mid-Semester Pitch Handover Document

> **Purpose of this file:** A complete context handover so another agent (or team member) can continue preparing the mid-semester project pitch deliverable without re-reading all the source PDFs. It captures the unit requirements, the assigned project, and the content drafted so far.
>
> **Working hub:** [ParaShot FYP — kickoff notes](https://app.notion.com/p/3cd3a300c24f81ff939bd03c12cf04ce) (31 Aug 2026). The previous FYP hub is in Notion trash; unarchive if you need the 9-slide pack. Keep this file as the long-form dump.

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

### Supervisor kickoff (Dr. Sicily, team workspace) — 31 Aug 2026

Treat this as **locked direction**, not a new topic. Scope is scalable; the FYP is still a student prototype, not Dr. Azdayanti’s field diagnostic.

**Scope (supervisor wording).** Detection pipeline (object detection for parasite eggs), confidence-threshold control, and a case-management system supporting manual correction, re-analysis, and export. Tasks may include integrating a detection model, designing the case-record schema, building correction UI, and wiring corrections into a running accuracy summary.

**Origin (who the work is for).** Research collaboration: Dr. Sicily (SOIT) × Assoc. Prof. Satoshi Ogawa (Jeffrey Cheah School of Medicine & Health Sciences) × Dr. Azdayanti (UiT; parasitologist, public health in Orang Asli communities). Dr. Azdayanti’s One Health work collects **soil and animal stool** from Orang Asli villages to study environmental/zoonotic transmission. **Key challenge she named:** many parasite eggs from humans and animals are **morphologically indistinguishable**, which limits diagnostic accuracy. They want AI/deep-learning image analysis to **enhance her diagnostic workflow**.

**FYP honesty rule (do not overclaim).** Public training data does **not** label host (human vs animal). Chula-ParasiteEgg-11 is 11 *species* of eggs in faecal smears; AI-KFM is cattle GINs. This semester we draft **where** eggs are and **which species they look like**, with a human correcting. We do **not** claim we will tell human-origin from animal-origin eggs. That collaboration problem is the *motivation* (slide 2); the *product* (slide 3) is the screening-support app on public data.

**Datasets (supervisor-named; search for more is allowed).**

1. **Chula-ParasiteEgg-11** — primary. 11-class parasite-egg microscopy set from the ICIP 2022 challenge. ~13,750 images; bounding-box labels; train ~1,000 images/class. IEEE Dataport DOI: [10.21227/vyh8-4h71](https://dx.doi.org/10.21227/vyh8-4h71). Classes: *Ascaris lumbricoides, Capillaria philippinensis, Enterobius vermicularis, Fasciolopsis buski, Hookworm egg, Hymenolepis diminuta, Hymenolepis nana, Opisthorchis viverrini, Paragonimus* spp., *Taenia* spp., *Trichuris trichiura*.
2. **AI-KFM 2022** — supplementary/comparison. Cattle faecal microscopy (GIN eggs; varying concentration/contamination). Kaggle; described in Capuozzo et al. (2024).

**Model (supervisor-named).** Train a standard object detector on Chula-ParasiteEgg-11 first (most established public set with a challenge): YOLOv8–v12 ([yolov12.com](https://yolov12.com/); [Ultralytics docs](https://docs.ultralytics.com/)) or Faster R-CNN.

**Papers they pointed at (add to §5.3b).**

1. Anantrasirichai, N., Chalidabhongse, T. H., Palasuwan, D., Naruenatthanaset, K., Kobchaisawat, T., Nunthanasup, N., Boonpeng, K., Ma, X., & Achim, A. (2022). ICIP 2022 challenge on parasitic egg detection and classification in microscopic images: Dataset, methods and results. *IEEE ICIP*. https://doi.org/10.1109/icip46576.2022.9897267 (arXiv: [2208.06063](https://arxiv.org/abs/2208.06063))
2. Capuozzo, S., Marrone, S., Gravina, M., Cringoli, G., Rinaldi, L., Maurelli, M. P., … Sansone, C. (2024). Automating parasite egg detection: insights from the first AI-KFM challenge. *Frontiers in Artificial Intelligence*. https://doi.org/10.3389/frai.2024.1325219

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

- **G1:** Build a working web app that detects parasite eggs in uploaded microscopy images and displays bounding boxes with species labels, achieving a defined baseline detection accuracy (e.g. ≥70% precision or F1 on a held-out **Chula-ParasiteEgg-11** test split) by end of semester.
  - *Why 70% is SMART, not random:* ICIP 2022 challenge methods on this same dataset are the right comparison class (Anantrasirichai et al., 2022). Kato-Katz detectors also report high in-distribution scores (Ward et al., 2022; Oyibo et al., 2025). A ≥70% FYP baseline is **conservative**. We are not claiming clinical SOTA, and we are not evaluating on Orang Asli field images unless those are provided.
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
| Opportunity: detectors can draft boxes + species labels, with a human still checking | Ward et al. (2022); Oyibo et al. (2025); Anantrasirichai et al. (2022) on Chula-ParasiteEgg-11 |
| Local collaboration motivation (Orang Asli One Health; human vs animal eggs look the same) | Supervisor kickoff 31 Aug 2026 (Dr. Sicily / Ogawa / Azdayanti) — **not** a labelled FYP task |
| What we actually train/compare on | Anantrasirichai et al. (2022) Chula-ParasiteEgg-11; Capuozzo et al. (2024) AI-KFM |
| We are not a diagnostic device | Same papers frame AI as *support* for screening/control programmes, plus our out-of-scope clinical validation |

**References (copy onto a tiny slide-6 footer or backup slide)**

1. Keller, L., Patel, C., Welsche, S., Schindler, T., Hürlimann, E., & Keiser, J. (2020). Performance of the Kato-Katz method and real time polymerase chain reaction for the diagnosis of soil-transmitted helminthiasis… *Parasites & Vectors*. https://doi.org/10.1186/s13071-020-04401-x
2. Stuyver, L. J., & Levecke, B. (2021). The role of diagnostic technologies to measure progress toward WHO 2030 targets for soil-transmitted helminth control programs. *PLOS Neglected Tropical Diseases, 15*(6), e0009422. https://doi.org/10.1371/journal.pntd.0009422
3. Ward, P., Dahlberg, P., Lagatie, O., Larsson, J., Tynong, A., Vlaminck, J., … Stuyver, L. J. (2022). Affordable artificial intelligence-based digital pathology… Kato-Katz stool thick smears. *PLOS Neglected Tropical Diseases, 16*(6), e0010500. https://doi.org/10.1371/journal.pntd.0010500
4. Mohammed, M. A., Anzaku, E. T., Ward, P. K., Levecke, B., Krishnamoorthy, J., De Neve, W., et al. (2025). Detecting soil-transmitted helminth and *Schistosoma mansoni* eggs… YOLOv7 variants. *PLOS Neglected Tropical Diseases, 19*(7), e0013234. https://doi.org/10.1371/journal.pntd.0013234
5. Oyibo, P., Meulah, B., Oyibo, W., Diehl, J.-C., Agbana, T., van Lieshout, L., & Vdovin, G. (2025). Deep learning-based automated detection and multiclass classification of soil-transmitted helminths and *Schistosoma mansoni* eggs in fecal smear images. *Scientific Reports*. https://doi.org/10.1038/s41598-025-02755-9
6. Anantrasirichai, N., Chalidabhongse, T. H., Palasuwan, D., et al. (2022). ICIP 2022 challenge on parasitic egg detection and classification… *IEEE ICIP*. https://doi.org/10.1109/icip46576.2022.9897267 — **Chula-ParasiteEgg-11** (supervisor-named primary dataset)
7. Capuozzo, S., Marrone, S., Gravina, M., et al. (2024). Automating parasite egg detection: insights from the first AI-KFM challenge. *Frontiers in AI*. https://doi.org/10.3389/frai.2024.1325219 — **AI-KFM** (supervisor-named supplementary set)

**Honest limits (say if asked).** Papers 1–5 are Kato-Katz / STH control programmes. Papers 6–7 are the datasets we will actually train/compare on. ParaShot is an FYP screening-support prototype (one uploaded photo, not a field scanner, not host-origin classification). Cite them for *why the problem exists*, *why detect+correct is plausible*, and *what data we use* — not as proof we will hit 95% on Orang Asli field samples.

### 5.4 Problem / Opportunity statement (slide 2)

**Problem.** Identifying parasite eggs in microscope images is still done largely by eye. A reader must both *find* eggs on a cluttered slide and *name* the species from shape. WHO still treats Kato-Katz microscopy as the programmatic standard for soil-transmitted helminths (Stuyver & Levecke, 2021). That work depends on scarce skill, slows as volume or fatigue rises, and readings vary with the reader (Keller et al., 2020; Mohammed et al., 2025). Each screen is usually a one-shot judgement — nothing structured is kept about what was seen, missed, or corrected.

**Local hook (supervisor, 31 Aug 2026 — use on slide 2, not as an FYP claim).** This topic sits in a SOIT × JCSMHS × UiT collaboration. Dr. Azdayanti’s One Health work in Orang Asli villages collects soil and animal stool; many human and animal eggs look the same under the microscope, which limits diagnostic accuracy. That is *why the collaboration wants an image-analysis tool*. It is **not** this semester’s labelled task.

**Opportunity.** Object-detection models can already draft boxes and species labels on Kato-Katz images at high in-distribution accuracy (Ward et al., 2022; Oyibo et al., 2025), but published systems still pair AI with **human verification**, not fully automatic diagnosis. ParaShot explores that human-in-the-loop alternative at FYP scale: upload one microscopy photo, run detection on demand, set a single confidence threshold, and get proposed bounding boxes plus species labels. The user can correct mistakes. Each analysis is saved as a **case** in a personal history log, so the image becomes a reviewable record rather than a discarded glance.

**Positioning.** This is screening *support* — a draft for a human to confirm — not a diagnostic device and not a replacement for a trained reader.

**Slide bullets (3–5, for sign-off):**
- By eye today: find eggs *and* name the species; scarce skill; slower with volume and fatigue (Keller et al., 2020; Mohammed et al., 2025)
- Local hook: Orang Asli One Health work — many human vs animal eggs look the same (collaboration motivation, not this semester’s label)
- No saved record — each screen is a one-shot judgement
- Opportunity: on-demand detect → proposed species label → human corrects → case log (Ward et al., 2022; Anantrasirichai et al., 2022)
- Screening support, not diagnosis; not host-origin classification

**Spoken (~45s):**
“Egg ID on microscope images is still mostly done by eye: find the eggs and name the species from shape. That is slow, skill-scarce, and usually leaves no record. This topic comes from a SOIT–JCSMHS–UiT collaboration: Dr. Azdayanti’s One Health work in Orang Asli villages, where many human and animal eggs look the same. We are not classifying host origin this semester. We are building screening support: upload one photo, draft boxes and species labels, a human checks, save it as a case — not a diagnostic device.”

Keep flags, re-run, accuracy summary, and export off this slide — they belong on slide 3.

### 5.4b Project overview (slide 3a) — what is needed

Supervisor definition: *a general summary of what the project does, in reference to slide 2.* The topic-card Overview paragraph is the source. Users/stakeholders are **3b** on the same slide (see §5.5).

**This slide is the product, not the pain.** Answer: upload a microscopy photo → on-demand detection → boxes + species labels → human check → saved **case**.

**Must cover (supervisor kickoff, 31 Aug 2026 — locked):**

- Detection pipeline (object detector for parasite eggs; train YOLO v8–v12 or Faster R-CNN on Chula-ParasiteEgg-11)
- One **confidence threshold** for the whole run
- **Correction** of wrong labels and **flag** uncertain detections
- Optional **re-run** of the *same* photo with a new threshold (same case)
- **Personal history log** (each analysis becomes a case)
- **Export** of a case report
- **Accuracy summary** from corrections (human vs model)

**Workflow on-slide:** `Upload → threshold → run → overlay → correct/flag → re-run if needed → save case → export`

**Positioning (one clause):** screening **support**, not diagnosis. Full out-of-scope stays on slide 7. **Do not claim** human-vs-animal / host-origin classification — public labels are species, not origin.

**On-slide bullets (3–5, for sign-off):**
- One photo in → boxes + species labels → human confirms → saved as a case
- One confidence threshold; on-demand detect (not live video)
- Correct / flag, optional re-run of the same photo, history log, export, accuracy summary
- Train YOLO (or Faster R-CNN) on Chula-ParasiteEgg-11; AI-KFM is comparison only
- Screening support, not a diagnostic device; not host-origin classification

**Spoken (~45s):**
“ParaShot is what we build for that problem. You upload one microscopy photo, set a confidence threshold, and run detection on demand. The model drafts boxes and species labels. You correct mistakes, flag uncertain ones, optionally re-run the same photo with a different threshold, and save that as a case you can export. Corrections feed a running accuracy summary. We train a standard detector on the public Chula-ParasiteEgg-11 set. Screening support — not diagnosis, and not telling human eggs from animal eggs.”

**Leave off this slide:**

| Belongs on | Leave off slide 3 |
|---|---|
| Slide 2 | Why the problem exists; Orang Asli / morphology hook; literature citations |
| Slide 4 | WSM / option analysis |
| Slide 5 | Requirements list (the overview is the product story; requirements are the contract) |
| Slide 6 | SMART goals, deliverables, research citations |
| Slide 7 | Full in/out of scope and limitations |

**Rubric hook.** Pitch content (30%) wants the **project definition** connected to the business case. Slide 3 is that definition. HD needs it project-specific — not a generic “AI image app.”

### 5.4c Business case (informative, per original worksheet — maps into supervisor slides 2–5)

- **Introduction / Background:** Manual microscopy screening for parasite eggs is slow, expertise-dependent, and prone to inconsistency and fatigue-based error; labs face high sample volumes with limited specialist staff.
- **Business Objective:** Assist screening readers by drafting egg detection and species labels — speeding the first pass while keeping a human in the loop for correction and final judgement.
- **Current Situation & Problem/Opportunity:** See **§5.4** (slide 2 draft).
- **Critical Assumptions & Constraints:** Assumes a labelled dataset or fine-tunable pre-trained model exists; prototype (non-clinical) scope. Constrained by one semester, 5 developers, no guaranteed GPU, no clinical validation.
- **Analysis of Options & Recommendation:** Summarise WSM; recommend ParaShot as maximising learning value + impact while feasible.
- **Preliminary Requirements:** upload, configurable detection pipeline, detection overlay, case DB, correction/re-run, accuracy summary, report export, responsive UI.
- **Schedule Estimate (high-level phases):** Requirements & design (Wk 1–5) → Core detection + upload (Wk 6–9) → Case management + correction (Wk 9–11) → Reporting + polish + testing (Wk 11–13). Present as a simple Gantt.



### 5.5 Users / stakeholders (slide 3b)

**Working default for the pitch** (operator = screening reader in an Azdayanti-lab-style workflow; still lock lab-tech vs trainee vs student-proxy wording).

**Primary user (operator):** a **screening reader** — in this collaboration, closest to Dr. Azdayanti’s lab team (or a student/tech running the same workflow). Job: find eggs, name the species, keep a record. They upload, set the threshold, run detection, correct/flag, re-run, save the case, export.

**Secondary users / stakeholders (they care; they are not at the slider):**
- Domain collaborators: Dr. Azdayanti (UiT / parasitology) and Assoc. Prof. Satoshi Ogawa (JCSMHS) — workflow quality, whether drafts are usable on their kind of images later
- Lab supervisor / lecturer — corrections, exported reports, accuracy summary
- Project supervisor (Dr. Sicily) + unit — academic FYP stakeholders (scope, deliverable, marks)
- **Not users:** patients, Orang Asli community members as app users, or clinical decision-makers — screening *support*, not diagnosis, not a field deployment this semester

**On-slide (3–5 bullets):**
- Operator: screening reader (Azdayanti-lab-style workflow) — upload → detect → correct → log
- Domain stakeholders: Dr. Azdayanti + Assoc. Prof. Ogawa
- Academic: Dr. Sicily and the unit
- Not in scope: patient / diagnostic / community-facing user

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



### 5.9 Conclusions (slide 9) — what the project still has to figure out

Close on **ParaShot**. Recap the locked product, then the open investigations that change the detector, the case loop, or the data we can honestly claim.

**Product, locked:** one microscopy photo → on-demand detector → boxes + species labels → human corrects/flags → optional re-run of the *same* photo → saved case → export. Train YOLO v8–v12 or Faster R-CNN on Chula-ParasiteEgg-11. AI-KFM is comparison only. Screening support, not a diagnostic device, not host-origin classification.

---

**Still open — detection pipeline**

| What we still need to investigate | Why it matters | Working default |
|---|---|---|
| Fine-tune a COCO-pretrained detector vs train from scratch | Compute, time, and whether we ever get a usable overlay | Fine-tune |
| Which detector: YOLOv8 vs later YOLO vs Faster R-CNN | Speed vs accuracy trade-off on microscopy; YOLO is the usual first try | Start YOLOv8 or v11; compare only if the first model is weak |
| All 11 Chula classes vs a smaller first set | Day-one overlay completeness vs a pipeline that actually trains | All 11 if training holds; otherwise a documented subset |
| Default confidence threshold, and whether it is remembered per case | The slider is the user’s main control; a bad default makes the first run look empty or noisy | Start ~0.25–0.5; store the value used on the case |
| Backend inference vs in-browser; CPU vs GPU; “reasonable” latency for one photo | A lab reader waiting on a laptop is a different system than a Colab notebook | Backend; CPU acceptable; target seconds-not-minutes per image |
| Input constraints (file type, resolution, one field-of-view vs a stitched slide) | Chula images are already cropped microscopy stills, not a whole-slide scanner | One uploaded still; common image types; no WSI / stitching |

**Still open — data and how we measure “good”**

| What we still need to investigate | Why it matters | Working default |
|---|---|---|
| Evaluation protocol on Chula (split, metric: mAP vs F1 vs precision/recall at the operating threshold) | We need a number we can defend; ICIP SOTA is the wrong bar | Held-out Chula test split; report F1 *and* that it is in-distribution |
| What “≥70%” actually means until we have a first training run | Placeholder, not a clinical target | Conservative bar on Chula; revise after the first val curve |
| What AI-KFM is *for* (cattle GIN eggs; different host, different classes) | Supervisor named it as supplementary/comparison — not a second product | Optional stress/comparison set; do not mix labels into the 11-class head |
| Search for further public sets (allowed) | More data may help, or may be the wrong magnification/stain | Chula first; add a set only if boxes + species labels exist |
| Any of Dr. Azdayanti’s soil / animal-stool images this year | Chula is faecal smears from a challenge. Her images are a different distribution (debris, host, preparation). That is the collaboration’s real hardness | Do not assume we get them. If we do: qualitative demo only; no retrain unless they are labelled |
| Domain gap vs the Orang Asli / One Health motivation | Public labels are species, not human-vs-animal origin; morphology overlap is why the collaboration exists | Stay honest: we draft *looks like species X*; host-origin is future / not this dataset |

**Still open — correction, re-run, and what a case actually stores**

The brief names the loop; it does not specify the semantics. These are the product holes.

| What we still need to investigate | Why it matters | Working default |
|---|---|---|
| Wrong *species* on an existing box | Core correction | Dropdown of the 11 classes (or current class set) |
| False positive (dirt, bubble, junk box) | Reader must be able to reject a draft | Delete / dismiss the box; count as disagreement |
| False negative (egg the model missed) | Brief says “correct mislabelled detections” — not clearly “draw a missed egg” | Allow add-a-box if we can do it cleanly; otherwise flag the *image* as incomplete |
| Uncertain **flag** (and optional note) | Separate from a hard correction | Persist on the box; does not require a re-run |
| Re-run after moving the threshold | New boxes vs the human’s existing edits | Re-run replaces the *model* overlay; keep flags/corrections that still match a box, or store the previous run as history on the same case |
| What the **accuracy summary** counts | Must not be sold as diagnostic accuracy | Human-vs-model disagreement: label changes, deletions, flags; per-case + running tally. Not clinical PPV, not host-origin |
| Case schema: image, threshold, boxes, corrections, flags, re-runs, export snapshot | “Case management” is empty without this | One case = one photo; re-runs are versions on that case; export the latest reviewed state |
| What an exported **case report** contains, and in what file | A screenshot is not a record | Image + threshold + boxes/labels/scores + corrections/flags + timestamp; PDF for a human, CSV/JSON for the boxes |

**Still open — who uses it, on what surface**

| What we still need to investigate | Why it matters | Working default |
|---|---|---|
| Operator wording: lab tech vs trainee vs student running the same workflow | Changes UI copy and how “expert correction” is framed | Screening reader in an Azdayanti-lab-style workflow |
| Web vs mobile | Bench microscope + PC vs a phone in a village — we are not a field deployment this year | Web first; responsive layout if cheap |
| Logged-in personal history vs a single-operator session | “Personal history log” can mean auth, or just this browser’s cases | Session is enough for a prototype; auth only if we need two named users |
| Who walks upload → detect → review → correct → export before we call the UI done | Usability is a product claim, not a screenshot | Team, plus a screening reader if we can get one |

**Not pending — already decided, do not reopen on this slide:** live video, batch processing, LIS/LIMS, clinical validation, treating patients, classifying human vs animal origin, training on unlabelled field photos as if they were Chula.

**Next on the project:** train on Chula, freeze a case schema, wire detect → correct/flag → re-run → export, then use a first val run and any collaborator images (if they appear) to settle the open rows above.

---

**On-slide bullets** (clusters; tables above for detail):

- ParaShot: one photo → draft boxes + species → human checks → saved case. Not diagnosis, not host-origin
- Detector still open: fine-tune vs scratch, which YOLO/Faster R-CNN, 11 classes vs a first subset, operating threshold, backend latency
- Data still open: Chula metric and split; what AI-KFM is for; any Azdayanti images this year (assume public data; qualitative only if they arrive)
- Case loop still open: delete junk boxes, add missed eggs, what a re-run does to edits, what the accuracy summary actually counts, what a report contains
- Surface still open: web vs mobile, session vs login, who the screening reader is
- Next: train on Chula, freeze the case record, wire the loop, let the first val run and any collaborator images answer the rest

**Spoken (~45s):**
“ParaShot is the screening-support loop: one photo, draft boxes and species, a human checks, save it as a case. We train on public Chula data — not diagnosis, and not telling human eggs from animal eggs. What we still have to work out is the detector itself: fine-tune versus from scratch, which model, all eleven species versus a smaller first set, and a realistic bar on a Chula hold-out. We also have not nailed the case semantics: can the reader delete junk boxes and add a missed egg, what a re-run does to their edits, what the accuracy summary counts — disagreement with the model, not a medical result — and what an exported case actually contains. We do not yet know if we will see any of Dr. Azdayanti’s soil or stool images this year; until then we stay on public data, and AI-KFM stays a comparison set. Next we train, freeze what a case stores, wire the loop, and let those results settle the rest.”

**If asked.** Give the working default and why. Do not promise field images, host-origin labels, or a clinical accuracy number.

**Leave off this slide:** problem story (2), product walkthrough (3), SMART wording (6), the full in/out-of-scope *list* (7) — point at the investigations instead.

---



## 6. Questions to ask the supervisor (still open / to confirm)

**Detection model & data** *(partly answered 31 Aug 2026)*

- ~~Train our own model or use/fine-tune a pre-trained one (e.g. YOLOv8)?~~ → Train a standard detector (YOLOv8–v12 or Faster R-CNN) on Chula-ParasiteEgg-11. Still confirm: from-scratch vs COCO-pretrained fine-tune (almost certainly fine-tune).
- ~~Specific dataset provided, or source our own microscopy images?~~ → Public sets named: Chula-ParasiteEgg-11 (primary), AI-KFM (supplementary). No Orang Asli field set promised for this semester.
- ~~Which parasite species must be supported — minimum set or team-defined?~~ → The 11 Chula classes (see §1 kickoff). Confirm whether a subset is acceptable for MVP.
- Reasonable baseline accuracy target at this stage? **Still open** (ICIP 2022 challenge numbers exist — can cite, but set a conservative FYP bar).
- Will we get any of Dr. Azdayanti’s images for a *qualitative* demo, or public data only? **Still open — do not assume.**

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

- [ ] **Users / stakeholders:** §5.5 default is screening reader in an Azdayanti-lab-style workflow. Team still lock wording (lab tech vs trainee vs student proxy) before the deck is final.
- [ ] Confirm remaining supervisor questions in Section 6 (web-vs-mobile, tech stack, FYP accuracy bar, any field images, export format, auth). Dataset + 11 Chula classes + YOLO/Faster R-CNN are locked.
- [ ] Replace WSM example alternatives + scores with the team's real considered options and agreed reasoning.
- [x] Add cited background research — see **§5.3b** (seven papers, including supervisor-named Chula + AI-KFM). Still put 2–3 of them on slides 2/6; do not overclaim we are a field diagnostic device or host-origin classifier.
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
- Supervisor team-workspace kickoff (Dr. Sicily, 31 Aug 2026) — collaboration, scope, datasets, model, papers

