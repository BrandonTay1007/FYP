# ParaShot Project Management Methodology

Status: PROPOSED, 12 Oct 2026. Agent recommendation, not yet agreed by the team or supervisor. Change to AGREED and record the date once the team confirms. Section 7 lists what must be decided first.

Related: `final_pitch_content.md` (slide content, section 0 rules), `scoring_focus.md` (rubric weights), `teaching_team_clarification.md` (MUM content flow).

---

## 1. Decision

Run a phase-gated hybrid: fixed phases with exit gates taken from the Gantt, and two-week Scrum sprints inside each phase.

## 2. Why it is in the pitch at all

- Rubric v260915, Pitch Content, names "project management methodology" in both the HD and D bands alongside testing, WBS, schedule, dependencies and milestones.
- The MUM content flow (Ed, 30 Sep) has no methodology item. Staff ruling on Ed, 7 Oct: "Devp methodology goes earlier into the presentation if shown. This is the conclusion where you do reflection on the progress thus far." So it is optional, and if shown it sits with the project plan.
- Staff on Ed, 14 Aug, about group meetings: methodology is "Chosen by teams but typically based on the topic assigned. Some projects may naturally favour a phased development method whilst others will tend to work better as a cyclic agile deployment instead."
- Meeting 1 minutes already record "Everyone to determine which Scrum practices to adopt before project inception." The team has half-chosen Scrum.
- Open conflict: `final_pitch_content.md` says methodology is "not needed this semester (returns in Part 2)". That ruling is not in the Ed export. Confirm its source before dropping the slide line.

## 3. Why hybrid, not pure Scrum or pure phased

- The semester fixes hard-ordered, hard-dated milestones: proposal, report on 2 Nov, model baseline over the break, integration before deployment, final demo. Pure Scrum has no answer for fixed order and fixed dates, and supervisor availability is not negotiable per sprint.
- The detector is research work. Nobody can schedule "reach mAP 0.90" as a Gantt bar. Pure phased planning fails here.
- Mid-sem feedback: deployment overlapped integration testing with no buffer. Gates make the sequence explicit and address that feedback directly.
- Two parallel streams (AI engineers, full-stack) are an anticipated issue in the working file. A shared sprint boundary is the mitigation.

## 4. Outer loop: phases and gates

| Phase | When | Gate to leave it |
|---|---|---|
| Proposal | Sem 1, pitch 20 Oct, report 2 Nov | Pitch delivered, report submitted |
| Model foundation | Semester break | Baseline detector trained on Chula-ParasiteEgg-11, per-class metrics logged |
| Build | Sem 2 early to mid | App features done per the per-feature checklist; model meets NFR1 on held-out split |
| Integration testing | Sem 2, own window | Upload to report works end to end; senior review flow tested |
| Deployment | Sem 2, own window after testing | Deployed; fallback exercised |
| Final demo and report | Sem 2 end | Done |

Gate criteria go on the Gantt as milestone labels so the slide and the Q&A answer match.

## 5. Inner loop: sprints inside Build and Integration

- Two-week sprints, each ending on a Gantt milestone or a supervisor meeting.
- Roles: Brandon product owner (already PM per Meeting 4 roles), scrum master rotates, others dev. Keep ceremonies light; the meeting-minutes rubric grades artefacts that are "current and connected to the team's actual project activity", not ceremony count.
- One Notion backlog and board for both streams. Both streams end the sprint at the same review.
- At least one backlog item per sprint touches both streams, for example "detector output renders in the report page", so the model and app meet before the integration phase.
- Model experiments are time-boxed spikes with a measurable exit: "try X for two days, report per-class F1". A spike ends when time is up. The result is reviewed as a number and the next sprint decides pursue or drop.
- Definition of done for model work: metric logged, not "it runs". For app work: the per-feature checklist.
- NFR1 targets (mAP@0.5 and F1 at or above 0.90 per class on the held-out Chula split) are the Build gate, not a sprint task.

## 6. Ceremonies and artefacts mapped to what already exists

| Scrum element | ParaShot equivalent | Artefact |
|---|---|---|
| Sprint planning | First team meeting of the sprint | Minutes record the sprint goal |
| Daily standup | Async Discord post, three lines, blockers flagged | Discord channel |
| Sprint review | Weekly supervisor meeting in the sprint's last week | Minutes, metrics shown |
| Retrospective | Short section in the minutes | Minutes |
| Product backlog and sprint board | Notion | Notion views (name them, see section 7) |
| Increment | Merged pull requests | GitHub |
| Phase plan | Gantt with gate labels | Gantt slide |

The retro section doubles as the "evidence-based reflection on project management" the rubric wants in the conclusion.

## 7. Open decisions before this goes on a slide

1. Confirm hybrid over pure Scrum with the team.
2. Sprint length and the Part 2 start date.
3. Which Notion views are the official backlog and board.
4. How experiments are logged (where the metric lives) so Q&A has a concrete answer.
5. Who ruled that methodology is "not needed this semester" and whether that stands given the rubric wording.

## 8. Slide wording (one line under the Gantt)

"Phase-gated with two-week Scrum sprints inside each phase. Gates: baseline model, NFR1 on held-out split, end-to-end test, deployment. Artefacts: Notion board, GitHub PRs, per-feature checklist, minutes as review and retro."

Q&A one-liner: "The semester gives us fixed milestones and a research component we cannot fully plan, so we gate the phases and iterate inside them."

Pitfalls: do not list ceremonies you do not run; do not let the model stream skip reviews because training is still running; do not keep gate criteria only in your head.

---

## Changelog

- 12 Oct 2026: created as PROPOSED from the Ed export, rubric v260915, Meeting 1 minutes and the content working file.
