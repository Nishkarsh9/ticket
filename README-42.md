# SOP: Migrate

| Created     | Version | Author          | Comment         | Reviewer |
|-------------|---------|-----------------|-----------------|----------|
| 18-04-2025  | V1      | Nishkarsh Kumar | Internal review | Pritam   |

## Introduction

---

## Table of Contents

1. [Why migrate?](#why-migrate)
2. [What is migrate?](#what-is-migrate)
3. [Step by step installation guide](#step-by-step-installation-guide)
     - [Install go](#1-install-go)
     - [Install Migrate](#2-install-migrate)
     - [Verify installation](#3-verify-installation)
     - [Run Migrations](#4-run-migrations)
     - [Deactivation](#5-deactivation)
     - [Deleting a Virtual Environment](#6-deleting-a-virtual-environment)
5. [Contacts](#contacts)
6. [References](#references)

---

## Why migrate?
Migrate helps you manage database schema changes in a version-controlled way, ensuring consistency across different environments.  It automates database updates, making them reliable and reproducible.

## What is migrate?
Migrate is a versatile command-line tool used to manage database schema migrations. It allows you to evolve your database schema over time in a structured and organized way. Instead of manually altering your database structure, you write migrations as code, which can then be applied to any database environment. This ensures consistency and simplifies database updates, especially in complex or collaborative projects.

## Step by step installation guide

### 1. **Install go**

```bash
sudo apt install -y golang-go
```

### 2. Install Migrate

```bash
curl -L https://github.com/golang-migrate/migrate/releases/download/v4.15.2/migrate.linux-amd64.tar.gz | tar xvz
```
Downloads golang-migrate package into current working directory and extracts it.

```bash
sudo mv migrate /usr/local/bin/migrate
```
Moves migrate binary to /usr/local/bin/ so that it can be used system-wide.

### 3. Verify installation

```bash
migrate --version
```

### 4. Run Migrations
After setting up the database and migration files for the database, use the migrate command with the -path (location of your migrations) and -database (your connection string) flags.  It's best to use an environment variable to store the connection string.

```bash
migrate -path migrations -database "$DATABASE_URL" up
```

## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |

---

## References

| **Title**                              | **Link**                                                                                      |
|----------------------------------------|-----------------------------------------------------------------------------------------------|
| Migrate GitHub Repository              | [Visit](https://github.com/golang-migrate/migrate)                                            |
| Migrate Command-Line Usage             | [Visit](https://github.com/golang-migrate/migrate/tree/master/cmd/migrate)                    |
