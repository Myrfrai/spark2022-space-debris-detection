# Spacecraft Detection with YOLOv8

Computer Vision project focused on spacecraft detection in images using YOLOv8 and the SPARK 2022 dataset.

## Project Overview

The goal of this project is to train an object detection model capable of identifying different spacecraft and space-related objects from images.

The project includes:

* Data preprocessing and annotation conversion
* YOLO format dataset generation
* Training and evaluation using YOLOv8n
* Analysis of model performance and predictions

## Dataset

This project uses the **SPARK 2022 Dataset: Spacecraft Detection and Trajectory Estimation** provided by the University of Luxembourg.

Classes:

* cheops
* debris
* double_star
* earth_observation_sat_1
* lisa_pathfinder
* proba_2
* proba_3_csc
* proba_3_ocs
* smart_1
* soho
* xmm_newton

Dataset statistics:

* Train images: 66,000
* Validation images: 22,000
* Total classes: 11

## Project Structure

```text
Spark_Model/
│
├── data/
│   ├── images/
│   ├── labels/
│   ├── labels_sample/
│   └── data.yaml
│
├── notebooks/
│   ├── runs/
│   ├── Part_1Data_Preparation.ipynb
│   └── Part_2Training.ipynb
│
├── README.md
└── .gitignore
```

## Technologies

* Python
* OpenCV
* Pandas
* NumPy
* Matplotlib
* PyTorch
* Ultralytics YOLOv8n

## Results

Two training experiments were conducted using YOLOv8n on the SPARK 2022 dataset.

### Training Configuration

| Parameter | Value |
|-----------|-------|
| Model | YOLOv8n |
| Image Size | 1024 × 1024 |
| Batch Size | 6 |
| Optimizer | AdamW |

### Model Comparison

| Metric | Model A (10 Epochs) | Model B (30 Epochs Total) |
|--------|--------------------:|--------------------------:|
| Precision | 0.287 | **0.431** |
| Recall | 0.321 | **0.513** |
| mAP50 | 0.196 | **0.347** |
| mAP50-95 | 0.123 | **0.243** |

### Training Strategy

**Model A**

- Trained for **10 epochs** from pretrained YOLOv8n weights.
- Used as the baseline model.

**Model B**

- Initialized from the **best weights of Model A**.
- Continued training for an additional **20 epochs**.
- Total effective training: **30 epochs**.

### Performance Improvements

Compared with the initial model, the continued training achieved:

- Precision: **0.287 → 0.431**
- Recall: **0.321 → 0.513**
- mAP50: **0.196 → 0.347**
- mAP50-95: **0.123 → 0.243**

### Per-Class Performance (Final Model)

| Class | mAP50 | mAP50-95 |
|------|------:|---------:|
| cheops | 0.374 | 0.274 |
| debris | 0.209 | 0.148 |
| double_star | **0.456** | **0.316** |
| earth_observation_sat_1 | 0.156 | 0.100 |
| lisa_pathfinder | 0.375 | 0.293 |
| proba_2 | 0.338 | 0.248 |
| proba_3_csc | 0.389 | 0.264 |
| proba_3_ocs | 0.428 | 0.308 |
| smart_1 | 0.449 | 0.281 |
| soho | 0.396 | 0.281 |
| xmm_newton | 0.247 | 0.164 |

### Observations

- Continued training substantially improved all evaluation metrics.
- The model successfully learned to localize and classify spacecraft across all 11 classes.
- Best performance was achieved on **double_star**, **smart_1**, **proba_3_ocs**, and **soho**.
- Lower performance on **earth_observation_sat_1** and **debris** indicates these classes remain challenging due to appearance variability and limited discriminative features.
- Qualitative inspection of validation predictions shows noticeably better localization accuracy after continued training.

## Citation

If you use the SPARK dataset, please cite:

@dataset{rathinam_2022_spark,
author = {Rathinam, Arunkumar and
Gaudilliere, Vincent and
Mohamed Ali, Mohamed Adel and
Ortiz Del Castillo, Miguel and
Pauly, Leo and
Aouada, Djamila},
title = {{SPARK 2022 Dataset : Spacecraft Detection and
Trajectory Estimation}},
month = jun,
year = 2022,
publisher = {Zenodo},
doi = {10.5281/zenodo.6599762},
url = {https://doi.org/10.5281/zenodo.6599762}
}

@article{pauly_2023_lessons,
author = {Pauly, Leo and Jamrozik, Michele Lynn and del Castillo, Miguel Ortiz and Borgue, Olivia and Singh, Inder Pal and Makhdoomi, Mohatashem Reyaz and Christidi-Loumpasefski, Olga-Orsalia and Gaudillière, Vincent and Martinez, Carol and Rathinam, Arunkumar and Hein, Andreas and Olivares-Mendez, Miguel and Aouada, Djamila},
title = {Lessons from a Space Lab: An Image Acquisition Perspective},
journal = {International Journal of Aerospace Engineering},
volume = {2023},
number = {1},
pages = {9944614},
doi = {https://doi.org/10.1155/2023/9944614},
url = {https://onlinelibrary.wiley.com/doi/abs/10.1155/2023/9944614},
year = {2023}
}

## Acknowledgements

This project uses the SPARK 2022 dataset provided by the University of Luxembourg (SnT).
The dataset remains the property of its respective authors and institutions.