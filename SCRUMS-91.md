# OT-MICROSERVICES Full Stack Documentation


## **Author Information**

| Created     | Last Updated | Version | Author          | Comment         | Reviewer |
|-------------|--------------|---------|-----------------|-----------------|----------|
| 01-05-2025  |  01-05-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

---

## Table of Contents

1. [Introduction](#introduction)  
2. [Pre-requisites](#pre-requisites)  
3. [System Requirements](#system-requirements)  
4. [Dependencies](#dependencies)  
    - [Build Time Dependency](#build-time-dependency)  
    - [Run Time Dependency](#run-time-dependency)  
5. [Important Ports](#important-ports)  
6. [Architecture](#architecture)  
7. [Dataflow Diagram](#dataflow-diagram)  
8. [Application Components](#application-components)  
    - [Frontend](#frontend)  
    - [Backend](#backend)  
9. [Conclusion](#conclusion)  
10. [Contact Information](#contact-information)  
11. [References](#references)  

---

## Introduction

**OT-MICROSERVICES** is a full-stack microservices system designed to manage employee operations, including attendance, salary processing, and notifications. It leverages a scalable, decoupled architecture with a ReactJS frontend and multiple independent backend APIs.

---

## Pre-requisites

Before running the application, ensure you have installed:
- Git
- Node.js (18+)
- PostgreSQL (14+)
- Redis (6.0.16+)
- ScyllaDB (6.2+)/
- Elasticsearch (7.17.17+)
- Python 3.8+

---

## System Requirements

| Hardware Specification  | Minimum Recommendation         |
|--------------------------|---------------------------------|
| Processor                | Dual Core                      |
| RAM                      | 4 GB                           |
| Disk Space               | 50 GB                          |
| OS                       | Ubuntu 22.04 LTS (Recommended) |

---

## Dependencies

### Build Time Dependency

| Name            | Version | Description                               |
|-----------------|---------|-------------------------------------------|
| Node.js         | 18+     | Backend and frontend runtime              |
| React.js        | 18+     | Frontend Framework                        |
| Git             | 2.34+   | Version control system                    |

### Run Time Dependency

| Name            | Version | Description                               |
|-----------------|---------|-------------------------------------------|
| PostgreSQL      | 14+     | Relational Database                       |
| Redis           | 6.0.16+    | In-memory Cache database                  |
| ScyllaDB        | 6.2+    | High-performance NoSQL database           |
| Elasticsearch   | 7.17.17+      | Search and analytics engine               |
| Python          | 3.8+   | For processing notifications from Elasticsearch |
| Linux OS        | 22.04 LTS | Recommended Operating System            |

---

## Important Ports

| Inbound Traffic | Service                    | Port No |
|-----------------|-----------------------------|---------|
| Frontend (React) | React Development Server    | 3000    |
| Backend (Node.js ) | API Servers          | 5000+   |
| PostgreSQL      | Database                     | 5432    |
| Redis           | In-memory database           | 6379    |
| ScyllaDB        | NoSQL database               | 9042    |
| Elasticsearch   | Search engine                | 9200    |

---

## Architecture
[1]!(https://github.com/Nishkarsh9/images/blob/main/Screenshot%202025-04-29%20155617.png)
- React frontend interacts with the backend microservices: Employee, Salary, Attendance, and Notification APIs.
- Redis serves as a caching layer for performance.
- ScyllaDB and PostgreSQL are used for persistent data storage.
- Elasticsearch acts as the centralized log and event store for notification processing.
- A Python script consumes data from Elasticsearch and triggers notifications.

---

## Dataflow

1. Frontend initiates API requests.
2. Backend APIs process requests, use Redis for caching, and store data in ScyllaDB or PostgreSQL.
3. Salary and Employee APIs push selected data to Elasticsearch.
4. Notification API reads from Elasticsearch and sends notifications.

---

## Application Components

### Frontend

**Repository**: [Frontend](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-82-Nishkarsh/ot-ms-understanding/frontend/poc/README.md)

- Built with **React.js**, **HTML**, and **CSS**.
- Provides interfaces for employees, attendance and salaries
- Connects to:
  - [Employee API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-78-YUVRAJ/ot-ms-understanding/employee/poc/README.md)
  - [Salary API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-80-Durgesh/ot-ms-understanding/salary/poc/README.md)
  - [Attendance API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-76-SHIVANI/ot-ms-understanding/attendance/poc/README.md)
  - [Notification API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-74-Prateek/ot-ms-understanding/notification/poc/README.md)

### Backend

#### 1. Employee API  
**Repo**: [Employee-API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-78-YUVRAJ/ot-ms-understanding/employee/poc/README.md)  
- Built using **Go-language**  
- Uses **Redis** for caching and **ScyllaDB** for persistent storage  
- Pushes relevant data to **Elasticsearch** for downstream notification processing  

#### 2. Salary API  
**Repo**: [Salary-API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-80-Durgesh/ot-ms-understanding/salary/poc/README.md)  
- Built with **Java**  
- Uses **Redis** for caching and **ScyllaDB** for salary records  
- Pushes salary alerts and logs to **Elasticsearch** for notifications  

#### 3. Attendance API  
**Repo**: [Attendance-API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-76-SHIVANI/ot-ms-understanding/attendance/poc/README.md)  
- Built using **Python**    
- Uses **Redis** as a caching layer  
- Uses **PostgreSQL** for attendance records  

#### 4. Notification API  
**Repo**: [Notification-API](https://github.com/snaatak-Downtime-Crew/Documentation/blob/SCRUMS-74-Prateek/ot-ms-understanding/notification/poc/README.md)  
- Built in **Python**  
- Consumes employee/salary events from **Elasticsearch**  
- Sends appropriate notifications (email/SMS/logs)   

---

## Conclusion

This documentation outlines the complete architecture, tools, and interdependencies in the OT-MICROSERVICES full-stack application. Each microservice is responsible for a domain-specific function and integrates using best practices. Elasticsearch serves as the bridge for real-time data processing and triggering notifications via a Python worker, making the system scalable and event-driven. The modular nature of the system ensures maintainability, scalability, and performance for modern enterprise requirements.

---

## Contact Information

| Name       | Email Address                        |
|------------|--------------------------------------|
| Nishkarsh Kumar    | nishkarsh.kumar.snaatak@mygurukulam.co         |

---

## References

| **Title**                    | **Link**                                    |
|-------------------------------|---------------------------------------------|
| Ubuntu Official Documentation | [Ubuntu Docs](https://help.ubuntu.com)     |
| Node.js Official Documentation | [Node.js Docs](https://nodejs.org/en/docs) |
| ScyllaDB Official Documentation | [Scylla Docs](https://docs.scylladb.com)  |
| PostgreSQL Official Documentation | [PostgreSQL Docs](https://www.postgresql.org/docs/) |
| Elasticsearch Docs | [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/index.html) |

---
