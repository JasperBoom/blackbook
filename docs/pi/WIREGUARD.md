# WireGuard
To access services running on my LAN without exposing them all to the outside
world, a VPN is essential. One of the best options is WireGuard, which provides
secure and straightforward access to my LAN.

Below are some commands I used to set up or configure WireGuard, as well as
commands I reference during installation or afterwards for testing and
management.

[Tutorial](https://www.wundertech.net/setup-wireguard-on-a-raspberry-pi-vpn-setup-tutorial/)

## Commands
These are commands I can use to test or configure after WireGuard is installed.
```bash
# Check the VPN interface and subnet.
ip addr show

# Show current clients.
pivpn list

# Add new client.
pivpn add

# Restart WireGuard.
sudo systemctl restart wg-quick@wg0

# Make sure IP forwarding is handled correctly from the VPN LAN to local LAN.
sudo iptables -t nat -A POSTROUTING -s 10.3.70.0/24 -o eth0 -j MASQUERADE
```

## IP Forwarding
Command below were required to get outbound internet working on phones.
```bash
sudo sysctl -w net.ipv4.ip_forward=1
```

## Dynamic DNS Settings
The following settings are required to connect my router to DuckDNS. On my
router, this is configured under Services → DNS → Dynamic DNS.
```bash
eth0
custom
https
ac-25-jb
ac-25-jb
e7ad206d-904e-4238-9c95-aac72a607777
zoneedit1
www.duckdns.org/nic/update?hostname=ac-25-jb&wildcard=NOCHG&mx=NOCHG&backmx=NOCHG
```

## Updating The Configuration
After first install, a configuration file is stored here
`/etc/pivpn/wireguard/setupVars.conf`. These values are used when new clients
are added.

New client configs actually live here `/etc/wireguard/configs` and not in
`~/configs`, as it might seem, these are just copies for easy access (the
`/etc` version is restricted access).

Make sure to adjust settings here, and restart WireGuard, also recreate the
clients, otherwise those settings are not live.

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```