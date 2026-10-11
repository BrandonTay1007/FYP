# ParaShot — what this project actually is

Cheat sheet from team discussion. Working hub: [kickoff notes](https://app.notion.com/p/3cd3a300c24f81ff939bd03c12cf04ce). Local dump: `ParaShot_Pitch_Handover.md`. Official topic text is in that file under **Topic brief**; supervisor kickoff is under **Supervisor kickoff**.

You do not need to become a biologist. This is software: look at a photo of a microscope slide, find blobs that look like parasite eggs, guess the species, let a human fix it, save it as a record.

---

## Pitch (Week 5 draft, Moodle sign-off)

Week 4 studios are done. Topics are assigned and **locked** (no swaps; Moodle setup is complete). Supervisors will mostly **not** email first — we have to chase details. Presentation scheduling is a later post.

**By end of Week 5:** draft pitch deck on Moodle under sign-offs, then **ping our supervisor to sign off**. No sign-off → later presentation is invalid and scores **zero**, even if we present. Slides can keep changing until the actual presentation.

Sign-off is on three things: **scope**, **WSM**, **project goals**. The deck also has to show we understood (1) requirements, (2) goals / objectives / outcomes / deliverables, (3) limitations / scope / constraints, (4) anything else vital below.

Suggested 9-slide flow (adjust if needed; ignore the generic worksheet order):

1. **Introduction**
2. **Problem / opportunity** — what we solve or explore
3. **Project overview** — summary of what we will do, tied to (2)
4. **Analysis of option and recommendation** — WSM with **at least one example** used to pick direction
5. **Preliminary requirements / objectives** — from supervisor, our decisions, what we plan to use
6. **Project goals (SMART) / deliverables** — the output at the **end of the whole project** (after Part 2), not just this pitch
7. **Limitations / scope** — **scope** = what we set as in vs out (achievable vs not); **limitations** = constraints often outside our control. They can overlap.
8. **Schedule estimate / timeline**
9. **Conclusions** — what is still pending, needs more investigation

Full assessment + slide copy: `ParaShot_Pitch_Handover.md`.

---

## One line

People still find and name parasite eggs by staring at a slide. ParaShot drafts the boxes and species names, lets the user fix them, and saves each photo as a **case** instead of a forgotten glance.

## Collaboration (supervisor, 31 Aug 2026)

Origin: Dr. Sicily (SOIT) × Assoc. Prof. Satoshi Ogawa (JCSMHS) × Dr. Azdayanti (UiT). Her One Health work in Orang Asli villages collects soil and animal stool; many human and animal eggs look the same, which limits diagnosis. That is the **motivation**, not this semester’s labelled task.

**Train on:** Chula-ParasiteEgg-11 (11 species, ICIP 2022) with YOLOv8–v12 or Faster R-CNN. **Optional compare:** AI-KFM 2022 (cattle GINs). **Do not claim** we classify host (human vs animal) this year — public labels are species, not origin.

---

## Biology in 30 seconds

Some parasites lay **eggs**. A lab puts a sample (often stool) on a **glass slide**. A trained person looks under a microscope and does two jobs by eye:

1. **Find** the eggs (small; the picture is messy).
2. **Name** them — different species have different egg **shapes**. Shape ≈ species.

That is all the biology you need. You are not treating patients. You are helping someone **read a picture**.

---

## What a user actually does

1. **Upload** one microscopy photo.
2. Set a **confidence threshold** (one slider — see below).
3. Click **Run** (on demand — not live video).
4. App draws **boxes** on suspected eggs and a **species label** on each box.
5. Human **checks**: fix wrong labels, **flag** uncertain ones, optionally add notes.
6. Optionally **re-run** the same photo with a different threshold.
7. That session is saved as a **case** in a **personal history log**.
8. **Export** a case report.
9. Over time, corrections feed a simple **accuracy summary** (how often the human disagreed with the model).

Without 5–8 this is a one-shot demo (upload → boxes → close tab). The brief says **do not build only that**.

**IT pieces:** detection pipeline + case database + UI (upload, slider, overlay, correct, history, export).

---

## Case, history log, case management

**Case** = one saved analysis of **one uploaded photo**. It stores roughly: the image, the threshold used, boxes + species labels, corrections, uncertain flags, and any re-runs.

- Photo of slide A → **case 1**
- Photo of slide B (a different image) → **case 2**

**Personal history log** = that user’s list of their own cases (open, look back, export). “Personal” = your screening history, not a hospital chart. Auth vs session is still a supervisor question.

**Case management** = CRUD around those records: create after detection, open from the log, update (correct / flag / re-run), export a report. The “case-management database” is where those records live.

---

## Re-run vs second slide

These are different.

| | Same photo? | Same case? | What happens |
|---|---|---|---|
| **Second slide** | No — new image | **New case** | Like File → New |
| **Re-run** | Yes | **Same case** | Run the detector again, usually after changing the **threshold** |

**Flags and comments do not need a re-run.** Those are notes on the current answer.

**Re-run purpose:** try a different detection cutoff on *this* image.

- Too few boxes (missed eggs) → **lower** threshold → re-run → more boxes (including weaker guesses).
- Too much junk (dirt, bubbles) → **raise** threshold → re-run → fewer, more confident boxes.

**Corrections** (wrong species name) update the **accuracy summary**. That does not require a re-run.

---

## Confidence threshold (one slider, not per species)

The model, for each candidate box, outputs:

- **where** (the box)
- **what species it thinks** (the class / label)
- **how sure it is** — a score usually **0 to 1**. That is **confidence**. It is the model’s own certainty, **not** a lab test and **not** a biological rule.

**Species** and **confidence** are two fields on the same box.

```
Box A:  species = Ascaris    confidence = 0.91
Box B:  species = Trichuris  confidence = 0.44
Box C:  species = Ascaris    confidence = 0.22
```

**Threshold** = one number for the whole run (topic brief: a single “detection-confidence threshold”).

**Show the box if `confidence ≥ threshold`. Hide it otherwise.**

| Threshold | A 0.91 | B 0.44 | C 0.22 |
|---|---|---|---|
| 0.80 (picky) | shown | hidden | hidden |
| 0.40 (looser) | shown | shown | hidden |

Same photo, same model, same species guesses. You only change **which guesses are drawn**.

Not “each species has its own threshold” (that would be extra). Not “this % proves it is a valid egg.” Not a diagnosis.

Low threshold → more boxes, more junk. High threshold → cleaner picture, more real eggs dropped.

---

## Detect, then species (what the product is)

Two jobs, in order:

1. **Detect** — are there eggs, and where? (boxes)
2. **Identify** — what **species** does each egg look like? (labels)

Pitch wording: “this image contains objects that *look like* species X eggs — check them.”  
Not: “this patient has species X.”

---

## Screening support vs diagnostic device

**Diagnostic device** = intended to decide what a patient has as a clinical result. Needs clinical validation, regulation, liability.

**Screening support** (us) = flag possible eggs for a human to confirm. Wrong boxes are expected. The workflow includes correction.

FYP prototype, not a diagnostic device. Say that on slide 2 in one clause; full out-of-scope list stays on slide 7.

---

## Slide 2 (problem) vs the topic brief (overview)

The long Overview paragraph in the topic card is **what you will build** → **slide 3 (project overview)**.

**Slide 2** is **why it exists** — not a feature dump.

Working slide 2 beats — full text + citations in `ParaShot_Pitch_Handover.md` §5.4 and §5.3b.

1. **Pain:** find eggs *and* name the species by eye; scarce skill; volume/fatigue; no saved record.
2. **Local hook:** Orang Asli One Health collaboration — many human vs animal eggs look the same (motivation, not this semester’s label).
3. **Opportunity:** on-demand detect → species label → human corrects → case log.
4. **Limit:** screening support, not diagnosis, not host-origin classification.

**Slide 3** is **what you will build** — full bullets + spoken in `ParaShot_Pitch_Handover.md` §5.4b. Users/stakeholders are 3b (§5.5): operator = screening reader (Azdayanti-lab-style); not patients.

---

## Why this is an IT project

| Part | CS meaning |
|---|---|
| Detection pipeline | Image in → boxes + class names + scores |
| Threshold | Filter predictions by confidence |
| Case DB | CRUD for image + results + edits |
| History log | List/detail UI |
| Correction / re-run | Edit labels; run pipeline again on same image |
| Export | Record → file |
| Accuracy summary | Count human vs model disagreement |

Species names are **class labels** in a dataset, like `cat` / `dog`. Supervisor-locked: train YOLO v8–v12 or Faster R-CNN on **Chula-ParasiteEgg-11** (11 species). **AI-KFM** is comparison only. Still open: fine-tune vs from-scratch, MVP subset vs all 11, FYP accuracy bar.
