# MorphoScale_Path_LJJ
MorphoScale-Path addresses the limited field-of-view issue in fine-grained OED morphological classification. It freezes a Virchow2 encoder, extracts multi-scale patches (40×/20×/10×) from shared tissue regions, and fuses them via scale-aware, morphology-conditioned routing.

## Full Source Code & Trained Weights

Due to the large file size (approximately 300MB, including trained model
weights and WSI visualization data), the complete source code, trained
model weights, final test results, and visualization viewer have been
packaged and uploaded as a GitHub Release. Please click the link below to
view and download:

📦 [Download MorphoScale_Path_Code.zip](https://github.com/lijiangjie50-png/MorphoScale_Path_LJJ/releases/tag/v1.0)

**Contents:**

- **`code/`** — Complete source code (222 files: 168 Python scripts, 29
  shell scripts, 19 config files) covering data processing, model
  training, evaluation, and ablation experiment pipelines.
- **`weights/`** — Trained model checkpoints, organized into three parts:
  - `morphoscale/`: 21 checkpoints spanning the E0–E8 main ablation chain
    and several variants (E6_EMA, E7_FIX, E7_FIX2, E8_FIX, E8_FIX2, the
    S2 series, etc.)
  - `baselines/`: linear-probe head weights for the 13 comparison
    pathology foundation models (CTransPath, UNI2-h, Virchow2, GPFM,
    Phikon, Phikon-v2, CONCHv1.5, HIPT-ViT256, Midnight, Path Foundation,
    PathoDuet, EXAONEPath, GenBio-PathFM)
  - `sota_plus/`: the final SOTA+ system's probability-fusion recipe
    (per-label blend configuration, not a single checkpoint)
- **`results/sota_frozen_test.json`** — Final headline result of the
  SOTA+ system on the held-out frozen test set (macro ROC-AUC, macro F1,
  macro recall), with SHA-256 checksums of the archived prediction files.
- **`viewer/`** — A browser-based WSI visualization tool for whole-slide
  morphology prediction, patch-type mapping, multi-label overlap
  counting, and MCSR (morphology-conditioned scale routing) projection,
  corresponding to Section 5.6.2 of the thesis.

**Note:** All checkpoint files had training-time metric fields (e.g.
`val_macro_roc_auc`) stripped before packaging; only the weight tensors
and model/architecture configuration are retained. Weight tensors
themselves are bit-identical to the original files. Package integrity
can be verified via `checks/SHA256SUMS.txt`.

---

## WSI Visualization Viewer

The browser-based interactive viewer corresponding to Section 5.6.2 of
the thesis has been packaged and released separately. Please click the
link below to view and download:

📦 [Download WSI_Morphology_GUI_EN.zip](https://github.com/lijiangjie50-png/MorphoScale_Path_LJJ/releases/tag/gui-v1)

**Usage:** Download and unzip, then open `index.html` in a browser (or
run `start_gui.command` / `start_gui.bat`).

**Contents:** Covers the 6 held-out test slides with morphology
prediction heatmaps, patch-level classification maps, multi-label
overlap counting, and MCSR (morphology-conditioned scale routing)
weight visualization.
