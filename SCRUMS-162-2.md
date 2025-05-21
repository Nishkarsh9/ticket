# Proof of Concept: Python Code Compilation Check with `py_compile`

| Last Updated | Version | Author          | Comment         | Reviewer |
|--------------|---------|-----------------|-----------------|----------|
|  21-05-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

## 📑 Table of Contents

1. [Introduction](#introduction)  
2. [Prerequisites](#prerequisites)  
3. [Step 1: Navigate to Project Directory](#step-1-navigate-to-project-directory)  
4. [Step 2: Basic Compilation Check](#step-2-basic-compilation-check)  
   - [Check a Single File (`app.py`)](#check-a-single-file-apppy)  
   - [Check All Python Files Recursively](#check-all-python-files-recursively)  
   - [Expected Outcomes](#expected-outcomes)  
     - [1. Successful Compilation (No Output)](#1-successful-compilation-no-output)  
     - [2. Failed Compilation (Error Output)](#2-failed-compilation-error-output)  
5. [Contact](#contact)  
6. [References](#references)  


## Introduction
Demonstrate how to use Python's built-in `py_compile` module to check for syntax errors in the Attendance API codebase.

## Prerequisites
- Python 3.x installed

---

## Step 1: Navigate to Project Directory

```bash
cd ~/attendance-api or notification-worker
```
**For Attendance-api:**
![1](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20153033.png)

**For Notification-worker:**
![2](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20155718.png)
## Step 2: Basic Compilation Check

### Check a Single File (`app.py`)

```bash
python3 -m py_compile app.py
```
**For Attendance-api:**
![3](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20155317.png)

**For Notification-worker:**
![4](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20155805.png)

### Check All Python Files Recursively

```bash
find . -name "*.py" -exec python3 -m py_compile {} +
```
### Expected Outcomes

#### 1. Successful Compilation (No Output)

When all files compile successfully:

```bash
$ python3 -m py_compile app.py
# No output means success

**Verification:**

```bash
ls __pycache__/
# Should show compiled .pyc files
```
#### 2. Failed Compilation (Error Output)

When errors exist:

```bash
$ python3 -m py_compile app.py
```
**output:**
  File "app.py", line 15
    return user_id == None
                ^
SyntaxError: invalid syntax

## Contact

| **Name**    | **Email**                |
|-------------|--------------------------|
| Nishkarsh Kumar     | nishkarsh.kumar.snaatak@mygurukulam.co  |


## References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| Python py_compile Documentation       | [Visit](https://docs.python.org/3/library/py_compile.html) |  
| Python Official Tutorial: Errors and Exceptions                  | [Visit](https://docs.python.org/3/tutorial/errors.html) | 
