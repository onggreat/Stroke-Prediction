# Stroke Prediction

Choice of my Data set will be on kaggle under healthcare-dataset-stroke-data 
(WHO | Stroke: a global response is needed )

Base on my selection, I will be choosing this data set. According to the World Health Organization (WHO) stroke is the 2nd leading cause of death globally, responsible for approximately 11% of total deaths.This dataset is used to predict whether a patient is likely to get stroke based on the input parameters like gender, age, various diseases, and smoking status. Each row in the data provides relevant information about the patient.

## Problem Statement
According to the World Health Organization (WHO) stroke is the 2nd leading cause of death globally, responsible for approximately 11% of total deaths, Can we predict stroke before it happens for better preventive healthcare?


## Attributes
* id: unique identifier
* gender: "Male", "Female" or "Other“
* age: age of the patient
* hypertension: 0 if the patient doesn't have hypertension, 1 if the patient has hypertension
* heart_disease: 0 if the patient doesn't have any heart diseases, 1 if the patient has a heart disease
* ever_married: "No" or "Yes“
* work_type: "children", "Govt_jov", "Never_worked", "Private" or "Self-employed“
* Residence_type: "Rural" or "Urban“
* avg_glucose_level: average glucose level in blood
* bmi: body mass index
* smoking_status: "formerly smoked", "never smoked", "smokes" or "Unknown"*
* stroke: 1 if the patient had a stroke or 0 if not

## Different Types Of Stroke
There are two main types of stroke. Ischemic strokes are more common and occur when a blood clot blocks an artery in the brain. In some cases, the clot develops in the vessel itself (thrombotic stroke). In other cases, the clot forms in the heart or in an artery that carries blood to the brain; the clot breaks off and travels to the brain, where it lodges in a small artery (embolic stroke). Hemorrhagic strokes occur when an artery in the brain ruptures, releasing blood into the brain tissue.
![image](https://user-images.githubusercontent.com/74976732/126281219-78762698-b74f-48f3-9770-502818a6c29a.png)

## Data Insights
From distribution it is clear that every 4.9percent out of 100 people are having strokes from ths sampling data. Moreover,this is a highly unbalanced data distribution, and null accuracy score of this distribution it self is 95.1%, whcih imploys any dump model should randomly predictions of stroke could reach accuracy of 95%. So, while modeling and training data, either over sampling or under sampling has to be done to obtain best results.
![image](https://user-images.githubusercontent.com/74976732/126281239-28925273-65fa-46d7-9b4a-4956b1a18c72.png)
![image](https://user-images.githubusercontent.com/74976732/126281262-4dc71b76-9bcc-494c-9cfb-7ba43ddc0209.png)



## Problem Description 
* Before starting actual analysis
* First of all we will be do data processing
![image](https://user-images.githubusercontent.com/74976732/126281397-98b7768c-eb13-4695-bd78-46c9b039460d.png)

* overview of univariate categorical features on stroke VS healthy
* ![image](https://user-images.githubusercontent.com/74976732/126281452-370c5293-1bca-42b1-86c4-58b89ce8ca37.png)

* Plot smoking status, keep the 'unknown' observations, by doing this I treat smokers and non smokers as a one class, which would be alright if our variable is not important. #smoking is not good for health
* ![image](https://user-images.githubusercontent.com/74976732/126281486-377c0c73-fd5a-479d-b1d1-fb2a0dbe6404.png)
![image](https://user-images.githubusercontent.com/74976732/126281498-6b6c86e3-d8aa-4628-9e4d-38eb47a02f89.png)

* that Age is a big factor in stroke patient
![image](https://user-images.githubusercontent.com/74976732/126281563-9084601e-3916-4e2c-9b2b-8ccad35d1648.png)

* predict on age and bmi, See that the older you are, the chances of getting Stroke/heart disease/ hypertension is higher or lower
![image](https://user-images.githubusercontent.com/74976732/126281584-cbf0e95e-ec3c-44fc-9a13-abc018974470.png)


## Modeling
Data sampling is a technique where we either populate or reduce our data to make it balance. This is called oversampling and undersampling in general. Whereas model modifications are involved in the implementation of folds and cross-validation techniquesM
Using recall will be a good evaluation matric but precision and recall will be able to work hand in hand.
i will be trying 5 modeling To do testing:
* KNN
* Logistic Regression
* Random Forest Classifier
* XGBClassifier
* LGBMClasifier

## Automated Hyper- Parameter tuning
![image](https://user-images.githubusercontent.com/74976732/126281893-0658e4ca-ab58-4924-9c02-12fec8315bdc.png)

i create a population of N Machine Learning models with some predefined Hyperparameters, then calculate the accuracy of each model and decide to keep just half of the models (the ones that perform best).now i generate some offsprings having similar Hyperparameters to the ones of the best models so that to get again a population of N models. At this point, we can again calculate the accuracy of each model and repeat the cycle for a defined number of generations. In this way, just the best models will survive at the end of the process.In order to implement Genetic Algorithms in Python, I can use the TPOT Auto Machine Learning library. TPOT is built on the scikit-learn library and it can be used for either regression or classification tasks.

The report and the best parameters are identified above using Genetic Algorithms.
The overall accuracy of our Random Forest Genetic Algorithm optimized model is shown below.
![image](https://user-images.githubusercontent.com/74976732/126281958-ba23939e-eb2d-400b-8f7f-a0203b6cf9da.png)

XGBoost is a tree based ensemble machine learning algorithm which is a scalable machine learning system for tree boosting. XGBoost stands for Extreme Gradient Boosting. It uses more accurate approximations to find the best tree model.
![image](https://user-images.githubusercontent.com/74976732/126282130-a5115149-673b-4c29-b9c4-dc39439ed004.png)


## Explaination of algorithm
![image](https://user-images.githubusercontent.com/74976732/126281820-bcef75ff-1918-46fb-b6ab-e319b82a751b.png)
![image](https://user-images.githubusercontent.com/74976732/126282028-5cefedb8-be30-4640-8fce-bda54e981090.png)

* Random forest is a supervised learning algorithm which is used for both classification as well as regression. But however, it is mainly used for classification problems. As we know that a forest is made up of trees and more trees means more robust forest.
* The random forest is a classification algorithm consisting of many decisions trees. It uses bagging and feature randomness when building each individual tree to try to create an uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree.
What do we need in order for our random forest to make accurate class predictions?
We need features that have at least some predictive power. After all, if we put garbage in then we will get garbage out.
* The trees of the forest and more importantly their predictions need to be uncorrelated (or at least have low correlations with each other). While the algorithm itself via feature randomness tries to engineer these low correlations for us, the features we select and the hyper-parameters we choose will impact the ultimate correlations as well.






