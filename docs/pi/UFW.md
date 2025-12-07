# UFW Firewall
This guide explains how to set up **UFW** (Uncomplicated Firewall) on your
Raspberry Pi to secure your network while allowing necessary traffic.

UFW is a whitelist-based firewall: by default, all incoming traffic is blocked.
Only explicitly allowed ports are accessible.

This adds an extra layer of security when setting up external access through a
VPN such as WireGuard, which requires opening at least one port to the outside
world. With UFW, the only entry points to the Pi are those
specifically configured.

[Tutorial](https://www.wundertech.net/raspberry-pi-firewall-configuration-with-ufw/)

## Basic Setup
```bash
# Deny all incoming traffic by default.
sudo ufw default deny incoming

# Allow all outgoing traffic.
sudo ufw default allow outgoing

# Allow WireGuard port.
sudo ufw allow 51820/udp

# Allow SSH from LAN & VPN subnets.
sudo ufw allow from 192.168.178.0/24 to any port 22
sudo ufw allow from 10.3.70.0/24 to any port 22

# Protect the Pi from DNS queries from the internet.
sudo ufw deny in on eth0 to 192.168.178.201 port 53

# Allow LAN devices & VPN clients to query DNS (Pi-Hole & DNSCrypt Proxy).
sudo ufw allow from 192.168.178.0/24 to any port 53 proto udp
sudo ufw allow from 192.168.178.0/24 to any port 53 proto tcp
sudo ufw allow from 10.3.70.0/24 to any port 53 proto udp
sudo ufw allow from 10.3.70.0/24 to any port 53 proto tcp

# Allow LAN access to Monitoring UI (DNSCrypt Proxy).
sudo ufw allow from 192.168.178.0/24 to any port 8001
sudo ufw allow from 10.3.70.0/24 to any port 8001

# Allow LAN access to Monitoring UI (Pi-Hole).
sudo ufw allow from 192.168.178.0/24 to any port 8002
sudo ufw allow from 10.3.70.0/24 to any port 8002

# Enable logging for blocked connections.
sudo ufw logging medium

# Enable the firewall.
sudo ufw enable

# Check status.
sudo ufw status verbose
sudo ufw status numbered

# Delete a specific rule (example: rule 4).
sudo ufw delete 4

# If reloading is required.
sudo ufw reload

# Confirm no other services are exposed.
sudo iptables -L -v -n
```

## Best Practices
Only open ports for services you actually need and restrict access to LAN or
VPN subnets whenever possible.

Example: Allow access to an NGINX app on port 8018 only from LAN & VPN subnets.
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