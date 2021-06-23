# Model Card

### *Team Information*

GWU Student Members
* Zach Vila (zrvila)
* Minhye Kim (minhyekimlee)
* Tivon Johnson (tivonj)
* Qunzhe Ding (dingqunzhe1222)

## Model Details
Our group has developed interpretable machine learning models as a part of our semester project in the Responsible Machine Learning class taught by Professor Hall during the Summer Semester in 2021. We have used Home Mortgage Disclosure Act historic mortgage reporting data to predict the probability of applicants being charged a higher rate for their mortgages. In order to address growing concerns on risks of black box machine learning models deployed to highly impactful social areas without much needed contemplation and precaution on adverse effects, we demonstrate available techniques to interpret and explain predictive models to prevent unjust discrimination, improve security and encourage ethical decisions.

### Basic Information
* Model date: June 2021
* Model version: 1.0
* Model types: EBM, MGBM, Ensenble 
* Information about training algorithms, parameters, fairness constraints or other applied approaches, and features
* Paper or other resource for more information
* Citation details
* [License](https://github.com/zrvila/Interpretable-Machine-Learning/blob/main/LICENSE)
* Where to send questions or comments about the model

## Intended Use
### Use cases that were envisioned during development.
* Primary intended uses
* Primary intended users
* Out-of-scope use cases

## Factors
### Factors could include demographic or phenotypic groups, environmental conditions, technical attributes, or others listed in Section 4.3.
* Relevant factors
* Evaluation factors

## Metrics
### Metrics should be chosen to reflect potential realworld impacts of the model.
* Model performance measures
* Decision thresholds
* Variation approaches

## Evaluation Data
### Details on the dataset(s) used for the quantitative analyses in the card.
* Datasets
* Motivation
* Preprocessing

## Training Data
### Mirror Evaluation Data
If such detail is not possible, minimal allowable information
should be provided here, such as details of the distribution
over various factors in the training datasets.

## Quantitative Analysis
* Unitary results:
  * Our best remediated EBM model produced an AUC of **0.7804** after employing sevral post-processing techniques such as removing outliers and sensitivity analysis to economic recession conditions. 100 model iterations were trained on the data utilizing a 70/30% training/validation split.
  Best training/validation AUC (pre-remediation): **0.8247**
* Intersectional results:
  * Among the models explored (Ensemble, GML, MGBM, EBM) we found that the EBM model produced the greatest fidelity to the true outcomes. We compared AUC results to evaluate the  models independently, and once we determined the superiority of the EBM class model, we continued on to remediation techniques.
### Visualizations

![Partial Dependence Plots](/img/pdps.png)
![Partial Dependence Plots](/img/pdps2.png)
![Partial Dependence Plots](/img/pdps3.png)

![Global Variable Importance](/img/global_features.png)

## Ethical Considerations
* Although we use the 4/5ths rule, one should aim for full parity where possible in a machine learning model (i.e. 1 to 1 parity in classification)
* Pre-processing remediation techniques should be scrutinized for potential legal issues (e.g. manipulating data with racial class could consitute affirmative action)
* Failure to perform bias testing and remediation of machine learning models can lead to discrimination, which can become self-reinforcing over time
 
## Caveats and Recommendations
* See 4/5ths Rule: https://www.prevuehr.com/resources/insights/adverse-impact-analysis-four-fifths-rule/
* This model card does not consitute legal advice
* Further exploration is warranted for our models, but we provide a baseline here

*All models are wrong, but some are useful* - George E. P. Box
