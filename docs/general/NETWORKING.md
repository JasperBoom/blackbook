# Networking
## LAN Devices & IP Assignments
This document lists all devices on my local network (LAN), along with their
MAC addresses, IP addresses, and names. It serves as a reference for managing
devices, troubleshooting, and firewall rules.

## Local Area Network (LAN)
This section lists devices connected to the network via LAN.

| Device Name            | MAC Address       | IP Address      | Host Name |
|------------------------|-------------------|-----------------|-----------|
| ER-X-SFP-JB            | E4:38:83:E3:92:0A | 192.168.178.1   |           |
| D1-JB                  | D4:5D:64:05:48:93 | 192.168.178.41  | d1-jb     |
| L1-JB                  |                   | 192.168.178.42  |           |
| LAPTOP-BEJO            | C0:47:0E:8A:9F:C7 | 192.168.178.43  |           |
| MESH-WOONKAMER         | 30:DE:4B:0B:CD:64 | 192.168.178.101 |           |
| MESH-SLAAPKAMER        | 30:DE:4B:0B:FB:74 | 192.168.178.102 |           |
| MESH-KANTOOR           | 30:DE:4B:0B:E7:E0 | 192.168.178.103 |           |
| SAMSUNG-KOELKAST       | BC:10:2F:1F:58:12 | 192.168.178.111 |           |
| SAMSUNG-WASMACHINE     | 50:FD:D5:FA:2E:14 | 192.168.178.112 |           |
| SONY-BDP-S6700-BLU-RAY | 14:3F:A6:41:CE:E9 | 192.168.178.113 |           |
| TCL-QLED-43C635-TV     | C0:79:82:42:25:59 | 192.168.178.114 |           |
| PLAY-STATION-2         |                   | 192.168.178.115 |           |
| PI4-8GB-JB-ETHERNET    | D8:3A:DD:02:C4:29 | 192.168.178.201 | pi4-8gb   |
| PI4-8GB-JB-WIFI        | D8:3A:DD:02:C4:2A | 192.168.178.202 |           |
| PI4-2GB-JB-ETHERNET    | E4:5F:01:EB:DE:D1 | 192.168.178.203 | pi4-2gb   |
| PI4-2GB-JB-WIFI        | E4:5F:01:EB:DE:D2 | 192.168.178.204 |           |
| PI-ZERO-JB-WIFI        | B8:27:EB:FE:32:4A | 192.168.178.205 | pi-zero   |

## WireGuard VPN
This section lists devices connected to the network via WireGuard VPN.

| MAC Address    | IP Address | Device Name |
|----------------|------------|-------------|
| FA:66:5B:D6:30 | 10.3.70.2  | SM-S921B    |

## Port Forwardings
These port forwardings are required for services running within my LAN.

| Original Port | Protocol | Forward To Address | Forward To Port | Description |
|---------------|----------|--------------------|-----------------|-------------|
| 51820         | UDP      | 192.168.178.201    | 51820           | WireGuard   |

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```