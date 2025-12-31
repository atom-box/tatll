---
title: Updates, Apt versus Snap versus Flatpak
description:
date: 2025-12-13
tags:
  - linux
layout: layouts/post.njk
---


# Question: How can I Tell What Needs Updating Outside of APT (Ubuntu)

# Answer
__Written 100% by ChatGPT__   
    
This guide explains how to identify software on your Ubuntu system that **does not get updated by `apt`**, and how to check updates for each category.

---

## 1. APT-managed software (baseline)

```bash
sudo apt update
apt list --upgradable
```

Anything listed here is handled by APT and updated with:

```bash
sudo apt upgrade
```

If something is **not listed**, it is managed elsewhere.

---

## 2. Snap-managed software

Snaps are very common on modern Ubuntu and are **not updated by APT**.

### List installed snaps
```bash
snap list
```

### Show pending snap updates
```bash
snap refresh --list
```

### Force snap updates
```bash
sudo snap refresh
```

Executables under `/snap/bin` are snap-managed.

Examples:
- Chromium
- Firefox (on newer Ubuntu)
- VS Code
- Slack

---

## 3. Flatpak-managed software

If Flatpak is installed, it is another parallel update system.

### List Flatpak apps
```bash
flatpak list
```

### Update Flatpak apps
```bash
flatpak update
```

APT has no visibility into Flatpak apps.

---

## 4. AppImage programs

AppImages are **completely unmanaged**.

How to find them:
```bash
find ~ /opt -iname "*.AppImage" 2>/dev/null
```

Updating usually means:
- Downloading a new AppImage
- Or using `appimageupdate` (if supported)

---

## 5. Manually installed software

Check common manual install locations:

```bash
ls /opt
ls /usr/local/bin
```

Anything here is **outside APT control**.

---

## 6. Language-specific package managers

These maintain their own ecosystems.

### Python
```bash
pip list --outdated
pipx list
```

### Node.js
```bash
npm -g outdated
```

### Rust
```bash
cargo install --list
```

### Ruby
```bash
gem outdated
```

APT does not manage any of these.

---

## 7. Firmware updates (fwupd)

Firmware updates are handled separately:

```bash
fwupdmgr get-updates
```

This may include:
- BIOS / UEFI
- SSD firmware
- Thunderbolt controllers

---

## 8. Self-updating applications

Some applications update themselves:
- Google Chrome
- Zoom
- Dropbox
- Steam

Check background update timers:
```bash
systemctl list-timers
```

---

## 9. Identify where programs come from

```bash
which chromium firefox code slack docker python node
```

Interpretation:
- `/usr/bin` → likely APT
- `/snap/bin` → Snap
- `/usr/local/bin` → manual
- Other paths → investigate

---

## Mental Model

Think in **layers**:

| Layer | Update mechanism |
|------|------------------|
| OS libraries | APT |
| Desktop apps | APT / Snap / Flatpak |
| Developer tools | Language managers |
| Portable apps | AppImage |
| Firmware | fwupd |
| Vendor apps | Self-updating |

---

## Recommended maintenance routine

```bash
apt list --upgradable
snap refresh --list
flatpak update
fwupdmgr get-updates
```

Stick to one or two ecosystems where possible to reduce update complexity.