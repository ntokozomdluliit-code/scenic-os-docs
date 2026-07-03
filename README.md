# 🌄 ScenicOS

<div align="center">

**A Hardened Debian Distribution Built with Intent**

[![Debian 13](https://img.shields.io/badge/Base-Debian_13_Trixie-A81D33?style=for-the-badge&logo=debian)](https://www.debian.org/)
[![Kernel](https://img.shields.io/badge/Kernel-6.12.94-0033A0?style=for-the-badge&logo=linux)](https://kernel.org/)
[![License](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge)](https://www.gnu.org/licenses/gpl-3.0.html)
[![Desktop](https://img.shields.io/badge/Desktop-Niri_+_DankMaterialShell-7C4DFF?style=for-the-badge)](https://github.com/YaLTeR/niri)

</div>

---

## What is ScenicOS?

ScenicOS is a **hardened Debian-based Linux distribution** built from the ground up for people who refuse to compromise on security, privacy, or beauty. It is the result of countless hours in the terminal, a relentless pursuit of knowledge, and a single question:

> *"What if an operating system was built with the same care that a craftsman puts into their work?"*

ScenicOS is that answer.

It is not just another Linux distro. It is a statement. A rebellion against bloated, insecure, and soulless software. It is a system that protects you by default, respects your privacy, and gives you full control — because you deserve nothing less.

---

## Why ScenicOS Exists

I built ScenicOS because I believe that **security should never be an afterthought**.

For years, I watched as operating systems shipped with broken defaults, unnecessary telemetry, and gaping security holes. I saw people being exploited — not because they were careless, but because the systems they trusted failed them.

So I decided to do something about it.

This is not a project that was outsourced to a corporation. This is not a product designed to extract data from you. This is a **labor of love** — a system forged in the fire of late-night debugging sessions, endless kernel parameters, and the stubborn refusal to accept "good enough."

ScenicOS is built by someone who cares. Someone who believes that software should empower, not exploit. Someone who is committed to making a difference.

---

## The Philosophy

### Security is Not a Feature — It is a Right

Every default in ScenicOS is chosen with security in mind. From KASLR and PTI to AppArmor and UFW, the system is hardened from the moment it boots. You do not need to be a security expert to be safe.

- **Kernel Hardening** – KASLR, PTI, slab_nomerge, page_poison, nosmt
- **Mandatory Access Control** – AppArmor pre-configured
- **Firewall** – UFW with default deny
- **Brute Force Protection** – Fail2ban
- **System Auditing** – Auditd active by default

### Privacy is Not a Negotiable Option

ScenicOS ships with **zero telemetry**. There is no data collection, no analytics, no cloud dependency, no corporate surveillance. Your data is yours — always.

- No telemetry
- No cloud required
- No AI watching your every move
- No ads
- No tracking

### Beauty is Not Frivolous — It is a Sign of Quality

A system that looks good is a system that is cared for. ScenicOS combines the power of the **Niri scrollable tiling compositor** with the elegance of **DankMaterialShell**, creating a desktop experience that is both functional and stunning.

- **Niri** – Scrollable tiling Wayland compositor
- **DankMaterialShell** – Complete desktop shell with dynamic theming
- **Kaiju** – The official mascot, representing strength, resilience, and the refusal to back down

### Community is the Heart of Open Source

ScenicOS is not owned by a corporation. It is owned by the people who use it. Every contribution, every bug report, every suggestion shapes the future of this project. You are not a user — you are part of the family.

---

## The Journey

This project was not built in a day. It was built in the trenches, one command at a time.

- **From zero to ISO** — Learning live-build, configuring every package, and shaping a system from nothing.
- **Rebuilding the kernel** — Adding hardening flags, testing, failing, and trying again.
- **Branding the system** — Creating the Kaiju mascot, the ASCII art, the MOTD, the identity.
- **Fixing what was broken** — GRUB errors, network issues, audio problems, permission denials.
- **Building the community** — Because software is only as strong as the people who stand behind it.

Every moment was worth it.

---

## What You Will Find Inside

### Security Tools

| Tool | Purpose |
|------|---------|
| AppArmor | Mandatory Access Control |
| UFW | Firewall |
| Auditd | System auditing |
| Fail2ban | Brute force protection |
| Lynis | Security auditing |
| Wireshark | Network analysis |
| tcpdump | Packet capture |

### Desktop Components

| Component | Purpose |
|-----------|---------|
| Niri | Scrollable tiling Wayland compositor |
| DankMaterialShell | Complete desktop shell |
| Alacritty | GPU-accelerated terminal |
| NetworkManager | Network management |

### Custom Scripts

| Command | Description |
|---------|-------------|
| `scenic-info` | Display system information |
| `kaiju-info` | Display Kaiju mascot information |
| `scenic-help` | Display security command help |
| `scenic_health.sh` | System health check script |

### Branding

- **Kaiju Mascot** – A symbol of strength and resilience
- **Tux ASCII Art** – Classic penguin with a modern twist
- **Custom MOTD** – Personalized welcome message
- **Custom Wallpaper** – Kaiju-themed desktop background

---

# Boot from USB
# Select "Install" from GRUB
# Follow the installer
