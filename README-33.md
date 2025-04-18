# ReactJS Installation Guide

| Created     | Version | Author          | Comment         | Reviewer |
|-------------|---------|-----------------|-----------------|----------|
| 15-04-2025  | V1      | Nishkarsh Kumar | Internal review | Pritam   |

## Introduction
This guide provides a step-by-step process for setting up a ReactJS development environment.

## Table of Contents

1. [Why ReactJS?](#why-reactjs)
2. [What is ReactJS?](#what-is-reactjs)
3. [Prerequisites](#prerequisites)
4. [Step-by-step-installation-guide](#step-by-step-installation-guide)
     - [Update system packages](#1-update-system-packages)
     - [Install nodejs and npm](#2-install-nodejs-and-npm)
     - [Create a React App with Vite](#3-create-a-react-app-with-vite)
     - [Install Dependencies](#4-install-dependencies)
     - [Start-the-local-development-server](#5-start-the-local-development-server)
5. [Troubleshooting](#troubleshooting)
     - [Permission Denied](#if-you-encounter-permission-errors)
     - [Other Error](#if-the-app-doesnt-start)
6. [Contacts](#contacts)
7. [References](#references)

---

## Why ReactJS?
ReactJS is a fast, component-based JavaScript library for building interactive UIs. It simplifies development with reusable components and efficient DOM updates.

## What is ReactJS?
ReactJS is an open-source JavaScript library developed by Facebook for building user interfaces, especially single-page applications. It allows developers to create reusable UI components that efficiently update and render with changing data.

## Prerequisites
Before installing ReactJS, ensure you have the following installed on your Ubuntu system:
 - Node.js (version 14 or later recommended)
 - npm (comes with Node.js) 

## Step-by-Step Installation Guide

### 1. Update System Packages
First, update your package list to ensure you have the latest versions:

```bash
sudo apt update
```
### 2. Install Node.js and npm
React requires Node.js to run.

```bash
sudo apt install nodejs npm
```

Verify the installation:

```bash
node --version
npm --version
```

### 3. Create a React App with Vite
Create React App is the official way to create single-page React applications.

```bash
npm create vite@latest my-react-app -- --template react
```

### 4. Install Dependencies
Navigate to your development directory and create a new React app:

```bash
npm install
```

### 5. Start the local Development Server

```bash
npm run dev
```
This will start the development server at http://localhost:5173.

## Troubleshooting

### If you encounter permission errors:
```bash
sudo chown -R $(whoami) ~/.npm
```
### If the app doesn't start:
 - Ensure you're in the correct directory (the one with package.json)
 - Try clearing npm cache:

      ```bash
       npm cache clean --force
      ```
 - Reinstall dependencies:

      ```bash
       rm -rf node_modules
       npm install
      ```

## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |


## References

| **Title**                              | **Link**                                                                                            |
|----------------------------------------|-----------------------------------------------------------------------------------------------------|
| React Official Documentation           | [Visit](https://reactjs.org/docs/getting-started.html)                                              |
| Node.js Official Installation Guide    | [Visit](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)|

---
