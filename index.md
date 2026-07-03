🏔️ ScenicOS Documentation
Table of Contents

    Overview

    Philosophy

    System Requirements

    Installation

    Security Hardening

    Post-Installation

    Custom Commands

    Troubleshooting

    Contributing

Overview

ScenicOS is a hardened Debian-based Linux distribution designed for security, privacy, and performance. It combines the stability of Debian 13 (Trixie) with aggressive security hardening, custom branding, and a curated set of tools.
Key Features
Feature	Description
Kernel Hardening	KASLR, PTI, slab_nomerge, page_poison, nosmt enabled by default
Mandatory Access Control	AppArmor pre-configured and active
Firewall	UFW with default deny policy
System Auditing	Auditd for comprehensive system monitoring
Brute Force Protection	Fail2ban pre-installed and configured
Custom Branding	Unique visual identity with custom MOTD and scripts
Desktop Environment	Niri window manager with DankMaterialShell
Network Security	Wireshark, tcpdump, nmap pre-installed or available
Philosophy

Security by Default
The system is hardened out of the box. Users should not need to be security experts to operate safely.

Deliberate Design
Every package, configuration file, and user interface element is intentional and serves a specific purpose.

Community Ownership
ScenicOS is shaped by its users, not by corporate roadmaps or monetization plans.
System Requirements
Minimum Hardware
Component	Requirement
CPU	64-bit (Intel or AMD)
RAM	2 GB
Storage	20 GB available space
Graphics	Wayland-compatible GPU
Network	Ethernet or WiFi adapter
Recommended Hardware
Component	Requirement
CPU	4 cores or more
RAM	8 GB or more
Storage	50 GB SSD
Graphics	Intel, NVIDIA, or AMD with open-source drivers
Supported Architectures

    amd64 (x86_64) - Primary

    arm64 (AArch64) - Experimental

Installation
Method 1: Ventoy USB (Recommended)

    Download the ScenicOS ISO from the official repository

    Install Ventoy on a USB drive

    Copy the ISO to the Ventoy USB

    Boot from the USB

    Select "Install" from the GRUB menu

    Follow the Calamares installer

Method 2: Direct USB Write
bash

sudo dd if=ScenicOS-Kaiju-2025.06.iso of=/dev/sdX bs=4M status=progress

Method 3: VM Installation

ScenicOS can be installed in GNOME Boxes, VirtualBox, or QEMU/KVM.
bash

# GNOME Boxes
gnome-boxes ScenicOS-Kaiju-2025.06.iso

# QEMU/KVM
qemu-system-x86_64 -cdrom ScenicOS-Kaiju-2025.06.iso -m 2048 -enable-kvm

Installation Steps

    Language Selection: Choose your preferred language

    Location: Select your timezone

    Keyboard Layout: Choose your keyboard configuration

    Partitioning: Select "Erase disk" or "Manual"

    User Setup: Create username and password

    Review: Confirm settings

    Install: Wait for installation to complete

    Reboot: Remove installation media and restart

Security Hardening
Kernel Hardening

ScenicOS applies the following kernel parameters at boot:
text

kaslr pti=on slab_nomerge page_poison=1 nosmt

Parameter	Purpose
kaslr	Kernel Address Space Layout Randomization
pti=on	Page Table Isolation (Meltdown mitigation)
slab_nomerge	Prevents heap merging attacks
page_poison=1	Detects use-after-free vulnerabilities
nosmt	Disables Simultaneous Multithreading
Verify Kernel Hardening
bash

cat /proc/cmdline | grep -E "kaslr|pti|slab_nomerge|page_poison|nosmt"

AppArmor

AppArmor is enabled by default. Check status:
bash

sudo aa-status

Firewall (UFW)

UFW is active with default deny policy.
bash

sudo ufw status

SSH Hardening

Default SSH configuration:
text

PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
MaxAuthTries 3

SUID Binary Audit

ScenicOS includes a hardening script for SUID binaries:
bash

sudo ~/hardening_suid.sh

Post-Installation
System Update
bash

sudo apt update && sudo apt upgrade -y

Enable Additional Repositories
bash

sudo sed -i 's/main/main contrib non-free non-free-firmware/g' /etc/apt/sources.list
sudo apt update

Install Security Tools
bash

sudo apt install wireshark tcpdump nmap radare2 ghidra binwalk -y

Configure Wireshark Permissions
bash

sudo usermod -a -G wireshark $USER
sudo reboot

Install Virtualization
bash

# GNOME Boxes (already installed)
sudo apt install gnome-boxes -y

# QEMU/KVM
sudo apt install qemu-system-x86 qemu-kvm libvirt-daemon-system virt-manager -y

Custom Commands

ScenicOS includes the following custom commands:
Command	Description
scenic-info	Display system information
kaiju-info	Display Kaiju mascot information
scenic-help	Display security command help
scenic_health.sh	System health check script
scenic-info

Displays comprehensive system information including OS, kernel, architecture, and security status.
kaiju-info

Displays information about the Kaiju mascot and system branding.
scenic-help

Lists all available security commands with brief descriptions.
scenic_health.sh

Comprehensive system health check with the following options:
bash

# Basic health check
./scenic_health.sh

# Auto-fix common issues
./scenic_health.sh --fix

# Generate detailed report
./scenic_health.sh --report

# Quiet mode
./scenic_health.sh --quiet

Troubleshooting
Network Issues

WiFi Not Detected
bash

sudo apt install firmware-iwlwifi firmware-realtek -y
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi

DNS Resolution Fails
bash

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

Audio Issues
bash

sudo apt install pipewire pipewire-pulse wireplumber -y
systemctl --user enable pipewire pipewire-pulse wireplumber
systemctl --user start pipewire pipewire-pulse wireplumber

Virtualization Issues

KVM Permission Denied
bash

sudo usermod -a -G kvm $USER
sudo usermod -a -G libvirt $USER

GNOME Boxes No Network

    Open Boxes

    Select VM → Properties

    Change network to "NAT" or "Host-only"

Package Not Found

Enable contrib and non-free repositories:
bash

sudo sed -i 's/main/main contrib non-free non-free-firmware/g' /etc/apt/sources.list
sudo apt update

Wireshark No Capture Permissions
bash

sudo usermod -a -G wireshark $USER
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
sudo reboot

Contributing
Reporting Issues

    Check existing issues on GitHub

    Include system information (scenic-info)

    Describe the problem and steps to reproduce

    Attach relevant logs

Development

ScenicOS is built with live-build. To rebuild the ISO:
bash

cd ~/my-hardened-debian
sudo lb clean
sudo lb config
sudo lb build

Code of Conduct

    Be respectful and inclusive

    Focus on constructive feedback

    Keep discussions on-topic

    Follow security best practices

License

ScenicOS is licensed under the GNU General Public License v3.0 (GPL-3.0).

You are free to:

    Use ScenicOS for any purpose

    Share it with others

    Modify it and share your modifications

Acknowledgments

    Debian – The foundation that makes ScenicOS possible

    Niri – Scrollable tiling Wayland compositor

    DankMaterialShell – Material 3 desktop shell

    live-build – Tools for building custom Debian ISOs

    The Kaiju – The mascot that makes ScenicOS unique

Contact

    Website: https://scenicos.org

    GitHub: https://github.com/scenicos/scenic-os

    Discord: https://discord.gg/scenicos

Documentation Version 1.0.0
Last Updated: July 2026
text


---
