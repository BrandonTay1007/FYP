# ParaShot: Image format research

Date: 13 Oct 2026. Questions: which file formats do brightfield faecal-smear workflows and Chula-ParasiteEgg-11 actually use, and which single internal raster should a YOLO or RF-DETR detector store after upload?

Scope already in the pitch notes: one uploaded field-of-view still, no whole-slide imaging, no stitching. ParaShot supports screening of parasite eggs on faecal-smear stills. The team has no trained model results.

Team notes, not a survey of labs: the supervisor in early Oct 2026 asked for several formats (PNG, TIFF), with the backend converting and resizing and a test for data loss. The 9 Oct 2026 meeting asked to standardise on one image format, with resize required. Draft FR1 (PROPOSED) accepts PNG, TIFF, and JPEG, one or many, up to a batch cap. Draft FR2 (PROPOSED) converts and resizes to one standard format, verified for no data loss.

## Recommendation (PROPOSED)

Accept `.jpg` / `.jpeg`, `.png`, and `.tif` / `.tiff` at upload. JPEG is a usual camera and phone-through-eyepiece output, and it is the container IEEE DataPort lists for Chula-ParasiteEgg-11. TIFF is the still format Olympus cellSens, Zeiss ZEN, Nikon NIS-Elements, and Leica Acquire tell a user to save or export. PNG is an export option in those same programs. No parasitology methods page opened here says a diagnostic bench routinely captures PNG.

Store one internal file: 8-bit RGB PNG. Train and run on that file. The detector does not detect "in JPEG" or "in PNG". Ultralytics decodes the file, letterboxes it, and runs on an RGB tensor. RF-DETR's run page takes a file path or an RGB frame. The format choice is about what was destroyed before that array exists.

Reword FR2: decode each upload once and store 8-bit RGB PNG. When the source is PNG, or TIFF with no compression or with LZW, the stored pixels must match the decoded pixels. When the source is JPEG, or TIFF that uses JPEG compression, the source has already discarded detail; do not compress it as JPEG again. Resize to the detector input is a separate, declared resample, and it is not part of the lossless check. Keep the original filename, and keep magnification and scale only when the upload or the user supplies them.

Do not promise OME-XML fidelity, 16-bit pixels through to the detector, whole-slide DICOM, or proprietary vendor files (Olympus VSI, Nikon ND2, Leica LIF, Zeiss CZI). Nothing opened here shows that the screening users hand those files over without first exporting a still.

## Evidence

### 1. What a brightfield bench can emit

Vendor camera software and the community container, from the pages opened:

| Software or container | Native or recommended store | Also writes or exports | Source |
|---|---|---|---|
| Olympus cellSens | User manual: recommended save is TIF or VSI. TIF and VSI keep the image information, including HDR entries. Other formats lose most of that information on time stacks, Z-stacks, and multi-channel images. | Product page lists JPEG, JPEG 2000, TIFF, BMP, AVI, PNG, VSI, PSD, Big TIFF, OIR. Also "Import OME tiff". | Evident cellSens page; cellSens user manual |
| Nikon NIS-Elements | ND2 for images the user will edit. ND2 holds hardware settings and experiment conditions. | Open/save list includes JPG, TIFF, PNG, OME-TIFF, JPEG 2000, BMP, GIF. PNG: interlaced PNG is not supported. ShuttlePix microscopes "produce standard TIFF and JPEG files". | NIS-Elements supported formats |
| Leica | Bio-Formats: LAS AF native file is LIF (`.lif`). LAS X is the free reader named on that page. The LAS X pages opened do not list a still-export menu. | Leica Acquire 3.4.6 (Jan 2021), for Leica digital microscope cameras: "TIFF (8 & 16 bit). JPEG (8 bit only) PNG (8 & 16 bit)". | Bio-Formats LIF page; Leica Acquire user manual |
| Zeiss ZEN | "It is recommended to work with the Carl Zeiss Image format (.czi)." CZI has lossless compression and metadata for reusing imaging parameters. | Export list: JPEG, BMP, TIFF, Big TIFF, PNG, JPEG XR, SUR. TIFF compression: None, LZW (lossless), ZIP (lossless). BigTIFF also has a Lossy option (JPEG XR). "Convert to 8 Bit" exists for TIFF, BigTIFF, PNG, and JPEG XR. | ZEN file-type section |
| OME-TIFF | Community container: a TIFF or BigTIFF plus OME-XML in the ImageDescription tag of the first IFD. Extensions `.ome.tif`, `.ome.tiff`, and BigTIFF `.ome.tf2`, `.ome.tf8`, `.ome.btf`. Pixels stay in the TIFF. Any TIFF reader can read the pixels; an OME-aware reader is needed for the XML. | Pyramidal levels may use LZW, JPEG, or JPEG 2000. JPEG there is not lossless. | OME-TIFF specification, OME model 6.3.1 |
| Bio-Formats 8.3.0 | Reads 163 formats. Plain containers it names: TIFF (`.tiff`, `.tif`, `.tf2`, `.tf8`, `.btf`), JPEG (`.jpg`), PNG (`.png`), OME-TIFF. Vendor files that are not those: cellSens VSI (`.vsi`), Nikon ND2 (`.nd2`), Leica LIF (`.lif`), Zeiss CZI (`.czi`), Zeiss ZVI (`.zvi`), Olympus FluoView (`.oib`, `.oif`). Several vendor rows are themselves TIFF plus a companion (Nikon Elements TIFF, Olympus FluoView TIFF, Zeiss AxioVision TIFF). | The supported-formats table names extensions. The rating columns did not survive the page conversion, so this note does not repeat pixel or metadata ratings. | Bio-Formats supported formats |

Inference: a research microscope attached to cellSens, NIS-Elements, LAS X, or ZEN usually stores a proprietary file or a TIFF. JPEG and PNG are export choices. A faecal-smear bench that only has a camera body or a phone on the eyepiece is a different path, and the parasitology papers below describe that path.

Phone through the eyepiece, from primary parasitology papers:

- Chula acquisition (Anantrasirichai et al. 2022): images came from a Canon EOS 70D on Olympus BX53 microscopes, a Nikon DS-Fi2 on Nikon Eclipse Ni microscopes, and a Samsung Galaxy J7 Prime, iPhone 12, and iPhone 13 "with either 10× times eyepieces lens" of those two microscopes. The paper states that these devices produce different resolutions, lighting, and settings. It does not name the file each camera wrote.
- Dacal et al., PLOS Neglected Tropical Diseases (Kato-Katz, Leica DM-2000): a 3D-printed adapter put a phone on the eyepiece. "Images were acquired in the JPG format with a resolution of 12 Mpx." Objective 10×, stated total magnification 100×. Phones: Xiaomi Pocophone F1 and Bq Aquaris X2. This is a digitisation study, not a claim that every diagnostic bench does this.

PNG: cellSens, NIS-Elements, ZEN, and Leica Acquire can write PNG. None of the parasitology methods pages opened here say the bench's routine capture file is PNG.

Whole-slide DICOM is a different object. DICOM Supplement 145 (WG-26, final text 24 Aug 2010) defines a whole-slide microscopy image for storing very large tiled slide scans in a PACS. It describes slide scanners and pan-and-zoom images. It does not describe a Kato-Katz eyepiece camera. A Kato-Katz study that did scan whole smears (von Bahr et al., Scientific Reports, 27 Jun 2025, PMC12205037) saved the scan as TIFF on a Grundium Ocus scanner, then converted to JPEG tiles. That workflow is whole-slide imaging. ParaShot's notes already exclude it.

### 2. What Chula-ParasiteEgg-11 actually ships as

Two primary sources. They do not say the same thing about the container.

IEEE DataPort, DOI 10.21227/vyh8-4h71, record last updated 11 Jul 2025. The field "Data Format" is `*.jpg *.json *.zip`. Files listed: `Chula-ParasiteEgg-11.zip` (8.49 GB), `Chula-ParasiteEgg-11_test.zip` (2.28 GB), `test_labels_200.json`. The page does not state bit depth, colour mode, pixel dimensions, or magnification.

Anantrasirichai et al. 2022, arXiv 2208.06063 (open version; the IEEE ICIP PDF was not opened). What that HTML states:

- 13,750 faecal-smear images. Training is 1,000 images per class. Testing is about 250 per class. Some test images have two or more egg types. Some have none. Labels are bounding boxes.
- Visual examination used "a light microscope with 40× magnification". Capture devices are the Canon, Nikon, and phone list in section 1, including "10× times eyepieces". The paper does not state the objective used for the camera frames, and it does not give micrometres per pixel.
- "These result in different resolutions." It does not give the pixel width or height of the image files.
- Table 1 gives egg size in micrometres and egg width in pixels. The pixel column runs from 41–186 (Opisthorchis viverrine) to 170–806 (Fasciolopsis buski). Those are egg widths, not file dimensions.
- Degradation is applied per colour channel (Gaussian noise) and on the S channel of HSV. The paper therefore treats the images as colour. It does not state 8-bit or 16-bit.
- The paper does not name JPG, PNG, TIFF, or any other container. The container claim comes from the DataPort record, not from the paper.

Inference: training copies are JPEG stills of uneven size, already colour, already through whatever compression the cameras and the DataPort JPG used. Matching that with another JPEG save adds a generation. Matching it with PNG keeps the pixels the JPEG decoder already produced.

### 3. What "convert with no data loss" can honestly mean

JPEG, ITU-T T.81 (the copy at `w3.org/Graphics/JPEG/itu-t81.pdf`):

- DCT-based processes are lossy. The baseline sequential process, required in DCT decoders, takes 8-bit samples in each component.
- Each component has horizontal and vertical sampling factors, so components need not share a grid. Annex K's example luminance and chrominance quantisation tables "are derived empirically using luminance and chrominance and 2:1 horizontal subsampling." That annex is informative, not a rule that every file uses 2:1. A camera JPEG has already quantised DCT coefficients. Decoding it cannot return the sensor samples. Encoding the decoded image as JPEG again quantises a second time.

PNG, W3C PNG Specification, Third Edition (`https://www.w3.org/TR/png-3/`):

- "Lossless, portable, well-compressed storage." Filtering and compression "should preserve all information." The only compression method defined is deflate.
- Bit depth is bits per sample, not per pixel. Truecolor allows 8 or 16. Greyscale allows 1, 2, 4, 8, or 16. A 16-bit PNG is a legal file. Whether the detector keeps those bits is a separate question (section 4).

TIFF, Adobe TIFF 6.0:

- Baseline compression tag values include 1 (no compression) and 32773 (PackBits). PackBits is often a poor fit for continuous-tone images; the spec says to leave those uncompressed.
- Section 13, compression scheme 5, is LZW. "LZW is lossless. All information is preserved."
- Section 22 adds JPEG inside TIFF. The baseline process there is DCT, 8 bits per component, and "inherently introduces error into the reconstructed image and cannot be utilized for lossless compression."

So "TIFF" is not a lossless promise. A TIFF can be uncompressed, LZW, or JPEG-compressed. "PNG" is lossless relative to the samples it was given. "JPEG" is not lossless relative to the camera's source. OME-XML lives in a TIFF tag. Writing a PNG of the first plane drops that XML even when the pixels are copied exactly.

Resize is a resample. ZEN's own export page describes its resize as point-sampling from a pyramid tile. Ultralytics letterbox is a scale-and-pad to `imgsz` (section 4). Neither operation is reversible. A test that requires the resized file to equal the upload will fail for every format.

### 4. What object-detection training and inference actually use

Ultralytics, local training and predict, from docs.ultralytics.com:

- Image suffixes in `IMG_FORMATS`, stated on the predict page and the simple-utilities page: `.avif`, `.bmp`, `.dng`, `.heic`, `.heif`, `.jp2`, `.jpeg`, `.jpg`, `.mpo`, `.png`, `.tif`, `.tiff`, `.webp`. The COCO12-Formats page is a 12-image loader test and lists the same set except that `.heif` has no sample image. Labels for detection are YOLO `*.txt` files, one per image, `class x_center y_center width height`, normalised 0 to 1. The dataset guide also accepts COCO JSON via `convert_coco`, and an NDJSON alternative. It does not say that a YOLO dataset must be stored as JPEG.
- After load, the container is finished. `BasePredictor.preprocess` takes a list of BGR `uint8` arrays shaped `(H, W, 3)`, letterboxes them, and returns a tensor of shape `(N, 3, H, W)`. Channel order is flipped from BGR to RGB, then values are divided by 255 into float. The predict page calls `imgsz` the letterbox target. Default shown there is 640. An integer is a square target. Training "accepts only a single integer `imgsz`". Aspect ratio is kept; padding fills the rest. With `rect=True` the tensor can be smaller than `imgsz`.
- 16-bit: the documented `imread` path right-shifts `uint16` and casts to `uint8` ("16-bit images keep their high byte as 8-bit"), unless the read flag includes `IMREAD_ANYDEPTH`. A 16-bit TIFF or PNG does not arrive at this preprocess as 16-bit.
- EXIF: the Pillow fallback applies `ImageOps.exif_transpose` and converts to RGB before handing BGR to OpenCV. The comment says this matches upright JPEG decoding. The page does not say every suffix gets that transpose.
- Ultralytics Platform is a different product. Its dataset page says most uploads are re-encoded as JPEG at quality 92, while TIFF originals are stored as uploaded. That re-encode is a second lossy save. It is not what the local `model.train` pages describe.

RF-DETR, `rfdetr.roboflow.com` (latest):

- Training labels: COCO JSON (`train/_annotations.coco.json`) or YOLO (`data.yaml` or `data.yml`, plus a training image directory). COCO wins if both are present. That matches the model note. The dataset-formats page does not list image extensions. Its directory examples use `image1.jpg` and say "other image files". It does not name PNG or TIFF.
- Inference examples: `model.predict` on a `.jpg` URL, or on an RGB frame after `cv2.cvtColor(..., COLOR_BGR2RGB)`. The page states a fixed input resolution per checkpoint: Nano 384×384, Small 512×512, Medium 576×576, Large 704×704, XLarge 700×700, 2XLarge 880×880. It does not describe the tensor inside `predict`. The ONNX export example opens an image with Pillow, converts to RGB, resizes, and applies ImageNet normalisation. The TFLite calibration note lists JPEG, PNG, BMP, and WebP for a calibration directory. That list is for export calibration, not for the training loader.
- The run page does not mention 16-bit, EXIF, or a preferred training container.

COCO, as a check on "detection datasets are JPEG": the COCO download page lists image archives (for example "2017 Train images [118K/18GB]") and a bucket `gs://images.cocodataset.org/val2017`. It does not name a container. The ECCV 2014 HTML opened here does not name JPEG either. This note does not say that COCO ships as JPEG.

Inference, marked as such: both code paths decode to an array and then resize. A batch of hundreds pays that decode either way. Neither docs page gives a decode-time comparison of PNG and JPEG, so this note does not rank them on speed. The quality difference is the DCT quantisation already inside a JPEG, and any further JPEG encode, not the choice of suffix after the array exists.

### 5. Three choices, side by side

| Choice | PROPOSED | Why |
|---|---|---|
| (a) Accept from the microscopist | `.jpg`, `.jpeg`, `.png`, `.tif`, `.tiff` | JPEG: DataPort Chula files, and Dacal's Kato-Katz phone capture. TIFF: the still save cellSens, ZEN, NIS-Elements, and Leica Acquire document. PNG: those programs can write it; no methods page here shows it as the routine capture. |
| Leave for a later export step | `.vsi`, `.nd2`, `.lif`, `.czi`, `.ome.tif`, `.dcm` | Real microscope files. Reading them means a vendor or Bio-Formats stack, and OME or DICOM metadata this product is not set up to keep. Supplement 145 DICOM is whole-slide. |
| (b) One stored file, and the training copy | 8-bit RGB PNG | Lossless given the samples it receives. Ultralytics lists `.png`. Storing JPEG would run T.81 a second time on every PNG or lossless TIFF. Chula JPG is decoded once; the PNG stores those decoded samples. RF-DETR's training page does not name PNG. Confirm with one load before implementation. If that load fails, feed the decoded RGB array. Do not fall back to a second JPEG. |
| (c) What the detector consumes | Resized RGB tensor | Ultralytics: `(N, 3, H, W)`, float, 0 to 1, letterboxed to `imgsz` (training: one integer; predict default shown as 640). RF-DETR checkpoints have their own square size (384 to 880 on the run page). 16-bit does not survive the Ultralytics `imread` path documented above. |

Metadata worth keeping beside the pixels, as ordinary fields, not inside the PNG:

- Original filename, so a case can be traced to the microscopist's file.
- Magnification, only if the user or the file states it. Chula's paper states 40× for the visual exam and 10× eyepieces for the phone captures. It does not give one magnification for every file.
- Scale in micrometres per pixel, only if present. OME-XML can carry physical size. A camera JPEG often does not. Chula's paper gives egg size in micrometres and in pixels, and does not state micrometres per pixel.
- A flag that the source was JPEG or JPEG-in-TIFF, so a later "no data loss" check is not applied to a file that could not pass it.

## Takeaways

- Usual files to plan for are JPEG from a camera or a phone on the eyepiece, and TIFF from microscope software. Proprietary files are what that software prefers to keep, and they are an export problem, not an upload list for this semester.
- Chula, as distributed, is JPG plus JSON, inside zip. The paper never says so. The paper also never states bit depth or the pixel size of the files.
- "No data loss" is true for a PNG or a lossless TIFF copied to 8-bit RGB PNG without resize. It is false for JPEG sources, for JPEG-compressed TIFF, and for any required resize.
- The model never sees the container. Pick PNG so the array is not damaged again before letterbox. Pick the detector's `imgsz` separately, and say that the resample is declared.
- 16-bit, OME-XML, and whole-slide DICOM are real microscopy features. The Ultralytics loader documents an 8-bit conversion, OME-XML is not in a PNG, and Supplement 145 is a slide scan. Leave all three out of the pitch promise.

## Sources

Pages opened on 13 Oct 2026:

- OME data model 6.3.1 contents: https://docs.openmicroscopy.org/ome-model/6.3.1/index.html
- OME-TIFF format page: https://docs.openmicroscopy.org/ome-model/6.3.1/ome-tiff/
- OME-TIFF specification: https://docs.openmicroscopy.org/ome-model/6.3.1/ome-tiff/specification.html
- Bio-Formats 8.3.0 supported formats: https://bio-formats.readthedocs.io/en/v8.3.0/supported-formats.html
- Bio-Formats Leica LIF: https://bio-formats.readthedocs.io/en/v8.3.0/formats/leica-lif.html
- Evident cellSens, compatible formats: https://evidentscientific.com/en/products/software/cellsens
- cellSens user manual (TIF or VSI recommended): https://bpb-us-e2.wpmucdn.com/sites.ua.edu/dist/1/35/files/2024/07/olympus_cellsens_user_manual.pdf
- Nikon NIS-Elements supported formats: https://www.nisoftware.net/NikonSaleApplication/Help/Docs-BR/eng_br/image.formats.html
- Zeiss ZEN export file types: https://knowledge.zeiss.com/rms/en/zen/basic-concepts/image-processing/image-processing-functions/export-import/image-export/file-type-section
- Leica Acquire 3.4.6 user manual: https://downloads.leica-microsystems.com/DMS1000/User%20Manual/Leica%20Acquire%203.4.6%20User%20Manual.pdf
- DICOM Supplement 145 final text: https://dicom.nema.org/MEDICAL/Dicom/Final/sup145_ft.pdf
- ITU-T T.81 JPEG: https://www.w3.org/Graphics/JPEG/itu-t81.pdf
- W3C PNG specification, third edition: https://www.w3.org/TR/png-3/
- Adobe TIFF 6.0: https://download.osgeo.org/libtiff/doc/TIFF6.pdf
- IEEE DataPort Chula record: https://ieee-dataport.org/competitions/parasitic-egg-detection-and-classification-microscopic-images
- Anantrasirichai et al. 2022, arXiv HTML: https://ar5iv.labs.arxiv.org/html/2208.06063
- Dacal et al., phone JPG on Kato-Katz: https://journals.plos.org/plosntds/article?id=10.1371/journal.pntd.0009677
- von Bahr et al., whole-slide Kato-Katz TIFF then JPEG tiles: https://pmc.ncbi.nlm.nih.gov/articles/PMC12205037/
- Ultralytics detection datasets: https://docs.ultralytics.com/datasets/detect
- Ultralytics COCO12-Formats: https://docs.ultralytics.com/datasets/detect/coco12-formats
- Ultralytics predict, suffixes and `imgsz`: https://docs.ultralytics.com/modes/predict
- Ultralytics `IMG_FORMATS`: https://docs.ultralytics.com/usage/simple-utilities
- Ultralytics `imread` (16-bit shift, EXIF transpose): https://docs.ultralytics.com/reference/utils/patches
- Ultralytics preprocess tensor: https://docs.ultralytics.com/reference/engine/predictor
- Ultralytics Platform re-encode note: https://docs.ultralytics.com/platform/data/datasets
- RF-DETR dataset formats: https://rfdetr.roboflow.com/latest/learn/train/dataset-formats/
- RF-DETR detection run: https://rfdetr.roboflow.com/latest/learn/run/detection/
- COCO download page (no container named): https://cocodataset.org/dataset/download.htm
- COCO paper HTML (no JPEG named): https://arxiv.org/html/1405.0312
