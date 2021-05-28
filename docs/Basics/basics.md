---
layout: default
title:  Basic Computational Software
parent: Computation Basics
has_children: false
has_toc: false
nav_order: 1
---


# Background

The following sections describe the initial actions that are needed before the more useful tutorials in other sections can be run. Each tutorial lists the prerequisites separately, but this will get you started for
general purpose computational work.

# Installing python

Estimated time: 15 minutes

First, get a package management system. Recommended is miniconda (conda): **Conda quickly installs, runs and updates packages and their dependencies.**

https://docs.conda.io/en/latest/miniconda.html.

You can check if you have this successfully by going to the terminal and doing:
```
$ which conda
```

You may need to log out and log back in before you're able to access the `conda` command.

## Start a virtual environment

Use miniconda to create a virtual environment, a restricted workspace where your programs and processes can operate without affecting everything on your computer. Create an environment called flywheel (or something else unique and memorable), in the terminal:
```
$ conda create -n flywheel anaconda python=3
```
At the prompt for which packages to install, type y and hit enter. It’s better to have them all, and they will not take up a lot of space on your machine:
```
:
:
:
$ wurlitzer          pkgs/main/osx-64::wurlitzer-1.0.2-py37_0
$ xlrd               pkgs/main/osx-64::xlrd-1.2.0-py37_0
$ xlsxwriter         pkgs/main/noarch::xlsxwriter-1.1.8-py_0
$ xlwings            pkgs/main/osx-64::xlwings-0.15.8-py37_0
$ xlwt               pkgs/main/osx-64::xlwt-1.3.0-py37_0
$ xz                 pkgs/main/osx-64::xz-5.2.4-h1de35cc_4
$ yaml               pkgs/main/osx-64::yaml-0.1.7-hc338f04_2
$ zeromq             pkgs/main/osx-64::zeromq-4.3.1-h0a44026_3
$ zict               pkgs/main/noarch::zict-1.0.0-py_0
$ zipp               pkgs/main/noarch::zipp-0.5.1-py_0
$ zlib               pkgs/main/osx-64::zlib-1.2.11-h1de35cc_3
$ zstd               pkgs/main/osx-64::zstd-1.3.7-h5bba6e5_0


$ Proceed ([y]/n)?
```

Activate your environment, so that any packages you install or use stay restricted to this project:

```
$ conda activate <your_environment_name>
```

If you ran the `conda create` command above, you would replace `<your_environment_name>` with `flywheel`.

You can make lots of conda environments. It makes sense to have a single environment for Flywheel, but you may want to make separate environments if you're using Python for analysis.

## Install Jupyter

Many of the tutorials here will display Python commands as if they were being entered in an interactive python session (i.e. with a leading `>>>` or `...` if the line is a continuation). If you install `jupyter`, you can paste these directly into a jupyter console session.

```bash
$ conda install jupyter
$ jupyter console
Jupyter console 6.0.0

Python 3.7.2 (default, Dec 29 2018, 00:00:04)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.2.0 -- An enhanced Interactive Python. Type '?' for help.



In [1]:

```

You can now directly paste the Python code (`>>>` included) into the console and it will be run correctly.


## Installing an editor

Writing easily-readable code is very important. A good editor will help you check your code's syntax and can provide hints as you write. One great way to get started is to use the [Atom](https://atom.io/) text editor. A version should be available for your operating system.

Atom lets you install packages that add functionality to the editor. If you go to `Preferences > Packages`, you can search for and install a package called `ide-python` that will help with python development.


## FSL and FSLeyes
[FSLeyes](https://users.fmrib.ox.ac.uk/~paulmc/fsleyes/userdoc/latest/) may not work properly on a personal desktop, PMACS or CUBIC. This is because python27  is  always used to [install FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslInstallation) including (FSLeyes). However, FSLeyes requires python3 to work properly. The fsleyes can be be resintalled  with conda and [fslpython](https://pypi.org/project/fslpy/).

The following steps  are required:
- Try to install [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/) enviroment in  home  or project directory ( for CUBIC)

- Remove previous installed FSLeyes

   This only possible on  a personal desktop as administrative privilege is required:
    ```sh
   rm $FSLDIR/bin/fsleyes
   rm -r $FSLDIR/bin/FSLeyes
   ```

- Install [fslpython](https://pypi.org/project/fslpy/) if not available.

   with pip
   ```bash
    pip install fslpy
    ```
    or  with conda
   ```sh
   conda install -c conda-forge fslpy
    ```

- Install new FSLeyes with conda

  ```sh
  $FSLDIR/fslpython/bin/conda install -n fslpython -c conda-forge fsleyes
  ```

see [here](https://users.fmrib.ox.ac.uk/~paulmc/fsleyes/userdoc/latest/install.html) for more information
