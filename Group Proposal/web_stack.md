# Web Stack (PROPOSED)

Drafted 31 Oct 2026 for the proposal report due Mon 2 Nov 2026. Revised the same day after a source check (every hosting, library and pricing page below was opened on 31 Oct 2026) and a merge of the separate `methodology_research.md` note (31 Oct 2026, Downloads). Feeds 4.3 System architecture, 4.6 Tools, 3.3.2 Resources and Appendix B Risk Register. Everything here is **PROPOSED** until the team confirms the WSM scores on Sun 1 Nov 2026 and records the result in the Shared Decisions sheet. The one **AGREED** item is training on Google Colab with an Ultralytics YOLO model (user).

## 0. Pre-checks

| Check | Result |
|---|---|
| Did Dr Sicily state a preferred stack? | **No.** Nothing in the supervisor rulings (`final_pitch_content.md` section 2), the Notion supervisor questions, or minutes 1–4. The September handover listed "Preferred/required tech stack (Python/Flask, React, specific DB)?" as a question to ask her and no answer was ever recorded. Her constraints that do bear on the stack: backend converts and resizes images; CPU is fine for single-image inference, GPU better for batch; basic authentication with case ownership; an architecture plan before implementation; a "feature-rich, production-like app" from a five-member team. |
| What do the two full-stack developers (Hong Zhi Hong, Kam Joshua) already know well? | **Not recorded anywhere in the repo.** Meeting 2 put "decide on technical stack" on the agenda and it was never closed. The team-familiarity column below is therefore a placeholder and must be filled in on Sun 1 Nov. |
| Anything already fixed by the features? | Python inference (Ultralytics / RF-DETR); batch detection as a background job; relational DB for users, roles, cases, boxes and corrections; file storage for images; browser-side box drawing and threshold filtering; junior and senior logins; PDF/CSV export; Chrome and Edge; CPU inference on free or cheap hosting. |
| Team laptops | Windows and Mac (user, 31 Oct 2026). The development environment must run on both, which is why Docker Compose is in the recommended stack. Because the API and worker run in Linux containers, the operating-system support of a queue library is **not** a selection criterion. |

## 1. Candidates per layer

| Layer | Candidate 1 | Candidate 2 | Candidate 3 |
|---|---|---|---|
| Frontend | **React + TypeScript (Vite)**. What CVAT and Label Studio use (both React 18); largest component ecosystem. Vite needs Node 20.19+ or 22.12+ | Vue 3. Smaller learning curve, fewer annotation-tool precedents | Django templates + HTMX. Least JavaScript, but a canvas editor still needs a JS library, so it saves little |
| Box-drawing library | **Konva via react-konva**. Scene graph, built-in Transformer for move/resize, `dash` property for dashed boxes. Label Studio ships konva + react-konva (CVAT uses its own canvas package) | Fabric.js. Strong selection UX, heavier, aimed at design editors (text, SVG export) | Plain `<canvas>` or SVG with hand-written hit-testing, drag and resize. Zero dependencies, most work |
| API | **Django + Django REST Framework**. Users, groups, permissions, admin and migrations built in; CVAT and Label Studio precedent (both on Django 5.2) | FastAPI + SQLAlchemy. Typed validation, automatic OpenAPI docs, async; auth, roles and admin are assembled by hand. `methodology_research.md` preferred this option but weighed none of the role, admin or settings-page requirements | Next.js API routes (TypeScript) calling a separate Python inference service. Two languages, two deployments |
| Background jobs | **RQ (Redis Queue) via django-rq**. Simple, what CVAT and Label Studio use. RQ docs name SimpleWorker for Windows if anyone ever runs the worker outside Docker | Celery + Redis. More features (retries, scheduling, chains), more configuration. Celery's docs say "we don't support Microsoft Windows"; moot inside a Linux container | DB-backed queue (Django-Q2 or Procrastinate on PostgreSQL). No Redis to host; lower throughput, fine for our volumes. Prefer a library over a hand-written jobs-table poller, which would need row locking, retries and dead-job handling |
| Database | **PostgreSQL** (SQLite locally). Required by every managed host; CVAT/Label Studio default | SQLite in production. Single-file, no server, but single-writer and no managed hosting | MySQL. Equivalent to PostgreSQL for us with fewer free hosts |
| Image storage | **S3-compatible object storage: Cloudflare R2** (10 GB-month, 1 M Class A and 10 M Class B operations free per month, no egress fees; Standard storage only) via django-storages | Supabase Storage (1 GB free, 5 GB egress, project pauses after 1 week idle) | Host's persistent disk (Railway volume; Render disks attach to paid services only). Simplest, not shareable between API and worker on some hosts |
| Auth and roles | **Django built-in auth** (session cookie) + two Groups (junior, senior) + DRF permission classes; case ownership is a foreign key to the uploader | Supabase Auth or Clerk (hosted). Less code, third-party dependency, roles still enforced in our API | JWT with fastapi-users or djangorestframework-simplejwt. Needed only if frontend and API live on different origins |
| Hosting | **Railway** (Hobby, USD 5/month with USD 5 usage credit; API, worker, PostgreSQL and Redis in one project; Singapore region available). Railway's Free plan (USD 1 credit/month, 0.5 GB RAM and 1 vCPU per service) and 30-day Trial (USD 5 once, 1 GB RAM) are too small for a worker that holds a model | Render (free web service: 0.1 CPU / 512 MB, spins down after 15 min idle, 750 h/month; free PostgreSQL 1 GB, expires after 30 days; workers and disks are paid-only) | Hugging Face Spaces. "Gradio and Docker Spaces run on compute and require a paid plan to create", so no longer a free option even though CPU Basic (2 vCPU, 16 GB) has no hourly cost; free hardware also sleeps when idle |
| Dev environment | **Docker Desktop + Docker Compose**. Runs on Windows, Mac and Linux; Compose starts API, worker, PostgreSQL and Redis from one file | Manual installs per laptop. Setup drift between Windows and Mac | Dev containers / Codespaces. Same images, adds a GitHub dependency |
| Image decoding | **Pillow**. Reads JPEG, PNG and TIFF and writes 8-bit RGB PNG (FR2) | OpenCV. Already an Ultralytics dependency, weaker TIFF support | tifffile + Pillow if LZW/multi-page TIFF turns up in testing |

Considered and rejected before scoring: Streamlit or Gradio single-app frameworks. They cannot do editable bounding boxes, two roles with case ownership, or background batch jobs without fighting the framework.

## 2. WSM

Three whole-stack options are scored rather than eight layers separately, because the layers are not independent (the API choice fixes the auth and job options).

- **A. Django stack:** React + react-konva · Django + DRF · RQ + Redis · PostgreSQL · R2 · Django auth · Railway.
- **B. FastAPI stack:** React + react-konva · FastAPI + SQLAlchemy · RQ or Celery + Redis · PostgreSQL · R2 · fastapi-users JWT · Railway.
- **C. Next.js stack:** Next.js (TypeScript) + react-konva · Next API routes + Prisma · Python FastAPI inference service polled through the DB or Redis · PostgreSQL · Supabase Storage and Auth · Vercel + Railway.

Scores 1 (poor) to 5 (best). Weights sum to 100. Weighted score = Σ weight × score, maximum 500.

| Criterion | Weight | A Django | B FastAPI | C Next.js | Why the weight |
|---|---|---|---|---|---|
| Team familiarity | 20 | **?** (3) | **?** (3) | **?** (3) | Largest single driver of MVP speed. **Fill in Sun 1 Nov**; 3 is a placeholder |
| Fit with Python ML | 15 | 5 | 5 | 3 | Inference is Python; same process as the API avoids a second service and serialisation |
| Background-job support | 15 | 5 | 4 | 3 | Batch detection must run off the request thread; A has django-rq precedent (CVAT, Label Studio); C needs a cross-language queue |
| Box editing | 10 | 4 | 4 | 4 | All three use react-konva; equal |
| Auth and roles | 10 | 5 | 3 | 4 | A: users, groups, permissions and admin page out of the box. B: assembled from libraries. C: Auth.js or Supabase, roles still custom |
| Free hosting / CPU inference | 10 | 4 | 4 | 3 | A and B: one Railway project. C: two hosts (Vercel + Python host) and two free tiers to watch |
| Docs and maintenance | 10 | 5 | 4 | 5 | Django and Next.js have the deepest docs; FastAPI is good but patterns for auth/admin are scattered |
| Speed to MVP (Sem 2 W8) | 10 | 4 | 3 | 3 | A: admin page replaces a settings/user-management UI for the MVP. B and C: more glue code |
| **Weighted total (with placeholder familiarity)** | 100 | **430** | 375 | 340 |

Sensitivity: the familiarity row can move a stack by at most 80 points (20 × 4). A still wins against C whatever the team enters. A loses to B only if the team scores FastAPI two or more points higher than Django on familiarity, so that is the one question to settle on Sunday. The separate `methodology_research.md` note (31 Oct) recommended FastAPI; it added no criterion missing from this table, so the two notes should state the same default once the team decides.

## 3. Recommended stack (PROPOSED)

| Layer | Choice | One-line reason |
|---|---|---|
| Frontend | React + TypeScript, built with Vite (Node 20.19+ or 22.12+) | Same shape as CVAT and Label Studio, so there are open-source examples of exactly our review screen to learn from |
| Box drawing | react-konva (Konva); major version must match the React major | Declarative React components, a built-in Transformer for move/resize, and a `dash` stroke property for the dashed "check" boxes; Label Studio ships the same pair; threshold filtering is just a React state filter over the stored boxes |
| API | Django 5.2 LTS (extended support to April 2028) + Django REST Framework | Users, groups, permissions, migrations and an admin page come free, which is most of FR6 and the settings page |
| Background jobs | RQ via django-rq, Redis broker (Celery if we need retries or scheduling later) | Smallest queue that CVAT and Label Studio both ship with; the worker imports the same Django models as the API |
| Inference | YOLO26 exported to ONNX, run with onnxruntime inside the RQ worker | Avoids installing PyTorch on the server (memory and image size) and Ultralytics documents CPU speed-ups for ONNX Runtime; benchmark before relying on the figure |
| Image decoding | Pillow | Decodes JPEG, PNG and TIFF uploads once and writes the stored 8-bit RGB PNG (FR2) |
| Database | PostgreSQL (SQLite for local dev) | Every managed host offers it; corrections and approval history are relational by nature |
| Image storage | Cloudflare R2 through django-storages (S3 API) | 10 GB free with no egress fees covers the batch-upload use case; the stored 8-bit PNG per image (FR2) goes here, not in the DB |
| Auth | Django session auth, two Groups (junior, senior), DRF permission classes | Matches the two-login requirement exactly; case ownership is a foreign key on the case row |
| Hosting | Railway Hobby, Singapore region (API + worker + PostgreSQL + Redis in one project); the built frontend is served by Django via WhiteNoise on the **same origin** | One bill, one project, no spin-down; cheapest option that can run a worker, which the free Render tier cannot. Same origin keeps session cookies and CSRF simple; a separate static host (Cloudflare Pages) would force the JWT option. Budget USD 8–15/month, not USD 5 (inference, see WS1) |
| Dev environment | Docker Desktop + Docker Compose (API, worker, PostgreSQL, Redis, optional MinIO as a local R2 stand-in) | Same containers on Windows and Mac; the Compose file doubles as the laptop-hosted demo fallback |
| Training | Google Colab + Ultralytics (AGREED) | Free GPU; checkpoint every run to Drive and resume, because sessions are capped (see WS9) |
| Export | WeasyPrint (PDF) and Python `csv` in a worker job | Report rendering is slow for big batches, so it belongs in the queue like detection. WeasyPrint needs Pango ≥ 1.44 and its libraries in the worker image |

## 4. Sources to cite (APA details to be completed by the writer)

All opened 31 Oct 2026.

1. CVAT architecture, official docs: https://docs.cvat.ai/docs/administration/community/advanced/cvat-architecture/ — "Main engine, uses Django + Django DRF", PostgreSQL, Redis as "Queue manager", a set of named workers. The page does **not** name the frontend or RQ; for those cite the repo: `cvat/requirements/base.in` (`Django~=5.2.0`, `rq==1.16.0`, `django-rq`) and `cvat-ui/package.json` (`"react": "18.2.0"`), https://github.com/cvat-ai/cvat. Cite for the precedent that annotation tools use this exact shape.
2. Label Studio repository, HumanSignal: https://github.com/HumanSignal/label-studio — README: React + mobx-state-tree UI; Docker Compose adds "PostgreSQL - production-ready database that replaces less performant SQLite3"; ML backend is a separate server. `pyproject.toml`: `Django (>=5.2.16,<5.3.0)`, `djangorestframework`, `django-rq`, `rq`, `redis`, `psycopg`, `django-storages`. `web/package.json`: `"konva": "^8.1.3"`, `"react-konva": "^18.2.10"`. Cite for the Django + RQ + react-konva precedent and the SQLite-in-dev, PostgreSQL-in-prod choice.
3. Django REST Framework documentation, authentication and permissions: https://www.django-rest-framework.org/api-guide/permissions/ — cite for role enforcement.
4. Konva, "Select and Transform" documentation: https://konvajs.org/docs/select_and_transform/Basic_demo.html — "Transformer ... allows you easily resize and rotate any node or set of nodes", with a React tab. Konva.Shape API: https://konvajs.org/api/Konva.Shape.html — `dash` "get/set dash array for stroke", `dashEnabled`. react-konva: https://konvajs.org/docs/react/index.html — "The react-konva major version must match the React major version". Cite for FR5/FR11 box editing.
5. Ultralytics, ONNX export integration: https://docs.ultralytics.com/integrations/onnx/ — "ONNX Runtime can provide up to 3x CPU speedup compared to native PyTorch models"; "YOLO26n runs up to 43% faster than YOLO11n on CPU ONNX inference". Ultralytics' own claims, not independent. Cite for CPU inference on cheap hosting. Training: https://docs.ultralytics.com/modes/train/ (pretrained fine-tuning, `imgsz`, mosaic, resume).
6. Celery, introduction: https://docs.celeryq.dev/en/stable/getting-started/introduction.html — task queues "distribute work across threads or machines"; Redis and RabbitMQ brokers; "we don't support Microsoft Windows". RQ workers: https://python-rq.org/docs/workers/ — SimpleWorker "executes jobs in the same process, without using fork()", recommended on Windows. FastAPI background tasks: https://fastapi.tiangolo.com/tutorial/background-tasks/ — heavy computation belongs in a separate queue. Cite if we justify the queue in general terms.
7. Hosting limits (cite only in the risk register, dates matter): Hugging Face Spaces overview, https://huggingface.co/docs/hub/en/spaces-overview ("Gradio and Docker Spaces run on compute and require a paid plan to create"; CPU Basic 2 vCPU / 16 GB; free hardware sleeps when unused); Render free tier, https://render.com/docs/free (15-minute spin-down, 750 free hours, free PostgreSQL expires after 30 days, 1 GB) and compute plans, https://render.com/docs/compute-plans (free 0.1 CPU / 512 MB, web services and Postgres only); Railway plans, https://docs.railway.com/reference/pricing/plans (Hobby USD 5/month with USD 5 usage included; Free plan USD 1/month credit, 0.5 GB RAM, 1 vCPU), free trial, https://docs.railway.com/reference/pricing/free-trial (USD 5 once, 30 days), usage rates, https://railway.com/pricing (about USD 10 per GB RAM-month, USD 20 per vCPU-month, USD 0.15 per GB volume-month), regions, https://docs.railway.com/reference/regions (`asia-southeast1`, Singapore); Supabase pricing, https://supabase.com/pricing (500 MB DB, 1 GB storage, 5 GB egress, paused after 1 week idle); Cloudflare R2 pricing, https://developers.cloudflare.com/r2/pricing/ (10 GB-month free, 1 M Class A and 10 M Class B operations free, free egress).
8. Tooling: Docker Desktop, https://docs.docker.com/desktop/ (Windows, Mac, Linux); Docker Compose, https://docs.docker.com/compose/ (several services from one YAML file); Vite guide, https://vite.dev/guide/ ("Vite requires Node.js version 20.19+, 22.12+"); Pillow image formats, https://pillow.readthedocs.io/en/stable/handbook/image-file-formats.html (JPEG, PNG, TIFF); WeasyPrint first steps, https://doc.courtbouillon.org/weasyprint/stable/first_steps.html (Python ≥ 3.10, Pango ≥ 1.44); Django releases, https://www.djangoproject.com/download/ (5.2 LTS supported to April 2028); Google Colab FAQ, https://research.google.com/colaboratory/faq.html ("notebooks can run for at most 12 hours", idle timeouts, GPU types vary, no guaranteed resources).

## 5. Risks for the register (PROPOSED ratings)

| ID | Risk | Type | L | I | Mitigation |
|---|---|---|---|---|---|
| WS1 | **Free hosting cannot run the worker.** Render's free tier offers web services only, spins down after 15 min idle (about a minute to wake), and its free PostgreSQL is deleted after 30 days. Railway's Free and Trial plans cap a service at 0.5–1 GB RAM. Hugging Face Docker Spaces need a paid plan. Railway bills usage on top of the Hobby fee, so an always-on API plus a worker holding a model will likely exceed the USD 5 credit | Technical / cost | High if we insist on "free" | High (batch detection and the demo depend on the worker) | Budget USD 8–15/month on Railway Hobby (inference from the usage rates; measure in Sem 2 W1). Render would need a paid web service **and** a paid worker, so it is not the cheaper path. Keep the `docker compose` stack as the fallback so the demo can run on a laptop if hosting fails |
| WS2 | **Model memory on a small instance.** A PyTorch install plus Ultralytics is hundreds of MB on disk and several hundred MB of RAM at import; 512 MB instances (Render free, Railway Free) will be killed on first inference | Technical | Medium | High | Export YOLO26 to ONNX and run onnxruntime in the worker; size the worker at 1 GB; load the model once per worker process, not per job |
| WS3 | **RF-DETR is not a CPU model** (~30 M params). If it is ever deployed instead of YOLO26, inference time per image rises sharply on CPU | Technical | Low (it is the comparison model, not the deployable one) | Medium | Deploy YOLO26 only; report RF-DETR results offline from Colab |
| WS4 | **Batch storage volume.** Hundreds of field-trip images per batch, each stored as an 8-bit PNG, can exceed 1 GB quickly; Supabase free is 1 GB, R2 free is 10 GB. R2 also caps free writes at 1 M per month, far above our volumes | Technical / cost | Medium | Medium | Use R2; cap batch size (FR1 "batch cap"); store one PNG per image, no duplicates; set a retention rule for the demo instance |
| WS5 | **Learning curve.** If the full-stack pair have not used React + Konva or Django before, the review screen (FR4, FR5, FR11) is the hardest UI in the app and sits on the critical path to M2 (Sem 2 W8) | PM | Depends on Sunday's familiarity scores | High | Spike the box editor in Sem 2 W1–W2 with a stand-in model; copy patterns from Label Studio's react-konva editor and CVAT's UI; keep the detection API behind a fixed JSON contract so AI and web streams work in parallel |
| WS6 | **Redis on free tiers.** Managed Redis is often the first thing a free plan drops | Technical | Medium | Medium | Railway runs Redis inside the project credit; fallback is a DB-backed queue (Django-Q2 or Procrastinate) with no Redis at all |
| WS7 | **Cold-start on first upload.** With spin-down hosting the first request after idle takes about a minute, which looks like a failure in a demo | Technical | High on Render free, nil on Railway | Low | Use an always-on plan for the demo window, or warm the service before the session |
| WS8 | **Two-stream integration.** Model output format (boxes, scores, class ids, model version) must be fixed before the web team builds the review screen | PM | Medium | High | Agree the prediction JSON schema in Sem 2 W1 and store it in the repo; include "detector output renders in the review page" as a sprint-1 backlog item |
| WS9 | **Colab limits interrupt training.** Free notebooks "can run for at most 12 hours", runtimes time out when idle, GPU types vary and no resources are guaranteed | Technical | High | Medium | Checkpoint every epoch to Google Drive and use Ultralytics `resume`; keep runs under 12 h; Colab Pro or a Kaggle GPU as the paid fallback |
| WS10 | **Cross-platform setup drift.** Team laptops run Windows and Mac; native installs of PostgreSQL, Redis, Pango (WeasyPrint) and onnxruntime differ per OS | PM / technical | Medium | Medium | Docker Desktop + Compose for everyone; the worker image installs Pango. Still to check: Docker Desktop licensing for students and Apple silicon images for every dependency |
| WS11 | **Free-tier terms change.** Every limit above was checked on 31 Oct 2026; Hugging Face already moved Docker Spaces behind a paid plan | Cost | Medium over two semesters | Low | Re-check the register each sprint review; keep the Compose fallback |

## 6. Where it goes in the report

| Report section | Take from this file |
|---|---|
| 4.3 System architecture and integration | Browser (React + Konva, served by Django) → Django/DRF API → RQ queue (Redis) → inference worker (onnxruntime, YOLO26) → PostgreSQL (cases, boxes, corrections, users) + R2 (images). Model output stored immutably; corrections are a separate table keyed by user and time |
| 4.6 Tools | Table rows: Python 3.12, Django 5.2 LTS + DRF, django-rq + Redis, onnxruntime + Ultralytics (export), Pillow, PostgreSQL, Cloudflare R2 + django-storages, Node 20.19+ with React + TypeScript + Vite, react-konva, WeasyPrint, Docker Desktop + Docker Compose, Railway, GitHub, Colab (training) |
| 3.3.2 Resources | Software row: the list above. Compute row: Colab for training (12 h session cap); Railway Hobby (USD 8–15/month estimated) for the deployed app; CPU inference. Storage row: R2 10 GB free |
| Appendix B Risk register | WS1–WS11 above, merged with the existing ten |

## 7. Open items for Sun 1 Nov 2026

1. Zhi Hong and Joshua enter the team-familiarity scores (1–5) for A, B and C. That row decides A versus B.
2. Confirm the team is willing to pay about USD 8–15/month for hosting from Sem 2, and who holds the Railway account, or accept a laptop-hosted demo as the fallback.
3. Confirm RQ versus Celery (the choice does not change the architecture diagram).
4. Confirm the frontend is served by Django on one origin (session auth) rather than a separate static host (JWT).
5. Batch cap and expected images per week, so storage and cost can be sized for 3.3.2.
6. Where trained weights live: R2, Hugging Face Hub, or inside the worker image.
7. Check Docker Desktop licensing for students and Apple silicon support for every image.
8. Align `methodology_research.md` with the decided API default so the two notes agree.
9. Authorship statement: record the WSM table and this section under the developer who takes it, as "figures/tables led: Web stack WSM".
