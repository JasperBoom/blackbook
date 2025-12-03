# WireGuard
To access services running on my LAN without exposing them all to the outside
world, a VPN is essential. One of the best options is WireGuard, which provides
secure and straightforward access to my LAN.

Below are some commands I used to set up or configure WireGuard, as well as
commands I reference during installation or afterwards for testing and
management.

## Commands
These are commands I can use to test or configure after WireGuard is installed.
```bash
# Check the VPN interface and subnet.
ip addr show

# Show current clients.
pivpn list

# Add new client.
pivpn add
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

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```