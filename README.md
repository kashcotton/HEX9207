# HEX9207

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## Description

A Python script that enables root access on the T-Mobile (Wingtech) TMOHS1 (MDM9207) and replaces the stock firmware interface. 

This is a fork of the original TMOHS1-Root-Utility. It expands on the original exploit by stripping the default carrier UI, replacing it with a custom web panel, and integrating local network management tools. Major major credit to them.

## New in This Fork

- **Custom Web Panel:** Replaces the stock T-Mobile web interface.
- **Web Shell:** Integrated root shell accessible directly through the web panel.
- **`dnsmasq` Support:** Manage custom DNS and DHCP directly from the interface.
- **Root Password Patch:** Fixed the upstream bug to allow persistent root password updates.

## Core Features

- Root shell via telnet
- Temporarily or persistently enable ADB
- Disable OMA-DM update bootstrap
- On-device root FTP server to browse the filesystem
- Mood lighting control
- Mask hotspot data as "on-client-device" data (TTL modification)

## What it doesn't (yet?) feature

- SIM unlock :(
- SSH server installation
- Other USB modes (can be implemented by editing `utils.py`)

## Setup

Requires Python >= 3.6 and pip.

```bash
pip install -r requirements.txt

```

## Usage

Connect to the hotspot via USB tethering (recommended) or WiFi, then run:

```sh
python ./rootScript.py

```

For verbose output:

```sh
python ./rootScript.py -v

```

### Notes

* Tested on Windows 10 & 11
* Assumes the hotspot IP is `192.168.0.1`.
* **Security:** The script leaves an unauthenticated root FTP server running on the device *only if you enable it*. Close it when finished by running `killall tcpsvd` as root, or reboot the device.
* You can build custom binaries and a portable cross-SDK using [this custom Buildroot fork](https://github.com/c-herz/tmohs-buildroot). Note: This is experimental.
