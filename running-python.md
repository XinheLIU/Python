# Running Python

- [Running Python](#running-python)
  - [Python Interpreters](#python-interpreters)
  - [IDEs](#ides)
  - [Editors](#editors)
  - [Python Installation Tools](#python-installation-tools)
    - [Virtual Environment](#virtual-environment)
  - [Ipython and Jupyter Notebook](#ipython-and-jupyter-notebook)
  - [Docker](#docker)

## Python Interpreters

- Cpython
  - default python intepreter
- Ipython
  - interactive
- Pypy
  - [difference between PyPy and Cpython](https://pypy.readthedocs.io/en/latest/cpython_differences.html)
- JPython
  - on Java platform and translate to java bytecode
- IronPython
  - .Net platform, translate to bytecodes

## IDEs

- VS Code
- PyCharm

## Editors

- [Vim](https://realpython.com/vim-and-python-a-match-made-in-heaven/)
  - [Full stack python with Vim](https://www.fullstackpython.com/vim.html)
- [Emacs](https://realpython.com/emacs-the-best-python-editor/)

## Python Installation Tools

- pip
  - install [third-party packages](https://pypi.org/)
  - pip3 on Mac and Linux
- [conda](https://docs.conda.io/en/latest/)
- Anaconda
  - suggestion: use [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
- kernel

```shell
# install kernel
python3 -m ipykernel install --user --name=py3

```

### Virtual Environment

Create independent and clean running environment

- use [virtualenv](https://virtualenv.pypa.io/en/latest/user_guide.html)
  - [pipenv and virtualenv](https://docs.python-guide.org/dev/virtualenvs/)
- [use conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

```shell
# conda commands
conda info -e # check environments
# same
conda-env list
# create environment named py38name
conda create -n py38name python=3.8
# same, based on an environment file
conda-env create <name>
# remove it
conda create -n py38name --all
# activate (environment)
conda activate py38name
# deactivate
conda deactivate 
```

## [Ipython and Jupyter Notebook](running-python/ipython-and-jupyter-notebook.md)


## Docker

- for windows, use [kitematic]
- Pure docker: Guide for [windows](https://docs.docker.com/docker-for-windows/), [linux](https://docs.docker.com/engine/installation/), or [macOS](https://docs.docker.com/docker-for-mac/).
- If you want to use your GPU make sure you have [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) and [NVidia driver](https://www.nvidia.com/en-us/drivers/unix/) + [CUDA 10.2](https://developer.nvidia.com/cuda-downloads) installed