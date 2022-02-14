# Credit Risk Analysis
> *by Nelson Buainain, February 2020*

## Description

A notebook with data processing, exploratory analyses and modeling to solve a credit loan risk problem. 

## The problem

Acme is a retail company that sells different items to its customers. To increase its sales, it decided to grant credit to these customers based on an automatic risk model. More specifically, given various information about a customer C, obtained at the time of the credit request, the company wants to infer the risk associated with C. Risk is understood as the probability that C will not pay the debt he has acquired in the following months, thus becoming a bad payer.

To this end, Acme collected data from requesting customers during the months of August and September 2015, recording their performance as good or bad payers in subsequent months. 

## The goal

The task is to propose a predictive model using Python's sklearn-based machine learning stack that identifies bad payers.

## Install

You will Python, Jupyter-notebook and a few Python modules to run all the analyses. 

* Intructions to install Python3 can be found [here](https://www.python.org/downloads/)

* Intructions to install Jupyter-notebook can be found [here](https://docs.jupyter.org/en/latest/install.html)

* To install the necessary Python Modules type:

```Python
pip3 install -r requirements.txt
```


## Data processing 

Data was inspected in order to search for:

1) Missing data
2) Outliers
3) Data out of shape 
4) abdormal distributions
5) Unbalancing

## Data transformation

* A few rows with missing data were removed
* Some categorical variables were transformed to dummy (binary)

## Exploratory Analyses

Data was inspected to look for:

* Variables that could potentially explain the target variable

* Variables that were potentially correlated

PCA was used to reduce dimensionality of data and see if the problem was spatially separable by the different PCs. 

## Data modeling

According to some recent papers:

**1)** Balacing the data and coding category variables as binary significantly improves data modeling in Credit Risk analyses [Fenerich et al. 2020](https://www.scipedia.com/public/Fenerich_et_al_2020a)

 **2)** Random Forest ([Aniceto et al. 2020](https://fbj.springeropen.com/articles/10.1186/s43093-020-00041-w)) and XGBoost [Wang et al. 2022](https://www.sciencedirect.com/science/article/pii/S1877050922001442) Perform really well in Credit Risk analyses.

 Therefore we focused our analyses in these two algorithms.

We have also tested the effect of following processing methods over a preliminary Random Forest model which performs well "out of the box" with most problems and data:

1) Balancing the data

2) Feature selection

3) Data normalization

4) Data dimensionality reduction

5) Remove uncorrelated features

6) Remove outliers

**Evaluation Metric**
* Because the goal is to identify badpayers (i. e. reduce the cost of False Negative, this is, say a bad client is a good payers) the recall metric, especially of the badpayers, was used as the main metric to evaluate the models

 ## Results

 * The only processing method that expressively improved our model was Balacing the two target variables.

* The two final tuned models (RF and XGBoost) performed well in identifying bad payers with a high Recall score 

* AUC metrics were above 0.90, recall scores of bad payers were 0.98 in both models

* Both models performed similar, RF was slower but less redundant regarding the variables used and favored the continuous variables. XGBoost was much faster and more redundant because it favored the categorical dummy variables

* Badpayers are younger, with smaller salary income, residence and employment time, and smaller value for debt_score. Good and bad payers also differ in debit and marital profiles. Because the database did not come with a dictionary it is not possible to further interpret the results from the categorical data


## Conclusions

* Random Forests and XGBoost perform well in identifying badpayers in Credit Risk Analyses

* Balancing the data improves data modeling in Credit Risk Analyses
