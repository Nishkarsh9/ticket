# SOP: Python Virtual Environment

| Created     | Version | Author          | Comment         | Reviewer |
|-------------|---------|-----------------|-----------------|----------|
| 15-04-2025  | V1      | Nishkarsh Kumar | Internal review | Pritam   |

## Introduction

To isolate Python dependencies and avoid conflicts between project packages by using virtual environments.

---

## Table of Contents

1. [Why python environment?](#why-python-environment)
2. [What is python environment?](#what-is-python-environment)
3. [Commands and usage](#commands--usage)
     - [Creation of Virtual Environment](#1-creation-of-virtual-environment)
     - [Activation](#2-activation)
     - [Package Installation](#3-package-installation)
     - [Freezing Installed Packages](#4-freezing-installed-packages)
     - [Deactivation](#5-deactivation)
     - [Deleting a Virtual Environment](#6-deleting-a-virtual-environment)
5. [Example](#example)
6. [Troubleshooting](#troubleshooting)
     - [Permission Denied](#permission-denied)
     - [Pip Installation Errors](#pip-installation-errors)
7. [Contacts](#contacts)
8. [References](#references)

---

## Why python environment?
Python virtual environments isolate project dependencies, preventing version conflicts across projects.
They ensure consistent, reproducible setups for development, testing, and deployment.

---

## What is python environment?
A Python environment is a self-contained directory that includes a specific Python interpreter and installed packages. It allows you to run and manage Python projects with isolated dependencies.

---
## Commands & Usage

### 1. **Creation of Virtual Environment**

```bash
python3 -m venv venv_name
```
- venv_name: Name of the virtual environment directory.

### 2. Activation

```bash
source venv_name/bin/activate
```

- You should see the environment name prefixed in your terminal prompt.

### 3. Package Installation

```bash
pip install <package_name>
```

Install multiple packages via requirements.txt:

```bash
pip install -r requirements.txt
```

### 4. Freezing Installed Packages

```bash
pip freeze > requirements.txt
```
- This saves the exact versions of all installed packages.

### 5. Deactivation

```bash
deactivate
```
- This will return you to the system’s default Python environment.

### 6. Deleting a Virtual Environment

```bash
rm -rf venv_name
```
- Ensure the environment is deactivated before deletion.

---

## Example
In the context of ot/attendance-api we have used:

 ```bash
poetry config virtualenvs.create true --local
```
This command simply enable creation of a virtual environment locally within the project directory using Poetry.

## Troubleshooting

### Permission Denied
If you see a permissions error while activating:

```bash
chmod +x venv_name/bin/activate
```

Also consider:

```bash
sudo chown -R $USER venv_name/
```

### Pip Installation Errors
If packages fail to install due to permissions:

```bash
python3 -m pip install --upgrade pip
```
Make sure virtualenv is active. If still failing, use:

```bash
pip install --user <package_name>
```


## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |

---

## References

| **Title**                              | **Link**                                                                                      |
|----------------------------------------|-----------------------------------------------------------------------------------------------|
| Python venv Documentation              | [Visit](https://docs.python.org/3/library/venv.html)                                          |
| pip Documentation                      | [Visit](https://pip.pypa.io/en/stable/)                                                       |
