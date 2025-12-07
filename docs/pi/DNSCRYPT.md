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

**NOTE**, when combining with Pi-hole, set the port to **53530** instead of
**53**. Pi-hole will use 53 and forward all outbound looksup to DNSCrypt.

## Change The UI Port
Change the default port on which the UI can be accessed. It will try to use
80 by default, but almost all UI software will try to use that, switch to
**8001**.

Edit the `dnscrypt-proxy.toml` file for this.
```bash
## Listen address for the monitoring UI.
listen_address = "0.0.0.0:8001"
```

## Common Commands
Below is a list of commands used to start, stop, and test the service:
```bash
# Reload the systemctl daemon.
sudo systemctl daemon-reload

# Stop the dnscrypt-proxy service.
sudo systemctl stop dnscrypt-proxy

# Start the dnscrypt-proxy service.
sudo systemctl start dnscrypt-proxy

# Restart the dnscrypt-proxy service.
sudo systemctl restart dnscrypt-proxy

# Check the dnscrypt-proxy service status.
sudo systemctl status dnscrypt-proxy

# Check if the service is enabled at boot.
sudo systemctl is-enabled dnscrypt-proxy

# Enable the service to start automatically at boot.
sudo systemctl enable dnscrypt-proxy

# Check the logs.
sudo journalctl -u dnscrypt-proxy.service -b
```

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```