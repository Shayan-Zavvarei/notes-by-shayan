# Arch Linux + KDE Plasma: Essential & Customization Commands

>  Tested on Arch Linux with KDE Plasma (as of 2025).  
>  Avoid partial upgrades. Always read the [Arch Wiki](https://wiki.archlinux.org/) before making system changes.

---

## 1. Core Package Management (`pacman`)

| Command | Description |
|--------|-------------|
| `sudo pacman -Syu` | Full system update (sync + upgrade). **Always do this first.** |
| `sudo pacman -S package_name` | Install package from official repos |
| `sudo pacman -R package_name` | Remove package (keep dependencies) |
| `sudo pacman -Rs package_name` | Remove package + unused dependencies |
| `sudo pacman -Ss keyword` | Search repos for packages |
| `sudo pacman -Q` | List all installed packages |
| `sudo pacman -Qe` | List **explicitly installed** packages (not dependencies) |
| `sudo pacman -Qi package_name` | Show info about installed package |
| `sudo pacman -Ql package_name` | List files owned by package |
| `sudo pacman -Sc` | Clean package cache (keep current versions) |
| `sudo pacman -Scc` | **Wipe all** package cache (frees space) |
| `sudo pacman -U /path/to/package.pkg.tar.zst` | Install local package file |

>  **Never run `pacman -Sy` alone**—it causes partial upgrades, which break Arch systems.

---

## 2. AUR Helpers (e.g., `yay` or `paru`)

> *Assumes `yay` is installed (`sudo pacman -S yay`)*

| Command | Description |
|--------|-------------|
| `yay` | Update **all** packages (official + AUR) |
| `yay -S package_name` | Install from AUR or repos |
| `yay -Rs package_name` | Remove AUR package + deps |
| `yay -Ps` | Show system stats (orphans, AUR count, etc.) |
| `yay -Yc` | Clean AUR source cache |

---

## 3. System & Service Management (`systemd`)

| Command | Description |
|--------|-------------|
| `sudo systemctl start service` | Start a service |
| `sudo systemctl stop service` | Stop a service |
| `sudo systemctl restart service` | Restart a service |
| `sudo systemctl enable service` | Enable at boot |
| `sudo systemctl disable service` | Disable at boot |
| `systemctl status service` | Check service status |
| `sudo systemctl daemon-reload` | Reload systemd configs |
| `systemctl list-units --type=service` | List all services |

---

## 4. Kernel & Boot

| Command | Description |
|--------|-------------|
| `uname -r` | Show current kernel version |
| `sudo mkinitcpio -P` | Rebuild initramfs for all kernels |
| `sudo grub-mkconfig -o /boot/grub/grub.cfg` | Regenerate GRUB config (if using GRUB) |
| `sudo dracut --force` | Rebuild initramfs (if using Dracut instead of mkinitcpio) |

---

## 5. Disk & File System

| Command | Description |
|--------|-------------|
| `lsblk` | List block devices (disks/partitions) |
| `df -h` | Disk usage (human-readable) |
| `du -sh /path` | Directory disk usage |
| `mount` | List mounted filesystems |
| `sudo umount /mount/point` | Unmount filesystem |
| `sudo fdisk -l` | List partition tables |
| `sudo pacman -S ntfs-3g` | Enable NTFS read/write support |

---

## 6. Networking

| Command | Description |
|--------|-------------|
| `ip a` | Show IP addresses and interfaces |
| `ping archlinux.org` | Test internet connectivity |
| `nmcli` | Control NetworkManager from CLI |
| `iwctl` | Manage Wi-Fi (if using `iwd`) |
| `sudo systemctl start dhcpcd@interface` | Start DHCP on interface (if not using NetworkManager) |

---

## 7. User & Permissions

| Command | Description |
|--------|-------------|
| `sudo usermod -aG wheel username` | Add user to `wheel` group (enables `sudo`) |
| `passwd` | Change current user password |
| `sudo passwd username` | Change another user’s password |
| `groups` | Show current user’s groups |

---

## 8. Logs & Debugging

| Command | Description |
|--------|-------------|
| `journalctl -u service` | View logs for a service |
| `journalctl -b` | Show logs from current boot |
| `journalctl -f` | Follow live system logs |
| `dmesg` | Show kernel messages |

---

## 9. Arch Maintenance Tips

| Command | Description |
|--------|-------------|
| `sudo pacman -Qm` | List packages installed from **AUR only** |
| `sudo pacman -Qdt` | List **orphan packages** (no longer needed) |
| `sudo pacman -Rns $(pacman -Qdtq)` | Remove all orphan packages |
| `sudo reflector --latest 10 --protocol https --sort rate --save /etc/pacman.d/mirrorlist` | Optimize mirrorlist (install `reflector` first) |

---

## 10. Useful CLI Utilities

| Command | Description |
|--------|-------------|
| `grep "text" file` | Search text in file |
| `find /path -name "*.txt"` | Find files by name |
| `tar -xzf archive.tar.gz` | Extract gzip tarball |
| `htop` | Interactive process viewer |
| `neofetch` | Show system info + distro logo |
| `pacdiff` | Manage `.pacnew`/`.pacsave` config files (`pacman-contrib` package) |

> **Recommended base tools**:  
> ```bash
> sudo pacman -S base-devel git htop neofetch vim nano reflector pacman-contrib
> ```

---

# KDE Plasma Customization Commands (Arch Linux)

> All paths and commands assume a standard KDE Plasma 5/6 setup on Arch.

---
## 1. Core KDE Tools & Packages
```bash
# Essential GUI settings
sudo pacman -S systemsettings plasma-desktop kwin

# Advanced theming support
sudo pacman -S kvantum kvantum-manager breeze-gtk oxygen oxygen-icons

# Useful themes & fonts
sudo pacman -S papirus-icon-theme bibata-cursor-theme noto-fonts noto-fonts-cjk noto-fonts-emoji ttf-fira-code
```

## 2. Configuration Files (Key Locations)

| Path | Purpose |
|------|---------|
| `~/.config/kdeglobals` | Global appearance: fonts, colors, widget style |
| `~/.config/kwinrc` | Window behavior, compositing, effects |
| `~/.config/plasmarc` | Desktop layout settings |
| `~/.config/plasma-org.kde.plasma.desktop-appletsrc` | Main file: panels, widgets, wallpaper, activities |
| `~/.local/share/plasma/` | Custom widgets, layouts, and scripts |

**After** editing config files manually, reload Plasma:
```bash
kquitapp5 plasmashell && kstart5 plasmashell
# OR
plasmashell --replace &
```

## 3. Apply Themes & Styles via CLI

| Command | Description |
|--------|-------------|
| `systemsettings5` | Launch KDE System Settings from terminal |
| `lookandfeeltool --list` | List installed desktop themes (Look-and-Feel packages) |
| `lookandfeeltool --apply org.kde.breeze.desktop` | Apply a full desktop theme |
| `plasma-apply-wallpaperimage ~/Pictures/wall.jpg` | Set wallpaper from CLI |
| `plasma-apply-colorscheme BreezeDark` | Apply a color scheme |

## 4. Fonts
```bash
# Set default font (requires Plasma restart)
kwriteconfig5 --file kdeglobals --group General --key font "Noto Sans,10"
kwriteconfig5 --file kdeglobals --group General --key fixed "Fira Code,10"

# Apply
plasmashell --replace &
```

## 5. Icons & Cursor
```bash
# Set icon theme
kwriteconfig5 --file kdeglobals --group Icons --key Theme 'Papirus-Dark'

# Set cursor theme
kwriteconfig5 --file kcminputrc --group Mouse --key cursorTheme 'Bibata-Modern-Classic'
```
#### Note: Cursor changes often require logout/login to fully apply.

## 6. KWin (Window Manager) Effects & Compositor
```bash
# Enable compositing
kwriteconfig5 --file kwinrc --group Compositing --key Enabled true

# Set rendering backend (glx = OpenGL, xrender = fallback)
kwriteconfig5 --file kwinrc --group Compositing --key Backend 'glx'

# Resume compositing (if paused)
qdbus org.kde.KWin /Compositor resume

# Suspend compositing (e.g., for gaming)
qdbus org.kde.KWin /Compositor suspend
```
**Note**:Common backends: `glx` (OpenGL), `xrender` (slower, compatible).

## 7. Reset or Backup Desktop Layout
```bash
# Backup current layout
cp ~/.config/plasma-org.kde.plasma.desktop-appletsrc ~/plasma-layout-backup.cfg

# Reset to default (deletes panels/widgets)
kquitapp5 plasmashell
rm ~/.config/plasma-org.kde.plasma.desktop-appletsrc
kstart5 plasmashell
```
## 8. Install Custom Themes from KDE Store
```bash
# Install CLI tools for KDE Store interaction
sudo pacman -S kde-cli-tools

# Apply a downloaded Look-and-Feel theme
plasma-apply-lookandfeel --path ~/Downloads/MyCustomTheme

# Or install directly via GUI: System Settings > Appearance > Look and Feel > Get New...
```

## 9. Kvantum (Advanced Qt Theming)
1. Install: `sudo pacman -S kvantum kvantum-theme-arc`
2. Set environment (add to `~/.profile` or `~/.pam_environment`):
```bash
export QT_STYLE_OVERRIDE=kvantum
```
3. In **System Settings > Application Style > Widget Style**, choose **Kvantum**.
4. Launch **kvantummanager** to select/engineer themes.
**Note**:
- Kvantum enables modern, rounded, transparent Qt app styling (e.g., for Firefox, LibreOffice, etc.).
- Pro Tip: Always backup ~/.config/ before major theming changes.
- Use rsync -av ~/.config/ ~/kde-config-backup/ for safe snapshots.

