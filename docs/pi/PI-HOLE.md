# Pi-hole
The Pi-hole is a DNS sinkhole that protects your devices from unwanted content
without installing any client-side software.

[Tutorial](https://privacyinternational.org/guide-step/4341/raspberry-pi-setup-and-run-pi-hole/)

## Configuration
Pi-hole can be installed using this command:
```bash
git clone --depth 1 https://github.com/pi-hole/pi-hole.git Pi-hole
cd "Pi-hole/automated install/"
sudo bash basic-install.sh
```

It will force you through a installation setup for which most options should
be default, configuration can be done via the UI later.

## Change the UI port
In order to change the port on which you can reach the UI for Pi-hole, edit
the `/etc/pihole/pihole.toml` file.

Now change this section:
```bash
# Ports to be used by the webserver.
#
# Allowed values are:
#     A comma-separated list of <[ip_address:]port>
port = "8002o,[::]:8002o"
```

## Common commands
Below is a list of commands used to start, stop, and test the service:
```bash
# Reload the systemctl daemon.
sudo systemctl daemon-reload

# Restart the pihole-FTL service.
sudo systemctl restart pihole-FTL

# Check the pihole-FTL service status.
sudo systemctl status pihole-FTL
```