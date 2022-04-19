# Let's Code Academy - Machine Learning - Classification with COVID Data
(Data Science Degree - [Let's Code](https://letscode.com.br/))

## Introduction

The goal of this project is to develop a study of the 'COVID.csv' dataset, a database which contains information about COVID cases. From symptom diagnosis and other informations about the patients, we'll develop a model to predict confirmed COVID cases.

The variables in the dataset represent:
	
	Features:
    id: A unique number for each patient
    sex: Patient's sex (0 - Man / 1 - Woman)
    patient_type: Whether the patient was discharged (1) or hospitalized (0)
    intubed: Whether the patient was intubated (1) or not (0)
    pneumonia: Whether the patient showed signs of pneumonia (1) or not (0)
    age: Patient's age
    pregnancy: Whether the patient was pregnant (1) or not (0)
    diabetes: Whether the patient had diabetes (1) or not (0)
    copd: Whether the patient had a Chronic Obstructive Pulmonary Disease (1) or not (0)
    asthma: Whether the patient had Asthma (1) or not (0)
    inmsupr: Whether the patient showed signs of immunosuppression (1) or not (0)
    hypertension: Whether the patient had hypertension (1) or not (0)
    other_disease: Whether the patient had other diseases (1) or not (0)
    cardiovascular: Whether the patient had cardiovascular diseases (1) or not (0)
    obesity: Whether the patient had obesity (1) or not (0)
    renal_chronic: Whether the patient had kidney problems (1) or not (0)
    tobacco: Whether the patient was a smoker (1) or not (0)
    contact_other_covid: Whether the patient came in contact with other people diagnosed with COVID
    icu: Whether the patient had to be hospitalized in the ICU (1) or not (0)
    
	Target:
	covid_res: Whether the result of the COVID test was positive (1) or negative (0) 

## Development

This project was developed following these steps:

- Data Preparation and Consistency Check: In this topic, I verify the consistency of the data, modify and transform the data. The procedures performed here were: Removal/treatment of missing values, removal of duplicates, adjustment of the types of variables and outlier analysis;

- Exploratory Data Analysis: To create our classification model, we need to know very well the data we're working with. For this purpose, in this part of the project I develop analysis and visualizations of the data I'll be using.

- Classification Model: I created a classifier for the results of the COVID tests ("covid_res"). The models tested were: __Logistic Regression__, __Decision Tree__, __Random Forest__, __AdaBoost__, __Gradient Boost__, __XGBoost__, __LightGBM__ and __CatBoost__. The problem we had demanded we focus on labeling few __False Negatives__, since it's more dangerous to tell a patient they're not sick when they are (False Negative) than to tell them they're sick when they aren't (False Positive). Considering this, the model CatBoost had the best performance among the models tested.

- Optimization: Using Cross Validation, techniques to ensure the data is well balanced (Undersampling, Oversampling and SMOTE) and tuning of hyperparameters with Optuna, I tried to make the model perform as better as possible.

## Conclusions

Different models and optimization techniques were used in order to obtain the best possible result (best Recall, specially) with the available data for the problem at hands. Still, the result is far from satisfactory, since the evaluation metrics are still low, and it wouldn't be a good idea to use this model in production. Despite this, it was interesting to practice the techniques used.

Some considerations:

- The features we had were not ideal. Some of them have to be input in the dataset after the test, such as "intubed", "patient_type" and "icu". This incurrs in an error known as __data leakage__. I ran a quick test with the parameters from Optuna and dropping these columns to show how, despite the fact that this is indeed a problem,  removing these features wasn't enough to make the model perform well enough.
- A more logic way to deal with this problem would be to predict whether a patient needs to be hospitalized, sent to the ICU or intubed using the result of the test as one of the features. This could be an interesting result to help deal with the pandemic in a more efficient manner.
- In case we really want to predict the result of the test, the selection of features we use for this purpose has to be reconsidered. We could use the oxygen level of the patients and other features related to COVID symptoms.

## Files

[Dataset in CSV format](https://github.com/GabrielZinatoSP/-ML-Covid_LetsCode/blob/Master/Dataset.zip)

[Python Notebook](https://github.com/GabrielZinatoSP/-ML-Covid_LetsCode/blob/Master/ML_Project_Covid-Lets_Code_Academy-Gabriel_Zinato_Rosa.ipynb)

[HMTL version of the notebook](https://github.com/GabrielZinatoSP/-ML-Covid_LetsCode/blob/Master/ML_Project_Covid-Lets_Code_Academy-Gabriel_Zinato_Rosa.html)
The interactive charts from Plotly and Optuna work on the browser in this version (you have to download it, unfortunately).

_______

Thank you for reading! I'm open to any criticism or tips that may help me learn.




