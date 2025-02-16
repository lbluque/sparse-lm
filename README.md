<img src="docs/_static/logo.png" width="500px" alt=" ">

Sparse Linear Regression Models
===============================

[![test](https://github.com/CederGroupHub/sparse-lm/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/CederGroupHub/sparse-lm/actions/workflows/test.yml)
[![Codacy Badge](https://app.codacy.com/project/badge/Coverage/9b72db506d9c49b2a6c849348de8945e)](https://www.codacy.com/gh/CederGroupHub/sparse-lm/dashboard?utm_source=github.com&utm_medium=referral&utm_content=CederGroupHub/sparse-lm&utm_campaign=Badge_Coverage)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/CederGroupHub/sparse-lm/main.svg)](https://results.pre-commit.ci/latest/github/CederGroupHub/sparse-lm/main)
[![pypi version](https://img.shields.io/pypi/v/sparse-lm?color=blue)](https://pypi.org/project/sparse-lm)
[![Static Badge](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/downloads/)


**sparse-lm**  includes several (structured) sparse linear regression estimators that are absent in the
`sklearn.linear_model` module. The estimators in **sparse-lm** are designed to fit right into
[scikit-learn](https://scikit-learn.org/stable/index.html), but the underlying optimization problem is expressed and
solved by leveraging [cvxpy](https://www.cvxpy.org/).

---------------------------------------------------------------------------------------

Available regression models
---------------------------
- Lasso, Group Lasso, Overlap Group Lasso, Sparse Group Lasso & Ridged Group Lasso.
- Adaptive versions of Lasso, Group Lasso, Overlap Group Lasso, Sparse Group Lasso & Ridged Group Lasso.
- Best Subset Selection, Ridged Best Subset, L0, L1L0 & L2L0 (all with optional grouping of parameters)

Installation
------------
**sparse-lm** is available on [PyPI](https://pypi.org/project/sparse-lm/), and can be installed via pip:

```bash
pip install sparse-lm
```

Additional information on installation can be found the documentation [here](https://cedergrouphub.github.io/sparse-lm/install.html).

Basic usage
-----------
If you already use **scikit-learn**, using **sparse-lm** will be very easy. Just use any
model like you would any linear model in **scikit-learn**:

```python
import numpy as np
from sklearn.datasets import make_regression
from sklearn.model_selection import GridSearchCV
from sparselm.model import AdaptiveLasso

X, y = make_regression(n_samples=100, n_features=80, n_informative=10, random_state=0)
alasso = AdaptiveLasso(fit_intercept=False)
param_grid = {'alpha': np.logspace(-8, 2, 10)}

cvsearch = GridSearchCV(alasso, param_grid)
cvsearch.fit(X, y)
print(cvsearch.best_params_)
```

For more details on use and functionality have a look at the
[examples](https://cedergrouphub.github.io/sparse-lm/auto_examples/index.html) and
[API](https://cedergrouphub.github.io/sparse-lm/api.html) sections of the documentation.

Contributing
------------

We welcome any contributions that you think may improve the package! Please have a look at the
[contribution guidelines](https://cedergrouphub.github.io/sparse-lm/contributing.html) in the documentation.
