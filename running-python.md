# Running Python

- [Running Python](#running-python)
  - [Python Interpreters](#python-interpreters)
  - [IDEs](#ides)
  - [Editors](#editors)
  - [Python Installation Tools](#python-installation-tools)
    - [Virtual Environment](#virtual-environment)
  - [Ipython](#ipython)
    - [Features](#features)
      - [Magic Commands](#magic-commands)
    - [Advanced Features](#advanced-features)
  - [Jupyter](#jupyter)
    - [Keyboard Shortcuts](#keyboard-shortcuts)
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

[Jupyter Notebook](https://jupyter.org/) is an web application for creating and sharing computational documents. It offers a simple, streamlined, document-centric experience.

> The notebooks documents are documents produced by the Jupyter Notebook App, which can contain both code (e.g. Python) and rich text elements (paragraphs, equations, links, etc..).
>
>The Jupyter Notebook App is a client-server application that allows editing and running notebook documents by a browser.

- Running on cloud alternatives
  - [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb#recent=true)
  - [Binder](https://gke.mybinder.org/)
- Local Run
  - [Install](https://jupyter.org/install.html)
  - [Run](https://jupyter.readthedocs.io/en/latest/running.html#running)
- [Config Jupyter](https://jupyter-notebook.readthedocs.io/en/stable/config_overview.html)
  - jupyter lab --config=...
  - jupyter notebook...


```shell
# install
pip install jupyter -i <source>
pip install jupyter lab

#launch
jupyter notebook
jupyter lab

```

### Keyboard Shortcuts

Two modes (command/edit mode) for Jupyter Notebook

> Mac and Windows Difference
> 
> - Ctrl: command key ⌘
> - Shift: Shift ⇧
> - Alt: option ⌥

Shortcuts in both modes:

- Shift + Enter run the current cell, select below
- Ctrl + Enter run selected cells
- **Alt + Enter run the current cell, insert below**
- Ctrl + S save and checkpoint

While in command mode (press Esc to activate):

- Enter take you into edit mode
- **H show all shortcuts**
- Up select cell above
- Down select cell below
- Shift + Up extend selected cells above
- Shift + Down extend selected cells below
- A insert cell above
- B insert cell below
- X cut selected cells
- **C copy selected cells**
- **V paste cells below**
- Shift + V paste cells above
- **D, D (press the key twice) delete selected cells**
- **Z undo cell deletion**
- S Save and Checkpoint
- **Y change the cell type to Code**
- **M change the cell type to Markdown**
- Shift + Space scroll notebook up
- Space scroll notebook down
- **P open the command palette.**
  - This dialog helps you run any command by name. It’s really useful if you don’t know some shortcut or when you don’t have a shortcut for the wanted command.

While in edit mode (pressEnter to activate)

- Esc take you into command mode
- **Tab** code completion or indent
- Shift + Tab tooltip
- **Ctrl + ] indent**
- **Ctrl + [ dedent**
- Ctrl + A select all
- Ctrl + Z undo
- Ctrl + Shift + Z or Ctrl + Y redo
- Ctrl + Home go to cell start
- Ctrl + End go to cell end
- Ctrl + Left go one word left
- Ctrl + Right go one word right
- Ctrl + Shift + P open the command palette
- Down move cursor down
- Up move cursor up

## Docker

- for windows, use [kitematic]
- Pure docker: Guide for [windows](https://docs.docker.com/docker-for-windows/), [linux](https://docs.docker.com/engine/installation/), or [macOS](https://docs.docker.com/docker-for-mac/).
- If you want to use your GPU make sure you have [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) and [NVidia driver](https://www.nvidia.com/en-us/drivers/unix/) + [CUDA 10.2](https://developer.nvidia.com/cuda-downloads) installed