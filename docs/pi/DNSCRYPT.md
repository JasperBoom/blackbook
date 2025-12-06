# DNSCrypt 
DNSCrypt Proxy is a DNS proxy service that encrypts DNS communication with the
outside world. This ensures that when devices on the local network attempt to
reach, for example, a website, DNS information is requested securely without
disclosing unnecessary private information.

[Tutorial](https://hndrk.blog/tutorial-pi-hole-and-dnscrypt/)

## Configuration
DNSCrypt Proxy can be downloaded using the instructions
in its GitHub repository:
[DNSCrypt Proxy on GitHub](https://github.com/DNSCrypt/dnscrypt-proxy)

The main configuration file is `dnscrypt-proxy.toml`. My personalised version
is stored in the [docs](../docs) folder of this repository.

DNSCrypt requires port **53**, as this is the standard DNS port. Ensure that the
firewall allows communication on this port on the Raspberry Pi. See the
firewall configuration guide in [UFW.md](./UFW.md).

A note is, when combining with Pi-hole, set the port to 53530 instead 53.
Pi-hole will use 53 and forward all outbound looksup to DNSCrypt.

## Common commands
Below is a list of commands used to start, stop, and test the service:
```bash
# Reload the systemctl daemon.
sudo systemctl daemon-reload

# Restart the dnscrypt-proxy service.
sudo systemctl restart dnscrypt-proxy

# Stop the dnscrypt-proxy service.
sudo systemctl stop dnscrypt-proxy

# Start the dnscrypt-proxy service.
sudo systemctl start dnscrypt-proxy

# Check the dnscrypt-proxy service status.
sudo systemctl status dnscrypt-proxy

# Check if the service is enabled at boot.
sudo systemctl is-enabled dnscrypt-proxy

# Enable the service to start automatically at boot.
sudo systemctl enable dnscrypt-proxy

# Check the logs.
sudo journalctl -u dnscrypt-proxy.service -b

# Test DNS resolution via the proxy.
dig @127.0.0.1 hndrk.blog

# Scan local network devices (useful for troubleshooting).
sudo nmap -sP 192.168.178.0/24
```

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```