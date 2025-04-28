# VCS Authentication

| Created     | Last Updated | Version | Author          | Comment         | Reviewer |
|-------------|--------------|---------|-----------------|-----------------|----------|
| 28-04-2025  |  28-04-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

---

## Table of Contents  
1. [Introduction](#introduction)  
2. [Why Authentication?](#why-authentication)  
3. [Authentication Strategies](#authentication-strategies)  
   - [SSH Key-Based Authentication](#ssh-key-based-authentication)  
   - [OAuth 2.0 / OpenID Connect](#oauth-20--openid-connect)  
   - [Personal Access Tokens (PATs)](#personal-access-tokens-pats)  
   - [Username/Password (Basic Auth)](#usernamepassword-basic-auth)  
4. [Comparison Table](#comparison-table)  
5. [Advantages & Disadvantages](#advantages--disadvantages)  
6. [Best Practices](#best-practices)  
7. [Conclusion](#conclusion)  
8. [Contact Information](#contact-information)  
9. [References](#references)  

---

## Introduction  
Authentication (Authn) is a critical component of Version Control System (VCS) security. This document outlines strategies for securing access to VCS platforms (e.g., GitLab, GitHub, Bitbucket) and compares different authentication methods.  

---

## Why Authentication?  
- Verifies user identity (e.g., ensuring a user is who they claim to be)  
- Prevents unauthorized access to repositories  
- Helps maintain compliance with security policies  

---

## Authentication Strategies  

### SSH Key-Based Authentication  
- Uses asymmetric cryptography (public/private keys)  
- Common for Git operations over SSH  
- Example: `ssh-keygen -t ed25519`  

### OAuth 2.0 / OpenID Connect  
- Delegated authentication (e.g., "Sign in with Google/GitHub")  
- Uses tokens (JWT) for stateless validation  
- Ideal for web-based VCS dashboards  

### Personal Access Tokens (PATs)  
- Token-based alternative to passwords  
- Scoped permissions (e.g., `repo:read`, `user:email`)  
- Example: GitHub PATs  

### Username/Password (Basic Auth)  
- Legacy method (discouraged due to security risks)  
- Requires HTTPS + rate limiting to mitigate brute-force attacks  

---

## Comparison Table  

| Method               | Security | Ease of Use | Scalability | Recommended Use Case          |  
|----------------------|----------|-------------|-------------|-------------------------------|  
| SSH Keys             | High     | Moderate    | High        | Developer CLI operations      |  
| OAuth 2.0 / OIDC     | High     | Easy        | High        | Web apps, third-party integrations |  
| PATs                 | Medium   | Easy        | Medium      | Automated scripts, CI/CD      |  
| Username/Password    | Low      | Easy        | Low         | Legacy systems (avoid)        |  

---

## Advantages & Disadvantages  

### SSH Keys  
- **Advantages**: High security, no password phishing risk  
- **Disadvantages**: Key management overhead  

### OAuth 2.0  
- **Advantages**: Centralized identity management  
- **Disadvantages**: Dependency on third-party providers  

### PATs  
- **Advantages**: Fine-grained permissions  
- **Disadvantages**: Tokens must be securely stored  

### Basic Auth  
- **Advantages**: Simple to implement  
- **Disadvantages**: Vulnerable to brute-force attacks  

---

## Best Practices  
1. **Prefer SSH/OAuth over passwords**  
2. **Enforce 2FA** for all users  
3. **Rotate tokens/keys** periodically  
4. **Use short-lived tokens** for OAuth  
5. **Audit logs** for all authentication attempts  

---

## Conclusion  
Personal Access Tokens (PATs) offer the most practical authentication solution, combining strong security with ease of use for most VCS workflows. While SSH and OAuth remain viable for specific use cases, PATs' granular access control and widespread adoption make them the preferred choice for modern version control systems.

All PATs will be:  
- Scope-limited to minimum required permissions  
- Rotated every 90 days  
- Stored in encrypted secrets managers  

---

## Contact Information

| **Name**    | **Email**                |
|-------------|--------------------------|
| Nishkarsh Kumar     | nishkarsh.kumar.snaatak@mygurukulam.co  |

## References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| GitHub PAT Documentation       | [Visit](https://docs.github.com/en/authentication) |  
| OAuth 2.0 RFC                  | [Visit](https://tools.ietf.org/html/rfc6749) |  
