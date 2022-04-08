# [Scikit-Learn](https://scikit-learn.org/stable/) Library

- [Scikit-Learn Library](#scikit-learn-library)
  - [Basics](#basics)
  - [Supervised Learning](#supervised-learning)
  - [Unsupervised Learning](#unsupervised-learning)
  - [Model Training and Model Selection](#model-training-and-model-selection)
- [Pasty](#pasty)
- [StatsModel](#statsmodel)
    - [Basic Usage](#basic-usage)
  - [Additional Libraries](#additional-libraries)
    - [Boosting Trees](#boosting-trees)
    - [H2O](#h2o)
    - [Probabilistic Graphical Models](#probabilistic-graphical-models)
      - [Gaussian Process](#gaussian-process)

## Basics

Data Processing: Use encoders

- [categorical encoders](http://contrib.scikit-learn.org/categorical-encoding/)
- [preprocessing](https://scikit-learn.org/stable/modules/preprocessing.html)

Modeling

1. Instantiate model
2. model.fit
3. model.predict

## Supervised Learning

[Supervised Learning](https://scikit-learn.org/stable/supervised_learning.html)

- [linear\_model](https://scikit-learn.org/stable/modules/linear_model.html)
  - LinearRegression
  - LogisticRegression
  - Lasso
- [tree](https://scikit-learn.org/stable/modules/tree.html)
- ensemble
- [naive\_bayes](https://scikit-learn.org/stable/modules/naive_bayes.html)
  - BernoulliNB
    - alpha for laplace smoothing

## Unsupervised Learning

[unsupervised learning](https://scikit-learn.org/stable/unsupervised_learning.html)

- [neighbors.](https://scikit-learn.org/stable/modules/neighbors.html#)
  - KNeighborsClassifier\(3, weights='distance'\)
- [cluster](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.cluster)
  - KMeans
- decomposition

## Model Training and Model Selection

sklearn.

- [model\_selection](https://scikit-learn.org/stable/model_selection.html)
  - _train\_test\_split\(X, y, test\_size, \[random\_state, stratify\]\)_
  - GridSearchCV
    - tune hyper parameters
  - cross\__val\_score_
- [metrics](https://scikit-learn.org/stable/modules/classes.html)
  - roc\_curve, auc
  - _confusion\_matrix, precision\_score, recall\_score, classification\_report_

---

# Pasty

[Pasty](https://patsy.readthedocs.io/en/latest/)

It is closely inspired by and compatible with the [formula](http://cran.r-project.org/doc/manuals/R-intro.html#Formulae-for-statistical-models) mini-language used in [R](http://www.r-project.org/) and [S](https://secure.wikimedia.org/wikipedia/en/wiki/S_programming_language)

pasty.

- dmatrices\('y~x0+x1\[+0\]\)
  - returns nd array with additional info
    - X.design\_info
  - can use standardize\(x\), center\(x\), C\(x\)
    - C\(x\) - categorical data
      - treat like dummy variable automatically
- _build\_design\_matrices\(&lt;design\_info&gt;, new data\)_

pasty objects can be taken directly to methods like

numpy.linalg

- [lstsq](https://docs.scipy.org/doc/numpy/reference/generated/numpy.linalg.lstsq.html#numpy.linalg.lstsq)

---

# StatsModel

[StatsModels ](https://www.statsmodels.org/stable/index.html)include classical frequentists statistical models like

- Linear Models, generalized linear models
- Linear Mixed Effects Models
- Analysis of Variance methods
- Time Series Processing and State Space Models
- Generalized Methods of Moments

### Basic Usage

**statsmodels.api*- - array based model api

sm.

- add\_constant\(\)
- OLS
  - yields a model
- [tsa](https://www.statsmodels.org/stable/tsa.html) 

**statsmodels.formula.api*- - formula \(pasty-like\) based model api

smf.

- ols

model.

- fit\(\)
- predict\(\)

---

## Additional Libraries

### Boosting Trees

[XGBoost](https://github.com/dmlc/xgboost)

[LightGBM](https://github.com/Microsoft/LightGBM)

Examples

- [Examples of Gradient Boosting](http://arogozhnikov.github.io/2016/06/24/gradient_boosting_explained.html)

### H2O

H2O is a Java-based software for data modeling and general computing. The H2O software is many things, but the primary purpose of H2O is as a distributed \(many machines\), parallel \(many CPUs\), in memory \(several hundred GBs Xmx\) processing engine.

H2O[ algorithms](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science.html)

Vowpal Wabbit

[Vowpal Wabbit](https://github.com/JohnLangford/vowpal_wabbit)

### Probabilistic Graphical Models

[pgmpy](https://pgmpy.org/)

- models
- factor
- sampling

[hmmlearn](https://hmmlearn.readthedocs.io/en/latest/)

[PyMC3](https://docs.pymc.io/)

#### Gaussian Process

[GPy](http://sheffieldml.github.io/GPy/) 

Bayesian Optimization

[GyOpt](http://sheffieldml.github.io/GPyOpt/)

- [Tutorial](https://nbviewer.jupyter.org/github/SheffieldML/GPyOpt/blob/master/manual/index.ipynb)