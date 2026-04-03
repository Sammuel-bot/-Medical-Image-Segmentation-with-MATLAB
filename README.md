# 🧠 Medical Image Segmentation with MATLAB

> Visualizing and labeling 2D/3D medical image data using MATLAB's Medical Image Labeler app and Image Processing Toolbox.

![MATLAB](https://img.shields.io/badge/MATLAB-Online-orange?style=flat-square&logo=mathworks)
![Toolbox](https://img.shields.io/badge/Image%20Processing%20Toolbox-required-blue?style=flat-square)
![Format](https://img.shields.io/badge/Formats-DICOM%20%7C%20NIfTI-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

---

## Overview

Hands-on medical image segmentation using MATLAB's Medical Image Labeler app. Covers importing DICOM and NIfTI files, annotating anatomical structures across 2D slices and 3D volumes, exporting labeled ground truth data, and generating animated GIF visualizations.

Completed as a lab project at the **University of Ghana, School of Engineering Sciences**.  
Scripts updated to run on **MATLAB Online** using built-in sample data — no file uploads needed.

---

## Results

### 3D CT Volume — Sagittal Plane
| Original | Labeled |
|---|---|
| ![Original Sagittal](sample_output/Original_Sagittal.jpeg) | ![Labeled Sagittal](sample_output/Labeled_Sagittal.jpeg) |

### 3D CT Volume — Coronal Plane
| Original | Labeled (Heart) | Labeled (Lungs) |
|---|---|---|
| ![Original Coronal](sample_output/Original_Coronal.jpeg) | ![Labeled Coronal Heart](sample_output/Labeled_Coronal_Heart.jpeg) | ![Labeled Coronal Lungs](sample_output/Labeled_Coronal_Lungs.jpeg) |

### 3D Volume Render
| Original | Labeled |
|---|---|
| ![Original Volume](sample_output/Original_Volume_Image.jpeg) | ![Labeled Volume](sample_output/Labeled_Volume_Image.jpeg) |

### Ultrasound — Human Heart (2D)
| Original | Labeled |
|---|---|
| ![Original Ultrasound](sample_output/Original_Ultrasound.jpeg) | ![Labeled Ultrasound](sample_output/Labelled_Ultrasound.jpeg) |

### CT Transverse Slice — Lungs
| Original | Labeled |
|---|---|
| ![Original CT Lungs](sample_output/Original_CT_Lungs.jpeg) | ![Labeled CT Lungs](sample_output/Labeled_CT_Lungs.jpeg) |

> Labels include: heart, lungs, vertebral column, cardiac ventricles, and tumors

## Repo Structure

```
matlab-medical-labeler/
├── scripts/
│   ├── load_and_visualize.m     # Load & display MRI slices (works in MATLAB Online)
│   ├── polygon_roi_label.m      # Draw polygon ROIs and export masks
│   └── export_gif.m             # Export animated GIF of volume slices
├── sample_output/               # Screenshots and GIFs from the original lab
└── README.md
```

---

## Skills Demonstrated

| Skill | Details |
|---|---|
| **Medical Image I/O** | Read DICOM series and NIfTI volumes |
| **Multi-planar Visualization** | Sagittal, coronal, and transverse slice display |
| **Interactive Annotation** | Polygon ROI + manual interpolation across 10+ frames per series |
| **3D Volume Segmentation** | Labeled heart, lungs, vertebral column across volumetric CT data |
| **Ground Truth Export** | Exported annotations as `groundTruthMedical` objects for ML pipelines |
| **GIF Animation** | Generated and exported animated slice-through visualizations |

---

## Running the Scripts (MATLAB Online)

All scripts use MATLAB's built-in `mri` dataset — no uploads needed.

**1. Visualize MRI slices**
```matlab
% Paste load_and_visualize.m into the editor and hit Run
% You'll get: multi-planar view, montage, and 3D isosurface
```

**2. Draw a Polygon ROI**
```matlab
% Paste polygon_roi_label.m and hit Run
% Draw your polygon on the image, double-click inside to confirm
% Mask saves automatically to MATLAB Drive
```

**3. Export a GIF**
```matlab
% Paste export_gif.m and hit Run
% brain_slices.gif saves to MATLAB Drive
% Download it from drive.matlab.com
```

---
## Background

Medical image labeling is a critical step in building AI-powered diagnostic tools. Labeled datasets (ground truth) are used to train deep learning segmentation models — such as U-Net — that can automatically identify anatomical structures in clinical scans. This project provided hands-on experience with the full annotation pipeline used in real medical AI workflows.

---
## Requirements

- [MATLAB Online](https://matlab.mathworks.com) (free account) — or MATLAB R2023a+
- Image Processing Toolbox

---

## References

- [MATLAB Medical Image Labeler Docs](https://www.mathworks.com/help/images/medical-image-labeler-app.html)
- Yang et al., "Classification of Medical Image Notes for Image Labeling by Using MinBERT," *Tsinghua Science and Technology*, 2023. [DOI](https://doi.org/10.26599/TST.2022.9010012)

