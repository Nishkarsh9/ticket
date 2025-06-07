# Ansible Role: ScyllaDB

| Last Updated | Version | Author          | Comment         | Reviewer |
|--------------|---------|-----------------|-----------------|----------|
|  07-06-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

---

## Table of Contents

- [Introduction](#1-introduction)
- [How to Create an Ansible Role](#2-how-to-create-an-ansible-role)
- [Directory Breakdown](#3-directory-breakdown-with-purpose-use-case-and-example)
- [Role Details](#4-role-details)
- [Directory Structure Explanation](#5-directory-structure-explanation)
- [Flow Diagram Requirements](#6-flow-diagram-requirements)
- [Contact Information](#7-contact-information)
- [Reference Table](#8-reference-table)

---

## 1. Introduction

This document details the ScyllaDB Ansible role, which automates the installation and configuration of ScyllaDB NoSQL database on Debian-based systems. The role handles repository setup, package installation, system configuration, and service management for ScyllaDB clusters.

---

## 2. How to Create an Ansible Role

For detailed instructions on creating an Ansible role, refer to the official guide:
[Click here](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/ansible/roles/directory_structure/README.md#how-to-create-an-ansible-role)

---

## 3. Directory Breakdown (with Purpose, Use Case, and Example)

For detailed explanation of directory structures and their use cases, see:
[Click here](https://github.com/snaatak-Downtime-Crew/Documentation/blob/main/common_stack/ansible/roles/directory_structure/README.md#directory-breakdown-with-purpose-use-case-and-example)

---

## 4. Role Details

### Role Name

**scylladb** - This role installs and configures ScyllaDB NoSQL database with optimized settings for production environments.

### Requirements

| Hardware Specifications | Minimum Recommendation |
|-------------------------|------------------------|
| Processor               | 2 cores                |
| RAM                     | 4GB                    |
| Disk                    | 15GB SSD               |
| OS                      | Ubuntu 22.04 LTS       |

### Role Variables

Default variables (`defaults/main.yml`):

```yaml
scylla_version: "6.2"
scylla_repo_url: "http://downloads.scylladb.com/deb/debian/scylla-{{ scylla_version }}.list"
gpg_key: "a43e06657bac99e3"
scylla_service_state: started
scylla_service_enabled: true
```
## 5. Directory Structure Explanation

scylladb/
├── defaults/        # Default variables for ScyllaDB version and config
│   └── main.yml
├── handlers/       # Service management handlers
│   └── main.yml
├── tasks/          # Installation and configuration tasks
│   └── main.yml
├── templates/      # Configuration templates (optional)
├── files/          # Static files (optional)
├── vars/           # Internal variables
│   └── main.yml
├── meta/           # Role metadata and dependencies
│   └── main.yml
├── tests/          # Test cases
│   ├── inventory
│   └── test.yml
└── README.md       # Documentation

## 6.  Flow Diagram Requirements
flowchart TD
    A[Install Prerequisites] --> B[Setup GPG Key]
    B --> C[Configure Repository]
    C --> D[Install ScyllaDB Package]
    D --> E[Configure I/O Scheduler]
    E --> F[Run scylla_setup]
    F --> G[Start and Enable Service]
    G --> H[Wait for Port 9042]
    H --> I[Verify Installation]

    
## 7. Contact Information  
| **Name**    | **Email**                |
|-------------|--------------------------|
| Nishkarsh Kumar     | nishkarsh.kumar.snaatak@mygurukulam.co  |  

---

## 8. References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| Scylladb Official Documentation       | [Visit](https://docs.scylladb.com/) |  
| Ansible Official Documentation                  | [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html) |  
