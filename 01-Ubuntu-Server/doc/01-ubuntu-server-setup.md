# Ubuntu Server Home Lab Setup

## Overview

I decided to repurpose my old HP Pavilion laptop into a home server rather than buying additional hardware. The idea is to use it as a learning environment where I can practise Linux administration, networking, troubleshooting and cybersecurity.

## Hardware

- Device: HP Pavilion 14-ce3606sa
- RAM: 8GB
- Storage: 512GB SSD
- Operating system: Ubuntu Server
- Network connection: Wi-Fi

## Installation

I installed Ubuntu Server directly onto the laptop and logged into the terminal.

One of the first challenges was getting the server connected to my home network. I didn't have an Ethernet connection available, so I needed to configure Wi-Fi manually.

## Configuring Wi-Fi with Netplan

Ubuntu Server uses Netplan to manage its network configuration.

I edited the configuration file at:

`/etc/netplan/00-installer-config.yaml`

Initially, I received an error about inconsistent YAML indentation around the `access-points` section. I corrected the indentation and validated the configuration.

Commands I used:

```bash
sudo netplan generate
sudo netplan try
ip -br addr
```

After confirming the new settings, my Wi-Fi interface `wlo1` was UP and had received a local IP address.

## Testing Connectivity

I tested whether the server could reach the internet:

```bash
ping -c 4 1.1.1.1
```

Result: Four packets received with 0% packet loss.

I also tested DNS resolution:

```bash
getent ahostsv4 ubuntu.com
```

Result: Ubuntu successfully resolved the domain name into IP addresses.

## What I Learned

- How to configure Wi-Fi on Ubuntu Server using Netplan
- Why YAML indentation matters
- How to validate and safely apply network changes
- How to identify network interfaces and check IP addresses
- The difference between testing internet connectivity and DNS resolution

## Next Steps

Now that networking works, I want to prepare the laptop for remote administration, system updates and future home lab projects.
