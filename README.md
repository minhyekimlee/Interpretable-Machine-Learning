# Model Card

### *Team Information*

GWU Student Members
* Zach Vila (zrvila)
* Minhye Kim (minhyekimlee)
* Tivon Johnson (tivonj)
* Qunzhe Ding (dingqunzhe1222)

## Model Details

Our group has developed interpretable machine learning models as a part of our semester project in the Responsible Machine Learning class taught by Professor Hall during the Summer Semester in 2021. We have used Home Mortgage Disclosure Act historic mortgage reporting data to predict the probability of applicants being charged a higher rate for their mortgages. In order to address and mitigate growing concerns on risks of black box machine learning models deployed to highly impactful social areas without much needed contemplation and precaution on adverse effects, we demonstrate available techniques to interpret and explain predictive models to prevent unjust discrimination, improve security and encourage ethical decisions.

### Basic Information
* Model date: June 2021
* Model version: 1.0
* Model types: 
  * Explainable Boosting Machines (EBM)
  * Monotonic Gradient Boosting Machine (MGBM)
  * Ensemble
  * Penalized Gradual Machine Learning (GML)
* Paper or other resource for more information
  * [The Elements of Statistical Learning](https://web.stanford.edu/~hastie/ElemStatLearn/)
  * [Generalized Additive Models](https://www.routledge.com/Generalized-Additive-Models/Hastie-Tibshirani/p/book/9780412343902)
  * [Responsible Artificial Intelligence](https://www.springer.com/gp/book/9783030303709)
* [License](https://github.com/zrvila/Interpretable-Machine-Learning/blob/main/LICENSE)
* Where to send questions or comments about the model
  * Please refer to “Team Information” section.

## Intended Use

* Primary intended uses
  * The primary intended use is to provide an interpretable machine learning model that helps explain predictions as opposed to black box models which provide little, if any, explanation. Such transparency may help prevent bias and discrimination that can occur with black-box models as it relates to applicants with higher mortgage rates.
* Primary intended users
  * The primary intended users of this model are professors, students, and researchers of interpretable machine learning models.
* Out-of-scope use cases
  * This model is for educational purposes and not intended to evaluate real-world credit worthiness.

## Factors

* Relevant factors
  * Since our project goal is to determine if the annual percentage rate (APR) charged for a mortgage is High-priced(or not), which we consider as one of many issues that perpetuates a massive disparity in overall wealth between different demographic groups in the US. As a result, a demographic factor that if a mortgage is belonging to a white or minority(black, asian, latin...) family should be include, and we supposed that white family are more likely to get a low-priced mortgage and minority family are more likely to get a High-priced mortgage.    
  * From our common sense, a high-amount and long-period mortgage usually result in a comparetively higher APR(since the financial institutions are correspondingly taking on more risk), so we thought high-amount and long-period mortgage are two foreseeable salient factors could make our model performance vary.
* Evaluation factors
  * Accoring to our dataset, the factors that if the mortage is high-priced are being reported(showed as loan amount std), the reason why was these chosen is because it is a imporant features of the mortgage. According to our feature importance,the loan amount is 4th importance toward our preditive object. 

## Metrics

* Model performance measures
  * In our project, we choose Area Under the Curve (AUC) as the evaluation metric of the model: in machine learining, AUC is one of the most important evaluation metrics for checking the model’s performance in classification.
* Decision thresholds
  * Typically, an excellent model has AUC near to the 1 and a poor model has an AUC near 0, if a model's AUC is 0.5, it means the model has no class separation capacity. In our project, we didn't set decision thresholds of the AUC, but we select our best model (EBM), with the highest AUC which is **0.82472**(pre-remediation), **0.7804**(remediation).
* Variation approaches
  * Our EBM model Grid search runs through 100 iterations
  * We split our data by 70/30% training/validation

## Evaluation Data
* Datasets
  * Home Mortgage Disclosure Act (HMDA) historic mortgage reporting data  
* Motivation
* Preprocessing
  * This data contains no major quality issues, so no preprocessing was required.  
* Link

## Training Data
* Datasets
  * Home Mortgage Disclosure Act (HMDA) historic mortgage reporting data
  * The same data was used to create training and validation partitions.  
* Link

## Quantitative Analysis
* Unitary results:
  * Our best remediated EBM model produced an AUC of **0.7804** after employing sevral post-processing techniques such as removing outliers and sensitivity analysis to economic recession conditions. This AUC was also achieved when ensuring a minimum Adverse Impact Ratio (AIR) of 0.8.
  * Best training/validation AUC (pre-remediation): **0.8247**
* Intersectional results:
  * Among the models explored (Ensemble, GML, MGBM, EBM) we found that the EBM model produced the greatest fidelity to the true outcomes, while maintaining the highest standards of fairness. We compared AUC results to evaluate the  models independently, and once we determined the superiority of the EBM class model, we continued on to remediation techniques.
### Visualizations

**Partial Dependence Plots:**
The partial dependence plot (short PDP or PD plot) shows the "marginal effect one or two features have on the predicted outcome of a machine learning model" (J. H. Friedman 2001).

![Partial Dependence Plots](/img/pdps.png)
![Partial Dependence Plots](/img/pdps2.png)
![Partial Dependence Plots](/img/pdps3.png)

**Global Model Variable Importance:**
Global variable importance values give an indication of the magnitude of a variable’s contribution to model predictions for all of the data.

![Global Variable Importance](/img/global_features.png)

## Ethical Considerations
* Although we use the 4/5ths rule, one should aim for full parity where possible in a machine learning model (i.e. 1 to 1 parity in classification)
* Pre-processing remediation techniques should be scrutinized for potential legal issues (e.g. manipulating data with racial class could consitute affirmative action)
* Failure to perform bias testing and remediation of machine learning models can lead to discrimination, which can become self-reinforcing over time
 
## Caveats and Recommendations
* See 4/5ths Rule: https://www.prevuehr.com/resources/insights/adverse-impact-analysis-four-fifths-rule/
* This model card does not consitute legal advice
* Further exploration is warranted for our models, but we provide a baseline here
* Additional Reading
  * [Interpretable Models](https://originalstatic.aminer.cn/misc/pdf/Molnar-interpretable-machine-learning_compressed.pdf#:~:text=Interpretable%20Machine%20Learning%20refers%20to%20methods%20and%20models,that%20make%20the%20behavior%20and%20predictionsofmachinelearningsystemsunderstandabletohumans.%20ADatasetisatablewiththedatafromwhichthemachinelearns.Thedatasetcontainsthefeatures%20andthetargettopredict.Whenusedtoinduceamodel%2Cthedatasetiscalledtrainingdata.)
  * ["Black Boxes"](https://y-sbm.com/blog/black-box-in-machine-leraning)
  * [Discimination in algorithms](https://www.brookings.edu/research/auditing-employment-algorithms-for-discrimination/)

*All models are wrong, but some are useful* - George E. P. Box
