# Debian Linux Migration Guide for Legacy Intel MacBooks

## Table of Contents

- [Background](#background)
- [Structure](#structure)
  - [Step 1 — WiFi Bootstrap](#step-1-wifi-bootstrap)
  - [Step 2 — Post-Installation Setup](#step-2-post-installation-setup)
- [Compatibility](#compatibility)
- [License](#license)

A two-part project for migrating Intel MacBooks from macOS to a fully
functional Debian GNU/Linux 13 (Trixie) desktop environment.

---

## Background

Apple discontinued macOS support for Intel MacBooks with the release of
macOS Sequoia in September 2024. Hardware from this generation — primarily
2012 to 2019 MacBook Air and MacBook Pro models — remains mechanically
sound but is no longer eligible for operating system security updates.

This project was developed on a 2015 MacBook Air (Intel Core i5, 8GB RAM).
The migration was driven by one reason: macOS Monterey — the last version
Apple supports on this hardware — had become genuinely unusable due to idle
RAM consumption. Monterey consumes roughly 4GB of RAM at idle, leaving
almost nothing available for actual work on an 8GB machine. The only path
forward was a full OS migration.

Debian Trixie was chosen for one reason: RAM. A minimal terminal install
uses under 500MB at idle. After the full desktop setup in Step 2, idle RAM
rises to approximately 1GB — XFCE, NetworkManager, Bluetooth, and all
MacBook-specific drivers included. That is still under a quarter of what
Monterey used on the same hardware. The machine became completely usable
again.

Stability, package freshness, and long-term security updates are welcome
bonuses. This guide was written in April 2026, when a significant number of
Intel MacBooks from the 2013–2017 era are reaching end of Apple support. For
users who want to keep this hardware running securely, Debian Trixie is the
most viable path forward.

---

## Structure

The project is split into two independent repositories, each targeting a
distinct phase of the migration.

### Step 1 — WiFi Bootstrap
**[debian-intel-macbook-broadcom-offline](https://github.com/willardcsoriano/debian-intel-macbook-broadcom-offline)**

Intel MacBooks use Broadcom WiFi chipsets that require a proprietary driver
not included in the Linux kernel. A fresh Debian minimal install has no
network access and no package manager connectivity — and you cannot get WiFi
without packages you cannot download because you have no WiFi. This
repository breaks that loop.

All 92 required packages are provided for offline installation via USB,
along with a step-by-step guide and a full dependency map of the build
chain. If you found this project searching for how to get WiFi working on
Debian without internet access, start here.

### Step 2 — Post-Installation Setup
**[debian-intel-macbook-post-install](https://github.com/willardcsoriano/debian-intel-macbook-post-install)**

Once WiFi is working you have a terminal and nothing else — no desktop, no
browser, no keyboard shortcuts that feel familiar from macOS, no FaceTime
camera, no brightness control. This repository fixes all of that in one
command.

The setup script configures a complete daily-driver desktop: XFCE, MacBook
keyboard remapping, backlight control, FaceTime HD camera via DKMS, battery
management, audio, Bluetooth, and an optional theming script for users
transitioning from macOS.

---

## Compatibility

Tested on MacBook Air 7,2 (Mid-2015, 13-inch) running Debian GNU/Linux 13
(Trixie). Expected to work on most Intel MacBook models from 2012–2019.
Apple Silicon Macs (M1 and later) are not supported.

---

## License

MIT

---

*Born out of a real offline install session on a MacBook Air in April 2026.
Every package in the WiFi bootstrap collection was manually identified and
verified through trial and error — sometimes a lot of error.*
