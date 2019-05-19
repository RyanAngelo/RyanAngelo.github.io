---
layout: post
title:  "Creating a Python Virtual Environment"
date:   2019-05-19 09:00:00 -0400
categories: Python
tags: Python
author: Ryan Angelo
---

{% include nav.html %}

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

{% include nav.html %}