
# Python Set-up

- [Python Set-up](#python-set-up)
  - [Install Python](#install-python)
  - [MiniConda(Recommended) / Conda / Anaconda](#minicondarecommended--conda--anaconda)
  - [Install Necessary Packages](#install-necessary-packages)
  - [Set-up Python Editors](#set-up-python-editors)
    - [Jupyter Notebook Set-up](#jupyter-notebook-set-up)


## Install Python

On Linux

```bash
sudo apt update
sudo apt install build-essential
sudo apt install python3.11 # python version
```

on Mac/Windows, python is built-in (you can upgrade it or choose other distributions in virtual environments )

## [MiniConda(Recommended) / Conda / Anaconda](https://towardsdatascience.com/managing-project-specific-environments-with-conda-b8b50aa8be0e)

Tools to manage python environments

- conda: A cross-language package and environment manager, ideal for data science, supporting a wide range of packages beyond Python.
  - Anaconda: A comprehensive distribution of Python and R for scientific computing, which includes a large collection of pre-installed packages, a package manager (conda), and tools like Jupyter Notebook.
  - Miniconda: A minimal installer for conda, providing just the conda package manager and Python without any pre-installed packages, allowing users to create lightweight environments and install only the packages they need.
  - Conda: The package and environment management system used by both Anaconda and Miniconda, enabling users to install, update, and manage packages and environments efficiently.
- Virtualenv: A third-party tool for creating isolated Python environments, allowing for separate package installations without affecting the global Python setup.
- Venv: A built-in Python module (since 3.3) for creating lightweight isolated environments, offering basic functionality similar to virtualenv but with a simpler interface.

Install [Miniconda](https://docs.anaconda.com/free/miniconda/)

```bash
# Create directory and download Miniconda installation script
mkdir -p ~/miniconda3
# on Linux, follow instructions for other systems
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh

# Run the installation script
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3

# Remove the installation script
rm -rf ~/miniconda3/miniconda.sh

# in your .bashrc or .zshrc file you should find
# export PATH="$HOME/miniconda3/bin:$PATH"

```

Run Conda

```bash
#Initialize conda for shell interaction.
conda init 

# Create a new conda environment named 'd2l' with Python 3.11 (-y is for "yes" in all choices)
conda create --name py1 python=3.12 -y

# Activate a conda environment
conda activate py1

```

## Install Necessary Packages

- pip is the package installer for Python. It allows you to install and manage additional libraries and dependencies that are not included in the Python standard library.
- pip vs conda: conda focus on managing environments and packages from multiple programming languages, while pip is primarily designed for managing Python packages.
  - Use pip if you primarily need to manage Python packages and are comfortable using virtualenv or venv for environment management.
  - Use conda if you need to manage environments and packages from multiple programming languages, or if you are working in data science, machine learning, or scientific computing and prefer the Anaconda ecosystem.

```bash
# to use Conda in Ipython (Interactive Environments Such as the Note books)
conda install ipykernel
# register the environment as a Jupyter kernel using the following command, so it can be selected by jupyter notebooks
python -m ipykernel install --user --name py11 --display-name "Python1 (py12)"

# Create a new Conda environment called py1
conda create -n py1 python

# Activate the Conda environment py1
conda activate py1
```

Install Packages, you can write a bash script (example in this repo) and run 

```bash
chmod +x setup_py1_env.sh
./setup_py1_env.sh
```

or run manually

```bash
# Install numpy and pandas using conda, which is preferred for scientific packages
conda install numpy pandas
# Install Jupyter Notebook using conda, which is preferred for managing environments
conda install jupyter notebook

## Visualization packages
# Install matplotlib using conda, which is preferred for consistency in managing packages
conda install matplotlib
# Install seaborn using conda
conda install seaborn
# Install plotly using conda
conda install plotly

# Common ML Models
# Install scikit-learn using conda
conda install scikit-learn
# Install lightgbm using conda
conda install lightgbm
# Install xgboost using conda
conda install xgboost
# Install bayesian-optimization using pip since it may not be available in conda
pip install bayesian-optimization

# python EDA
# Install graphviz using conda
conda install graphviz
# Install pydotplus using pip, as it may not be available in conda
pip install pydotplus
# Install wheel using conda, it's a utility for building and installing Python packages
conda install wheel
# Install pandas profiling using pip, as it may not be available in conda
pip install pandas-profiling

# interpretable ML
# Install PDPbox using pip, as it may not be available in conda
pip install PDPbox
# Install eli5 using pip, as it may not be available in conda
pip install eli5
# Install shap using conda, if available, otherwise use pip
conda install shap -c conda-forge
# If shap is not available via conda, you can uncomment the following line:
# pip install shap

# use LLM (Large Language Models)
# Install python-dotenv using pip, as it may not be available in conda
pip install -q python-dotenv
# Install openai using pip, as it may not be available in conda
pip install -q openai
```

Install [Pytorch](https://pytorch.org/get-started/locally/#anaconda)

```bash
conda install pytorch torchvision -c pytorch
# or 
# pip3 install torch torchvision
```

Install[Tensorflow2](https://www.tensorflow.org/install)

```bash
conda install tensorflow
# or
# pip install tensorflow
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

## Set-up Python Editors

### Jupyter Notebook Set-up


Install [Jupyter Notebook](https://test-jupyter.readthedocs.io/en/latest/install.html)

```bash
conda install jupyter
```

Set-up

```bash
pip install  jupyterthemes -i <https://pypi.tuna.tsinghua.edu.cn/simple>

# reference : https://bbs.huaweicloud.com/blogs/314114>

jt -t gruvboxd -fs 11 -cellw 85% -ofs 12 -dfs 11 -T

#jt -l 可以看所有可用主题

# 扩展功能：
pip install jupyter_contrib_nbextensions -i <https://pypi.tuna.tsinghua.edu.cn/simple>
jupyter contrib nbextension install --sys-prefix

```

use [config](https://jupyter-notebook.readthedocs.io/en/5.7.4/config.html)

```bash
# Defaults for these options can also be set by creating a file named jupyter_notebook_config.py in your Jupyter folder. The Jupyter folder is in your home directory, ~/.jupyter.

jupyter notebook --generate-config

```

change the following lines in config

```plaintext
c.NotebookApp.iopub_data_rate_limit = 1000000000
c.NotebookApp.ip = "*"
# on remote machine
c.NotebookApp.open_browser=False
# change to a separate file
c.NotebookApp.notebook_dir = 'home/liuxinhe.x/jupyter
```

- VS Code
  - Follow the Instructions [Use Jupyter Notebook with VS Code](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)
  - Click on the kernel picker in the top right corner of the notebook interface (it usually displays the current kernel name).

further reading

- https://www.jianshu.com/p/21ba32a057c4
- [Notebook 7](https://jupyter-notebook.readthedocs.io/en/latest/migrate_to_notebook7.html)