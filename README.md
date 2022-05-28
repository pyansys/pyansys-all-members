# PyAnsys all-members team
Repository for updating the pyansys/all-members team automatically.

## Table of contents

<!--ts-->
   * [Introduction](#introduction)
   * [How does it work?](#how-does-it-work?)
   * [Requirements](#requirements)
<!--te-->


## Introduction
GitHub organizations do not provide an off-the-shelf capability of creating
and maintaining up-to-date an *all-members* team. The goal of the ``update_team`` script
in this repository is to:

* Provided an org and an *all-members* team (i.e. ``@<MY_ORG>/all-members``), update its
members on the execution of this script.
* Provide the capability to automate the update of the members using GitHub Actions.

Feel free to fork this repository for your own application. You are also welcome to help
contribute to it in any possible way! Please submit an issue with any proposal you may have.

## How does it work?
This repository basically contains a simple Python script ``update_team.py``. Within this
script, there are two main variables which a user must take into account:

* ``MY_PAT``: this variable will basically include your personal authentication token in order
to interact with GitHub (using [PyGitHub](https://github.com/PyGithub/PyGithub)). You can also
make use of the automated mechanism, by which the script will search for an environment variable
named ``TOKEN`` which should contain your PAT.
* ``MY_ORG``: the organization whose team *all-members* we want to update.

In order to run it, simply modify these values and run:

```bash
    python update_team.py
```

Bare in mind that this specific version of the script has already set up the ``MY_ORG`` variable
to ``pyansys``, since it the organization for which this repository is oriented.

Furthermore, this repository has a GitHub Actions workflow to automate the update of the team
members on a regular basis (since it has an ``on.schedule`` argument). If you want to make use of
this capability take into account that a PAT must be stored as a repository secret. Check the 
[workflow file](https://github.com/pyansys/pyansys-all-members/blob/main/.github/workflows/team_update.yml)
for further details.

## Requirements
In order to run the previous script, one only needs to install ``pygithub``. In order to ease the
user its installation, we have created a requiorements file: ``requirements.txt``. You can install
the latest version of the package by doing as follows with the ``pip`` package manager:

```bash
    pip install -r requirements.txt
```