# Cardiovascular_Risk_Prediction

Built Supervised Binary classification model to help patients to take precautions and change lifestyle by risk prediction of cardiovascular disease in upcoming 10 years.

# Problem Statement

The dataset is from an ongoing cardiovascular study on residents of the town of Framingham, Massachusetts. The classification goal is to predict whether the patient has a 10-year risk of future coronary heart disease (CHD). The dataset provides the patients’ information. It includes over 4,000 records and 15 attributes.Each attribute is a potential risk factor. There are both demographic, behavioral, and medical risk factors.

# Attributes

• Sex: male or female("M" or "F")

• Age: Age of the patient;(Continuous - Although the recorded ages have been truncated to whole numbers, the concept of age is continuous) Behavioral

• is_smoking: whether or not the patient is a current smoker ("YES" or "NO")

• Cigs Per Day: the number of cigarettes that the person smoked on average in one day.(can be considered continuous as one can have any number of cigarettes, even half a cigarette.)

• BP Meds: whether or not the patient was on blood pressure medication (Nominal)

• Prevalent Stroke: whether or not the patient had previously had a stroke (Nominal)

• Prevalent Hyp: whether or not the patient was hypertensive (Nominal)

• Diabetes: whether or not the patient had diabetes (Nominal)

• Tot Chol: total cholesterol level (Continuous)

• Sys BP: systolic blood pressure (Continuous)

• Dia BP: diastolic blood pressure (Continuous)

• BMI: Body Mass Index (Continuous)

• Heart Rate: heart rate (Continuous - In medical research, variables such as heart rate though in fact discrete, yet are considered continuous because of large number of possible values.)

• Glucose: glucose level (Continuous)

• 10-year risk of coronary heart disease CHD(binary: “1”, means “Yes”, “0” means “No”) - Dependent Variable

# The Metric Trap

One of the major issues when dealing with unbalanced datasets relates to the metrics used to evaluate their model. Using simpler metrics like accuracy score can be misleading. In a dataset with highly unbalanced classes, the classifier will always “predict” the most common class without performing any analysis of the features and it will have a high accuracy rate, obviously not the correct one.

# Handling Imbalanced Dataset

The given data is highly imbalanced data so I have used SMOTE Technique to overcome this problem. SMOTE is the technique of handling imbalanced dataset by creating synthetic datapoints of minority class. Here class 1 is the minority class which is oversampled by SMOTE by synthetic datapoints.

Synthetic Minority Oversampling Technique (SMOTE)

New examples are synthesized from the existing examples. This is a type of data augmentation for the minority class.

Dependent Variable count (Before SMOTE)

![image](https://user-images.githubusercontent.com/102653523/209868662-51f7c53f-8a74-41e6-a821-9996c43cd05a.png)


Dependent Variable count (After Sampling)

![image](https://user-images.githubusercontent.com/102653523/209868674-b2537aee-5ff1-4a7a-9a2d-89f23f37b186.png)


# Model Implementaion and Metrics

ROC Curve would be meaningless for Imbalanced dataset.

ROC Curve --> True_positive_rate vs False_positive_rate

True_positive_rate = True_positive/(True_positive + False_negative)

False_positive_rate = False_positive/(False_positive + True_negative)

For an Imbalanced dataset True_negative would be always high, if the majority class is 0. So we always get less False_positive_rate.

Presicion Recall curves would be appropriate for Imbalanced dataset.

# Evaluation

![image](https://user-images.githubusercontent.com/102653523/209868476-e535b69b-8e3b-4c30-89b3-de2ae83ba2ec.png)



# Conclusion

* Achieved ROC-AUC score of 0.978 and used confusion matrix to visualize TP,TN,FP,FN. ln focus to reduce False Negatives model is designed.

* It’s quite obvious that smokers have a high risk of 10 year CHD.

* Patients with no history of hypertensive, stroke, diabetes have less risk of 10 year CHD.

* By using simple Logistic Regressor algorithm we were able to get the Precision Recall AUC score of 68 % Very little improvement in Precision Recall AUC score after using Random Forest classifier because of data imbalance.

* Top five most important features are SysBP,Glucose ,Totchol,age,Cigsperday
