# POC: Frontend

| Created     | Last Updated | Version | Author          | Comment         | Reviewer |
|-------------|--------------|---------|-----------------|-----------------|----------|
| 25-04-2025  |  25-04-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

---

## Table of Contents

1. [Introduction](#introduction)  
2. [Purpose](#purpose)  
3. [System Requirements](#system-requirements)
4. [Prerequisites](#prerequisites)
5. [Ports Required](#ports-required)  
6. [Commands to setup](#commands-to-setup)      
7. [Contact](#contact)  
8. [References](#references)

---

## Introduction

This document provides a Proof-of-Concept (PoC) for setting up and running the Frontend of the OT-Microservices project. The frontend is developed using ReactJS, a popular JavaScript library for building user interfaces.

## Purpose

The primary goal of this PoC is to demonstrate the setup and execution of the ReactJS-based frontend within the OT-Microservices ecosystem. This frontend serves as the visual interface through which users interact with underlying microservices such as Employee, Attendance, and Salary microservices.

## System Requirements

| Component        | Minimum Requirement           |
|------------------|-------------------------------|
| OS               | Ubuntu or other Linux-based   |
| Disk Space       | 8 GB                         |
| RAM              | 2 GB                          |
| Processor        | Single-core                     |
| Instance Type    | t2.small                      |

---

## Prerequisites

| Tool        | Description |
|--------------|-------------|
| **Node.js**  | JavaScript runtime for running build and dev tasks. |
| **NPM**      | Node Package Manager for installing project libraries. |
| **make**| Build automation tool used to simplify and execute project build steps |

---

## Ports Required

| Port | Used By     | Description                                      |
|------|-------------|--------------------------------------------------|
| 22   | SSH         | Used for secure remote login and VM access.     |
| 3000 | React App   | Default port used by React development server.  |

---

## Commands to setup

### 1. Update Package Index

**Follow Step 3 here**: [Ubuntu Basic System Commands](https://github.com/snaatak-Downtime-Crew/Documentation/tree/main/common_stack/operating_system/ubuntu/sop/commoncommands#1-basic-system-commands)

![update-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20221405.png)


### 2.  Install Node.js and NPM

**Follow Step 2 here**: [SOP for NPM](https://github.com/snaatak-Downtime-Crew/Documentation/blob/shivani_scrums_36/common_stack/application/reactjs/npm/sop/README.MD#step-2-check--install-nodejs-and-npm)

![nodejs-npm-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20221756.png)


### 3. Install make

**Follow Step 2 here**: [SOP for Make](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/others/make/sop/README.md#installation-on-linux)

![make-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20221857.png)


### 4. Clone the repository

```bash
git clone https://github.com/OT-MICROSERVICES/frontend.git 
```
![clone-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20221952.png)


### 5. Set the enviornment variable

```bash
export NODE_OPTIONS=--openssl-legacy-provider
```

![env-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222022.png)


### 6. Install the dependencies and build the react app

change the directory and move inside the frontend, then run:

```bash
make build
```

![make-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222345.png)


![make-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222521.png)


###    Alternate Command:

```bash
npm install
npm run build
```

### 7. Launch the React development server

```bash
npm start
```

![clone-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222631.png)


![clone-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222721.png)


![clone-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222631.png)



Starts a development server (usually on http://<public_ip>:3000):

![clone-command](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-25%20222745.png)

---

## Contact

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |


## References

| **Title**                              | **Link**                                                                                        |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| Node.js Official Docs                  | [Visit](https://nodejs.org/en/download/package-manager) |
| NPM Documentation               | [Visit](https://docs.npmjs.com/)                                 |
| React Official Documentation               | [Visit](https://reactjs.org/docs/getting-started.html)                                 |

---
