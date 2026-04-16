# CSE_881_Project
# Physiological State Classification from Wearable Sensor Data

This project builds a multimodal machine learning pipeline to classify physiological states: **stress, aerobic exercise, and anaerobic exercise**, using wearable sensor data collected from the Empatica E4 wristband.

The full implementation, analysis, and results are provided in the source notebook and rendered reports.

---

## Overview

This project develops an end-to-end pipeline that:

* Processes raw multimodal physiological signals
* Aligns and normalizes time-series data across sensors
* Segments data into fixed-length windows
* Extracts interpretable physiological features
* Trains and evaluates machine learning models

The goal is to accurately distinguish between physiological states using signals such as heart rate, electrodermal activity, and motion data .

---

## Repository Structure

```
.
├── source/        # Source notebook (full pipeline + code)
├── output/        # Rendered reports (HTML and PDF)
├── data/          # Raw wearable sensor dataset
└── README.md
```

---

## Methodology

### Data

The dataset consists of recordings from wearable sensors capturing:

* Blood Volume Pulse (BVP)
* Electrodermal Activity (EDA)
* Accelerometer (ACC)
* Skin Temperature (TEMP)
* Heart Rate (HR)
* Inter-beat intervals (IBI)

Data is collected across three conditions:

* Stress
* Aerobic exercise
* Anaerobic exercise 

---

### Preprocessing Pipeline

The pipeline includes:

1. **Signal Alignment**

   * Resampling all channels to a common frequency (4 Hz)

2. **Normalization**

   * Subject-level z-score normalization to remove baseline differences

3. **Windowing**

   * 30-second sliding windows with 50% overlap

4. **Feature Extraction**

   * Time-domain statistical features
   * Heart Rate Variability (HRV) metrics
   * Motion and physiological summaries

This results in a feature matrix of ~12,000+ windows across subjects .

---

### Models

Three supervised models are trained and compared:

* Logistic Regression
* Random Forest
* Gradient Boosting

Evaluation is performed using **Leave-One-Subject-Out (LOSO) cross-validation**, ensuring generalization to unseen individuals.

---

## Results

* Best model: **Gradient Boosting**
* Accuracy: ~0.71
* Macro F1 Score: ~0.67 

### Key Observations

* **Stress** is the easiest class to detect due to strong EDA + HR patterns
* **Anaerobic exercise** is distinguished by high-intensity motion features
* **Aerobic vs anaerobic** confusion is the main challenge

Feature importance analysis shows that:

* HRV metrics
* Accelerometer energy
* Heart rate statistics

are among the most informative predictors.

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Madison-LH/CSE_881_Project.git
cd CSE_881_Project
```

### 2. Install dependencies

Python environment:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

### 3. Run the pipeline

Open and run:

```
source/CSE881_Final_Report_Notebook.ipynb
```

or view the rendered report:

```
output/CSE881_Final_Report_Notebook.html
output/CSE881_Final_Report_Notebook.pdf
```

---

## 📁 Data

* Raw data is stored in the `data/` directory
* Data follows the Empatica E4 export format (CSV per signal type)
* Each subject/session is stored in separate folders

---

## Outputs

The `output/` folder contains:

* Fully rendered HTML report
* PDF version of the final analysis

See full report:

CSE881_Final_Report_Notebook.html
CSE881_Final_Report_Notebook.pdf

---

## Notes

* The notebook in `source/` contains the full reproducible pipeline
* The `output/` files are final, presentation-ready results
* Cross-validation is subject-independent to avoid data leakage

---

## Authors

* Randal Burks
* Nyla Blagrove
* Madison Honore

Michigan State University — CSE 881 (Data Mining)

---
