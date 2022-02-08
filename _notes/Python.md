---
layout: post
title: Python
name: Python Notes
---
Notes on Python

{% include breadcrumbs.html %}

## Table of Contents

[Python Virtual Environment](#python-virtual-environment)

[Pyenv](#pyenv)

# Python Virtual Environment

The following steps allow for a user to create a Python virtual environment.
This allows a user to have one or more Python environments where different package combinations can be installed without affecting your system installation of Python.

## Setup PIP

pip is a python package manager. See if you already have pip:

```pip -h```

If you don't hve pip, you can [download and install pip](https://pip.pypa.io/en/latest/installing/)

## Install virtualenv

The virtualenv package allows you create the virtual environments. 
Install it with pip:

```pip install virtualenv```

## Create a Virtual Environment

Create a virtual environment by specifying a path where you would like the installation to live.
Example:

```virtualenv /home/Users/jon.snow/myLittlePython```

This will give us a separate python installation with its own packages that can be activated and used separately from the system Python installation.

## Activate a Virtual Environment

We can activate the python environment:

```source /home/Users/jon.snow/myLittlePython```

Any Python commands that are run while using this terminal will be using the virtual environment that we just created, and will have any libraries that we subsequently install while having this environment active.

## Deactivate a Virtual Environment

To stop using the virtual environment, returning us to the system environment we can simply:
```deactivate```

# Pyenv

Pyenv can make managing multiple versions of python a lot easier. Pyenv allows you to easily select, install and compile specific versions of python for testing and development.

## Setting up PyEnv

Using [Brew](https://brew.sh/)

```bash
brew update
brew install pyenv
```

Install the dependencies requires to build Python.
This includes the Xcode Command Line Tools and a few libraries.

```bash
xcode-select --install
brew install openssl readline sqlite3 xz zlib
```

Then add Pyenv to your path (In this case .zshrc):

```bash
export PYENV_ROOT="$HOME/.pyenv"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
export PATH="$PYENV_ROOT/bin:$PATH"
```

## Installing a Python version

Install the Python version of your choice.
These are installed to $(pyenv root)/versions

```bash
pyenv install <version number>
```

To see what versions are available:

```bash
pyenv install --list
```
