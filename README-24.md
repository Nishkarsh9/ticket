## Java Installation via Bash Script

| Created     | Version | Author          | Comment         | Reviewer |
|-------------|---------|-----------------|-----------------|----------|
| 16-04-2025  | V1      | Nishkarsh Kumar | Internal review | Pritam   |

## Introduction

This repository contains a generic bash script for installing and managing multiple versions of Java on Linux systems. The script supports installation of different Java versions, upgrades, and switching between installed versions.

## Table of Contents

1. [Why Java?](#why-java)
2. [What is Java?](#what-is-java)
3. [Commands and usage](#commands--usage)
     - [Download the script](#1-download-the-script)
     - [Make script executable](#2-make-script-executable)
     - [Run the script](#3-run-the-script)
4. [Options](#options)
5. [Environment configuration](#environment-configuration)
6. [Supported java versions](#supported-java-versions)
7. [Contacts](#contacts)
8. [References](#references)


## Why Java?

Java is a platform-independent, object-oriented programming language used to build scalable, secure, and high-performance applications. Its "write once, run anywhere" capability makes it ideal for web, enterprise, and mobile development.

## What is Java?

Java is a high-level, class-based, object-oriented programming language designed to have as few implementation dependencies as possible. It is widely used for building cross-platform applications, from web and enterprise software to mobile and embedded systems.

## Commands & Usage

### 1. **Download the script**

```bash
wget https://java-installl.s3.ap-south-1.amazonaws.com/install_java.sh
```

### 2. Make script executable

```bash
wget https://java-installl.s3.ap-south-1.amazonaws.com/install_java.sh
```

### 3. Run the script

```bash
./install_java.sh [options]
```

## Options

| Option        | Description                                                       |
|---------------|-------------------------------------------------------------------|
| `-v <version>`| Specify Java version (`8`, `11`, `17`, or `latest`)               |
| `-t <type>`   | JDK type (`openjdk` or `oracle`)                                  |
| `-p <path>`   | Custom installation path                                          |
| `-u`          | Upgrade existing installation                                     |
| `-s`          | System-wide installation (requires `sudo`)                        |
| `-l`          | List available Java versions                                      |
| `-h`          | Show help message                                                 |

## Examples

### **Install OpenJDK 11 system-wide**

```bash
sudo ./install_java.sh -v 11 -t openjdk -s
```

### **Install latest Oracle JDK for current user**

```bash
./install_java.sh -v latest -t oracle
```

### **Upgrade existing Java installation**

```bash
./install_java.sh -u
```

### **List available Java versions**

```bash
./install_java.sh -l
```

## Environment Configuration

The script automatically configures the following environment variables:
  - JAVA_HOME
  - Update to PATH

For system-wide installations, these are set in /etc/environment. For user installations, they're added to ~/.bashrc.

## Supported Java Versions

The script currently supports:
 - JDK 8 (1.8)
 - JDK 11
 - JDK 17
 - Latest version

## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |

## References

| **Title**                              | **Link**                                                                                        |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| Java SE Documentation                  | [Visit]([https://docs.python.org/3/library/venv.html](https://docs.oracle.com/en/java/javase/)) |
| OpenJDK Official Website               | [Visit]([https://pip.pypa.io/en/stable/](https://openjdk.org/))                                 |

---
