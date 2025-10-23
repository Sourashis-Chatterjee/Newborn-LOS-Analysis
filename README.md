# Analysis of Newborn Hospital Length of Stay (LOS) 🏥

Accurate LOS prediction is a critical task in healthcare. It enables hospitals to optimize resource allocation, manage bed capacity, reduce costs, and ultimately improve patient care planning.

## 🎯 Project Objectives

1.  **Ingest & Harmonize:** Combine and clean multiple years of large-scale SPARCS data (2015-2017, 2021-2023), resolving significant data quality and schema drift issues.
2.  **In-Depth EDA:** Conduct a comprehensive Exploratory Data Analysis (EDA) to uncover data anomalies (e.g., `Age Group` inconsistency) and understand the key clinical factors related to newborn LOS.

## 📊 Dataset

The dataset used is the **SPARCS (Statewide Planning and Research Cooperative System)** from the New York State Department of Health.

* **Source:** [NYS Health SPARCS Data](https://health.ny.gov/statistics/sparcs/de-identified_data.htm)
* **Data Size:** This project combines **6 years** of data (2015-2017 & 2021-2023), totaling millions of patient records.
* **Key Filtering:** The final study population was isolated by filtering for the `APR MDC Description` (Major Diagnostic Category) of **"Newborns and Other Neonates with Conditions Originating in the Perinatal Period."**

## 📓 Repository Structure

* `Newborn_Length_of_Stay.ipynb`: This notebook contains the complete Exploratory Data Analysis. It covers:
    * Loading and harmonizing the 6 individual yearly `.csv` files.
    * Extensive data cleaning and type correction (e.g., `Length of Stay`, `Birth Weight`).
    * Investigation of data quality issues and anomalies.
    * Creation of the final, clean `sparcs_eda.parquet` file.

* `LOS_EDA.ipynb`: This is the main modeling notebook. It includes:
    * Loading the final clean dataset.
    * Final preprocessing and feature selection
    * Univariate, bivariate, and multivariate analysis to understand the key predictors.
    * Finalizing the dataset for model creation and evaluation for predicting LOS of newborns.




