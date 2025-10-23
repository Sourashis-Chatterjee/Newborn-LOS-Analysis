# Advanced Prediction of Newborn Hospital Length of Stay (LOS) 🏥

This project develops a machine learning framework to accurately predict the hospital Length of Stay (LOS) for newborns, using the New York State SPARCS (Statewide Planning and Research Cooperative System) dataset.

Accurate LOS prediction is a critical task in healthcare. It enables hospitals to optimize resource allocation, manage bed capacity, reduce costs, and ultimately improve patient care planning.

This repository details the end-to-end process: from ingesting and harmonizing a massive, multi-year dataset to building and interpreting an advanced deep learning model designed to outperform established baselines.

## 🎯 Project Objectives

1.  **Ingest & Harmonize:** Combine and clean multiple years of large-scale SPARCS data (2015-2017, 2021-2023), resolving significant data quality and schema drift issues.
2.  **In-Depth EDA:** Conduct a comprehensive Exploratory Data Analysis (EDA) to uncover data anomalies (e.g., `Age Group` inconsistency) and understand the key clinical factors related to newborn LOS.
3.  **Establish Baseline:** Replicate and build a strong baseline model (Random Forest Regressor), based on the findings from reference research.
4.  **Develop Advanced Model:** Implement a Deep Learning (MLP) model with the goal of achieving superior predictive accuracy (lower RMSE) than the baseline.
5.  **Ensure Interpretability:** Apply SHAP (SHapley Additive exPlanations) to the final model to understand the "why" behind its predictions, making it transparent and trustworthy.

## 📊 Dataset

The dataset used is the **SPARCS (Statewide Planning and Research Cooperative System)** from the New York State Department of Health.

* **Source:** [NYS Health SPARCS Data](https://health.ny.gov/statistics/sparcs/de-identified_data.htm)
* **Data Size:** This project combines **6 years** of data (2015-2017 & 2021-2023), totaling millions of patient records.
* **Key Filtering:** The final study population was isolated by filtering for the `APR MDC Description` (Major Diagnostic Category) of **"Newborns and Other Neonates with Conditions Originating in the Perinatal Period."**

## 📓 Repository Structure

* `LOS_EDA.ipynb`: This notebook contains the complete Exploratory Data Analysis. It covers:
    * Loading and harmonizing the 6 individual yearly `.csv` files.
    * Extensive data cleaning and type correction (e.g., `Length of Stay`, `Birth Weight`).
    * Investigation of data quality issues and anomalies.
    * Univariate, bivariate, and multivariate analysis to understand the key predictors.
    * Creation of the final, clean `sparcs_eda.parquet` file.

* `Newborn_Length_of_Stay.ipynb`: This is the main modeling notebook. It includes:
    * Loading the final clean dataset.
    * Final preprocessing and feature selection (based on the reference project).
    * Train-test split and data scaling.
    * Building and evaluating the **Baseline (Random Forest Regressor)**.
    * Building, training, and evaluating the **Deep Learning (MLP) Model**.
    * (Future) SHAP analysis for model interpretation.




