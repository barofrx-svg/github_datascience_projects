⚠️ FOR DYNAMIC, 3D PLOTS AND BEST EXPERIENCE please view the notebook on nbviewer or Google Colab, as GitHub's built-in viewer cannot render heavy interactive JavaScript or 3D plots. ⚠️

[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/github_datascience_projects/blob/main/project_2_health_classification/project_2.ipynb) or [View full notebook on Google Colab](https://colab.research.google.com/github/barofrx-svg/github_datascience_projects/blob/main/project_2_health_classification/project_2.ipynb)


# Diabetes Classification
In this detailed project went through the steps of preprocessing, feature selection, model training, optimization and model interpretability with SHAP.

The final model achieved 75% accuracy on the out-of-fold test set, using only very basic sociological and health data.

# The following charts are just a subset of what is actually inside the project.

## Correlation Plot
<img width="1061" height="1111" alt="1" src="https://github.com/user-attachments/assets/83058b27-08a3-4c39-97ba-da285e351f5f" />


A good note is that there is no strong correlation between features, this eliminates the risk of multicolinearity, redundancy and data leakage onto the the target variable. Absolute values higher than 0.9 are strong sign that this problem exists.

The highest absolute correlation regarding the target variable is with General Health. They have a positive correlation of 0.41, this means that there are cases where GenHlth and Diabetes move together. However it is not causation. I can not say that if someone`s General health is below average than the risk of diabetes increases by 41%. It a factor that states the strength of how the two variables move together. 

- Close to 1 -> they move highly together, in the same direction.
- Close to -1 -> they move highly together, but opposite direction.

## Slice Plot
<img width="1800" height="525" alt="6" src="https://github.com/user-attachments/assets/a6b54613-d010-41b2-b8e4-1d8d696511f3" />

Slice plot shows how different values for hyperparameters influenced the accuracy. The color indicates which attempt of iteration it was. Blue -> end of the trial, white -> one of the first trials.

2 Hyperparameters show interesting releations
- C: a clear maximum point is visible. Too small and high C values result in medium accuracy while 0.006 are tends to produce higher accuracy.
High C (10-100), low regularization, the model tends to overfit to the train set and performs poorly on the test set.
Low C (100 micros 0.001), high regularization, model is penalized for creating complex decisions, this leads to underfitting.
So I can see where the underfitting and overfitting intersect, generating a maximum in accuracy.

- l1_ratio_val: I can see a negative releationship. As l1 increases the objective value decreases. Negativ slope
1. l1_ratio = 0 (Ridge): The model shrinks all the feature weights down to prevent overfitting, but it keeps every single column active.

2. l1_ratio = 1 (Lasso): The model aggressively forces feature weights to exactly 0.0. It acts as an automated feature selector, completely deleting columns what it considers unuseful.

If accuracy decreases as the l1_ratio approaches 1, it means that forcing the model to drop columns is destroying valuable information. This tells me that the dataset does not have just one or two features that predict the target on their own. Instead it relies on a complex web of many different features all working 

## Summary Plot
<img width="1757" height="790" alt="2" src="https://github.com/user-attachments/assets/56e1d8ad-a1ae-40e7-aa2c-ee954a4a98f4" />

Summary plot generates a clear explanation about the feature set. The features are sorted from top to bottom with highest feature importance being at the top. Then on the left side of each feature there is a violin plot with color differentiation.

- Red: Means that the patient had a high observed value in that feature. So it could be 1 for HighBP or 5 for GenHlth.
- Blue: Means that the patient had a low observed value. 0 for BP and 1 for GenHlth

The X axis distribution shows in what direction did that feature push with the known value (red/blue). If I look at the most important feature I can see that:
1. GenHlth (1- excellent 5- poor): If this feature increases, then the risk of having diabetes also increases, as it pushes shap value to the positive side.
Both models show the same insight: Positive relationship with target variable. Excellent general health significantly decreases the risk.

2. BMI (continuous variable): Higher BMI means more fat on a person. Once again both models align, positive relationship with targer variable. High BMI, high risk of diabetes

3. HighBP (0-no, 1-yes): Clear, aligned responses. If a patient has high blood pressure then it increases the risk of having diabetes

4. Age (increasing groups): Being young decreases the risk while being old increases. But there is a difference between the models.
The Linear model shows me from the plot that each 20 year old group has the same effect on the diabetes, while the non-linear sees it other. It shows that being in your 20s is a high protective shield against diabetes, however as you get older the risk of diabetes plateaous at around 60 years old. Which means it is not a linear relationship. Being 90 years means that the risk is almost the same with being 60 years old.

5. Income (1= less than 10.000$, 8 = 75.00$ or more): Now this is an inverse relationship as red is on the left side while blue is on the right side (increases shap value). This makes sense, having more disposable income gives the patient the chance to purchase healthier food and live a more balanced life.

6. Heavy Alcohol Consumption (0-no, 1-yes): This is a critical anomaly, the plot says that heavy drinking (red) decreases the risk of having diabetes. Does it logically make sense? Not at all, it is likely that the patients that got diagnosed with diabetes are ordered to stop consuming alcohol, so the only group left with heavy alcohol consumption is the healthy one. Since this is a contradiction I would 100% remove this column since the model rewards patients who drink heavily.

7. Education: Higher education, reduces the risk for both models, altough this is not a major effect.


Features that are not visible and that are shown at the bottom are not significant, dropping these should not make the models worse, even it could help by removing the noise they bring. So the models can focus truly on the useful information.

## Decision Plot for 250 patients
<img width="1990" height="989" alt="5" src="https://github.com/user-attachments/assets/db340377-3d06-4ff5-9bf3-70f289cb65d7" />

The decision plot is an elegant way to visualize the cumulative mathematical journey of multiple patients at once. Here I used a subset of 250 patients. It tracks the prediction trajectory from the baseline expectation at the bottom to the final output at the top. The plot naturally forms a funnel shape, starting narrow at the base and expanding out widely at the top. 

The narrow base visually proves that the bottom features have virtually zero impact on the target variable the lines travel straight up without deviating. As the lines reach the most important features at the top, the accumulated SHAP values cause them to violently snap left (decreasing risk) or right (increasing risk), fanning out into their final individual diagnoses. This visualization perfectly justifies dropping low-importance features, as they do not meaningfully steer the model's final decision. The two models, once again evaulate most of the features the same. That is why the funnel looks identical.
