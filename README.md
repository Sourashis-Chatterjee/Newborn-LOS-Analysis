# Newborn Length-of-Stay Prediction using Deep Learning (SPARCS Dataset)

## 📌 Project Overview
This project develops a robust **Deep Learning framework** to predict the **Length of Stay (LOS)** for newborns in New York State hospitals. Leveraging a **six-year composite dataset (2015–2017 & 2021–2023)** from the **SPARCS** database, the study addresses critical challenges in healthcare analytics, including high-dimensional sparse data, extreme outliers, and the need for clinical interpretability.

We propose a custom **Multi-Layer Perceptron (MLP)** architecture optimized with **Huber Loss** and **Log-Transformation**, achieving state-of-the-art performance (RMSE 2.1169) compared to a Random Forest baseline. Furthermore, **SHAP (SHapley Additive exPlanations)** is integrated to provide feature-level transparency for clinical decision support.

---

## 📂 Repository Structure
The project is divided into modular notebooks to ensure reproducibility and logical flow:

| File Name | Description |
| :--- | :--- |
| `01_Newborn_LOS Data preparation.ipynb` | **Data Preparation:** Loads raw CSVs, filters for MDC 15 (Newborns), cleans datatypes, handles missing values, and merges the 6-year dataset. |
| `02_LOS_EDA.ipynb` | **Exploratory Data Analysis:** Visualizes distributions (LOS, Birth Weight), analyzes correlations, and validates clinical assumptions (Severity vs. LOS). |
| `03_Dataset Preparation and ML modelling.ipynb` | **Model Training:** Performs One-Hot Encoding, Scaling, and Log-Transformation. Trains the Random Forest Baseline and the Deep Learning (MLP) Model. |
| `04_Deep Learning arcitecture & SHAP interpretability analysis.ipynb` | **Explainable AI:** Loads the trained Deep Learning model and generates SHAP Summary and Waterfall plots to explain predictions. |

---

## 📊 Dataset
**Source:** New York State Statewide Planning and Research Cooperative System (SPARCS).
* **Scope:** 2015–2017 and 2021–2023 (Composite dataset).
* **Cohort:** Newborns (Major Diagnostic Category 15).
* **Key Features:**
    * **Clinical:** Birth Weight, APR Severity of Illness (1-4), APR Risk of Mortality (1-4).
    * **Administrative:** Admission Type, Source of Payment.
    * **Coding:** CCS Diagnosis Codes & CCS Procedure Codes (441 distinct features).
* **Privacy:** Administrative identifiers (Zip, County, Facility ID) were removed.

---

## 🛠️ Methodology

### 1. Preprocessing Pipeline
* **Filtering:** Strict inclusion of only valid newborn records (MDC 15).
* **Transformation:**
    * **Target:** Log-transformation (y' = log(1+y)) to handle the right-skewed LOS distribution.
    * **Input:** One-Hot Encoding for categorical variables (Diagnosis/Procedures) and Standard Scaling for continuous variables.
* **Outlier Handling:** Trained on the 99th percentile of data (LOS ≤ 42 days) to stabilize learning.

### 2. Model Architecture
* **Baseline:** Random Forest Regressor (100 estimators).
* **Proposed Model:** Deep Neural Network (MLP).
    * **Structure:** 4-layer "Funnel" (256 $\to$ 128 $\to$ 64 $\to$ 32 neurons).
    * **Loss Function:** **Huber Loss** (robust to outliers).
    * **Optimization:** Adam Optimizer, Dropout (0.2), Batch Normalization.

---

## 📈 Experimental Results

| Model | RMSE (Lower is Better) | Status |
| :--- | :--- | :--- |
| Random Forest (Baseline) | 2.1787 | Benchmark |
| **Deep Learning (Proposed)** | **2.1169** | **Best Performing** |

* **Key Finding:** The Deep Learning model successfully captured non-linear interactions between rare procedure codes and birth weight, reducing prediction error for complex cases compared to the baseline.

---

## 🧠 Interpretability (SHAP)
To validate clinical trust, we used **SHAP** to explain the model's logic:
1.  **Global Importance:** `APR Severity of Illness` and `Birth Weight` were identified as the top two drivers of Length of Stay.
2.  **Local Explanation:** For individual patients, the model correctly credits "Minor Severity" as a protective factor (reducing stay) and "Surgical Procedures" as risk factors (increasing stay).

---

## 🚀 How to Run
1.  Clone the repository:
   
2.  **Download the Data:**
    * Due to file size limits, the raw `.csv` files are not included. Please download the "Hospital Inpatient Discharges (SPARCS)" datasets for years 2015-2017 & 2021-2023 from [health.data.ny.gov](https://health.data.ny.gov/).
3.  **Run the Notebooks:**
    * Open the notebooks in **Google Colab** or Jupyter.
    * Run them in numerical order (`01` $\to$ `04`).
    * *Note:* Please ensure the raw CSV files are uploaded to the root directory before running Notebook 01.

---

## 📜 License
This project is for academic purposes. The underlying data is owned by the NYS Department of Health.





