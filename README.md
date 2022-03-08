The project has been written in python in a Jupyter notebook ML_project_vaccination_readiness.ipynb. For a better view use the nbviewer:
https://nbviewer.org/github/ahaeni/ml_project_h1n1-flu-vaccine/blob/main/ML_project_vaccination_readiness.ipynb

# Flu Shot Learning - Predict H1N1 and Seasonal Flu Vaccines

Drivendata.org is a platform that deals with real world problems. It's a nonprofit organization to analyze data, model solutions, and make predictions. Drivendata organizes competitions where data scientists can participate and do something good for the world. In this project I tried to predict the willingness of the
of the American population in 2009 to be vaccinated against seasonal and swine flu (H1N1). The findings could be applied to the current situation with the
with vaccination against the coronavirus.

## 1.Problem Definition
A model must be developed that predicts how likely it is that the respondents will get vaccinated against seasonal and swine flu. The data comes from a "National 2009 H1N1 Flu Survey" which was  provided by the National Center for Health Statistics. The data set consists of 35 features and 2 Target variables:
- h1n1_vaccine - whether the respondent has had a swine flu vaccination;
- seasonal_vaccine - whether the respondent has had a vaccination against seasonal flu.
Both target variables are binary: 0 = "No", 1 = "Yes". There are cases where only one vaccination has been administered, or both, or none. The detailed description of the features can be found on the drivendata.org website.

There are 3 files provided:
- training_set_features.csv - the dataset with about 27,000 surveys;
- training_set_labels.csv - labels to the corresponding surveys in the training
dataset;
- test_set_features.csv - surveys for which predictions should be made.
The goal is to have a .csv file at the end of the project in the following format:
h1n1_vaccine seasonal_vaccine
respondent_id
26707 0.5 0.7
26708 0.5 0.7
26709 0.5 0.7
26710 0.5 0.7
26711 0.5 0.7
... ... ...
The probabilities should be in the value range from 0 to 1 which do not necessarily have to
add up to 1. So it is not about the prediction of the binary labels, but the probabilities for multilabels. The result is evaluated according to ROC/AUC.

## 2. Solution Approach
- First, the features are examined more closely in order to find out
which are the relevant ones and whether correlations exist.
- The data set is cleaned and standardized. NaN values are replaced.
- training_set_features.csv is split between "Train" and "Test".
- Different models are trained on the "Train" dataset. 
- Once the algorithm has reached a high accuracy of prediction according to ROC/AUC, it is trained on the whole training_set_features.csv dataset to improve the prediction for the test_set_features.csv dataset.

## 3. Result
For the prediction of probabilities the GradientBoostingClassifier gave the best results for both target variables with a joint score of 0.8403. This score ranked 286 out of 1,850 (February 2021)



