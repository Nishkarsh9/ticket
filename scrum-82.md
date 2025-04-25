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
5. [Commands to setup](#commands-to-setup)      
6. [Contact](#contact)  
7. [References](#references)

---

## Introduction

This document provides a Proof-of-Concept (PoC) for setting up and running the Frontend of the OT-Microservices project. The frontend is developed using ReactJS, a popular JavaScript library for building user interfaces.

## Purpose

The primary goal of this PoC is to demonstrate the setup and execution of the ReactJS-based frontend within the OT-Microservices ecosystem. This frontend serves as the visual interface through which users interact with underlying microservices such as Employee, Attendance, and Salary modules.

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

## Commands to setup

### 1. Update Package Index


### 2.  Install Node.js

```bash
sudo apt install nodejs
```

### 3. Install npm

```bash
sudo apt install npm
```

### 4. Install make

```bash
sudo apt install make
```

### 5. Clone the repository

```bash
git clone https://github.com/OT-MICROSERVICES/frontend.git 
```

### 6. Set the enviornment variable

```bash
export NODE_OPTIONS=--openssl-legacy-provider
```

### 7. Install the dependencies and build the react app

```bash
make build
```

### Alternate

```bash
npm install
npm run build
```

### 7. Launches the React development server

```bash
npm start
```

## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |

## References

| **Title**                              | **Link**                                                                                        |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| Node.js Official Docs                  | [Visit]([https://nodejs.org/en/download/package-manager]) |
| NPM Documentation               | [Visit](https://docs.npmjs.com/)                                 |
| React Official Documentation               | [Visit](https://reactjs.org/docs/getting-started.html)                                 |
