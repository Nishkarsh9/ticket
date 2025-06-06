# POC: OpenVPN

| Last Updated | Version | Author          | Comment         | Reviewer |
|--------------|---------|-----------------|-----------------|----------|
|  06-06-2025  | V1      | Nishkarsh Kumar | Internal Review | Pritam   |

# OpenVPN Server Setup Guide

## Table of Contents
1. [Server Setup](#server-setup)
2. [OpenVPN Installation](#openvpn-installation)
3. [Configuration](#configuration)
4. [Client Setup](#client-setup)
5. [Contact Information](#contact-information)
6. [Troubleshooting](#troubleshooting)
7. [References](#references)

## Server Setup

### 1. Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Configure Firewall
```bash
sudo ufw allow 1194/udp
sudo ufw allow OpenSSH
sudo ufw enable
```
# OpenVPN Installation and Configuration Guide

## OpenVPN Installation

### 1. Install Required Packages

```bash
sudo apt install openvpn easy-rsa -y
```

### 2. Set Up PKI Infrastructure

```bash
make-cadir ~/openvpn-ca
cd ~/openvpn-ca
```

### 3. Configure CA Variables

```bash
nano vars
```

Update the information:
```bash
export KEY_COUNTRY="US"
export KEY_PROVINCE="CA"
export KEY_CITY="SanFrancisco"
export KEY_ORG="YourOrg"
export KEY_EMAIL="admin@yourorg.com"
export KEY_OU="MyOrganizationalUnit"
export KEY_NAME="server"
```

Source the variables:
```bash
source vars
```

### 4.  Initialize and Build CA
```bash
./clean-all
./build-ca
```

## Configuration

### 1. Generate Server Certificates
```bash
./build-key-server server
```

### 2. Create DH Parameters
```bash
./build-dh
```

### 3. Generate HMAC Key
```bash
openvpn --genkey --secret keys/ta.key
```

### 4. Copy Certificates to OpenVPN Directory
```bash
cd ~/openvpn-ca/keys
sudo cp server.crt server.key ca.crt ta.key dh2048.pem /etc/openvpn/
```

### 5. Configure Server
Copy sample configuration:
```bash
gunzip -c /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz | sudo tee /etc/openvpn/server.conf
```

Edit configuration:
```bash
sudo nano /etc/openvpn/server.conf
```

Key settings to verify/modify:
```bash
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
tls-auth ta.key 0
cipher AES-256-CBC
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
```

### 6. Enable IP Forwarding

Edit sysctl:
```bash
sudo nano /etc/sysctl.conf
```

Uncomment/add:
```bash
net.ipv4.ip_forward=1
```

Apply changes:
```bash
sudo sysctl -p
```

### 7. Start and Enable OpenVPN
```bash
sudo systemctl start openvpn@server
sudo systemctl enable openvpn@server
```

## Client Setup

### 1. Generate Client Certificate
```bash
cd ~/openvpn-ca
source vars
./build-key client1
```

### 2. Create Client Config Directory
```bash
mkdir -p ~/client-configs/files
```

### 3. Create Base Configuration
```bash
nano ~/client-configs/base.conf
```

Add the following:
```bash
client
dev tun
proto udp
remote your_server_ip 1194
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
remote-cert-tls server
cipher AES-256-CBC
verb 3
```

### 4. Create Config Generation Script
```bash
nano ~/client-configs/make_config.sh
```

Add:
```bash
#!/bin/bash

KEY_DIR=~/openvpn-ca/keys
OUTPUT_DIR=~/client-configs/files
BASE_CONFIG=~/client-configs/base.conf

cat ${BASE_CONFIG} \
    <(echo -e '<ca>') \
    ${KEY_DIR}/ca.crt \
    <(echo -e '</ca>\n<cert>') \
    ${KEY_DIR}/${1}.crt \
    <(echo -e '</cert>\n<key>') \
    ${KEY_DIR}/${1}.key \
    <(echo -e '</key>\n<tls-auth>') \
    ${KEY_DIR}/ta.key \
    <(echo -e '</tls-auth>') \
    > ${OUTPUT_DIR}/${1}.ovpn
```

Make it executable:
```bash
chmod 700 ~/client-configs/make_config.sh
```

 ### 5. Generate Client Config
```bash
cd ~/client-configs
./make_config.sh client1
```

### 6. Transfer Config to Client
```bash
scp ~/client-configs/files/client1.ovpn user@client_machine:/path/to/save/
```

## Testing

 ### 1. Check Service Status
```bash
sudo systemctl status openvpn@server
```

 ### 2. Monitor Logs
```bash
sudo tail -f /var/log/syslog | grep openvpn
```

### 3. Test Client Connection
- Import client1.ovpn into OpenVPN client
- Connect to server
- Verify network access

## Contact Information  
| **Name**    | **Email**                |
|-------------|--------------------------|
| Nishkarsh Kumar     | nishkarsh.kumar.snaatak@mygurukulam.co  |  

---

## References  

| Title                          | Link                                                                 |  
|--------------------------------|----------------------------------------------------------------------|  
| OpenVPN Official Documentation       | [Visit](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-4/) |  
| Configuration Guides                  | [Visit](https://ubuntu.com/server/docs/service-openvpn) |  
---
