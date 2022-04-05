# Running Python

- [Running Python](#running-python)
  - [Python Interpreters](#python-interpreters)
  - [IDEs](#ides)
  - [Editors](#editors)
  - [Python Tools](#python-tools)
    - [Virtual Environment](#virtual-environment)
  - [Ipython](#ipython)
    - [Features](#features)
      - [Magic Commands](#magic-commands)
    - [Advanced Features](#advanced-features)
  - [Jupyter Notebook](#jupyter-notebook)

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

## Python Tools

- pip
  - install [third-party packages](https://pypi.org/)
  - pip3 on Mac and Linux
- [conda](https://docs.conda.io/en/latest/)
- Anaconda
  - suggestion: use [Miniconda](https://docs.conda.io/en/latest/miniconda.html)
- kernel

python3 -m ipykernel install --user --name=py3

### Virtual Environment

Create independent and clean running environment

- use [virtualenv](https://virtualenv.pypa.io/en/latest/user_guide.html)
  - [pipenv and virtualenv](https://docs.python-guide.org/dev/virtualenvs/)
- [use conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
  - conda create -name
  - conda activate
  - conda-env
    - list
    - create
  - conda activate

## Ipython

### Features

- Tab completion &lt;Tab&gt;
  - tab after command
  - object.&lt;tab&gt;
- introspection \(?\) operator after a variable \(object\)
  - ?? show more if possible
- Terminal Shortcuts
  - follow **Emacs*- keys and Linux shell keys
  - Ctrl + Shift + V paste from clipboard
- Command Line history
  - Ctrl + P \(Up\), Ctrl + N \(Down\) : previous or next history \(by %run\) 
  - \__ \_and \_\_ stored previous two commands,
    - \_&lt;n&gt; stores previous nth output
    - \_i&lt;n&gt; previous nth input
      - eval\(\_i27\)

#### [Magic Commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

- %run, %load
  - -d use debugger
    - c\(continue\), s\(step\)
    - !&lt;var&gt; to view variables
    - [debugger commands](https://docs.python.org/2.0/lib/debugger-commands.html)
  - -p 
- %prun - Execute with c profile statement
  - %paste, %cpaste
  - %%prun - profile code block
- %lprun - line profiler
  - uses line\_profiler
  - %lprun -f func1 -f func2 &lt;statement to profile&gt;
- %quickref, %magic - documentation
- %who, who\_ls whos
  - display variable
- %xdel &lt;variable&gt;
  - %reset - delete all variables
- % pdb - use **pdb **to debug
  - %debug : drops you to the stack frame after error is thrown
    - u and d to shift levels
- %page Object
  - pretty print object
- %time, %timeit &lt;statement&gt;
  - time time once, timeit takes multiple runs and average
- command line ones
  - !&lt;cmd&gt;
    - cmd in system shell
    - can combine with current python variables with $
      - ```py
        foo = 'test*' # wildcard
        !ls $foo
        ```
  - %alias &lt;alias\_name&gt; &lt;cmd&gt;
    - give command alias
  - %pwd
  - %bookmark &lt;name&gt; &lt;dir&gt;
    - -b: override and use bookmark location
    - -l: list all bookmarks
  - %cd
    - %pushd, %popd
  - %dirs
  - %ddhist
    - history of visited directories
  - %env
    - environmental variables
- Matplotlib
  - %matplotlib: configure matplotlib options
    - %matplotlib inline

### Advanced Features

- Ipython-Friendly Class
  - \_\__repr\_\_ _methods
- Profiles and [Configuration](https://www.google.com/search?q=create+ipython+config&oq=create+ipython+config&aqs=chrome..69i57j0l2.6031j0j4&sourceid=chrome&ie=UTF-8)
  - _.ipython/profile\_default/ipython\_config.py_
  - .jupyter/
  - ipython --profile=&lt;profile&gt;

## Jupyter

- Running on cloud alternatives
  - [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb#recent=true)
  - [Binder](https://gke.mybinder.org/)
- Local Run
  - [Install](https://jupyter.org/install.html)
  - [Run](https://jupyter.readthedocs.io/en/latest/running.html#running)
- [Config Jupyter](https://jupyter-notebook.readthedocs.io/en/stable/config_overview.html)
  - jupyter lab --config=...
  - jupyter notebook...

## Docker

- for windows, use [kitematic]
- Pure docker: Guide for [windows](https://docs.docker.com/docker-for-windows/), [linux](https://docs.docker.com/engine/installation/), or [macOS](https://docs.docker.com/docker-for-mac/).
- If you want to use your GPU make sure you have [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) and [NVidia driver](https://www.nvidia.com/en-us/drivers/unix/) + [CUDA 10.2](https://developer.nvidia.com/cuda-downloads) installed


