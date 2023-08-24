# Predicting Unplanned ICU Admissions: An NLP-Based Approach

## _**Objectives**_
The aim of this project is to evaluate the viability of using Machine Learning and Natural Language Processing for the prediction of unplanned re-admissions in hospitals. As
such, the processing and analysis of patients’ discharge notes will be performed in order
to analyse if they could be a sufficient and valid indicator for prediction. Accordingly,
a comparison of state-of-the-art ML-based techniques will be developed, taking into account DL strategies, and more specifically transfer learning and pre-trained Transformers.
Results will show a performance evaluation of the techniques involved in this work.
To this end, a number of objectives are defined:
* Data-base analysis and pre-processing for the application studied in this project.    
* Research and analysis of the state of the art in general Machine Learning and specific
Deep Learning techniques oriented to a binary classification medical application.    
* Natural Language Processing of discharge text notes in order to clean and filter the
relevant information required for the classification stage.    
* Training, validation, comparison and evaluation of different ML-based techniques to
predict unplanned re-admissions. Conclusions will be drawn based on the results.

## _**Dataset Description**_
This project relies on the MIMIC-III database [15] (‘Medical Information Mart for Intensive Care’). It includes clinical data of patients admitted to critical care units between
2001 and 2012 at the Beth Israel Deaconess Medical Center, comprising data associated
with 53,423 distinct hospital admissions for adult patients (aged 16 years or above) and
data for 7870 neonates. Given the sensitive nature of the medical information, the access
to the database is limited and its information has been de-identified to avoid patients’ privacy violations. Access has been requested to the Massachusetts Institute of Technology
(MIT) Lab for Computational Physiology after completing a course in ethics and research,
in order to maintain the integrity of the information and to ensure responsible processing,
complying with security standards and pledging not to identify individual patients.
Data covers 38597 distinct adult patients and 49785 admissions, where the median
ICU length stay is 2.1 days. It is structured in a relational database (traceable by ID
attributes) consisting of 26 tables distributed in a collection of CSV files.    

However, since only the notes issued during the patients’ stays in ICU will be used,
the study will be limited to the NOTEEVENTS and ADMISSIONS tables. Specifically,
these two tables contain the following information:
* **ADMISSIONS** – Subject and admission ID, admission time, discharge time, death
time, admission type, admission location, discharge location, type of insurance, language, religion, marital status, ethnicity and diagnoses.
* **NOTEEVENTS** – Subject and admission ID, date of creation, category of the note,
description and the actual text.
 
ADMISSIONS contains a total of 58976 observations. Since the aim is to predict unplanned readmissions, it is necessary that all observations have an associated admission
date to allow this traceability. However, no observation lacks this data. On the contrary, discharge or death times can contain missing values, patients may not have been
readmitted or deceased.     
NOTEEVENTS contains 2083180 observations, a significantly higher number than
those observed in the ADMISSIONS table. Where a single patient can generate multiple
notes during a stay in the ICU.


## _**Results**_

All results are listed on table, with the best result for each metric highlighted in bold.
When comparing the performance of the different models, it can be observed that the
deep learning models are outperformed by machine learning or statistical models. Where
regression models, and in particular Ridge Regression, yield the best results with an
AUROC of 0.70. By contrast, Random Forest has the highest recall, detecting higher number of
30-day readmissions.

| Algorithm       | Accuracy | Precision | Recall | AUROC |
|-----------------|----------|-----------|--------|-------|
| Logistic Regression | 0.65 | 0.68 | 0.57 | 0.69 |
| Ridge Regression | 0.65 | 0.67 | 0.57 | 0.70 |
| Lasso Regression | 0.63 | 0.66 | 0.55 | 0.69 |
| Elastic Net | 0.64 | 0.66 | 0.55 | 0.69 |
| SVM | 0.65 | 0.68 | 0.57 | 0.65 |
| MLP | 0.60 | 0.61 | 0.56 | 0.60 |
| RF | 0.65 | 0.64 | 0.67 | 0.65 |
| Naïve Bayes | 0.63 | 0.64 | 0.56 | 0.63 |
| XGBoost | 0.60 | 0.60 | 0.59 | 0.60 |
| GRU | 0.57 | 0.57 | 0.57 | 0.57 |
| LSTM | 0.55 | 0.55 | 0.55 | 0.55 |
| GRU-CNN | 0.56 | 0.56 | 0.56 | 0.56 |
| LSTM-CNN | 0.56 | 0.56 | 0.56 | 0.56 |
| BERTBASE | 0.64 | 0.53 | 0.61 | 0.61 |
| DistilBERT | 0.66 | 0.53 | 0.62 | 0.61 |

Being the main difference between the deep learning and machine learning models the
data processing. Where the former maintain the sequential order of words (thus allowing
the establishment of dependencies between words) and the latter only processes the raw
frequency of words. This difference highlights the limitations of models based on neural
networks, requiring large amounts of information for their proper functioning. In limited
data situations the simplicity of statistical models and machine learning provides better
performance.       

Results show great similarity with those found in the literature using only discharge
notes as only predictors. However, in the case of DL-based models the results could be
improved by using larger datasets, further development of transfer learning approaches
and notes from different sources and databases. Additionally, inclusion of numerical data
from patients at the time of discharge would improve the performance.
