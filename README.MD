# SOP: Ansible Playbook


| Created     | Version | Author          | Comment         | Reviewer |
|-------------|---------|-----------------|-----------------|----------|
| 16-04-2025  | V1      | Nishkarsh Kumar | Internal review | Pritam   |



## Introduction
This SOP outlines the standard procedure to execute the Ansible playbook reliably. It ensures consistent automation by detailing the objective, required inputs, validation checks, and step-by-step execution process.


## Table of Contents

1. [Why ansible playbook?](#why-ansible-playbook)
2. [What is ansible playbook?](#what-is-ansible-playbook)
3. [Prerequisites](#Prerequisites)  
4. [Required Inputs](#required-inputs)
3. [Commands and usage](#commands--usage)
     - [Run syntax check](#1-run-syntax-check-optional-but-recommended)
     - [Run dry-run](#2-run-dry-run-optional)
     - [Execute the playbook](#3-execute-the-playbook)
4. [Troubleshooting](#troubleshooting)
     - [Common errors](#common-errors)
     - [Check logs](#check-logs--use--vvv-for-verbose-output)
6. [Contacts](#contacts)
7. [References](#references)


## Why ansible playbook?
Ansible playbooks enable consistent, repeatable automation of IT tasks across multiple systems. They reduce manual errors and save time by executing complex workflows with simple, human-readable code.

## What is ansible playbook?
An Ansible playbook is a YAML file that defines a set of automation tasks to be executed on remote machines. It describes the desired system state and handles configuration, deployment, and orchestration efficiently.


## Prerequisites

Ensure the following before executing the playbook:

- Ansible is installed (version 2.9 or above).
- SSH access to the target nodes is configured.
- The inventory file is properly set with reachable hosts.
- Python installed on target nodes.
- Vault password file is available (if using Ansible Vault).


## Required Inputs

| Parameter        | Description                                      |  Requirement                            |
|------------------|--------------------------------------------------|-----------------------------------------|
| `playbook`       | Path to the Ansible playbook file to execute     | Required                                |
| `inventory`      | Inventory file or host group to target           | Required                                |
| `vault_password` | Vault password file (if using encrypted secrets) | Required (if using Vault)               |
| `extra_vars`     | Dynamic variables passed at runtime              | Required (if playbook expects variables)|


## Commands & Usage

### Execution Steps

### 1. Run syntax check (optional but recommended)

```bash
ansible-playbook site.yml --syntax-check
```

### 2. Run dry-run (optional)

```bash
ansible-playbook site.yml --check -i inventory/prod.ini
```

### 3. Execute the playbook

```bash
ansible-playbook site.yml -i inventory/prod.ini 
```
or:

```bash
ansible-playbook site.yml -i inventory/prod.ini --extra-vars "env=prod" --vault-password-file ~/.ansible/.vault_pass.txt
```


## Troubleshooting

### Common errors
    - SSH permission denied → Check user/SSH key.
    - Missing vars → Ensure all required variables are provided.
    - Vault decryption failed → Verify vault password file.

### Check logs : Use -vvv for verbose output

```bash
ansible-playbook site.yml -i inventory/prod.ini -vvv
```


## Contacts

| Name            | Email Address                                 |
|-----------------|-----------------------------------------------|
| Nishkarsh Kumar | nishkarsh.kumar.snaatak@mygurukulam.co        |


## References

| **Title**                                 | **Link**                                                                                      |
|-------------------------------------------|-----------------------------------------------------------------------------------------------|
| Ansible Playbooks – Official Documentation| [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)                    |
| Ansible Inventory – Official Guide        | [Visit](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)              |
| Passing Variables to Playbooks            | [Visit](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html)          |
| Best Practices for Ansible Playbooks      | [Visit](https://docs.ansible.com/ansible/latest/tips_tricks/index.html)                       |

---
