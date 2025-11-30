# Raspberry Pi Configuration Reference (`raspi-config`)
This document provides a structured guide to the options available in
`raspi-config`, the official Raspberry Pi configuration tool. It covers system,
display, interface, localisation, and advanced options, with explanations and
best practices.

## 1. System Options
| Option                | Description                                            | Notes / Recommendations                                          |
|-----------------------|--------------------------------------------------------|------------------------------------------------------------------|
| **S1: Wireless LAN**  | Configure Wi-Fi connection (SSID and password).        | Required for network access on headless setups.                  |
| **S2: Audio**         | Select audio output device (HDMI or headphone jack).   | Most setups default to HDMI; change only if using headphones.    |
| **S3: Password**      | Change the default user password (e.g., `pi`).         | Change immediately if using SSH; default passwords are insecure. |
| **S4: Hostname**      | Set the Pi’s network name.                             | Use a unique name (e.g., `PI-ZERO-JB`) to avoid conflicts.       |
| **S5: Boot**          | Choose boot behavior: console (text) or desktop (GUI). | Use console for headless, desktop if using monitor.              |
| **S6: Auto Login**    | Enable or disable automatic login at boot.             | Disable for security, especially on network-connected Pis.       |
| **S7: Splash Screen** | Enable/disable Raspberry Pi logo during boot.          | Cosmetic; optional.                                              |
| **S8: Power LED**     | Configure LED behavior (e.g., blink on activity).      | Optional; default is fine.                                       |
| **S9: Browser**       | Set the default browser for desktop mode.              | Optional; desktop only.                                          |

## 2. Display Options
| Option                  | Description                                          | Notes                                              |
|-------------------------|------------------------------------------------------|----------------------------------------------------|
| **D1: Underscan**       | Adjust screen edges to fit display.                  | Only change if black bars appear.                  |
| **D2: Screen Blanking** | Enable/disable automatic screen turn-off.            | Disable for always-on dashboards.                  |
| **D3: VNC Resolution**  | Resolution for remote desktop via VNC.               | Set to monitor’s native resolution for clarity.    |
| **D4: Composite**       | Adjust settings for older TVs using composite video. | Skip if using HDMI.                                |
| **D5: 4Kp60 HDMI**      | Enable 4K 60Hz output.                               | Only if using a 4K monitor and supported Pi model. |

## 3. Interface Options
| Option              | Description                                   | Notes                                              |
|---------------------|-----------------------------------------------|----------------------------------------------------|
| **I1: SSH**         | Enable SSH for remote command-line access.    | Essential for headless Pi management.              |
| **I2: RPi Connect** | Raspberry Pi Remote Desktop via Pi service.   | Optional; not needed with SSH/VNC.                 |
| **I3: VNC**         | Enable full GUI remote desktop.               | Use if GUI access is required remotely.            |
| **I4: SPI**         | Enable SPI pins for sensors/modules.          | Only if connecting SPI devices.                    |
| **I5: I2C**         | Enable I2C pins for sensors/modules.          | Enable only for I2C hardware.                      |
| **I6: Serial Port** | Enable UART (TX/RX) serial port.              | Required for serial devices like microcontrollers. |
| **I7: 1-Wire**      | Enable 1-Wire protocol for sensors (DS18B20). | Enable only if using 1-Wire sensors.               |

## 4. Localisation Options
| Option               | Description                                              | Notes                                          |
|----------------------|----------------------------------------------------------|------------------------------------------------|
| **L1: Locale**       | Set language & character encoding (e.g., English/UTF-8). | Defaults usually fine.                         |
| **L2: Timezone**     | Set local time zone.                                     | Required for correct timestamps/logs.          |
| **L3: Keyboard**     | Set keyboard layout (e.g., US, UK).                      | Match physical keyboard.                       |
| **L4: WLAN Country** | Set country for Wi-Fi regulations.                       | Must match your country for Wi-Fi to function. |

## 5. Advanced Options
| Option                          | Description                                    | Notes                                      |
|---------------------------------|------------------------------------------------|--------------------------------------------|
| **A1: Expand Filesystem**       | Resize root partition to use full SD card.     | Do this on new SD cards.                   |
| **A2: Network Interface Names** | Modern predictable names for interfaces.       | Leave default unless legacy naming needed. |
| **A3: Network Proxy Settings**  | Configure proxy server.                        | Skip for home network.                     |
| **A4: Boot Order**              | Set boot device order (SD, USB, network).      | Advanced use.                              |
| **A5: Bootloader Version**      | Update/check bootloader firmware.              | Only if troubleshooting.                   |
| **A6: Beta Access**             | Opt-in to experimental features.               | Avoid unless testing new features.         |
| **A7: Wayland**                 | Switch desktop compositor from X11 to Wayland. | Leave default unless needed.               |
| **A9: Network Install UI**      | Install OS over the network.                   | Advanced installation only.                |
| **A10: Libliftoff**             | Experimental GPU/graphics library.             | Leave default.                             |
| **A11: Shutdown Behaviour**     | Configure power-off behavior.                  | Usually default is fine.                   |
| **A12: Logging**                | Enable/disable system logs.                    | Keep enabled for troubleshooting.          |
| **A13: WLAN Power Save**        | Low-power mode for Wi-Fi.                      | Disable for maximum performance.           |
| **A14: Link-local Fallback**    | Fallback IP if DHCP fails.                     | Advanced networks only.                    |

## 6. Update & About
- **Update**: Updates `raspi-config` itself. Good to run occasionally.
- **About**: Displays version and info about `raspi-config`.

## 7. Serial Ports & Devices
| Term               | Description                                                                                                          |
|--------------------|----------------------------------------------------------------------------------------------------------------------|
| **Serial Port**    | Hardware interface sending/receiving data 1 bit at a time (GPIO UART pins).                                          |
| **Serial Device**  | Devices communicating via serial, e.g., microcontrollers, GPS, sensors.                                              |
| **Why it matters** | Serial is low-cost, widely used in embedded systems. Must enable serial port in `raspi-config` to use these devices. |

```
Copyright (C) 2025 Jasper Boom
All Rights Reserved.

Unauthorized copying, distribution, modification, or use of this file,
in whole or in part, is strictly prohibited without prior written consent
from the copyright owner.

For licensing inquiries, contact: info@jboom.org
```