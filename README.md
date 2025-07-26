# Fedora 41 Installation Guide

## Download ISO

[Download Fedora 41](https://fedoraproject.org/workstation/download)

---

## Installation

- **Language:** English (US)
- **Keyboard:** Norwegian
- **Disk:** Full disk encryption
- **Enable:** Third-party repositories (for RPM Fusion compatibility)

---

## Post-Install Setup

### System Update

```bash
sudo dnf upgrade -y
reboot
```

### NVIDIA Drivers (with Secure Boot)

Follow the official RPM Fusion guides:

- [NVIDIA Drivers](https://rpmfusion.org/Howto/NVIDIA#Installing_the_drivers)
- [Secure Boot Setup](https://rpmfusion.org/Howto/Secure%20Boot)

> Reboot after signing the kernel module.

---

## Remove Unused Applications

Open **Software Manager** and uninstall preinstalled apps you do not need.

---

## VS Code Setup

Add the Microsoft VS Code repository:

- [Setup Instructions](https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions)

---

## Install Common Packages

```bash
sudo dnf install -y code libreoffice-calc libreoffice-impress libreoffice-writer libreoffice-core thunderbird flameshot remmina htop timeshift gnome-disk-utility gnome-system-monitor gnome-control-center gnome-text-editor evince nautilus firefox baobab simple-scan vlc gnome-tweaks gnome-software gnome-clocks kubernetes-client zsh autojump-zsh alacritty nodejs gnome-extensions-app gnome-extensions thefuck vim nfs-utils
```

---

## Flatpak Apps

Install via **Software Manager** (requires Flatpak backend enabled):

- Bitwarden
- Discord
- Spotify
- Obsidian

---

## GNOME Tweaks

### Recommended Extensions

- [Pop Shell](https://github.com/pop-os/shell)
  ```bash
  sudo dnf install gnome-shell-extension-pop-shell xprop
  ```
- [Impatience](https://github.com/timbertson/gnome-shell-impatience?tab=readme-ov-file)
- [Lockscreen Background](https://github.com/pratap-panabaka/gse-lockscreen-extension)
- [System Monitor](https://extensions.gnome.org/extension/6807/system-monitor/)
- [Clipboard History](https://github.com/SUPERCILEX/gnome-clipboard-history)
- [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/)

Install extensions from [extensions.gnome.org](https://extensions.gnome.org) or via the GNOME Extensions app.

---

## Keyboard Latency Tuning

```bash
gsettings set org.gnome.desktop.peripherals.keyboard repeat-interval 22
gsettings set org.gnome.desktop.peripherals.keyboard delay 200
```

---

## Install Nerd Fonts

Download and install the Hack Nerd Font:

```bash
sudo mkdir -p /usr/local/share/fonts/nerd-fonts
cd /usr/local/share/fonts/nerd-fonts
sudo curl -LO https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/Hack.zip
sudo unzip Hack.zip
sudo rm Hack.zip LICENSE.md README.md
sudo fc-cache -fv
```
> Find the latest release URL at [Nerd Fonts Releases](https://github.com/ryanoasis/nerd-fonts/releases).

---

## GRUB Themes

- [GRUB2 Themes](https://github.com/vinceliuice/grub2-themes#)

```bash
sudo ./install.sh -t vimix -s 2k
```

**Note:**  
Under EFI, GRUB2 looks for its configuration in `/boot/efi/EFI/fedora/grub.cfg`. The postinstall script of `grub2-common` installs a shim that chains to `/boot/grub2/grub.cfg`.  
To reset this shim to defaults:

```bash
sudo rm -f /boot/efi/EFI/fedora/grub.cfg
sudo dnf reinstall grub2-common
```

---

## Copy Dotfiles

---

## Change Default Shell

Sign out and sign in again after running:

```bash
chsh -s /usr/bin/zsh
```