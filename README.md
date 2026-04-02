# 🧠 Medical Image Segmentation with MATLAB

> Visualizing and labeling 2D/3D medical image data using MATLAB's Medical Image Labeler app and Image Processing Toolbox.

![MATLAB](https://img.shields.io/badge/MATLAB-R2023a%2B-orange?style=flat-square&logo=mathworks)
![Toolbox](https://img.shields.io/badge/Medical%20Imaging%20Toolbox-required-blue?style=flat-square)
![Format](https://img.shields.io/badge/Formats-DICOM%20%7C%20NIfTI-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

---

## Overview

This project demonstrates hands-on medical image segmentation using MATLAB. It covers importing DICOM and NIfTI files, manually annotating anatomical structures across 2D slices and 3D volumes, exporting labeled ground truth data for machine learning, and generating animated visualizations.

Originally completed as a lab/group project at the University of Ghana, School of Engineering Sciences.

---

## What's in this repo

```
matlab-medical-labeler/
├── scripts/
│   ├── load_and_visualize.m     # Load DICOM/NIfTI files and display slices
│   ├── polygon_roi_label.m      # Draw polygon ROIs and create masks
│   └── export_gif.m             # Export animated GIF of labeled volume
├── sample_output/
│   └── (place your exported .mat and .gif files here)
├── docs/
│   └── lab_report.pdf           # Original lab report
└── README.md
```

---

## Skills Demonstrated

| Skill | Details |
|---|---|
| **Medical Image I/O** | Read DICOM series and NIfTI volumes using `dicomreadVolume`, `niftiread` |
| **Multi-planar Visualization** | Display sagittal, coronal, and transverse slices from 3D volumes |
| **Interactive Annotation** | Used Polygon ROI and manual interpolation to label 10+ frames per series |
| **3D Volume Segmentation** | Labeled heart, lungs, and vertebral column across volumetric CT data |
| **Ground Truth Export** | Exported annotations as `groundTruthMedical` objects (`.mat`) for ML pipelines |
| **GIF Animation** | Generated and exported animated slice-through visualizations |

---

## Labeled Structures

- **3D CT Volume** — Heart, lungs, vertebral column (sagittal + coronal planes)
- **Ultrasound (2D)** — Cardiac ventricles across 10 frames using manual interpolation
- **CT Transverse Slice** — Lung boundaries via Polygon ROI

---

## Requirements

- MATLAB R2023a or later
- [Medical Imaging Toolbox](https://www.mathworks.com/products/medical-imaging.html)
- Image Processing Toolbox

Install the Medical Imaging Toolbox from the MATLAB Add-On Explorer or MathWorks website.

---

## Usage

### 1. Load and visualize a DICOM volume

```matlab
% Load a DICOM series
[V, spatial] = dicomreadVolume('path/to/dicom_folder/');

% View sagittal and coronal slices
sagittal = squeeze(V(128, :, :));
coronal  = squeeze(V(:, 128, :));

figure;
subplot(1,2,1); imshow(sagittal, []); title('Sagittal');
subplot(1,2,2); imshow(coronal,  []); title('Coronal');
```

### 2. Open Medical Image Labeler

```
Apps → Image Processing and Computer Vision → Medical Image Labeler
```

- **Volume session** for 3D NIfTI/DICOM stacks
- **Image session** for 2D files
- Use **Polygon ROI** to outline regions of interest
- Use **Manual Interpolation** (right-click → Interpolate) to fill labels between keyframes

### 3. Export labeled data

After labeling, export from the app:

```
File → Export Labels → groundTruthMedical
```

Then load it in MATLAB:

```matlab
load('groundTruthMedical.mat');  % loads 'gTruth'
gTruth.LabelDefinitions          % inspect label names
```

### 4. Generate a GIF

```matlab
% Run the export script
run('scripts/export_gif.m')
% Output: labeled_volume.gif
```

---

## Results

| Image | Plane | Structures Labeled |
|---|---|---|
| 3D CT Volume | Sagittal | Vertebral column |
| 3D CT Volume | Coronal | Heart, Lungs |
| Ultrasound | 2D (10 frames) | Cardiac ventricles |
| CT Slice | Transverse | Lungs |

> Screenshots of labeled outputs are in `sample_output/`.

---

## Background

Medical image labeling is a critical step in building AI-powered diagnostic tools. Labeled datasets (ground truth) are used to train deep learning segmentation models — such as U-Net — that can automatically identify anatomical structures in clinical scans. This project provided hands-on experience with the full annotation pipeline used in real medical AI workflows.

---

## References

- [MATLAB Medical Image Labeler Documentation](https://www.mathworks.com/help/images/medical-image-labeler-app.html)
- Yang et al., "Classification of Medical Image Notes for Image Labeling by Using MinBERT," *Tsinghua Science and Technology*, 2023. [DOI](https://doi.org/10.26599/TST.2022.9010012)
