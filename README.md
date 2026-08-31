# Assumption-junction
# Team Name: JKJ
## Contributors: Jothi Gupta, Kuba Romanczuk, Jonathan Walker
## Dataset: https://www.kaggle.com/datasets/blastchar/telco-customer-churn?resource=download

[TODO] Briefly describe the Telco Customer Churn dataset and the churn prediction task.

## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression |  |  |  |
| Logistic regression |  |  |  |
| GAM |  |  |  |

## Model Comparison

| Model | Performance Evidence | Interpretability Strength | Interpretability Weakness |
|---|---|---|---|
| Linear regression | 79% accuracy (but naive approach yields 73%), ROC AUC of 0.83, F1-score of 0.55   | Very high! The presence of a variable translates to the coefficient of that variable being added to the baseline predicted probability of a customer churning- this is very easy to conceptualize | The probability output the model produces can be wrongly interpreted as "this variable definitively causes an N% increased chance of churn, or "N% of our customers with this variable present will/will not churn. |
| Logistic regression |  |  |  |
| GAM |  |  |  |

## Recommendation

**Recommended model:** Linear Regression

**Why this model:** The coefficients of the model are incredibly interpretable, where we can map the presence of a variable to a delta of the predicted probability of a customer churning.

**What the company can responsibly conclude:** Our model, given the data it was trained on, is able to linearly add the presence of given variables to predict a probability of a customer churning.

**What the company should not conclude yet:** We can definitively use the model to know whether a customer will churn or not.

**One next analysis we would run:** Right now, the decision threshold for the Linear model is at 0.5; the AUC-ROC is quite good, but there's a huge class-imbalance, by sweeping thresholds using the training data, we could optimize for the best F1-score, and this hopefully propagate to improved performance on the test set. (This is the low hanging fruit that could lead to performance gains without major rework). 

