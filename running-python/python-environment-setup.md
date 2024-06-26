
# Python Set-up

- [Python Set-up](#python-set-up)
  - [Install Python](#install-python)
  - [Install MiniConda(Recommended) / Conda / Anaconda](#install-minicondarecommended--conda--anaconda)
    - [Install Python Packages](#install-python-packages)
  - [Install PyTorch/Tensorflow](#install-pytorchtensorflow)
  - [Jupyter Notebook \& Iptython](#jupyter-notebook--iptython)

## Install Python
On Linux

```bash
sudo apt update
sudo apt install build-essential
sudo apt install python3.11

```


## [Install MiniConda(Recommended) / Conda / Anaconda](https://towardsdatascience.com/managing-project-specific-environments-with-conda-b8b50aa8be0e)

Install [Miniconda](https://docs.anaconda.com/free/miniconda/)

```bash
# Create directory and download Miniconda installation script
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh

# Run the installation script
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3

# Remove the installation script
rm -rf ~/miniconda3/miniconda.sh

```

Run Conda

```bash
# Initialize conda (add conda to your shell's PATH)
~/miniconda3/bin/conda init

# Create a new conda environment named 'd2l' with Python 3.11
conda create --name d2l python=3.11 -y

# Activate the 'd2l' conda environment
conda activate d2l

```

### Install Python Packages

- pip is the package installer for Python. It allows you to install and manage additional libraries and dependencies that are not included in the Python standard library. 
- pip vs conda: conda focus on managing environments and packages from multiple programming languages, while pip is primarily designed for managing Python packages.
  - Use pip if you primarily need to manage Python packages and are comfortable using virtualenv or venv for environment management.
  - Use conda if you need to manage environments and packages from multiple programming languages, or if you are working in data science, machine learning, or scientific computing and prefer the Anaconda ecosystem.


```bash

# no need if miniconda is there
pip install numpy pandas
pip install jupyter notebook

## Visualization packages
pip install matplotlib
pip install seaborn
pip install plotly

# Common ML Models
pip install scikit-learn  # -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install lightgbm
pip install xgboost
pip install bayesian-optimization


# python EDA
pip install graphviz pydotplus
pip install wheel pandas profiling 
 
# interpretable ML
pip install PDPbox
pip install eli5
pip install shap


# use LLM
pip install -q python-dotenv
pip install -q openai

```

Use in Python

```python
import numpy as np
import pandas as pd
# visluzation
import matplotlib.pyplot as plt
import plotly.express as px
import seaborn as sns
%matplotlib inline

# stats
import statsmodels.api as sm
from scipy import stats

# optional
import warnings
warnings.filterwarnings('ignore')
```

## Install PyTorch/Tensorflow

Install [Pytorch](https://pytorch.org/get-started/locally/#anaconda)

```bash
conda install pytorch torchvision -c pytorch
# or 
pip3 install torch torchvision
```

Install[Tensorflow2](https://www.tensorflow.org/install)

```bash
conda install tensorflow
# or
pip install tensorflow
```

optional: install d2l

```bash
pip install d2l==0.17.6 #chinese
pip install d2l==1.0.3 # Eng
mkdir d2l-en && cd d2l-en
curl https://d2l.ai/d2l-en-1.0.3.zip -o d2l-en.zip
unzip d2l-en.zip && rm d2l-en.zip
cd pytorch # or tensowflow

```

## [Jupyter Notebook & Iptython](ipython-and-jupyter-notebook.md)