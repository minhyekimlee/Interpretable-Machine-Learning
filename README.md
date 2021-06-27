# Model Card

## Authors

Students at the George Washington University School of Business
* Zach Vila (zrvila)
* Minhye Kim (minhyekimlee)
* Tivon Johnson (tivonj)
* Qunzhe Ding (dingqunzhe1222)

Corrections or suggestions? Please file a [GitHub issue](https://github.com/zrvila/Interpretable-Machine-Learning/issues/new).


## Model Details

Our group has developed interpretable machine learning models as a part of our semester project in the Responsible Machine Learning class taught by Professor Hall during the Summer Semester in 2021. We have used Home Mortgage Disclosure Act historic mortgage reporting data to predict the probability of applicants being charged a higher rate for their mortgages. In order to address and mitigate growing concerns on risks of black box machine learning models deployed to highly impactful social areas without much needed contemplation and precaution on adverse effects, we demonstrate available techniques to interpret and explain predictive models to prevent unjust discrimination, improve security and encourage ethical decisions.

### Basic Information
* Model date: June 2021
* Model version: 1.0
* Model Type: Explainable Boosting Machine (EBM)
* Software: Python 3.6+, [InterpretML](https://github.com/interpretml/interpret).v0.2.5.
* Hyperparameters:
{'max_bins': 512,
 'max_interaction_bins': 32,
 'interactions': 15,
 'outer_bags': 10,
 'inner_bags': 4,
 'learning_rate': 0.01,
 'validation_size': 0.4,
 'min_samples_leaf': 1,
 'max_leaves': 3,
 'early_stopping_rounds': 100.0,
 'n_jobs': 4,
 'random_state': 12345}
 * Columns used as inputs: ['intro_rate_period_std',
 'no_intro_rate_period_std',
 'debt_to_income_ratio_missing',
 'property_value_std',
 'income_std',
 'debt_to_income_ratio_std']
 * Column used as target: 'high-priced'
* Paper or other resource for more information
  * [The Elements of Statistical Learning](https://web.stanford.edu/~hastie/ElemStatLearn/)
  * [Generalized Additive Models](https://www.routledge.com/Generalized-Additive-Models/Hastie-Tibshirani/p/book/9780412343902)
  * [Responsible Artificial Intelligence](https://www.springer.com/gp/book/9783030303709)
* [License](https://github.com/zrvila/Interpretable-Machine-Learning/blob/main/LICENSE)

## Intended Use

* Primary intended uses
  * The primary intended use is to provide an interpretable machine learning model that helps explain predictions as opposed to black box models which provide little, if any, explanation. Such transparency may help prevent bias and discrimination that can occur with black-box models as it relates to applicants with higher mortgage rates.
  * Our project goal is to determine if the Annual Percentage Rate (APR) charged for a mortgage is high-priced or not, which we consider as one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US. As a result, a demographic factor such as race or sex was considered. We discovered black applicants are more likely to get high-priced mortgages.
* Primary intended users
  * The primary intended users of this model are professors, students, and researchers of interpretable machine learning models.
* Out-of-scope use cases
  * This model is for educational purposes and not intended to evaluate real-world credit worthiness.

## Metrics

* Model performance measures
  * In our project, we choose [Area Under the Curve](https://towardsdatascience.com/illustrating-predictive-models-with-the-roc-curve-67e7b3aa8914#:~:text=Area%20Under%20the%20Curve%20%28AUC%29%20The%20AUC%20is,means%20there%20is%20perfect%20prediction%20by%20the%20model.) (AUC) as the evaluation metric of the model: in machine learning, AUC is one of the most important evaluation metrics for checking the model’s performance in classification.
* Decision thresholds
  * Typically, an excellent model has AUC near to the 1 and a poor model has an AUC near 0, if a model's AUC is 0.5, it means the model has no class separation capacity. In our project, we didn't set decision thresholds of the AUC, but we select our best model (EBM), with the highest AUC which is **0.8247** (pre-remediation), or **0.8097** (post-remediation).
* Variation approaches
  * Our EBM model Grid search runs through 100 iterations
  * We split our data by 70/30% training/validation

## Training Data
* Datasets
  * Home Mortgage Disclosure Act ([HMDA](https://www.ffiec.gov/hmda/history2.htm)) aggregate lending data
* Preprocessing
  * This data contains no major quality issues, so no preprocessing was required.
  * The data was divided into training and validation data with random values in a shape of 70 (training):30 (evaluation).
* Data Shape
  * Training data rows = 112,253, columns = 23
  * Validation data rows = 48,085, columns = 23 
* Attributes selected to remediate our model for fairness regarding demographic information.
  * **black**: Binary numeric input, whether the borrower is Black (1) or not (0).
  * **asian**: Binary numeric input, whether the borrower is Asian (1) or not (0).
  * **white**: Binary numeric input, whether the borrower is White (1) or not (0).
  * **male**: Binary numeric input, whether the borrower is male (1) or not (0).
  * **female**: Binary numeric input, whether the borrower is female (1) or not (0).
* Attributes selected to fit our model which best explain the relationship of an independent variable with the target variable.
  * **term 360**: Binary numeric input, whether the mortgage is a standard 360 month mortgage (1) or a different type of mortgage (0).
  * **conforming**: Binary numeric input, whether the mortgage conforms to normal standards (1), or whether the loan is different (0), e.g., jumbo, HELOC, reverse mortgage, etc.
  * **debt to income ratio missing**: Binary numeric input, missing marker (1) for debt to income ratio std.
  * **loan amount std**: Numeric input, standardized amount of the mortgage for applicants.
  * **loan to value ratio std**: Numeric input, ratio of the mortgage size to the value of the property for mortgage applicants.
  * **no intro rate period std**: Binary numeric input, whether or not a mortgage does not include an introductory rate period.
  * **intro rate period std**: Numeric input, standardized introductory rate period for mortgage applicants.
  * **property value std**: Numeric input, value of the mortgaged property.
  * **income std**: Numeric input, standardized income for mortgage applicants.
  * **debt to income ratio std**: Numeric input, standardized debt-to-income ratio for mortgage applicants.
* Attributes engineered for residual analysis. 
  * **phat**: Numeric input, prediction probabilities of high-priced mortgage for mortgage applicants.
  * **r**: Numeric input, log loss residuals for the predicted probabilities 
* Attribute for the target variable.
  * **high priced**: Binary target, whether (1) or not (0) the annual percentage rate (APR) charged for a mortgage is 150 basis points (1.5%) or more above a survey-based estimate of similar mortgages. (High-priced mortgages are legal, but somewhat punitive to borrowers. High-priced mortgages often fall on the shoulders of minority home owners, and are one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US.)
* Attributes that were not used in our approaches.
  * **row id**: Numeric input, value that uniquely identifies a row in a table.
  * **amind**: Binary numeric input, whether the borrower is American Indian (1) or not (0). 
  * **hipac**: Binary numeric input, whether the borrower is Native Hawaiian or Other Pacific Islander (1) or not (0). 
  * **hispanic**: Binary numeric input, whether the borrower is Hispanic (1) or not (0).
  * **non hispanic**: Binary numeric input, whether the borrower is Non-Hispanic (1) or not (0).
  * **agegte62**: Binary numeric input, whether the borrower's age is over 62 (1) or not (0).
  * **agelt62**: Binary numeric input, whether the borrower's co-borrower's age is over 62 (1) or not (0).

* Link: [hmda_train_preprocessed.zip](https://github.com/jphall663/GWU_rml/blob/master/assignments/data/hmda_train_preprocessed.zip)

## Evaluation Data
* Datasets
  * Home Mortgage Disclosure Act (HMDA) aggregate lending data
* Data Shape
  * Test data rows = 19,832, columns = 22
* All Test Data Columns
  * All the columns are as the same as the training & validation data, except for that the target variable **high priced** column does not exist in this test data.

* Link: [hmda_test_preprocessed.zip](https://github.com/jphall663/GWU_rml/blob/master/assignments/data/hmda_test_preprocessed.zip)

## Quantitative Analysis
* Unitary results:
  * Our best remediated EBM model produced an AUC of **0.8097** after employing several post-processing techniques such as removing outliers and sensitivity analysis to economic recession conditions. This AUC was also achieved while ensuring a minimum Adverse Impact Ratio (AIR) of 0.8.
  * Best training/validation AUC (pre-remediation): **0.8247**
* Intersectional results:
  * Among the models explored (EBM, Ensemble, GBM, MGBM, and GLM), we found that the EBM model produced the greatest fidelity to the true outcomes, while maintaining the highest standards of fairness. We compared not only the AUC results to evaluate the models independently but also cross-validated over a number of evaluation metrics such as ACC, AUC, Log Loss, F1, and MSE. Once we determined the superiority of the EBM class model, we selected it as the best model and continued on to remediation techniques.
* AUC (pre-remediation) of other alternative models:
  * Ensemble: **0.8195**
  * Gradient Boosting Machine (GBM): **0.8183**
  * Monotonic Gradient Boosting Machine (MGBM): **0.8021**
  * Penalized Generalized Linear Model (GLM): **0.7628**

### Partial Dependence Plots:
The partial dependence plot (short PDP or PD plot) shows the "marginal effect one or two features have on the predicted outcome of a machine learning model" (J. H. Friedman 2001).
![Partial Dependence Plots](/img/pdps.png)
![Partial Dependence Plots](/img/pdps2.png)
![Partial Dependence Plots](/img/pdps3.png)
### Global Model Variable Importance:
Global variable importance values give an indication of the magnitude of a variable’s contribution to model predictions for all of the data.
![Global Variable Importance](/img/global_features.png)

## Ethical Considerations
* Although we use the [4/5ths rule](https://www.prevuehr.com/resources/insights/adverse-impact-analysis-four-fifths-rule/), one should aim for full parity where possible in a machine learning model (i.e. 1 to 1 parity in classification)
* Pre-processing remediation techniques should be scrutinized for potential legal issues (e.g. manipulating data with racial class could constitute affirmative action)
* Failure to perform bias testing and remediation of machine learning models can lead to discrimination, which can become self-reinforcing over time
* Our best model underperformed markedly when exposed to economic conditions mimicking a recession, which demonstrates that even the most carefully scrutinized training data can be undermined by shifting real-world conditions
* This model card does not constitute legal or compliance advice
* Further exploration is warranted for our models, but we provide a baseline here
* Additional Reading
  * [Interpretable Models](https://originalstatic.aminer.cn/misc/pdf/Molnar-interpretable-machine-learning_compressed.pdf#:~:text=Interpretable%20Machine%20Learning%20refers%20to%20methods%20and%20models,that%20make%20the%20behavior%20and%20predictionsofmachinelearningsystemsunderstandabletohumans.%20ADatasetisatablewiththedatafromwhichthemachinelearns.Thedatasetcontainsthefeatures%20andthetargettopredict.Whenusedtoinduceamodel%2Cthedatasetiscalledtrainingdata.)
  * ["Black Boxes"](https://y-sbm.com/blog/black-box-in-machine-leraning)
  * [Discrimination in algorithms](https://www.brookings.edu/research/auditing-employment-algorithms-for-discrimination/)

*All models are wrong, but some are useful* - George E. P. Box
