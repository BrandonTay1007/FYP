# ParaShot: Detection Model Selection Research

Date: 12 Oct 2026. Question: which detector should we train on Chula-ParasiteEgg-11, and if YOLO, which version?

## Recommendation (short)

Stay with YOLO. Train **Ultralytics YOLO26** (small, then compare nano) as the primary model, with **YOLO11** as the drop-in fallback. Do not use YOLO12 or YOLO13. Do not switch to Faster R-CNN or a DETR-family model as the main detector.

## Evidence

### 1. What won the ICIP 2022 challenge on this exact dataset
Source: Anantrasirichai et al. 2022, arXiv 2208.06063.
- 30 teams submitted. Winner NEGU: mIoU 0.942, F1 0.995, mAP@0.5:0.95 0.925, using CBNetV2 composite backbones, three models fused with weighted boxes fusion, plus pseudo-labelling.
- Runner-up ZUSTF4: YOLOv5 + Cascade R-CNN ensemble, mIoU 0.932, F1 0.989.
- Third BAD crew: five-model ensemble (Cascade R-CNN, GFL, HTC, TOOD), mIoU 0.930, F1 0.987.
- All entries used COCO or ImageNet pretraining; the paper states pretrained weights "significantly improve" results. Ensembles, test-time augmentation and pseudo-labelling gave the last few points.
- Hardest class: Capillaria philippinensis (mIoU 0.77 average across top 5). Large eggs (Ascaris, H. nana) were missed most under heavy blur. Taenia easiest.
- Takeaway: the 0.94 to 0.97 "benchmark" numbers come from multi-model ensembles with heavy backbones. A single student-trained model should not be held to them.

### 2. Single lightweight YOLO models on Chula-ParasiteEgg-11
| Paper | Model | mAP@0.5 | F1 | Params | Notes |
|---|---|---|---|---|---|
| Parasites & Vectors 2024 (YAC-Net, PMC11539555) | YOLOv5n baseline | 0.964 | 0.958 | 2.5M | 5-fold CV, 13,200 images |
| same | YAC-Net (YOLOv5n + AFPN neck) | 0.991 | 0.977 | 1.9M | also tested YOLOv3, v6n, v8n, v5n-SwinT; YOLOv8n highest recall 98.0% |
| Intelligence-Based Medicine 2025 (Amrita) | YOLOv5n/s, v7, v7-tiny, v8n/s, v10n/s | up to 0.987 (v7-tiny) | up to 0.986 (v10n) | n to s | YOLOv8n fastest, 55 FPS on Jetson Nano; v8n reported ~0.985 mAP@0.5 / 0.917 mAP@0.5:0.95, v10s ~0.984 / 0.927 |
| INJET 2025 (Giri et al., nepjol 87020) | Modified YOLO11n (Ghost conv, SimAM-ECA, DropBlock) | 0.963 | 0.922 | 2.79M | matches YOLO11s at 42% of its FLOPs |
| Sci Rep 2023 (CoAtNet, classification only) | EfficientDet + EffNetV2 | acc 0.88, F1 0.85 | | | anchor-based single model, weaker |
| arXiv 2208.01963 (ICIP entry) | EfficientDet EffNetV2 | acc 0.92, F1 0.93 | | | |

Takeaway: every single lightweight YOLO from v5 to v11 lands at mAP@0.5 0.96 to 0.99 and F1 0.92 to 0.98 on Chula. Version-to-version differences are about one point. Choice of version should therefore be made on ecosystem, stability, CPU speed and maintenance, not on a leaderboard.

### 3. Two-stage and transformer alternatives
- Faster R-CNN: no strong single-model Chula result found. On a related 5-class egg dataset (Diagnostics 2023, PMC10527934) YOLOv5 beat Faster R-CNN 0.995 vs 0.825 mAP and SSD 0.857. Two-stage detectors appear in the challenge only inside ensembles.
- DETR family: DT4PEIS (Applied Intelligence 2024) uses a DETR detector plus SAM for instance segmentation on Chula; full numbers paywalled. A claim of RT-DETR reaching ~0.93 mIoU on Chula surfaced in search summaries but could not be traced to a paper, so treat it as unverified. Ultralytics supports RT-DETR but recommends it only when a transformer detector is specifically needed. Transformers cost more GPU memory and training time, which matters on Colab.
- Vision-language model (arXiv 2602.13712, 2026): fine-tuned Florence reaches mIoU 0.94, but it is a research direction, not a practical FYP detector.

### 4. Which YOLO version (Ultralytics, as of Oct 2026)
Source: docs.ultralytics.com/models and /compare/yolo26-vs-yolo11, /models/yolo12.
- YOLO26: released 14 Jan 2026. Ultralytics' stated starting point for new projects. NMS-free end-to-end head (optional), DFL removed, MuSGD optimiser, ProgLoss + STAL for small targets. COCO: 26n 40.9 mAP / 38.9 ms CPU; 26s 48.6 / 87.2 ms; 26m 53.1 / 220 ms. About 31% faster CPU inference than YOLO11n. Trains via the standard ultralytics API and CLI; official Colab notebook exists.
- YOLO11: stable mature alternative, checkpoints for every task. COCO: 11n 39.5 / 56.1 ms; 11s 47.0 / 90.0 ms; 11m 51.5 / 183 ms.
- YOLO12: Ultralytics states it is "not recommended for most production workloads" because of training instability, elevated memory and slower CPU throughput. YOLO13: not listed on the Ultralytics models page.
- YOLOv8 and v10: still supported, fine for existing pipelines, no reason to start new work on them.
- YOLO27: "undergoing final R&D", no date.
- Licence: AGPL-3.0 or Enterprise. Fine for an academic FYP; note it if the collaboration ever commercialises.

### 5. Domain gap (for the risk register, not the model choice)
Heliyon 2024 (PMC11636797): a YOLOv5l6 trained on Chula scored F1 0.883 on Chula test but fell to F1 0.527 on in-the-wild phone images (precision 0.45). Adding a classifier stage after detection recovered about 4 points. Expect the same gap on Dr Azdayanti's lab or field images. This is the single most important caveat for the proposal.

## Why YOLO26 over YOLO11 (and why keep YOLO11 close)
- Same Ultralytics API: swapping is a one-string change (`yolo26s.pt` vs `yolo11s.pt`). Train both; report both. Low cost, and a built-in comparison for the report.
- CPU speed matters: supervisor said CPU is fine for single image, GPU better for batch. YOLO26's CPU gains help the free-tier deployment story.
- Small-target changes (STAL) are relevant: Opisthorchis eggs are 41 to 186 px wide in a dataset where images are often cropped and blurred.
- NMS-free head simplifies the backend inference code and threshold slider logic.
- Risk: YOLO26 is nine months old, so no parasite papers use it yet. Mitigation: YOLO11 fallback has published Chula results (INJET 2025).

## Model size for Colab
- Start with the small (s) variant: around 9.5M params, 21 GFLOPs. Also train nano (n) for the CPU story. Only try medium (m) if Colab budget allows after s is done.
- Rough estimate, not from a source: 11,000 images at 640 px, T4, YOLO26s, roughly 3 to 5 minutes per epoch, so 50 epochs is a few hours. Fits a free or Colab Pro session with checkpointing.

## Proposed accuracy target (replaces the rejected 70%)
On a held-out Chula-ParasiteEgg-11 test split, single model, no ensemble:
- Baseline target: mAP@0.5 >= 0.90 and F1 >= 0.90 (both at the operating threshold).
- Stretch: mAP@0.5 >= 0.95, matching published single lightweight YOLO results.
- Also report mAP@0.5:0.95 for comparability with the challenge (top entries 0.90 to 0.925).
Justification: published single-model YOLO results on this dataset sit between 0.96 and 0.99 mAP@0.5; the baseline leaves a margin for Colab compute limits and a first attempt, while being far above the mid-sem 70%. State explicitly that field-image performance is not targeted this semester (Heliyon 2024 shows why).

## Open items
- Confirm with supervisor: YOLO26 acceptable (the kickoff named YOLOv8 to v12 or Faster R-CNN; YOLO26 postdates that list).
- Decide input resolution (640 default vs larger for small eggs) after a first run.
- Decide whether to fine-tune from COCO weights (recommended by all evidence) vs scratch (no).

## Sources
- Anantrasirichai et al. 2022, ICIP challenge paper: https://arxiv.org/abs/2208.06063
- Ensemble entry (YOLOv5 + Cascade R-CNN): https://arxiv.org/abs/2207.01419
- EfficientDet entry: https://arxiv.org/abs/2208.01963
- YAC-Net, Parasites & Vectors 2024: https://pmc.ncbi.nlm.nih.gov/articles/PMC11539555/
- Compact YOLO comparison, Intelligence-Based Medicine 2025: https://www.sciencedirect.com/science/article/pii/S2666521225000158 (abstract via https://www.amrita.edu/publication/comparative-analysis-of-resource-efficient-yolo-models-for-rapid-and-accurate-recognition-of-intestinal-parasitic-eggs-in-stool-microscopy/)
- Modified YOLO11n on Chula, INJET 2025: https://nepjol.info/index.php/injet/article/view/87020
- Out-of-domain drop, Heliyon 2024: https://pmc.ncbi.nlm.nih.gov/articles/PMC11636797
- YOLOv5 vs Faster R-CNN on 5-class eggs, Diagnostics 2023: https://pmc.ncbi.nlm.nih.gov/articles/PMC10527934/
- CoAtNet classification on Chula, Sci Rep 2023: https://pmc.ncbi.nlm.nih.gov/articles/PMC10475085/
- DT4PEIS, Applied Intelligence 2024: https://link.springer.com/article/10.1007/s10489-024-06199-y
- Fine-tuned VLM, arXiv 2026: https://arxiv.org/abs/2602.13712
- Ultralytics models overview: https://docs.ultralytics.com/models/
- YOLO26 vs YOLO11: https://docs.ultralytics.com/compare/yolo26-vs-yolo11/
- YOLO26 model page: https://docs.ultralytics.com/models/yolo26/
- YOLO12 model page (not recommended note): https://docs.ultralytics.com/models/yolo12/
