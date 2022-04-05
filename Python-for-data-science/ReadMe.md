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

