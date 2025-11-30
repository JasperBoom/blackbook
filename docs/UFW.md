# UFW Firewall Configuration for Raspberry Pi (WireGuard VPN)
This guide sets up **UFW** (Uncomplicated Firewall) on your Raspberry Pi to
secure your network while allowing necessary traffic.  

UFW is a whitelist firewall: **by default all incoming traffic is blocked**.
Only explicitly allowed ports are accessible.

## Basic Setup
```bash
# Deny all incoming traffic by default
sudo ufw default deny incoming

# Allow all outgoing traffic
sudo ufw default allow outgoing

# Allow WireGuard port
sudo ufw allow 51820/udp

# Allow SSH from LAN subnet
sudo ufw allow from 192.168.178.0/24 to any port 22

# Allow SSH from VPN subnet
sudo ufw allow from 10.3.70.0/24 to any port 22

# Enable logging for blocked connections
sudo ufw logging on

# Enable the firewall
sudo ufw enable

# Check status
sudo ufw status verbose

# Confirm no other services are exposed
sudo iptables -L -v -n
```

## Best Practices
Only open ports for services you actually need. Restrict access to LAN or VPN
subnets whenever possible.

Example: NGINX app on port 8018 accessible only from LAN & VPN:
```bash
sudo ufw allow from 192.168.178.0/24 to any port 8018
sudo ufw allow from 10.244.38.0/24 to any port 8018
```

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```