# Assumption-junction
# Team Name: JKJ
## Contributors: Jothi Gupta, Kuba Romanczuk, Jonathan Walker
## Dataset: https://www.kaggle.com/datasets/blastchar/telco-customer-churn?resource=download

The Telco Customer Churn dataset characterizes Telco customers on demographic, account, and services data. The dataset also denotes whether the customer was affirmative for "Churn." Being positive for churn means that the customer was not a returning customer and whom left in the last month. The goal of the model is to determine whether we can predict which customers will be likely to Churn in the future based on their given demographic, account, and services data. 

## Assumption Checks

| Model | Key Assumptions Checked | Evidence | Concern |
|---|---|---|---|
| Linear regression | 1) Linearity <br><br> 2) no Autocorrelation <br><br> 3) no Multi-collinearity | 1) We plotted numerical variables against the target variable for a visual check- we could not confirm linearity, as there wasn't a smooth gradient nor separation between numerical values and the target values of 0 and 1; <br> 2) For categorical variables, we created a Cramer's V matrix to see if features correlated with each other, and then we used a correlation heat-map to see if numerical variables correlated with each other. In both cases, we had highly correlated features, and marked them (any above a threshold of 0.70). Further action is taken when working to remove collinearity. <br> 3) For removing multi-collinearity, we checked the correlation of features with the target variable (churn); for the previously calculated highly-autocorrelated features, which ever had the lesser association to churn, we removed it (to maintain predictive power) - this led to 13 features being removed. | 1) We did not check for multicollinearity between categorical and numerical variables, so this unexplored relationship could skew results. <br> 2) There's no understanding of usage- if someone had a variable present, there's no discriminator in intensity of usage or how it impacts their specific customer experience. <br>  3) We removed a lot of variables from the feature set in the name of no multi-collinearity.... this could lead to more nuanced relationships being omitted completely. |
| Logistic regression |  |  |  |
| GAM | 1) Linearity <br> | 1) We plotted numerical variables against the target variable and could not confirm linearity. This is likely because the target veriable is categorical so it's hard to plot a linear relationship from only two output options. | 1) We did not check for multicollinearity which could skew the results and the adaptive splines. |

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

