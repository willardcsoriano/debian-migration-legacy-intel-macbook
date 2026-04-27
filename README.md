# Intel MacBook on Debian Linux

A two-part project for migrating Intel MacBooks from macOS to a fully
functional Debian GNU/Linux 13 (Trixie) desktop environment.

---

## Background

Apple discontinued macOS support for Intel MacBooks with the release of
macOS Sequoia in September 2024. Hardware from this generation — primarily
2012 to 2019 MacBook Air and MacBook Pro models — remains mechanically
sound but is no longer eligible for operating system security updates.

Debian GNU/Linux 13 (Trixie) is a viable replacement. At idle, a configured
Debian desktop consumes under 1GB of RAM on the same hardware that requires
approximately 4GB under macOS Monterey. The tradeoff is a significantly more
involved setup process, primarily due to driver availability and the absence
of Ethernet on certain MacBook models.

This project addresses that setup process end to end.

---

## Structure

The project is split into two independent repositories, each targeting a
distinct phase of the migration.

### Step 1 — WiFi Bootstrap
**[debian-intel-macbook-broadcom-offline](https://github.com/willardcsoriano/debian-intel-macbook-broadcom-offline)**

Intel MacBooks use Broadcom WiFi chipsets that require a proprietary driver
not included in the Linux kernel. A fresh Debian minimal install has no
network access and no package manager connectivity, creating a
dependency resolution problem that cannot be solved from within the system.

This repository provides all 92 required packages for offline installation
via USB, along with a step-by-step installation guide and a full dependency
map of the build chain.

### Step 2 — Post-Installation Setup
**[debian-intel-macbook-post-install](https://github.com/willardcsoriano/debian-intel-macbook-post-install)**

Once network access is established, this repository provides an automated
setup script that configures a complete daily-driver desktop. Scope includes
the XFCE desktop environment, MacBook keyboard remapping, backlight control,
FaceTime HD camera driver installation via DKMS, battery management, audio,
Bluetooth, and an optional theming script that adapts the desktop aesthetic
for users transitioning from macOS.

---

## Compatibility

Tested on MacBook Air 7,2 (Mid-2015, 13-inch) running Debian GNU/Linux 13
(Trixie). Expected to work on most Intel MacBook models from 2012–2019.
Apple Silicon Macs (M1 and later) are not supported.

---

## License

MIT
