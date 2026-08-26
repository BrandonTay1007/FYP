# ParaShot — what this project actually is

Cheat sheet from team discussion. Working hub (source of truth for the pitch): [Notion FYP](https://app.notion.com/p/3c83a300c24f806bbbd0ff2cdfabbac7). Local dump: `ParaShot_Pitch_Handover.md`. Official topic text is in that file under **Topic brief**.

You do not need to become a biologist. This is software: look at a photo of a microscope slide, find blobs that look like parasite eggs, guess the species, let a human fix it, save it as a record.

---

## One line

People still find and name parasite eggs by staring at a slide. ParaShot drafts the boxes and species names, lets the user fix them, and saves each photo as a **case** instead of a forgotten glance.

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
2. **Opportunity:** on-demand detect → species label → human corrects → case log.
3. **Limit:** screening support, not diagnosis.

Users/stakeholders (who is at the microscope vs who reads exports) are **not locked** — rest of team still needs to argue student-operator vs lab-tech-operator. Do not block slide 2 on that.

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

Species names are **class labels** in a dataset, like `cat` / `dog`. Dataset, pretrained model, and which species are **supervisor questions**.
