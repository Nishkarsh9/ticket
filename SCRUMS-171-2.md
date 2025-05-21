# POC: Unit Testing in GO

| Last Updated | Version | Author          | Comment         | Reviewer |
|--------------|---------|-----------------|-----------------|----------|
|  21-05-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

## Table of Contents

- [Overview](#overview)
- [Test Execution Guide](#test-execution-guide)
  - [1. Clone and Prepare the Repository](#1-clone-and-prepare-the-repository)
  - [2. Basic Test Commands](#2-basic-test-commands)
    - [Run All Tests](#run-all-tests)
    - [Run Tests with Verbose Output](#run-tests-with-verbose-output)
    - [Run Tests for a Specific Package](#run-tests-for-a-specific-package)
    - [Run a Specific Test by Name](#run-a-specific-test-by-name)
  - [3. Advanced Test Execution](#3-advanced-test-execution)
    - [Generate Coverage Profile](#generate-coverage-profile)
- [Contact](#contact)
- [References](#references)

## Overview

This POC demonstrates how to execute and enhance the existing unit tests in the `Employee API` repository using the standard `go test` command, focusing on manual terminal-based testing.

---

## Test Execution Guide

### 1. Clone and Prepare the Repository

```bash
git clone https://github.com/OT-MICROSERVICES/employee-api.git
cd employee-api
```
![1](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20173429.png)
## 2. Basic Test Commands

### Run All Tests

```bash
go test ./...
```
![2](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20174457.png)

### Run Tests with Verbose Output

```bash
go test -v ./...
```
![3](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20174538.png)

### Run Tests for a Specific Package

```bash
go test -v ./internal/handler
```
### Run a Specific Test by Name

```bash
go test -v -run TestGetEmployee ./internal/handler
```
### 3. Advanced Test Execution

#### Generate Coverage Profile

```bash
go test -coverprofile=coverage.out ./...
```
![4](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20174627.png)

### For execution of the unit test cases, code coverage reports, etc., we can use the `go test` command.

```bash
go test $(go list ./... | grep -v docs | grep -v model | grep -v main.go) -coverprofile cover.out
```
![5](https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-05-21%20174218.png)

## Contact

| **Name**    | **Email**                |
|-------------|--------------------------|
| Nishkarsh Kumar     | nishkarsh.kumar.snaatak@mygurukulam.co  |


## References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| The Go Programming Language - Testing       | [Visit](https://pkg.go.dev/testing) |  
| Go Command - test flag                  | [Visit](https://pkg.go.dev/cmd/go#hdr-Testing_flags) |  
