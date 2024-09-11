# Poetry setup guide to create a local environment

## Introduction

This guide walks you through setting up a local Python environment using Poetry, a tool for dependency management and packaging in Python. Follow the steps below to configure your project environment.

## Setup

**Step 1**. Install Poetry

Run the following command to install Poetry:

```bash
pip install poetry
```

**Step 2**. Initialize the project

Run the following command to initialize Poetry:

```bash
poetry init
```

Follow the prompts in the terminal to configure your project.

Some of the questions to answer or skip:

```
Package name [package name]:  
Version [0.1.0]:  
Description []:  
Author [user name, n to skip]:  
License []:  
Compatible Python versions [^3.12]:
```

This will generate the pyproject.toml file, which defines your project's dependencies and settings.

**Step 3**. Install dependencies

To install the project's dependencies, run:

```bash
poetry install
```

This will create a poetry.lock file, which locks the specific versions of the dependencies.

**Step 4**. Update dependencies

If you make changes to the pyproject.toml file and need to update the dependencies, use:

```bash
poetry update
```

**Step 5**. View environment info

To check details such as where the virtual environment is located, run:

```bash
poetry env info
```

