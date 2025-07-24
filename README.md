Got it. Here's the revised **Fedora 41 Installation Guide** — same structure, but all shell commands are now without `\` line continuations for copy-paste ease.

---

# Fedora 41 Installation Guide

## 1. Download ISO

👉 [Download Fedora 41](https://fedoraproject.org/workstation/download)

---

## 2. Installation

* Language: **English (US)**
* Keyboard: **Norwegian**
* Disk: **Full disk encryption**
* Enable: **Third-party repositories** (for RPM Fusion compatibility)

---

## 3. Post-Install Setup

### System Update

```bash
sudo dnf upgrade -y
reboot
```

### NVIDIA Drivers (with Secure Boot)

Follow the official RPM Fusion guides:

* [NVIDIA Drivers](https://rpmfusion.org/Howto/NVIDIA#Installing_the_drivers)
* [Secure Boot Setup](https://rpmfusion.org/Howto/Secure%20Boot)

> Reboot after signing the kernel module.

---

## 4. Remove Bloat

Open **Software Manager** and remove unused preinstalled apps.

---

## 5. VS Code Setup

Add the Microsoft VS Code repo:

📖 [Setup Instructions](https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions)

---

## 6. Install Common Packages

```bash
sudo dnf install -y code libreoffice-calc libreoffice-impress libreoffice-writer libreoffice-core thunderbird flameshot remmina htop timeshift gnome-disk-utility gnome-system-monitor gnome-control-center gnome-text-editor evince nautilus firefox baobab simple-scan vlc gnome-tweaks gnome-software gnome-clocks kubernetes-client zsh autojump-zsh alacritty nodejs gnome-extensions-app gnome-extensions thefuck vim
```

---

## 7. Flatpak Apps

Install via **Software Manager**:

* Bitwarden
* Discord
* Spotify
* Obsidian

(Requires Flatpak backend enabled.)

---

## 8. GNOME Tweaks

### Extensions to Install

* Pop Shell https://github.com/pop-os/shell
sudo dnf install gnome-shell-extension-pop-shell xprop
* Impatience https://github.com/timbertson/gnome-shell-impatience?tab=readme-ov-file
* Lockscreen Background https://github.com/pratap-panabaka/gse-lockscreen-extension
* System Monitor https://extensions.gnome.org/extension/6807/system-monitor/
* Clipboard History https://github.com/SUPERCILEX/gnome-clipboard-history

Install from [extensions.gnome.org](https://extensions.gnome.org) or via the GNOME Extensions app.

---

## 9. Keyboard Latency Tuning

```bash
gsettings set org.gnome.desktop.peripherals.keyboard repeat-interval 22
gsettings set org.gnome.desktop.peripherals.keyboard delay 200
```

---

## 10. Font
sudo mkdir -p /usr/local/share/fonts/nerd-fonts
cd /usr/local/share/fonts/nerd-fonts
# get correct url http://github.com/ryanoasis/nerd-fonts/releases
sudo curl -LO https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/Hack.zip
sudo unzip Hack.zip
sudo rm Hack.zip LICENSE.md README.md
sudo fc-cache -fv

## 10. Copy Dotfiles
