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

The model was trained using YOLOv8n on the SPARK 2022 dataset.

Training configuration:

* Model: YOLOv8n
* Epochs: 10
* Image size: 1024×1024
* Batch size: 6
* Optimizer: AdamW

Validation metrics:

| Metric    | Value |
| --------- | ----- |
| Precision | 0.287 |
| Recall    | 0.321 |
| mAP50     | 0.196 |
| mAP50-95  | 0.123 |

Per-class performance highlights:

* Best performing class: `smart_1` (mAP50 = 0.308)
* Strong results on `double_star`, `cheops`, and `lisa_pathfinder`
* Lower performance on `earth_observation_sat_1` and `debris`

Observations:

* The model successfully learned to localize and classify spacecraft objects.
* Validation predictions show meaningful detections after training.
* Some classes remain challenging due to visual similarity and object orientation.
* Further improvements may be achieved through longer training, hyperparameter tuning, and larger model variants.

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