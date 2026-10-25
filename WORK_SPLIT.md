# Work Split

Who owns what, and who depends on whom.

## Overview

| Person | Name | Focus | Assignment tasks | Notebook | Depends on |
|--------|------|-------|------------------|----------|------------|
| 1 | Joao | Problem formulation, metrics & baseline model | Task 1, Task 3 | Task 3 | None to start; final predictions from Persons 4 & 5 |
| 2 | Olena | EDA & data leakage audit | Task 2 (data understanding & quality) | Task 2 | Person 1 (target framing) |
| 3 | Samuel | Preprocessing, feature engineering & time-aware split | Task 2 (data preparation & experimental setup) | Task 2 | Person 1 (framing), Person 2 (EDA & leakage flags) |
| 4 | Pedro | Tree-based ensembles (Random Forest, Gradient Boosting) | Task 3 | Task 3 (Section 7.1) | Person 3 (split datasets) |
| 5 | Nuno | Non-tree models & originality analysis | Task 3, originality | Task 3 (Section 7.2) | Person 3 (split datasets) |

**Notebooks:** `notebooks/Task2_Data_Understanding_Preparation.ipynb` (Olena, Samuel) and `notebooks/Task3_Predictive_Modelling.ipynb` (Joao, Nuno, Pedro).

**Flow:** Person 1 frames the problem → Person 2 audits the data → Person 3 builds the pipeline and splits → Persons 4 & 5 model → Person 1 summarises business impact.

---

## Person 1 (Joao): Problem Formulation, Metric Architecture & Baseline Model

**Task focus:** Task 1 (Problem Definition) & Task 3 (Baseline Benchmark)

**Dependencies:** None to start (initiates project formulation). Receives final predictions from Persons 4 & 5 to summarise business impact.

**Action items**
- Formulate the business question (e.g. predicting accident severity `accident_classification` to optimise emergency dispatch, or predicting high-risk accident conditions for patrol deployment).
- Define the prediction target, unit of analysis (individual accident vs. road-segment time block), and prediction horizon.
- Design cost-sensitive evaluation metrics aligned with business objectives (e.g. heavily weighting recall/F1 on fatal/injury accidents to penalise severe false negatives).
- Build, evaluate, and document the baseline model (e.g. Dummy Classifier or simple Logistic Regression / Decision Tree).

**Deliverables**
- Task 1 text and slide content.
- Baseline model implementation, benchmark evaluation metrics, and final business recommendation framework.

---

## Person 2 (Olena): Exploratory Data Analysis (EDA) & Data Leakage Audit

**Task focus:** Task 2 (Data Understanding & Quality Audit)

**Dependencies:** Person 1 for target framing.

**Action items**
- Conduct structural EDA on `highway_accidents.csv` (150,000 rows, 23 features): missingness, variable types, distributions, and outliers.
- Analyse interactions between features and the target (e.g. how road geometry like Curve, Tunnel, Bridge or `time_of_day` correlates with severity).
- Examine temporal distributions (2007–2025) for data gaps, seasonality, and trend shifts.
- Perform a strict data leakage audit to flag features that would not be available before an accident happens.

**Deliverables**
- Executable EDA notebook section with plots (heatmaps, temporal trends, target distribution).
- Data quality & leakage audit summary for Person 3.

---

## Person 3 (Samuel): Data Preprocessing, Feature Engineering & Time-Aware Splitting

**Task focus:** Task 2 (Data Preparation & Experimental Setup)

**Dependencies:** Person 1 (problem framing) and Person 2 (EDA & leakage flags).

**Action items**
- Clean data, handle missing values, drop leaked features identified by Person 2, and encode categorical variables (`roadway_type`, `area_type`, `highway_type`).
- Engineer new features: temporal indicators (month, day of week, rush hours), spatial risk indicators (km, latitude, longitude), and road feature interactions.
- Design a time-aware train/validation/test split (e.g. train on 2007–2021, validate on 2022–2023, test on 2024–2025) to prevent temporal leakage.
- Scale features (StandardScaler / MinMaxScaler) for models sensitive to scaling.

**Deliverables**
- Reproducible preprocessing and feature engineering pipeline notebook section.
- Clean, transformed split datasets ready for Persons 4 and 5.

---

## Person 4 (Pedro): Model Strategy A – Tree-Based & Ensemble Models

**Task focus:** Task 3 (Predictive Modelling — Ensembles), Section 7.1 of the Task 3 notebook

**Dependencies:** Person 3 for preprocessed datasets and temporal splits.

**Action items**
- Implement, tune and evaluate tree-based ensembles (Random Forest, Histogram Gradient Boosting).
- Tune hyperparameters on the validation set (2022–2023) only.
- Address class imbalance (class weights) and re-calibrate probabilities on validation.
- Explain predictions with permutation feature importance.

**Deliverables**
- Executable notebook section for tree-based / ensemble models.
- Performance table, PR curve and feature importance chart compared against the baseline (`reports/figures/task3_trees_*.png`).

---

## Person 5 (Nuno): Model Strategy B – Non-Tree Models & Originality / Value-Add Analysis

**Task focus:** Task 3 (Predictive Modelling — Non-Tree), Sections 7.2–7.3 of the Task 3 notebook, and the originality component (Section 8).

**Dependencies:** Person 3 for preprocessed data.

**Action items**
- Implement, tune and evaluate non-tree models: bag of 5 MLP neural networks on undersampled data (class imbalance), and LDA.
- Tune on the validation set only, re-calibrate probabilities (sigmoid) on validation.
- Compare against the baseline (Person 1) and the tree ensembles (Person 4); select the final model on validation (Section 7.3).
- Originality: cost-benefit of ALS capacity, GPS hotspot grid checked out-of-time, interactive Folium map, value of GPS location for the model (Section 8).

**Deliverables**
- Executable notebook sections 7.2, 7.3 and 8.
- Figures `reports/figures/task3_nontree_*.png`, `task3_value_vs_capacity.png`, `task3_hotspots.png` and the map `task3_hotspot_map.html`.
- Slides 17, 18, 21–24 and 26 of the group presentation.
