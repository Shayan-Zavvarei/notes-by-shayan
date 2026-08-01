# The Complete LPIC Certification Handbook
## A Comprehensive Self-Study Guide for LPIC-1, LPIC-2, and LPIC-3

---

## Table of Contents

### PART 1 — LPIC-1 (Exams 101 + 102)
1. System Architecture
2. Linux Installation & Package Management
3. GNU/Linux Commands — Complete Reference
4. Devices, Filesystems & FHS
5. Shell Scripting (Bash) — Complete Guide
6. User & Group Management
7. Networking Fundamentals
8. System Logging & Time
9. SSH & Basic Security

### PART 2 — LPIC-2 (Exams 201 + 202)
10. Linux Kernel
11. System Startup & Recovery
12. Storage — RAID, LVM, Filesystems
13. Networking Advanced
14. Backup & Recovery
15. DNS Server (BIND)
16. Web Servers
17. File Sharing Services
18. Mail Services
19. Remote Access & VPN

### PART 3 — LPIC-3 (Exams 300, 303, 305, 306)
20. LDAP & Directory Services (300)
21. Security (303)
22. Virtualization & Containers (305)
23. High Availability & Storage Clusters (306)

### PART 4 — Objective-Aligned Completion & Professional Labs
24. How Commands Work: Intent, Data Flow, Verification, and Safety
25. LPIC-1 Objective Completion: Scheduling, Localization, Desktops, and Printing
26. LPIC-2 Exam 201 Completion: Capacity, Boot, Filesystems, and Maintenance
27. LPIC-2 Exam 202 Completion: DHCP, Proxy, SQL, and Client Services
28. LPIC-3 Exam 300 Completion: Samba, FreeIPA, CIFS, and NFSv4
29. LPIC-3 Exam 303 Completion: PKI, Host Hardening, and Access Control
30. LPIC-3 Exams 305/306 Completion: Provisioning, Isolation, and HA Operations
31. Safe Scenario Labs and LPIC-3 Exam Preparation
32. Official Objective Master Checklist
33. Exam 300 Advanced Operations Supplement
34. Exam 303 Security Operations Supplement
35. Exam 305 Virtualization and Containerization Supplement
36. Exam 306 High Availability and Storage Supplement
37. Distribution-Aware Labs and Final Readiness Gate

### Final Section: Exam Preparation
- Mock Exam 1 — LPIC-1 (101)
- Mock Exam 2 — LPIC-1 (102)
- Mock Exam 3 — LPIC-2 (201)
- Mock Exam 4 — LPIC-2 (202)
- Quick Reference Cheat Sheet

---

## How to Use This Handbook

This handbook is **self-contained**. Read it cover-to-cover, then revisit chapters in any order for review. Every command shown includes its syntax, real-world use case, and runnable examples. Every chapter ends with exercises and mock questions.

**Objective baseline (verify before booking):** LPIC-1 objectives 5.0 (`101-500`, `102-500`), LPIC-2 objectives 4.5 (`201-450`, `202-450`), and LPIC-3 objectives 3.0 (`300-300`, `303-300`, `305-300`, `306-300`). Exam objectives change independently of distributions; always compare this handbook with the current [LPIC-1](https://www.lpi.org/our-certifications/exam-101-102-objectives/), [LPIC-2](https://www.lpi.org/our-certifications/exam-201-202-objectives/), [300](https://www.lpi.org/our-certifications/exam-300-objectives/), [303](https://www.lpi.org/our-certifications/exam-303-objectives/), [305](https://www.lpi.org/our-certifications/exam-305-objectives/), and [306](https://www.lpi.org/our-certifications/exam-306-objectives/) objective pages and weights.

**Lab safety rule:** commands that change partition tables, filesystems, bootloaders, firewall policy, authentication, cluster quorum, or encryption belong on disposable VMs or loop-backed images with snapshots and console access. Replace placeholders such as `/dev/sdX`; never paste them unchanged. Each professional lab in Part 4 includes a verification and rollback step.

**Conventions used throughout:**

- `command` — a shell command or filename
- `# command` — a command run as root
- `$ command` — a command run as a regular user
- **WARNING** — destructive or commonly mis-used behavior
- **NOTE** — clarification or tip
- **TRAP** — frequent LPIC exam pitfall

---

# PART 1 — LPIC-1 (Exams 101 + 102)

---

## Chapter 1: System Architecture

### 1.1 BIOS vs UEFI

**Concept.** When a computer powers on, firmware embedded in the motherboard runs first. Historically this firmware was **BIOS** (Basic Input/Output System), a 16-bit program that initializes hardware and hands control to a bootloader read from the first 512 bytes (MBR) of a disk. Modern systems use **UEFI** (Unified Extensible Firmware Interface), a 32/64-bit firmware that can read FAT-formatted **EFI System Partitions (ESP)**, supports drives larger than 2 TB, offers Secure Boot, and runs `.efi` executables directly.

| Feature | BIOS | UEFI |
|---|---|---|
| Disk style | MBR (max 2 TB, 4 primary) | GPT (zettabyte-scale, 128 partitions) |
| Boot code lives in | First sector (MBR) | EFI System Partition (FAT) |
| Mode | 16-bit real mode | 32/64-bit protected mode |
| Secure Boot | No | Yes |
| Pre-boot environment | Minimal | Shell, drivers, network stack |

**Detection on a running Linux system:**

```bash
# Method 1 — if /sys/firmware/efi exists, you booted via UEFI
#
# General structure:
#   [condition] && [if true] || [if false]
#
# Breakdown:
#   [ -d /sys/firmware/efi ]  — checks if this directory exists (-d = is a directory)
#                               the kernel only creates it on UEFI systems
#   && echo UEFI              — if the check passed (exit code 0), print "UEFI"
#   || echo BIOS              — if nothing succeeded so far, print "BIOS"
#
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

# Method 2 — efibootmgr lists UEFI boot entries (only present on UEFI)
# lists all UEFI boot entries; fails entirely on BIOS systems
efibootmgr -v

# Method 3 — inspect the firmware table only as supporting evidence
dmidecode -t bios
# DMI text is vendor-defined: absence/presence of the word "UEFI" does NOT prove boot mode.
# /sys/firmware/efi is the reliable indicator of how this kernel was booted.
```

**Secure Boot.** A UEFI feature that verifies bootloader signatures against keys stored in firmware (PK, KEK, db, dbx). Linux distributions ship a small signed bootloader called **shim** that loads GRUB. To check status:

```bash
mokutil --sb-state          # prints "SecureBoot enabled" or "disabled"
bootctl status              # systemd-boot view, also reports Secure Boot
```

**Real-world use cases.**
- Diagnosing why a freshly installed distro won't boot (often Secure Boot rejects an unsigned kernel module).
- Choosing the right partition table when installing: UEFI requires GPT + ESP (typically `/boot/efi`, FAT32, ~512 MB, flag `esp`).
- Recovering a wiped boot entry with `efibootmgr -c -d /dev/sda -p 1 -L "Linux" -l '\EFI\debian\grubx64.efi'`.

**Common Mistakes**
- Installing GRUB to `/dev/sda` on a UEFI system. On UEFI, GRUB must be installed into the ESP, not the MBR.
- Forgetting to mount `/boot/efi` before running `grub-install`.
- Disabling Secure Boot to load a third-party driver, then forgetting it's still off months later.

**Exercises**
- *Exercise 1:* On your own machine, determine whether it booted via BIOS or UEFI using three different methods.
- *Exercise 2:* List your current UEFI boot entries with `efibootmgr -v`. Identify which entry is the current default (`BootCurrent`) and which is the next-boot override (`BootNext`).

**Mock Exam Questions**

**Q1.** Which directory's existence reliably indicates the system booted in UEFI mode?
- A) `/proc/efi`
- B) `/sys/firmware/efi`
- C) `/etc/uefi`
- D) `/dev/efi`

**A:** **B.** The kernel exposes UEFI runtime services under `/sys/firmware/efi`. If the system booted via legacy BIOS, this directory does not exist.

**Q2.** Secure Boot verifies signatures against keys stored in which firmware variable?
- A) PK only
- B) db and dbx
- C) MBR
- D) `/etc/shadow`

**A:** **B.** `db` holds allowed signatures and `dbx` is the revocation list. PK and KEK are higher-tier keys used to manage db/dbx but do not directly validate bootloaders.

**Q3 (Scenario).** A technician installs Ubuntu on a UEFI laptop. After installation the machine boots straight to the UEFI shell instead of GRUB. What is the most likely cause and the first fix to try?

**A:** GRUB was likely installed into the MBR of the disk instead of the ESP, leaving no UEFI boot entry. From a live USB, mount the root and ESP, then `grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu`. Verify with `efibootmgr -v`.

**Exam Traps**
- The exam may ask about *gpt* vs *msdos* partition labels. UEFI strongly prefers GPT but can boot from MBR (CSM). BIOS can boot from GPT only if there's a 1 MB BIOS Boot Partition flagged `bios_grub`.
- `efibootmgr` only works on UEFI systems; failing with "EFI variables are not supported" means you booted via BIOS.

---

### 1.2 Hardware Inspection

Linux exposes hardware in several places — sysfs (`/sys`), procfs (`/proc`), and userspace tools that parse them. Know the difference between **what enumerates devices on a bus** (lspci, lsusb) and **what asks the firmware** (dmidecode).

#### `lspci` — list PCI devices

`lspci` enumerates devices on the PCI/PCIe bus and maps numeric vendor/device IDs to names. Use it to answer whether the kernel can see a controller and which driver/module claims it (`-k`); it does not prove the device or application is functioning. Compare with `dmesg`/journal and interface-specific tools for initialization errors.

```
lspci [OPTIONS]
```

| Flag | Meaning |
|---|---|
| `-v`, `-vv`, `-vvv` | Increase verbosity |
| `-k` | Show kernel driver in use |
| `-nn` | Show numeric IDs and names |
| `-t` | Tree view |
| `-s BUS:DEV.FN` | Filter to one device |
| `-d VENDOR:DEVICE` | Filter by vendor/device ID |

```bash
# lspci — list all PCI/PCIe devices (one line each)
# format: [bus]:[device].[function]  [type]  [vendor + model]
lspci

# lspci -nnk | grep -A3 VGA — show GPU driver info
#
# -nn   → append vendor:device IDs in brackets e.g. [8086:9a49]
# -k    → show kernel driver in use + available modules
# |     → pipe output into grep
# grep -A3 VGA → find the line containing "VGA" and print 3 lines After it
#                (those 3 lines contain the driver info we care about)
lspci -nnk | grep -A3 VGA

# lspci -vvv -s 00:1f.2 — exhaustive detail for one specific device
#
# -vvv      → maximum verbosity (interrupts, latency, capabilities...)
# -s 00:1f.2 → select only this address: bus=00, device=1f, function=2
lspci -vvv -s 00:1f.2
```

#### `lsusb` — list USB devices

`lsusb` enumerates USB buses/devices and descriptors. It is the first check for physical detection, vendor/product ID, speed and topology; `lsusb -t` also shows driver and hierarchy. A listed device may still lack permissions, firmware, a class driver, or application support.

```
lsusb [-v] [-s BUS:DEV] [-d VENDOR:PRODUCT] [-t]
```

```bash
lsusb                           # ID-line per attached device
lsusb -t                        # USB topology tree
lsusb -v -d 046d:c52b 2>/dev/null | less   # full descriptor for a Logitech device
```

#### `lshw` — list hardware (broad)

`lshw` combines multiple kernel/firmware sources into a broad hardware tree. Use it for an inventory or to spot `UNCLAIMED` devices, then confirm important facts with focused tools. Some fields require root and firmware-reported values can be incomplete; its output is observation, not configuration.

```
lshw [-class CLASS] [-short] [-html] [-json] [-businfo] [-sanitize]
```

```bash
lshw -short                  # compact, columnar overview
lshw -class network          # NICs only
lshw -class disk -class storage -businfo
```

**NOTE:** `lshw` needs root for full output. As an unprivileged user it warns and produces partial data.

#### `dmidecode` — read SMBIOS/DMI tables

`dmidecode` decodes firmware-provided SMBIOS tables for system, board, BIOS, memory-slot and chassis inventory. It is useful for model/serial/slot information without opening a machine, but firmware may be wrong or generic and DMI does not report how the current kernel actually booted. Treat sensitive serial/asset data accordingly.

`dmidecode` does *not* probe hardware; it reads the firmware's description of itself. Useful for serial numbers, slot layouts, and DIMM info even when slots are empty.

```
dmidecode [-t TYPE | -s KEYWORD]
```

Common type numbers: 0 BIOS, 1 System, 2 Baseboard, 4 Processor, 16 Memory Array, 17 Memory Device.

```bash
dmidecode -t system          # manufacturer, product name, serial
dmidecode -t memory          # all DIMM info incl. empty slots
dmidecode -s bios-version    # one-line lookup
```

#### `/proc` and `/sys` quick map

| File | What it shows |
|---|---|
| `/proc/cpuinfo` | Per-logical-CPU details: model, MHz, flags |
| `/proc/meminfo` | RAM and swap statistics |
| `/proc/interrupts` | IRQ counters per CPU per device |
| `/proc/iomem` | I/O memory map |
| `/proc/ioports` | I/O port allocation |
| `/proc/dma` | Active DMA channels |
| `/proc/modules` | Loaded kernel modules (same as `lsmod`) |
| `/proc/mounts` | Currently mounted filesystems |
| `/proc/partitions` | Block devices seen by the kernel |
| `/sys/block/` | Per-block-device sysfs nodes |
| `/sys/class/net/` | One subdir per network interface |
| `/sys/devices/` | Device tree |

**Common Mistakes**
- Confusing `lspci` (PCI bus only) with `lshw` (everything). Forgetting USB devices won't appear in lspci.
- Running `dmidecode` and expecting it to detect newly inserted hardware. It only knows what firmware advertised.

**Exercises**
- *Exercise 1:* Identify your network card's PCI ID and the kernel driver bound to it using a single `lspci` invocation.
- *Exercise 2:* Without rebooting or opening the case, list the speed of every installed DIMM and the number of empty slots.

**Mock Exam Questions**

**Q1.** Which command shows the kernel driver currently bound to a PCI device?
- A) `lspci -v`
- B) `lspci -k`
- C) `lshw -driver`
- D) `dmesg -d`

**A:** **B.** `-k` adds a "Kernel driver in use:" line. `-v` shows verbose info but the driver line technically comes from `-k` (combined as `-vk` or `-nnk`).

**Q2.** A serial number for the chassis must be retrieved without booting any vendor utility. Which command should be used?
- A) `lspci -t`
- B) `dmidecode -s system-serial-number`
- C) `lsusb -v`
- D) `hdparm -i /dev/sda`

**A:** **B.** `dmidecode -s` reads named SMBIOS fields directly.

**Q3 (Scenario).** A newly added PCIe NIC does not appear in `ip link`. Where do you check first to determine whether the kernel even sees the card?

**A:** `lspci -nnk` — if the card isn't listed, the kernel did not enumerate it (firmware/slot issue). If it is listed but no driver shows under "Kernel driver in use:", it's a driver problem; `dmesg | tail` will usually explain.

---

### 1.3 IRQ, DMA, I/O Ports

These three are legacy x86 hardware-resource concepts you must still know for the exam.

- **IRQ (Interrupt Request)** — a signal a device sends the CPU to demand attention. On modern systems the APIC routes hundreds of vectors; `/proc/interrupts` counts each.
- **DMA (Direct Memory Access)** — a channel allowing a device to read/write RAM without CPU mediation. Modern PCIe uses *bus mastering*; the old ISA DMA channels (0–7) are nearly extinct but `/proc/dma` still exists.
- **I/O Ports** — addresses in a separate I/O address space (in/out instructions on x86). Visible in `/proc/ioports`.

```bash
cat /proc/interrupts | head    # column per CPU, last column = device(s)
cat /proc/ioports | head
cat /proc/dma                   # often empty on modern hardware
```

**Common Mistakes**
- Trying to "free" an IRQ by removing a module — IRQs are not statically owned on modern systems; sharing is normal.

**Exercise**
- *Exercise:* Find which IRQ your keyboard uses, and identify the line in `/proc/interrupts` that has the highest count after one minute of typing.

**Mock Q.** Which file lists I/O memory address ranges assigned to each device?
- A) `/proc/iomem`  B) `/proc/ioports`  C) `/proc/dma`  D) `/proc/interrupts`

**A:** **A.** `/proc/iomem` = memory-mapped I/O regions. `/proc/ioports` = port-I/O addresses (different address space on x86).

---

### 1.4 The Boot Process

A Linux PC follows this chain:

```
Power on
  → Firmware (BIOS or UEFI) POSTs hardware
    → Firmware loads a bootloader
        BIOS: reads 512-byte MBR → stage1 → stage2 (GRUB)
        UEFI: reads ESP → /EFI/<distro>/grubx64.efi
      → Bootloader presents menu, loads kernel + initramfs
        → Kernel decompresses, mounts initramfs (a temporary root in RAM)
          → Kernel runs /init (in initramfs) which loads drivers, then pivots to the real root
            → Kernel executes /sbin/init (PID 1)
                On modern distros, /sbin/init is a symlink to systemd
                  → systemd activates default.target (multi-user.target or graphical.target)
                    → All required services start
                      → getty on tty1..6 (or display manager) → login prompt
```

Key files seen at boot:

| File | Role |
|---|---|
| `/boot/vmlinuz-<ver>` | Compressed kernel image |
| `/boot/initrd.img-<ver>` or `/boot/initramfs-<ver>.img` | Initial RAM filesystem |
| `/boot/System.map-<ver>` | Kernel symbol table (for debugging) |
| `/boot/config-<ver>` | Kernel build options |
| `/boot/grub/grub.cfg` (BIOS) or `/boot/efi/EFI/.../grub.cfg` (UEFI) | GRUB menu |

**Common Mistakes**
- Editing `grub.cfg` directly. It is regenerated; edit `/etc/default/grub` and `/etc/grub.d/*`, then run `grub-mkconfig -o /boot/grub/grub.cfg` (or `update-grub` on Debian).

**Exercises**
- *Exercise 1:* Add `quiet` to kernel command line for one boot only by editing the GRUB entry at the menu (press `e`).
- *Exercise 2:* From a running system, identify the exact kernel image and initramfs that were loaded at boot using `/proc/cmdline` and the current kernel version.

**Mock Exam Questions**

**Q1.** PID 1 on a modern systemd-based distribution is:
- A) `init`  B) `systemd`  C) `kthreadd`  D) `kernel`

**A:** **B.** `/sbin/init` is typically a symlink to `/lib/systemd/systemd`; the process visible as PID 1 is `systemd`.

**Q2 (Scenario).** A user reports "Boot hangs at 'Loading initial ramdisk'". Which file is being loaded and where is it located on a typical Debian system?

**A:** `/boot/initrd.img-<version>`, the initial RAM filesystem (initramfs). It contains drivers needed to mount the real root.

**Q3.** Which directory holds GRUB's modular files and font?
- A) `/etc/grub2/`  B) `/boot/grub/`  C) `/usr/share/grub/`  D) `/var/lib/grub/`

**A:** **B.** `/boot/grub/` is the installed location (with `i386-pc/`, `themes/`, `fonts/`, `locale/` subdirs).

---

### 1.5 SysVinit vs systemd vs Upstart

| | SysVinit | Upstart | systemd |
|---|---|---|---|
| Boot model | Serial, runlevel-based | Event-driven | Dependency-based, parallel |
| Config | `/etc/inittab`, `/etc/init.d/` | `/etc/init/*.conf` | `/etc/systemd/system/*.{service,target,...}` |
| Primary tool | `service`, `chkconfig` / `update-rc.d` | `initctl` | `systemctl` |
| Used by today | Devuan, old RHEL ≤6 | Old Ubuntu (9.10–14.10) | Almost every mainstream distro |

#### SysVinit runlevels

| Level | Meaning (Red Hat) |
|---|---|
| 0 | Halt |
| 1 / S | Single-user |
| 2 | Multi-user, no NFS (Debian: multi-user) |
| 3 | Multi-user with networking |
| 4 | Unused / custom |
| 5 | Multi-user with GUI |
| 6 | Reboot |

```bash
runlevel             # prints previous and current runlevel
who -r               # current runlevel with timestamp
init 3               # switch to runlevel 3 (legacy)
telinit 5            # same as above
```

#### systemd targets (equivalents)

| Runlevel | systemd target |
|---|---|
| 0 | `poweroff.target` |
| 1 | `rescue.target` |
| 3 | `multi-user.target` |
| 5 | `graphical.target` |
| 6 | `reboot.target` |
| — | `emergency.target` (minimal shell, no mounting beyond /) |

```bash
systemctl get-default                  # what target boots by default
systemctl set-default multi-user.target
systemctl isolate rescue.target        # switch now
systemctl list-units --type=target
```

#### `systemctl` — the core systemd command

`systemctl` is the control/query client for systemd's manager and unit dependency graph. Separate three questions: **runtime state** (`start`, `stop`, `is-active`), **boot policy** (`enable`, `disable`, `is-enabled`), and **configuration visibility** (`cat`, `show`, `daemon-reload`). Enabling does not start a unit now, and starting does not necessarily enable it for the next boot. Prefer `reload` only when the service supports a safe configuration reload; otherwise validate configuration and restart with an availability plan.

```
systemctl [OPTIONS] COMMAND [UNIT...]
```

| Command | Purpose |
|---|---|
| `start UNIT` | Activate a unit now |
| `stop UNIT` | Deactivate now |
| `restart UNIT` | Stop then start |
| `reload UNIT` | Ask service to re-read config without stopping |
| `enable UNIT` | Create symlinks so it starts at boot |
| `disable UNIT` | Remove those symlinks |
| `mask UNIT` | Make it impossible to start (symlinks to `/dev/null`) |
| `unmask UNIT` | Reverse mask |
| `status UNIT` | Active state, last log lines |
| `is-active UNIT` | Exit 0 if active |
| `is-enabled UNIT` | Exit 0 if enabled |
| `list-units` | Currently loaded units |
| `list-unit-files` | All known unit files and their enabled state |
| `daemon-reload` | Re-scan unit files after editing |
| `cat UNIT` | Print effective unit file (with drop-ins) |
| `edit UNIT` | Open drop-in override in `$EDITOR` |
| `show UNIT` | Print every property |

```bash
systemctl status sshd
systemctl restart nginx
systemctl enable --now docker         # enable AND start in one go
systemctl mask cups                   # ensure nothing brings printing back up
systemctl list-units --failed         # quick triage after boot
```

**Common Mistakes**
- Editing a unit file in `/lib/systemd/system/` directly — package updates overwrite it. Use `systemctl edit UNIT` to create `/etc/systemd/system/UNIT.d/override.conf`.
- Forgetting `daemon-reload` after editing a unit file.
- Using `enable` without `--now` and expecting the service to be running already.

**Exercises**
- *Exercise 1:* Create a one-line override that adds `Environment="DEBUG=1"` to your sshd service without touching the original unit file.
- *Exercise 2:* Find every service currently in a failed state and explain how to inspect *why* each failed.

**Mock Exam Questions**

**Q1.** Which systemctl subcommand makes a unit impossible to start by accident?
- A) `disable`  B) `stop`  C) `mask`  D) `freeze`

**A:** **C.** `mask` symlinks the unit to `/dev/null`, so even `start` fails.

**Q2.** Which target is approximately equivalent to runlevel 5?
- A) `multi-user.target`  B) `graphical.target`  C) `rescue.target`  D) `default.target`

**A:** **B.** `graphical.target` provides GUI on top of multi-user.target.

**Q3 (Scenario).** After editing `/etc/systemd/system/myapp.service` the next `systemctl start myapp` still uses the old config. Why, and how do you fix it?

**A:** systemd caches unit files in memory. Run `systemctl daemon-reload`, then start.

**Q4.** A unit is `enabled` but not `active`. What does that combination mean?
- A) It's running but won't start at boot
- B) It will start at next boot but is not running now
- C) It is masked
- D) It has failed

**A:** **B.** `enabled` controls boot persistence; `active` is current state.

---

### 1.6 Kernel Ring Buffer — `dmesg` and `journalctl -k`

The kernel logs to a circular memory buffer (the "ring buffer"). On boot this is the only log; after userspace starts, systemd-journald and rsyslog also persist these messages.

```
dmesg [OPTIONS]
```

| Flag | Meaning |
|---|---|
| `-T` | Estimated wall-clock timestamps (convenient, but may be inaccurate after clock changes) |
| `-H` | Pager + colors + relative times |
| `-w` | Follow (like `tail -f`) |
| `-l LEVEL` | Filter by level: emerg, alert, crit, err, warn, notice, info, debug |
| `-k` | Kernel facility only (default in dmesg) |
| `--clear` | Clear the buffer (root) |

```bash
dmesg | tail
dmesg -T --level=err,warn
dmesg -w &                  # tail-style monitoring in background
journalctl -k --since "10 min ago"
journalctl -b -p err        # errors from this boot
journalctl -b -1            # previous boot
```

**Common Mistakes**
- Believing `dmesg` survives reboots. The ring buffer is cleared at every boot; for history use `journalctl -k -b -N` (with negative N for older boots), assuming persistent journal is enabled (`/var/log/journal/` exists).
- Treating `dmesg -T` as forensic time. Kernel records use time since boot; `-T` converts them using the current clock offset. Prefer journal timestamps for correlation and retain monotonic timestamps when precision matters.

**Exercise**
- *Exercise:* Display every kernel error from the previous boot only.

**Mock Q.** Which command prints kernel messages from the *previous* boot only?
- A) `dmesg --previous`
- B) `journalctl -k -b -1`
- C) `cat /var/log/kern.log.1`
- D) `dmesg -b 1`

**A:** **B.** `dmesg` only knows current boot; `journalctl -b -1` selects the boot before current. (Option C may work but only if rsyslog kept it and is not the universal answer.)

---

## Chapter 2: Linux Installation & Package Management

### 2.1 Disk Partitioning Strategies — MBR vs GPT

| | MBR (`msdos`) | GPT |
|---|---|---|
| Max disk size | 2 TB (with 512-byte sectors) | ~9.4 ZB |
| Partitions | 4 primary, or 3 primary + 1 extended (with logical inside) | Up to 128 by default |
| Checksum | None | CRC32 on header + table |
| Backup | None | Yes (secondary GPT at end of disk) |
| Firmware required | BIOS or UEFI (CSM) | UEFI (or BIOS with `bios_grub` 1 MB partition) |

**Standard partition layouts you should be able to design:**

- **Workstation / laptop (UEFI):**
  - `/boot/efi` — 512 MB, FAT32, `esp` flag
  - `/` — 30 GB+, ext4
  - `/home` — remainder
  - swap — RAM size if you use hibernation, otherwise 1–4 GB or a swap file
- **Server:**
  - `/boot` — 1 GB, ext4 (so encryption can wrap everything else)
  - `/boot/efi` — 512 MB, FAT32
  - `/` — LVM PV → LVs for `/`, `/var`, `/home`, swap

### 2.2 `fdisk`, `gdisk`, `parted`

#### `fdisk` — interactive, MBR-first (also GPT since util-linux 2.23)

`fdisk` edits the partition table—the map describing regions of a disk—not the filesystems inside those regions. Most changes are staged in memory until the write command, but writing can make existing data unreachable. Print and record the table first, verify sector units/alignment, and work on disposable images while learning.

```
fdisk [-l] [DEVICE]
```

Interactive commands inside `fdisk`:
- `p` print, `n` new, `d` delete, `t` type, `l` list types
- `g` create new GPT label, `o` create new MBR label
- `w` write, `q` quit without writing

```bash
fdisk -l                       # all disks summary
fdisk -l /dev/sda              # one disk
fdisk /dev/sdb                 # interactive partitioning
```

#### `gdisk` — interactive, GPT-only

`gdisk` is GPT-focused and understands primary/backup GPT headers, GUIDs and GPT type codes. Use it when inspecting or repairing GPT-specific structures; recovery commands can rewrite metadata, so distinguish a damaged backup header from a wrong disk selection and preserve an image before repair.

Same letters as `fdisk`. Additionally: `r` (recovery menu), `x` (expert menu).

```bash
gdisk -l /dev/sda
sgdisk --print /dev/sda        # non-interactive scripted variant
sgdisk -n 1:0:+512M -t 1:ef00 -c 1:"EFI" /dev/sda
```

#### `parted` — script-friendly, supports both

`parted` supports GPT/MBR and scripted creation/resizing of partition boundaries. Unlike some interactive tools, many operations take effect immediately rather than waiting for a final write command. Its `resizepart` changes only the partition boundary, not the contained filesystem; grow/shrink layers in the safe order for that filesystem.

```
parted [-s] [-a ALIGN] DEVICE COMMAND [ARGS]
```

```bash
parted /dev/sdb mklabel gpt
parted -s /dev/sdb mkpart primary ext4 1MiB 100%
parted /dev/sdb print
parted /dev/sda set 1 esp on
```

**TRAP:** `parted` writes changes *immediately*; there is no "save and quit" like `fdisk`. Use a test VM!

**Common Mistakes**
- Re-creating a partition with `fdisk`, forgetting the filesystem header is still there, then surprised `mount` works on the "new" partition.
- Forgetting to inform the kernel of partition changes on a mounted disk: `partprobe /dev/sda` or `partx -u /dev/sda`.

**Exercises**
- *Exercise 1:* Using `parted` non-interactively, build a GPT layout on `/dev/sdX`: 512 MB ESP, 1 GB `/boot`, rest as LVM.
- *Exercise 2:* On a disposable VM disk or loop-backed image (never the host disk), back up the partition table, convert an MBR test image to GPT, verify it, and practise restoring the backup. Note: `sgdisk -g` randomizes a disk GUID; it is not the MBR-to-GPT conversion command.

**Mock Exam Questions**

**Q1.** Which partition flag identifies the EFI System Partition under `parted`?
- A) `boot`  B) `esp`  C) `bios_grub`  D) `lvm`

**A:** **B.** `set N esp on` (equivalent to `boot` on GPT for ESP). `bios_grub` is the 1 MB partition needed for GRUB on a *BIOS-booted GPT disk*.

**Q2.** A disk uses MBR. You created three primary partitions, then need a fourth and fifth. What is the correct approach?
- A) Use GPT — MBR allows only three partitions
- B) Make the fourth an extended partition and place logical partitions inside it
- C) Add a second disk
- D) Resize one primary partition

**A:** **B.** MBR allows up to four primary, but a logical partition must live inside an extended. So convert one to extended OR start with three primaries + one extended.

**Q3 (Scenario).** After running `parted /dev/sda mkpart primary ext4 1MiB 50%`, the filesystem isn't there. Why?

**A:** `parted` creates the partition table entry but does not create the filesystem. Run `mkfs.ext4 /dev/sda1`.

---

### 2.3 Filesystem Types and `mkfs`

| FS | Strengths | Weaknesses | Use case |
|---|---|---|---|
| ext2 | Simple, no journal | Slow fsck after crash | Embedded, USB |
| ext3 | ext2 + journal | Older | Legacy systems |
| ext4 | Journal, extents, large files (≤16 TB), online resize | None major for general use | Default for many distros |
| xfs | Excellent large-file & parallel I/O performance, online grow only | Cannot shrink | Big storage, RHEL default |
| btrfs | Snapshots, CoW, RAID, checksums | Some configs unstable | Snapshot-heavy workloads, openSUSE default |
| vfat | Universal compat | No POSIX perms, no journal | EFI partition, USB sticks |
| swap | Paging area | n/a | Memory overflow |
| ntfs | Windows interop | Performance via ntfs-3g userspace | Shared dual-boot data |

#### `mkfs` family

`mkfs` dispatches to a filesystem-specific formatter and writes new filesystem metadata onto a block device. It is destructive to prior contents and is not the command for making a mount point directory. Confirm the exact unused device, signatures, stack layers and desired filesystem/features before running it, then verify with `blkid` and a controlled mount.

```
mkfs.<TYPE> [OPTIONS] DEVICE
```

```bash
mkfs.ext4 -L data /dev/sdb1
mkfs.xfs  -L data /dev/sdb1
mkfs.vfat -F 32 -n EFI /dev/sda1
mkswap -L swap /dev/sdb2 && swapon /dev/sdb2
```

Useful ext flags:
- `-L LABEL` — filesystem label
- `-U UUID` — explicit UUID
- `-N COUNT` — inode count (e.g., many tiny files)
- `-b SIZE` — block size
- `-m %` — reserved-for-root percentage (default 5%, lower for large data disks)
- `-T TYPE` — usage hint (`largefile4`, etc.)

#### `tune2fs` — change ext2/3/4 parameters

`tune2fs` queries or changes persistent ext-family superblock settings such as label, reserved-block percentage and check policy. `-l` is query-only; other options can materially change recovery/capacity behavior. It is not a general tool for XFS/Btrfs and it does not replace `e2fsck`.

```bash
tune2fs -l /dev/sda1                  # print all superblock info
tune2fs -L newlabel /dev/sda1
tune2fs -U random /dev/sda1
tune2fs -c 30 /dev/sda1               # force fsck every 30 mounts
tune2fs -i 1m /dev/sda1               # force fsck every 1 month
tune2fs -m 1 /dev/sda1                # reserve 1% (default 5%)
tune2fs -O ^has_journal /dev/sda1     # remove journal (turns ext4 → ext2)
```

#### `xfs_info`, `xfs_growfs`, `xfs_repair`

These serve distinct XFS tasks: `xfs_info` reports geometry/features, `xfs_growfs` expands a mounted filesystem after its underlying device grows, and `xfs_repair` checks/repairs an unmounted filesystem. XFS cannot shrink. Never use `xfs_repair -L` casually—it discards a corrupt log and can lose recent metadata changes.

```bash
xfs_info /mnt/data
xfs_growfs /mnt/data              # online expand to fill underlying LV
xfs_repair -L /dev/sdb1           # offline; -L zeros the log (dangerous)
```

**TRAP:** XFS *cannot* shrink. The exam asks this repeatedly.

**Common Mistakes**
- Running `mkfs` on the wrong device. Always verify with `lsblk` first.
- Using `tune2fs -O ^has_journal` on a mounted filesystem (allowed but risky on the root).

**Exercises**
- *Exercise 1:* Create an ext4 filesystem with label `archive`, reserved-blocks 0%, and verify with `tune2fs -l`.
- *Exercise 2:* Convert an ext3 partition to ext4 in place using `tune2fs -O extents,uninit_bg,dir_index` and `fsck`.

**Mock Exam Questions**

**Q1.** Which filesystem cannot be shrunk while online?
- A) ext4  B) xfs  C) btrfs  D) ext2

**A:** **B.** XFS supports only growth.

**Q2.** What does `tune2fs -m 1 /dev/sda1` do?
- A) Sets max mount count to 1
- B) Reserves 1% of the filesystem for privileged processes
- C) Marks the FS read-only after 1 error
- D) Sets the block size to 1 KB

**A:** **B.** `-m` adjusts the reserved-blocks percentage (default 5%).

**Q3 (Scenario).** You ran `mkfs.ext4 /dev/sdb1` accidentally on a filesystem holding data. What is the *first* command you should consider before doing anything else?

**A:** Stop using the disk and run `e2undel`/`extundelete`/`testdisk` to attempt recovery. Do not mount, do not write. The data is likely still intact in unallocated blocks because `mkfs` mainly writes the superblock and inode tables; full overwrite would have required `mkfs -F` plus zero-fill.

---

### 2.4 GRUB2

GRUB2 reads `/boot/grub/grub.cfg` (or `/boot/grub2/grub.cfg` on RHEL) — **do not edit it directly**. Edit `/etc/default/grub` and scripts in `/etc/grub.d/`, then regenerate:

```bash
grub-mkconfig -o /boot/grub/grub.cfg          # Debian/Ubuntu/Arch
update-grub                                    # Debian wrapper
grub2-mkconfig -o /boot/grub2/grub.cfg         # RHEL/CentOS
```

#### Reinstalling GRUB

```bash
# BIOS
grub-install /dev/sda

# UEFI
grub-install --target=x86_64-efi \
             --efi-directory=/boot/efi \
             --bootloader-id=debian
```

#### Key `/etc/default/grub` variables

| Variable | Purpose |
|---|---|
| `GRUB_DEFAULT` | Default menu entry (number or "saved") |
| `GRUB_TIMEOUT` | Seconds to wait |
| `GRUB_CMDLINE_LINUX` | Kernel parameters always applied |
| `GRUB_CMDLINE_LINUX_DEFAULT` | Applied to normal entries only |
| `GRUB_DISABLE_RECOVERY` | If `true`, no "recovery" entries |
| `GRUB_GFXMODE` | Resolution |

#### Manual menu entry (`/etc/grub.d/40_custom`)

```
menuentry "My Custom Boot" {
    set root=(hd0,gpt2)
    linux /vmlinuz-5.15 root=/dev/sda2 ro quiet
    initrd /initrd.img-5.15
}
```

#### Password protection

```
# /etc/grub.d/40_custom
set superusers="admin"
password_pbkdf2 admin grub.pbkdf2.sha512.10000.XXXXXXXX...
```

Generate the hash with `grub-mkpasswd-pbkdf2`. Then `update-grub`.

#### Recovery — boot to a shell

At the GRUB menu press `e`. Edit the `linux` line, change `ro` to `rw`, and append `init=/bin/bash` (or `systemd.unit=rescue.target`). Press `Ctrl+X` to boot.

**Common Mistakes**
- Editing `grub.cfg`, then running `update-grub` and being surprised the changes vanished.
- Forgetting to mount `/boot/efi` before `grub-install` on UEFI.
- Setting `GRUB_DEFAULT=saved` without `GRUB_SAVEDEFAULT=true` and using `grub-set-default`.

**Exercises**
- *Exercise 1:* In a disposable VM, add a harmless parameter such as `systemd.show_status=1` for one boot, inspect `/proc/cmdline`, then remove it. Do not disable CPU vulnerability mitigations on a real system merely as an exercise.
- *Exercise 2:* Boot once into rescue without modifying any config file.

**Mock Exam Questions**

**Q1.** After editing `/etc/default/grub`, which command must you run?
- A) `grub-update`  B) `update-grub` (or `grub-mkconfig -o ...`)  C) `systemctl reload grub`  D) Nothing — GRUB rereads on next boot

**A:** **B.** GRUB does not parse `/etc/default/grub` at boot; the file is consumed by `grub-mkconfig` to regenerate `grub.cfg`.

**Q2.** Which file should *not* be edited manually on a modern Linux system?
- A) `/etc/default/grub`
- B) `/etc/grub.d/40_custom`
- C) `/boot/grub/grub.cfg`
- D) `/etc/fstab`

**A:** **C.**

**Q3 (Scenario).** You forgot the root password. Outline a recovery using GRUB.

**A:** Reboot, at GRUB menu press `e`, append `rw init=/bin/bash` to the linux line, `Ctrl+X` to boot. You land in a root shell with `/` mounted RW. Run `passwd`, then `exec /sbin/init` or reboot.

---

### 2.5 RPM Package Management

`rpm` works on a single-package level. The `.rpm` file is a CPIO archive plus header.

```
rpm [-i|-U|-F|-e|-q|-V] [OPTIONS] PACKAGE
```

| Mode | Meaning |
|---|---|
| `-i` (install) | Install if not present |
| `-U` (upgrade) | Install or upgrade |
| `-F` (freshen) | Upgrade only if installed |
| `-e` (erase) | Remove |
| `-q` (query) | Ask about installed package(s) |
| `-V` (verify) | Check integrity vs DB |

Common queries:

```bash
rpm -qa                            # all installed packages
rpm -qi httpd                      # detailed info
rpm -ql httpd                      # files installed by httpd
rpm -qf /etc/httpd/conf/httpd.conf # which package owns this file
rpm -qc httpd                      # config files only
rpm -qd httpd                      # doc files
rpm -q --scripts httpd             # pre/post install scripts
rpm -q --changelog httpd | head
rpm -qp --requires pkg.rpm         # deps of a not-yet-installed file
rpm -V httpd                       # verify integrity
rpm -Va                            # verify everything
```

Verify output legend (each column compares to original): `S` size, `M` mode, `5` MD5, `D` device, `L` symlink target, `U` owner, `G` group, `T` mtime, `c` config file.

```bash
rpm -ivh package.rpm           # install with progress bar
rpm -Uvh package.rpm           # upgrade
rpm -e --nodeps package        # force remove ignoring deps
rpm -e --justdb package        # remove from DB only (dangerous)
rpm --rebuilddb                # rebuild RPM DB if corrupted
```

**Common Mistakes**
- Using `rpm -i` to install a package that depends on others not yet installed. Use yum/dnf instead.
- Running `rpm --force --nodeps` to "fix" issues; this almost always makes it worse.

### 2.6 YUM / DNF

`yum` is the older Python 2 tool; `dnf` is its modern replacement (RHEL 8+). Commands are largely identical.

```
yum|dnf COMMAND [OPTIONS] [PACKAGE...]
```

| Command | Use |
|---|---|
| `install PKG` | Install + deps |
| `remove PKG` | Remove |
| `update [PKG]` | Update all or one |
| `upgrade` | Same as update on DNF |
| `search KEY` | Search names and summaries |
| `info PKG` | Detailed info |
| `list installed` | All installed |
| `list available` | All in enabled repos |
| `provides PATH` | Which package owns a file |
| `whatprovides PATH` | Same |
| `repolist` | Enabled repos |
| `clean all` | Clear cache |
| `history` | Transaction log |
| `history undo N` | Roll back transaction |
| `grouplist` | Available groups |
| `groupinstall "GROUP"` | Install a group |
| `module list / install` | (DNF 8+) Streams |

```bash
dnf install -y httpd
dnf install --enablerepo=epel htop
dnf history
dnf history undo 42
dnf provides */sshd
dnf repoquery -l httpd               # like rpm -ql but for a not-yet-installed pkg
```

#### Repository configuration

Files in `/etc/yum.repos.d/*.repo`:

```ini
[epel]
name=Extra Packages for Enterprise Linux
baseurl=https://download.fedoraproject.org/pub/epel/$releasever/Everything/$basearch/
enabled=1
gpgcheck=1
gpgkey=https://...
priority=10
```

#### Priorities & pinning

- Install `dnf-plugins-core`; lower `priority=` number means higher priority.
- `dnf config-manager --set-disabled REPO`

**Exercises**
- *Exercise 1:* Find which package provides `/usr/bin/awk` without installing it.
- *Exercise 2:* Undo the last DNF transaction.

**Mock Exam Questions**

**Q1.** Which command shows files that would be installed by a package available in a repository, before installation?
- A) `rpm -ql PKG`
- B) `dnf repoquery -l PKG`
- C) `yum filelist PKG`
- D) `dnf preview PKG`

**A:** **B.** `rpm -ql` only works on already-installed packages.

**Q2.** Which RPM verification flag means the file's MD5 checksum has changed?
- A) `S`  B) `T`  C) `5`  D) `M`

**A:** **C.** `5` indicates an MD5 mismatch. `S` is size, `M` is mode, `T` is mtime.

**Q3 (Scenario).** After installing several packages with `dnf install`, you want to roll back to the exact previous state. How?

**A:** `dnf history` to find the transaction ID, then `dnf history undo <ID>`.

---

### 2.7 DPKG and APT

`dpkg` is the low-level Debian-package tool (parallel to `rpm`). `apt`/`apt-get` is the high-level dependency resolver.

#### `dpkg`

`dpkg` is the low-level Debian package database/archive tool. It installs a local `.deb` and queries exact package/file ownership, but it does not resolve/download dependency graphs like APT. Use it for local inspection and repair diagnosis; if `dpkg -i` leaves dependencies unconfigured, let APT resolve them rather than repeatedly forcing state.

```bash
dpkg -i package.deb              # install
dpkg -r package                  # remove (keep configs)
dpkg -P package                  # purge (also configs)
dpkg --configure -a              # finish interrupted installs
dpkg -l                          # list installed (status flags in cols 1-3)
dpkg -l 'apache*'                # glob match
dpkg -L package                  # files installed by package
dpkg -S /etc/ssh/sshd_config     # which package owns this file
dpkg -s package                  # show package status
dpkg -c package.deb              # list files in a .deb file
dpkg -x package.deb /tmp/extract # extract without installing
dpkg-reconfigure tzdata          # rerun configuration
```

`dpkg -l` status columns: `Desired` (u=unknown, i=install, h=hold, r=remove, p=purge), `Status` (n=not-installed, c=config-files, U=unpacked, F=halfconf, i=installed, W=triggers-await, t=triggers-pend), `Error` (R=reinst-required).

So `ii` = installed cleanly; `rc` = removed but configs remain; `iU` = unpacked, needs configure.

#### `apt` / `apt-get` / `apt-cache`

APT resolves dependencies and retrieves packages from configured repositories above `dpkg`. `apt` is a friendly interactive interface; `apt-get`/`apt-cache` have more stable scripting traditions. `update` refreshes repository metadata but installs no upgrades; `upgrade` changes installed packages based on that metadata. Review removals/new dependencies before accepting high-impact transactions and use `apt-cache policy` to understand candidate versions.

```bash
apt update                       # refresh package lists
apt upgrade                      # upgrade without removing
apt full-upgrade                 # may remove obsolete
apt install pkg
apt remove pkg
apt purge pkg
apt autoremove                   # remove unused deps
apt search keyword
apt show pkg
apt list --installed
apt list --upgradable
apt-mark hold pkg                # prevent updates
apt-mark unhold pkg
apt-mark auto pkg                # mark as automatically installed
apt-cache policy pkg             # show installed/candidate/sources
apt-cache depends pkg
apt-cache rdepends pkg
```

#### sources.list

`/etc/apt/sources.list` and `/etc/apt/sources.list.d/*.list`:

```
deb http://deb.debian.org/debian bookworm main contrib non-free
deb-src http://deb.debian.org/debian bookworm main
deb http://security.debian.org/debian-security bookworm-security main
```

Format: `deb URL DISTRIBUTION COMPONENT [COMPONENT...]`

#### Keys

Older systems used `apt-key add`. Modern Debian/Ubuntu use signed-by:

```
deb [signed-by=/usr/share/keyrings/foo.gpg] https://... bookworm main
```

Place keyrings under `/etc/apt/keyrings/` or `/usr/share/keyrings/`.

#### Pinning

`/etc/apt/preferences.d/example`:

```
Package: *
Pin: release a=bookworm-backports
Pin-Priority: 100
```

APT selects the highest-priority available version, then applies version rules. A priority **below 0** prevents installation; `1–99` normally installs only when no version is installed; `100` is commonly the priority of the installed version/backports example; `500` is typical for an unconfigured repository; `990` is typical for the target release; and values above `1000` may permit a downgrade. Verify the real decision with `apt-cache policy PACKAGE`—do not memorize the ranges as a complete selection algorithm.

**Common Mistakes**
- `dpkg -r` leaves configs; users mistake it for full removal. Use `dpkg -P` (or `apt purge`).
- Forgetting `apt update` before `apt install`; you get stale candidates.

**Exercises**
- *Exercise 1:* Find which package owns `/etc/cron.daily/apt-compat`.
- *Exercise 2:* Hold the `linux-image-*` packages so a kernel upgrade does not run.

**Mock Exam Questions**

**Q1.** Which dpkg invocation lists files a package contains *before* installing the `.deb`?
- A) `dpkg -L pkg.deb`  B) `dpkg -c pkg.deb`  C) `dpkg -s pkg.deb`  D) `dpkg -I pkg.deb`

**A:** **B.** `-c` (contents). `-L` is for installed packages by name. `-I` shows control info.

**Q2.** What does the status `rc` mean in `dpkg -l` output?
- A) Reinstall required
- B) Removed, configs remain
- C) Real config (current)
- D) Recursive child package

**A:** **B.**

**Q3 (Scenario).** APT refuses to install a package, citing dependency conflicts. What is the safest *next* command?

**A:** `apt-cache policy <package>` and `apt-cache depends <package>` to see exactly what's missing and from which repo. Avoid `--force-*` until the cause is understood. `apt install -f` may fix broken deps after a failed dpkg.

---

### 2.8 Snap and Flatpak (Overview)

| Feature | Snap | Flatpak |
|---|---|---|
| Sponsor | Canonical | Independent |
| Store | snapcraft.io | flathub.org |
| Runtime | snapd | flatpak |
| Sandboxing | AppArmor + cgroups | Bubblewrap |
| File location | `/snap/`, `/var/snap/` | `/var/lib/flatpak/`, `~/.local/share/flatpak/` |
| Autoupdate | Yes, forced | Optional |

```bash
snap find vscode
snap install code --classic
snap list
snap refresh
snap revert code

flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.gnome.Calculator
flatpak run org.gnome.Calculator
flatpak update
```

**TRAP:** Snap mounts a squashfs per package and these appear in `df` and `mount` output. The exam may show a packed `mount` output and ask you to identify them.

---

## Chapter 3: GNU/Linux Commands — Complete Reference

This chapter is the heart of LPIC-1. Do not memorize flags in isolation. For each utility, know the problem it solves, what it reads, whether it changes state, what its exit status means, and which independent command verifies the result. Examples without `sudo` are normally queries or user-owned-file operations; destructive storage, account, process, and system configuration examples belong in a disposable lab.

### 3.1 Navigation & File Management

#### `ls` — list directory contents

`ls` asks the filesystem for directory entries and selected metadata. Use it for a quick human inventory, not as a reliable parser input: quoting, locale-dependent sorting, color escapes, newlines in filenames, aliases, and changing default formats make `ls` output fragile in scripts. For automation prefer globs, `find -print0`, or a command's machine-readable format.

```
ls [OPTIONS] [PATH...]
```

| Flag | Meaning |
|---|---|
| `-l` | Long format |
| `-a` | All including dotfiles |
| `-A` | All except `.` and `..` |
| `-h` | Human-readable sizes (with `-l`) |
| `-S` | Sort by size, largest first |
| `-t` | Sort by mtime, newest first |
| `-r` | Reverse sort |
| `-R` | Recursive |
| `-i` | Show inode numbers |
| `-d` | List the directory itself, not contents |
| `-1` | One entry per line |
| `--color=auto` | Colored output |

```bash
ls -lah                 # detailed, all, human sizes
ls -ltr                 # oldest at top (good for log dirs)
ls -ld /var             # info about /var, not its contents
ls -i file              # see inode number
```

The columns of `ls -l`:

```
-rwxr-xr-x  1  root  root  12345  Jun 11 10:00  /bin/ls
type+perms  links  user  group  size   mtime          name
```

Type letter: `-`=file, `d`=dir, `l`=symlink, `c`=char dev, `b`=block dev, `p`=fifo (named pipe), `s`=socket.

#### `cd`, `pwd`

`cd` is a shell builtin because it must change the working directory of the current shell; an external child process could not change its parent's directory. `pwd` reports that context. Logical mode preserves the path the user traversed (including symlink components), while physical mode resolves the kernel-visible directory path. This distinction matters when scripts compare paths or when `..` through a symlink is surprising.

```bash
cd                # home
cd ~              # home
cd -              # previous dir
cd ..             # parent
pwd               # logical path (may include symlinks)
pwd -P            # physical path (resolves symlinks)
```

#### `mkdir`, `rmdir`

`mkdir` creates directory entries; `-p` makes missing parents and makes an already-existing directory nonfatal, which is useful for repeatable setup. The requested mode is still filtered by the process umask unless adjusted afterward. `rmdir` intentionally removes only empty directories, so it is safer than recursive `rm` when emptiness is a required precondition.

```bash
mkdir -p a/b/c              # create parents
mkdir -m 700 secret         # specific perms at creation
rmdir empty                 # only succeeds if empty
```

#### `rm`, `cp`, `mv`, `touch`

These commands mutate directory entries and metadata. `rm` unlinks names (data survives while another hard link or open descriptor exists); `cp` creates a new destination object/data; `mv` renames atomically when source and destination are on the same filesystem but becomes copy-then-remove across filesystems; `touch` creates an empty file if absent or updates timestamps if present. Choose options according to the metadata contract—ordinary content copy, archival preservation, no-overwrite, or timestamp update are different intents.

```
rm [-rfiv] FILE...
cp [-arpviu] SRC... DST
mv [-fivn] SRC... DST
touch [-acmt] FILE...
```

Key `cp` flags: `-a` = archive (recursive, preserve perms/links/timestamps), `-r` = recursive, `-p` = preserve, `-u` = only newer, `-v` = verbose, `-i` = prompt. `-l` makes hard links, `-s` symlinks, `--reflink` (CoW on btrfs/xfs).

```bash
rm -rf /tmp/junk
rm -- -file             # delete a file literally named "-file"
cp -a src/ dst/         # mirror including dotfiles when src ends with /
cp -au src/ dst/        # only copy newer files (poor-man's rsync)
mv -n a b               # don't overwrite if b exists
mv -i *.log archive/    # confirm before overwrite
touch -t 202601011200 file        # set mtime to 2026-01-01 12:00
touch -d "yesterday" file
touch -a file                     # change atime only
touch -m file                     # change mtime only
```

**WARNING:** `rm -rf /` is catastrophic. Modern GNU coreutils refuses unless `--no-preserve-root`. Never run a command involving a variable like `rm -rf $DIR/` without confirming `$DIR` is non-empty.

#### `find` — search by criteria

`find` performs a live recursive walk starting at one or more paths, evaluates an expression for each entry, and optionally performs actions. Put narrowing tests before destructive actions for readability, quote glob patterns so the shell does not expand them early, and inspect with `-print` before replacing it with `-delete` or `-exec`. The overall expression is logic: implicit `-and` binds more tightly than `-or`, so use escaped parentheses for mixed conditions.

```
find [PATH...] [EXPRESSION]
```

Expression building blocks:

| Test | Description |
|---|---|
| `-name PATTERN` | Case-sensitive glob |
| `-iname PATTERN` | Case-insensitive |
| `-type f/d/l/b/c/p/s` | File type |
| `-size N[ckMG]` | Exactly N units; prefix `+`/`-` for greater/less |
| `-mtime N` | Modified N*24h ago; `+N` older than, `-N` newer than |
| `-mmin N` | Modified N minutes ago |
| `-atime`/`-amin`, `-ctime`/`-cmin` | Same for access / change |
| `-newer FILE` | Newer than FILE |
| `-user NAME` / `-group NAME` | Owned by |
| `-uid N` / `-gid N` | Numeric IDs |
| `-perm MODE` | Permission match (exact, `-MODE` all bits, `/MODE` any bits) |
| `-empty` | Empty file or dir |
| `-readable -writable -executable` | Effective ACL check |

Actions:

| Action | Description |
|---|---|
| `-print` | Default — print path |
| `-print0` | NUL-separated (safe for filenames with spaces) |
| `-ls` | ls-style |
| `-delete` | Delete found item |
| `-exec CMD {} \;` | Run once per match |
| `-exec CMD {} +` | Bulk: like xargs |
| `-ok CMD {} \;` | Like -exec but prompts |
| `-prune` | Don't descend |

Operators: `-and` (default), `-or`, `-not`, `( ... )` (must escape parens or quote).

```bash
find / -name '*.conf' 2>/dev/null
find /var/log -mtime +30 -type f -delete
find . -type f -size +100M
find /home -perm /u+s              # any SUID files
find /etc -newer /etc/passwd
find . -type f \( -name '*.log' -o -name '*.tmp' \) -delete
find . -type f -print0 | xargs -0 grep -l "needle"
find . -name node_modules -prune -o -type f -print
```

**TRAP:** `-mtime +7` means **strictly more than 7 days ago** (i.e., 8 days or older). `-mtime 7` means between 7 and 8 days. `-mtime -7` means less than 7 days (so newer).

#### `locate`, `updatedb`

`locate` uses a pre-built database (mlocate or plocate).

```bash
updatedb                     # rebuild the index (root)
locate sshd_config           # search index — instant
locate -i README             # case-insensitive
locate -c '*.conf'           # count matches
locate -r '\.conf$'          # regex
```

**TRAP:** `locate` may miss recently created files (stale DB) and may show deleted ones. Run `updatedb` first or use `find`.

#### `which`, `whereis`, `type`

```bash
which ls               # path of executable from PATH
which -a python        # all matches in PATH
whereis ls             # binary, source, manpages
type ls                # shell built-in / alias / function / file
type -a python         # all definitions
```

**TRAP:** `which` ignores shell builtins and aliases. `type` is more accurate inside bash because it queries the running shell.

#### `file`

Identifies file content by magic numbers, not extension.

```bash
file image.dat              # PNG image data, ...
file -b script.sh           # brief (no filename)
file -i script.sh           # MIME type
file -s /dev/sda1           # special files: don't follow, look inside
```

#### `stat`

```bash
stat file               # all metadata
stat -c '%s %n' *.log   # custom format: size and name
stat -c '%a %n' *       # octal perms and name
stat --printf='%Y\n' file   # mtime as epoch
```

Format specifiers: `%n` name, `%s` size, `%a` perm octal, `%A` perm symbolic, `%U` owner, `%G` group, `%i` inode, `%h` link count, `%X/%Y/%Z` atime/mtime/ctime epoch.

**Exercises**
- *Exercise 1:* Find all files in `/etc` modified in the last 5 minutes.
- *Exercise 2:* Delete all `*.bak` files under `/var` except those inside `/var/keep/`.

**Mock Exam Questions**

**Q1.** Which `find` expression matches files at least 200 MB in size?
- A) `-size 200M`  B) `-size +200M`  C) `-size -200M`  D) `-size >200M`

**A:** **B.** `+N` means greater than. `-size 200M` means exactly 200 MB (rounded up).

**Q2.** Which command prints the inode of `/etc/hostname`?
- A) `ls -i /etc/hostname`  B) `stat -c '%i' /etc/hostname`  C) Both A and B  D) `inode /etc/hostname`

**A:** **C.**

**Q3 (Scenario).** A user must locate a file but `locate myfile` returns nothing although they just created it. Explain.

**A:** `locate` reads a periodically refreshed database. The file was created after the last `updatedb`. Either run `updatedb` (root) or use `find`.

---

### 3.2 Text Processing — `cat`, `tac`, `head`, `tail`, `less`, `more`, `wc`

#### `cat`, `tac`

`cat` concatenates files in order and writes the bytes to stdout; with one file it is a simple way to feed a pipeline, not a general viewer for huge/binary files. `tac` reverses record order (normally lines). Neither edits the source. For interactive reading use `less`; for preserving binary bytes avoid options that number or decorate output.

```bash
cat file               # whole file to stdout
cat -n file            # number every line
cat -b file            # number nonblank lines
cat -A file            # show all (tabs as ^I, line ends as $, control chars as ^X)
cat > newfile <<EOF    # heredoc into file
hello
EOF
cat a b c > d          # concatenate
tac file               # reverse line order
```

**TRAP:** "Useless use of cat" (`cat file | grep x` vs `grep x file`) doesn't fail the exam but is ugly. Sometimes `cat` is used purely for argument order convenience.

#### `head`, `tail`

`head` selects the beginning of a stream and `tail` selects the end. They are useful for sampling a large file without loading it into an editor. `tail -f` follows a file descriptor while `tail -F` also retries by filename after log rotation, so `-F` is usually better for long-running log observation. Following output is observation, not proof that every event was persisted or processed.

```bash
head file                  # first 10 lines
head -n 25 file            # first 25
head -c 100 file           # first 100 bytes
tail file                  # last 10
tail -n 50 file
tail -n +5 file            # from line 5 to end
tail -f /var/log/syslog    # follow appends
tail -F file               # like -f but reopen if rotated
tail -f a -f b             # multiple files with headers
```

#### `less` and `more`

`less` is the modern pager. Inside `less`:

| Key | Action |
|---|---|
| Space / `f` | Forward one page |
| `b` | Back one page |
| `g` / `G` | Top / bottom |
| `/text` | Search forward |
| `?text` | Search backward |
| `n` / `N` | Next / previous match |
| `=` | Show file position |
| `&pattern` | Display only matching lines |
| `v` | Open in `$EDITOR` |
| `F` | Tail-follow like `tail -f` |
| `q` | Quit |

```bash
less +F /var/log/syslog            # start in follow mode
less -N file                       # show line numbers
less -S file                       # don't wrap; chop long lines
```

#### `wc`

`wc` counts stream properties. Lines are newline characters rather than visual records, so a final unterminated line affects `-l`; bytes (`-c`) and locale-aware characters (`-m`) differ for multibyte encodings. Use exit status and filenames carefully when aggregating multiple inputs because a total row is added.

```
wc [-clwLm] FILE...
```

| Flag | Counts |
|---|---|
| `-l` | Lines |
| `-w` | Words |
| `-c` | Bytes |
| `-m` | Characters (locale-aware) |
| `-L` | Length of longest line |

```bash
wc file               # lines words bytes
wc -l *.txt
find . -type f -print0 | xargs -0 wc -l
```

---

### 3.3 sort, uniq, cut, paste, join

#### `sort`

`sort` orders complete input lines according to keys, type and locale. It reads all required data (using temporary files for large inputs) and writes a new stream; it does not edit the source file unless redirected safely. Choose ordinary lexical order for text, `-n` for numbers, `-h` for displayed units, and `-V` for embedded version numbers. Set `LC_ALL=C` when scripts need deterministic byte-oriented ordering across machines.

```bash
sort file                  # alphabetical
sort -n file               # numeric
sort -r file               # reverse
sort -u file               # unique
sort -k 2 file             # by 2nd field (whitespace)
sort -t: -k 3 -n /etc/passwd      # by UID
sort -k 2.3,2.5 file       # by chars 3-5 of field 2
sort -h file               # human numeric (1K, 1M, 1G)
sort -V file               # version sort (file1, file2, file10)
sort -M file               # month names
```

**TRAP:** Without `-n`, `10` sorts before `2`. With `-n` it sorts after. With `-V` "file10" sorts after "file2".

#### `uniq`

`uniq` collapses or selects **adjacent** equal lines; it does not search the whole file for repeated values. Pair it with `sort` when order may change, or use an `awk` set when original order must be retained. Counts produced by `uniq -c` are commonly sorted numerically afterward to find the most frequent values.

```bash
sort file | uniq                # unique lines
sort file | uniq -c             # with count
sort file | uniq -d             # only duplicates
sort file | uniq -u             # only those without duplicates
sort file | uniq -i             # case-insensitive
```

#### `cut`

`cut` extracts fixed character/byte positions or delimiter-separated fields from every line. It does not understand quoted CSV, repeated semantic whitespace, or nested formats. Use it for simple stable records such as `/etc/passwd`; use `awk`, a CSV parser, JSON tooling, or the producing program's structured output when the format is richer.

```bash
cut -c 1-5 file                 # chars 1-5 of every line
cut -c 1,3,5 file               # specific chars
cut -d: -f 1,3 /etc/passwd      # delimiter ':', fields 1 and 3
cut -d: -f 1-3 /etc/passwd      # range
cut -d: --complement -f 2 file  # all fields except 2
```

#### `paste`

`paste` combines corresponding lines from input files into columns. It is useful for simple positional data where line 1 in each file belongs together; it is not a relational match. If one file ends early, empty fields are emitted. `-s` serializes each file's lines into one line.

```bash
paste a.txt b.txt               # tab-separated columns
paste -d, a.txt b.txt           # comma-separated
paste -s file                   # serial: file's lines on one line
paste -d: - - < file            # group every two lines
```

#### `join`

`join` performs a small relational equality join on a selected text field. Both inputs must be sorted using a compatible collation and the same join key, or matches can be lost/reported out of order. Use `-a` for unmatched rows and `-o` to control output; for quoted CSV or complex keys use a format-aware tool.

```bash
sort -k1 users.txt > u
sort -k1 emails.txt > e
join u e                         # join on field 1
join -1 2 -2 1 u e               # join u.field2 with e.field1
join -t: -1 1 -2 3 a b
join -a 1 a b                    # left outer join
```

---

### 3.4 tr, expand, unexpand, od, xxd

#### `tr` — translate or delete characters

`tr` transforms a stream character-by-character: it has no filename operand and therefore reads stdin and writes stdout. It is ideal for case conversion, deleting a known character, or squeezing runs; it cannot perform multi-character regular-expression substitutions. Locale affects character classes, so use `LC_ALL=C` when byte-level behavior is intended.

```bash
echo hello | tr a-z A-Z              # HELLO
echo "a-b-c" | tr '-' ' '            # a b c
tr -d '\r' < dos.txt > unix.txt      # strip CRs
tr -s ' ' < file                     # squeeze runs of spaces
tr -c '[:alnum:]\n' '_' < file       # replace non-alnum with _
```

POSIX classes: `[:alpha:]`, `[:digit:]`, `[:alnum:]`, `[:lower:]`, `[:upper:]`, `[:space:]`, `[:punct:]`, `[:cntrl:]`, `[:print:]`, `[:xdigit:]`.

#### `expand` / `unexpand`

These convert tab characters to equivalent spaces or suitable spaces back to tabs according to tab stops. They change representation, not visual intent in every font/editor. Use them when a downstream format or style policy requires consistent indentation; do not run `unexpand -a` blindly on data where interior spaces are significant.

```bash
expand file                # tabs → spaces (default tab=8)
expand -t 4 file
unexpand -a file           # spaces → tabs anywhere it fits
unexpand --first-only file # only leading spaces
```

#### `od` and `xxd` — view binary

`od` and `xxd` render bytes in human-readable numeric/character forms, which helps diagnose encoding, line endings, file signatures, and corruption invisible in a text editor. `xxd -r` reverses a compatible dump and therefore writes real binary data; verify offsets/content before using it as an editing mechanism.

```bash
od -c file               # character (escaped) view
od -A x -t x1z -v file   # hex offsets, hex bytes, ASCII
xxd file | head
xxd -b file              # binary view
xxd -r hexdump.txt > file # reverse: turn dump back into binary
```

---

### 3.5 grep (BRE, ERE, PCRE)

`grep` selects input lines that match a pattern and writes those lines (or requested metadata) to stdout. Use `-F` when the search term is literal, `-E` when alternation/grouping/repetition is needed, and default BRE when the objective specifically tests it. Exit status is part of the interface: `0` means at least one match, `1` means no match, and `2` (or greater in some implementations) indicates an error. Therefore “no match” is often a normal branch in scripts.

Recursive grep combines filesystem traversal with matching, but structured logs/data should be queried through their native tools when possible. Quote patterns so the shell does not expand `$`, `*`, brackets, or backslashes. `-q` is ideal for a condition because it suppresses output; `-l` answers which files matched rather than which lines.

```
grep [OPTIONS] PATTERN [FILE...]
```

| Flag | Meaning |
|---|---|
| `-i` | Case-insensitive |
| `-v` | Invert match |
| `-c` | Count only |
| `-l` | List files with matches |
| `-L` | List files without |
| `-n` | Line numbers |
| `-H` | Print filename |
| `-h` | Suppress filename |
| `-r` / `-R` | Recursive (R follows symlinks) |
| `-w` | Whole word |
| `-x` | Whole line |
| `-A N` | N lines after |
| `-B N` | N lines before |
| `-C N` | N lines both sides |
| `-E` | Extended regex (egrep) |
| `-F` | Fixed strings (fgrep) — fastest |
| `-P` | Perl-compatible regex |
| `-e PAT` | Multiple patterns |
| `-f FILE` | Patterns from file |
| `-o` | Print only the match |
| `-q` | Quiet (exit code only) |
| `--include='*.c'` | Only these names |
| `--exclude-dir=.git` | Skip dirs |

#### Basic Regular Expressions (BRE — default)

| Metachar | Meaning |
|---|---|
| `.` | Any single character |
| `*` | Zero or more of previous |
| `^` | Start of line |
| `$` | End of line |
| `[abc]` | Character class |
| `[^abc]` | Negated class |
| `[a-z]` | Range |
| `\<` `\>` | Word boundaries (GNU) |
| `\(...\)` | Group |
| `\{n,m\}` | Repetition |
| `\|` | Alternation (GNU BRE) |

#### Extended Regular Expressions (ERE — with `-E`)

In ERE the special characters `+`, `?`, `|`, `()`, `{}` are **active without backslashes**.

| Metachar (ERE) | Meaning |
|---|---|
| `+` | One or more |
| `?` | Zero or one |
| `|` | Alternation |
| `(...)` | Group |
| `{n,m}` | Repetition |

#### PCRE (with `-P`)

Adds: lookahead `(?=...)`, lookbehind `(?<=...)`, non-greedy `*?`, classes like `\d`, `\w`, `\s`, named groups.

```bash
grep -E '^(error|fail)' log.txt
grep -P '\d{3}-\d{4}' phones.txt
grep -rIn --include='*.py' 'TODO' src/
grep -A2 -B2 'ERROR' /var/log/syslog
grep -o '[0-9]\+\.[0-9]\+' file       # extract numbers
grep -v '^#' /etc/ssh/sshd_config | grep -v '^$'   # uncomment + non-blank
grep -lFr 'literal string' .
```

**TRAP:** `egrep` and `fgrep` are deprecated wrappers; prefer `grep -E` / `grep -F`.

**Exercises**
- *Exercise 1:* From `/var/log/auth.log`, list every distinct IP that attempted login failure today.
- *Exercise 2:* List only the *names* of files under `/etc` that contain the string `127.0.0.1`.

**Mock Exam Questions**

**Q1.** Which option to `grep` does NOT exist?
- A) `-E`  B) `-F`  C) `-P`  D) `-R`  E) `-S`

**A:** **E.** No `-S`.

**Q2.** In a BRE, which expression matches one or more digits?
- A) `[0-9]+`  B) `[0-9]\+`  C) `\d+`  D) `[:digit:]+`

**A:** **B.** In BRE you must backslash `+`. `\d` is PCRE. `[:digit:]` needs the `[[ ... ]]` form.

**Q3 (Scenario).** Why might `grep "/var/log" file` match lines you don't expect?

**A:** The forward slashes are literal but `.` is not — wait, `/var/log` has no metacharacters. Actually, the trap is that `grep "/var/log"` includes the slash. No traps — the real trap appears when the pattern contains `.` (e.g., `1.2.3.4` matches anything where `.` represents any char). Quote and use `-F`: `grep -F "1.2.3.4" file`.

---

### 3.6 sed — Stream Editor

`sed` applies a small editing program to each input line and normally prints the resulting pattern space. Without `-i`, it is a stream transformer and leaves input files untouched, which makes previewing and pipelines safe. With `-n`, default output is suppressed and commands such as `p` explicitly select output. With `-i`, it becomes a file mutation: create a backup, test the expression without `-i`, and remember GNU/BSD syntax differs.

Choose `sed` for line-oriented substitutions/deletions and simple stateful transformations; use `awk` when fields, arithmetic, aggregation, or richer logic dominate. A successful `sed` exit status does not prove the pattern matched—verify the changed content separately.

```
sed [OPTIONS] 'COMMANDS' [FILE...]
```

| Flag | Meaning |
|---|---|
| `-n` | Suppress default printing |
| `-e CMD` | Add a command (multi-cmd) |
| `-f FILE` | Script file |
| `-i[SUFFIX]` | Edit in place; with SUFFIX, create backup |
| `-r` / `-E` | Extended regex |
| `-s` | Treat each file separately |

#### Address forms

| Address | Meaning |
|---|---|
| `N` | Line N |
| `$` | Last line |
| `/REGEX/` | Lines matching REGEX |
| `N,M` | Range |
| `N,+K` | N and K following |
| `N~K` | Every K-th starting at N (GNU) |
| `addr1,addr2 !` | Negate |

#### Common commands

| Command | Action |
|---|---|
| `p` | Print |
| `d` | Delete |
| `s/RE/REP/FLAGS` | Substitute |
| `y/SRC/DST/` | Transliterate (like `tr`) |
| `a TEXT` | Append after |
| `i TEXT` | Insert before |
| `c TEXT` | Change |
| `q` | Quit |
| `=` | Print current line number |
| `n` / `N` | Next line into pattern space (append) |
| `b LABEL` | Branch |
| `t LABEL` | Branch if last `s` succeeded |
| `:LABEL` | Define label |
| `{cmds}` | Group |

#### Substitution flags

- `g` — global (all occurrences on the line)
- `N` — only Nth match
- `i` / `I` — case-insensitive (GNU)
- `p` — print if substitution made
- `w FILE` — write to FILE
- `e` — execute the result as shell (dangerous)

```bash
sed 's/foo/bar/' file               # first occurrence per line
sed 's/foo/bar/g' file              # all on each line
sed 's|/usr/bin|/usr/local/bin|g'   # alternate delimiter
sed -i.bak 's/old/new/g' file       # in-place with .bak backup
sed -n '5,10p' file                 # print lines 5-10
sed -n '/^ERROR/p' file
sed '/^#/d' /etc/ssh/sshd_config    # remove comments
sed '/^$/d' file                    # remove blank lines
sed '1d' file                       # delete first line
sed '$d' file                       # delete last line
sed '3a Inserted text' file         # append after line 3
sed '3i Inserted text' file         # insert before line 3
sed -e '1,5d' -e 's/abc/xyz/g' file
sed -n 'p;n' file                   # odd-numbered lines
sed -E 's/(.*)\s+(.*)/\2 \1/' file  # swap two columns
```

**TRAP:** `sed -i` without a backup suffix is fine on GNU sed but breaks on BSD/macOS (requires `sed -i ''`). Exam may test portability.

**Exercises**
- *Exercise 1:* Remove every comment line and every blank line from `/etc/ssh/sshd_config`.
- *Exercise 2:* Insert the line `# Managed by puppet` as line 1 of every `.conf` file in `/etc/`.

---

### 3.7 awk — Pattern-Action Language

`awk` reads records (normally lines), splits them into fields, evaluates pattern/action rules, and can aggregate state across the file. It is appropriate when the question is about columns, numeric calculations, counts, or reports rather than simple substring replacement. `BEGIN` initializes before input, ordinary rules run per record, and `END` emits final aggregates.

`-F` defines input splitting; `OFS` controls output separation. Avoid using the default whitespace field model for quoted CSV/JSON. Pass shell values with `-v` rather than constructing an awk program through unsafe string interpolation, and set locale deliberately for numeric/text comparisons in scripts.

```
awk [OPTIONS] 'PATTERN { ACTION } ...' [FILE...]
```

| Flag | Meaning |
|---|---|
| `-F SEP` | Input field separator |
| `-v VAR=VAL` | Pre-set a variable |
| `-f SCRIPT.awk` | Run from file |
| `-W posix` | POSIX strict |

#### Built-in variables

| Var | Meaning |
|---|---|
| `$0` | Whole record (line) |
| `$1, $2, ...` | Fields |
| `NF` | Number of fields |
| `NR` | Current record number |
| `FNR` | Record num in current file |
| `FILENAME` | Current file |
| `FS` | Input field separator |
| `OFS` | Output field separator |
| `RS` | Input record separator |
| `ORS` | Output record separator |

#### Special patterns

- `BEGIN { ... }` — run before any input
- `END { ... }` — run after all input
- `/regex/ { ... }` — for matching records
- `expr { ... }` — when expr is non-zero/non-empty

```bash
awk '{ print $1 }' file              # first column
awk -F: '{ print $1, $3 }' /etc/passwd
awk 'NR>1 && NR<6' file              # lines 2-5
awk '/error/ { print NR, $0 }' log
awk '{ sum += $1 } END { print sum }' nums
awk 'BEGIN{FS=":"; OFS="\t"} {print $1,$3}' /etc/passwd
awk 'length($0) > 80' file           # long lines
awk '!seen[$0]++' file               # remove dupes, preserve order
awk '{ for (i=NF; i>=1; i--) printf "%s ", $i; print "" }' file  # reverse columns
```

#### Built-in functions

- String: `length(s)`, `substr(s,i,n)`, `index(s,t)`, `split(s,a,sep)`, `sub(/re/,r,s)`, `gsub(/re/,r,s)`, `match(s,/re/)`, `sprintf(fmt,...)`, `tolower(s)`, `toupper(s)`
- Numeric: `int(x)`, `sqrt(x)`, `log(x)`, `exp(x)`, `rand()`, `srand(s)`
- I/O: `getline`, `printf`, `print > "file"`, `print | "cmd"`, `close()`, `system("cmd")`

```bash
awk '{ gsub(/  +/, " "); print }' file       # squeeze spaces
awk '{ printf "%-20s %5d\n", $1, $2 }' data
awk -v threshold=100 '$3 > threshold' file
```

**Exercises**
- *Exercise 1:* Print users whose UID ≥ 1000 from `/etc/passwd`.
- *Exercise 2:* Compute the average of the second column of a CSV.

**Mock Exam Questions**

**Q1.** Which awk variable holds the total number of fields on the current line?
- A) `$NF`  B) `NF`  C) `FS`  D) `NR`

**A:** **B.** `NF` is the count; `$NF` is the *value* of the last field.

**Q2.** Which awk invocation prints the user names from `/etc/passwd`?
- A) `awk '{print $1}' /etc/passwd`
- B) `awk -F: '{print $1}' /etc/passwd`
- C) `awk -d: '{print $1}' /etc/passwd`
- D) `awk '$FS=":";print $1' /etc/passwd`

**A:** **B.** Default separator is whitespace; `/etc/passwd` uses `:`.

**Q3 (Scenario).** Explain `awk '!seen[$0]++'`.

**A:** `seen[$0]++` increments the count of how many times this line has been seen and *returns the old value*. `!seen[$0]++` is true (prints the line) only the first time, deduplicating while preserving order — without needing `sort`.

---

### 3.8 diff, patch, comm

#### `diff`

`diff` compares two files or trees and describes how the first differs from the second. It is query-only: exit status `0` means identical, `1` means differences were found, and values greater than `1` mean an error. This is why `diff` returning `1` is useful information rather than a command failure in comparison scripts. Unified format is preferred for review and `patch` interoperability.

```bash
diff a.txt b.txt                # default normal diff
diff -u a.txt b.txt             # unified (most readable)
diff -c a.txt b.txt             # context
diff -y a.txt b.txt             # side-by-side
diff -r dir1 dir2               # recursive
diff -q dir1 dir2               # only report differences
diff -i a b                     # ignore case
diff -w a b                     # ignore whitespace
diff -B a b                     # ignore blank lines
diff --color=auto -u a b
```

Diff output legend:
- Normal: `5c5` means line 5 changed; `<` from first, `>` from second.
- Unified: `@@ -L,K +L,K @@` lines; `-` line removed, `+` added.

#### `patch`

`patch` applies a change description to a working tree. Unlike `diff`, it mutates files and may create backup/reject files. Always inspect the patch source, run `--dry-run`, confirm the path-stripping level, and apply inside version control or a restorable copy. A successful textual application does not prove the changed program builds or behaves correctly.

Applies a diff.

```bash
diff -u orig new > patch.diff
patch < patch.diff                  # apply patch to orig in current dir
patch -p1 < patch.diff              # strip 1 path component (typical for kernel patches)
patch -R < patch.diff               # reverse a patch
patch --dry-run < patch.diff
```

`-pN` controls how many leading directory components are stripped from each path.

#### `comm`

Compare **sorted** files line by line.

```bash
sort a > a.s; sort b > b.s
comm a.s b.s            # 3 columns: only-in-a, only-in-b, common
comm -1 a.s b.s         # suppress col 1
comm -12 a.s b.s        # common only (intersection)
comm -23 a.s b.s        # only in a (difference)
```

---

### 3.9 Archiving and Compression

#### `tar`

`tar` serializes a set of files and metadata into one archive stream; compression is an optional outer transformation. Use it when directory structure, symlinks, modes, and timestamps need to travel together. An archive is not automatically a backup: test listing and restoration, preserve ACLs/xattrs when required, record numeric ownership for disaster recovery, and inspect untrusted paths before extracting as root because absolute paths or `..` components can be dangerous.

```
tar [MODE] [OPTIONS] [-f ARCHIVE] [FILE...]
```

Modes (exactly one):

| Mode | Meaning |
|---|---|
| `-c` | Create |
| `-x` | Extract |
| `-t` | List |
| `-r` | Append (uncompressed only) |
| `-u` | Update (only newer) |
| `-A` | Concatenate archives |
| `-d` | Diff archive vs filesystem |

Common options:

| Flag | Meaning |
|---|---|
| `-f FILE` | Archive file (use `-` for stdin/stdout) |
| `-v` | Verbose |
| `-z` | gzip |
| `-j` | bzip2 |
| `-J` | xz |
| `--zstd` | zstd |
| `--xattrs` | Preserve xattrs |
| `--acls` | Preserve ACLs |
| `-p` | Preserve permissions |
| `--numeric-owner` | Use numeric UID/GID |
| `-C DIR` | Change directory before |
| `--exclude=PAT` | Skip matches |
| `--exclude-from=FILE` | Exclusions from file |
| `--strip-components=N` | Strip N leading dirs on extract |

```bash
tar -cvf bk.tar dir/
tar -czvf bk.tar.gz dir/
tar -cjvf bk.tar.bz2 dir/
tar -cJvf bk.tar.xz dir/
tar -tvf bk.tar.gz                 # list
tar -xzvf bk.tar.gz                # extract here
tar -xzvf bk.tar.gz -C /tmp        # extract elsewhere
tar -czvf - dir/ | ssh user@host 'cat > bk.tar.gz'   # stream
tar --exclude='*.log' -czvf bk.tar.gz dir/
tar --strip-components=1 -xzvf pkg-1.2.3.tar.gz -C /usr/src/pkg
```

**TRAP:** Older tar required no leading dash; modern GNU tar accepts both. But the order `tar f file ...` (old style) without dash is still tested.

#### `gzip`, `bzip2`, `xz`

These are single-stream compression formats, not multi-file archive formats. Compress a directory by archiving it with `tar` first. gzip usually favors speed/compatibility, xz favors compression ratio at greater CPU/memory cost, and bzip2 is common in older workflows. The ordinary commands replace the input unless `-k` is used; the `*cat` variants decompress to stdout for pipelines without creating an intermediate file.

```bash
gzip file                # creates file.gz, removes file
gzip -k file             # keep original
gzip -d file.gz          # decompress
gunzip file.gz           # same
gzip -9 file             # max compression
gzip -l file.gz          # list info

bzip2 -k file
bunzip2 file.bz2

xz file
unxz file.xz

zcat file.gz             # view without decompressing
bzcat file.bz2
xzcat file.xz
```

#### `zip` / `unzip`

ZIP combines archiving and per-entry compression and is widely interoperable with non-Unix systems. Traditional ZIP does not preserve every Unix metadata feature consistently, and `zip -e` uses legacy password-based encryption unsuitable for strong security requirements. List untrusted archives and extract into an isolated directory before moving reviewed files into place.

```bash
zip -r out.zip dir/
zip -e out.zip secret.txt           # encrypted (prompts for password)
unzip out.zip
unzip -l out.zip                    # list
unzip -d /tmp out.zip               # destination dir
unzip -p out.zip file.txt           # to stdout
```

#### `cpio`

`cpio` copies a list of pathnames into/out of an archive or between directory trees. Unlike `tar`, archive creation normally receives its file list on stdin, so it composes with `find`. It remains relevant to initramfs and legacy backup workflows. Use NUL-delimited modes where supported for arbitrary filenames and inspect archives before privileged extraction.

```bash
find . -name '*.c' -print | cpio -ov > src.cpio       # create
cpio -idv < src.cpio                                  # extract
cpio -itv < src.cpio                                  # list
```

Modes: `-o` (copy-out, create), `-i` (copy-in, extract), `-p` (pass-through). Flags: `d` create dirs as needed, `v` verbose, `m` preserve mtimes.

#### `dd`

`dd` copies byte blocks from one file/device stream to another without understanding partitions or filesystems. Use it for exact images, controlled regions, and device initialization—not for ordinary file copies where `cp`/`rsync` provide safer semantics. Input and output direction is easy to reverse, and success only proves bytes were copied, not that the source was consistent or the restored filesystem is healthy.

```bash
dd if=/dev/sda of=disk.img bs=4M status=progress
dd if=ubuntu.iso of=/dev/sdb bs=4M status=progress oflag=sync
dd if=/dev/zero of=/swapfile bs=1M count=2048
dd if=/dev/urandom of=/dev/sdb bs=1M count=10   # quick wipe of first 10MB
dd if=disk.img of=/dev/sda bs=4M conv=fsync
```

Operands: `if=` input, `of=` output, `bs=` block size, `count=` blocks, `skip=` input blocks to skip, `seek=` output blocks to skip, `conv=` conversions (`sync`, `notrunc`, `fsync`, `noerror`), `status=progress`.

**WARNING:** `of=/dev/sdX` overwrites a disk. Always `lsblk` first.

**Exercises**
- *Exercise 1:* Create a bz2-compressed tarball of `/etc/` that excludes `/etc/ssl/`.
- *Exercise 2:* Restore a single file from `bk.tar.gz` to `/tmp/` without extracting the whole archive.

**Mock Exam Questions**

**Q1.** Which `tar` flag uses xz compression?
- A) `-z`  B) `-j`  C) `-J`  D) `-Z`

**A:** **C.** `-z` gzip, `-j` bzip2, `-J` xz, `-Z` compress (legacy).

**Q2.** Which mode argument creates a new cpio archive?
- A) `-i`  B) `-o`  C) `-p`  D) `-t`

**A:** **B.**

**Q3 (Scenario).** A `tar.gz` extracts files at the wrong level; you want one fewer leading directory. Which flag?

**A:** `--strip-components=1`.

---

### 3.10 Streams, Pipes, Redirects

| Symbol | Effect |
|---|---|
| `>` | Redirect stdout (truncate) |
| `>>` | Redirect stdout (append) |
| `<` | Redirect stdin |
| `2>` | Redirect stderr |
| `2>>` | Append stderr |
| `&>` or `>&` | Redirect both stdout and stderr (bash) |
| `&>>` | Append both |
| `2>&1` | Send stderr to current stdout |
| `>&2` | Send stdout to current stderr |
| `1>&-` | Close fd 1 |
| `|` | Pipe stdout → next cmd's stdin |
| `\|&` | Pipe both stdout and stderr (bash 4+) |

The order matters:

```bash
cmd > file 2>&1        # both to file
cmd 2>&1 > file        # stdout to file, stderr to original stdout
```

```bash
ls /missing 2> err.log
ls /missing /etc &> all.log
cmd 2>/dev/null               # swallow stderr
cmd > /dev/null 2>&1          # swallow both
cmd 2>&1 | grep ERROR         # filter on both streams
```

#### `tee`

`tee` reads stdin and duplicates it to stdout and one or more files. Use it when a pipeline must continue while you also retain or display the same data. Shell redirection is established by the current shell before `sudo` runs, so `command | sudo tee /root-owned/file` is the correct pattern when the write itself requires privilege. By default it truncates; `-a` appends.

```bash
cmd | tee out.log
cmd | tee -a out.log               # append
cmd 2>&1 | tee out.log | grep ERROR
ls | sudo tee /etc/somefile        # write through sudo
```

#### `xargs`

`xargs` collects items from stdin and constructs one or more command invocations, staying under the system argument-length limit. It is useful when a program accepts path arguments but not stdin. Newlines and whitespace are unsafe delimiters for arbitrary filenames; pair `find -print0` with `xargs -0`, or prefer `find -exec ... {} +`. Parallel `-P` changes ordering and can make unsafe commands race, so use it only for independent work.

```bash
find . -name '*.log' | xargs rm                 # may break on spaces
find . -name '*.log' -print0 | xargs -0 rm      # safe
echo file1 file2 | xargs -n1 echo               # one arg per call
xargs -I {} echo "PATH: {}" < list.txt          # placeholder
ls | xargs -P 4 -I {} gzip {}                   # 4 parallel
xargs -t cmd                                    # echo command before running
xargs -p cmd                                    # prompt
```

#### Here-documents and Here-strings

```bash
cat <<EOF > /etc/motd
Welcome to $(hostname)
EOF

cat <<'EOF'                    # quoted — no expansion
$variable stays literal
EOF

cat <<-EOF                     # strip leading TABS only
	tabbed lines
	indented script
	EOF

grep root <<< "$line"          # here-string: $line becomes stdin
```

**TRAP:** Tab-stripping `<<-` strips tabs only, not spaces.

---

### 3.11 Hard Links vs Symbolic Links

Every file on a Linux filesystem is identified by an **inode**. A *hard link* is just another name (directory entry) pointing to the same inode. A *symlink* is a separate small file containing a path.

| | Hard link | Symlink |
|---|---|---|
| Across filesystems | No | Yes |
| To directories | No (except `.` and `..`) | Yes |
| Survives target deletion | Yes (link count > 0) | Becomes dangling |
| `ls -l` shows | Just the name | `name -> target` |
| Inode | Same as target | Different |
| Created with | `ln src dst` | `ln -s src dst` |

```bash
ln file linkname             # hard link
ln -s /etc/hosts ~/hosts.lnk # symbolic
ln -sf /new/path link        # force replace
readlink link                # just print target
readlink -f path             # canonical absolute path resolving all symlinks
realpath file
```

**Mock Q.** Which is true about hard links?
- A) They can cross filesystems
- B) They can target directories (for regular users)
- C) They share an inode with the target
- D) `rm` of the original makes the link dangling

**A:** **C.**

---

### 3.12 Process Management

#### `ps`

`ps` takes a snapshot of processes visible to the caller. It does not continuously monitor, and the process may change or exit immediately after the snapshot. Use explicit `-o` columns in scripts and diagnosis. Two historical option styles coexist—BSD (no dash, like `aux`) and UNIX (dash, like `-ef`)—and mixing styles can change selection/default columns.

```bash
ps                          # processes in current shell
ps aux                      # BSD: all users, with TTY-less, user-oriented
ps -ef                      # UNIX: full format, all
ps -eLf                     # threads too
ps -fU root                 # by user
ps -p 1                     # by PID
ps --forest                 # tree
ps -o pid,user,%cpu,%mem,comm
ps -eo pid,ppid,cmd,stat
```

`STAT` flags: `R` running, `S` interruptible sleep, `D` uninterruptible sleep, `T` stopped, `Z` zombie, plus modifiers `<` high prio, `N` low prio, `s` session leader, `+` foreground group, `l` multi-threaded.

#### `top`, `htop`, `pstree`

`top`/`htop` repeatedly sample process and system counters to find current CPU/memory pressure; `pstree` shows ancestry rather than resource consumption. A high instantaneous percentage is not automatically a fault—observe duration, load, I/O wait, memory/swap and workload expectations. Batch mode makes one or more `top` snapshots usable in evidence collection.

```bash
top                  # interactive: q quit, M sort by mem, P sort by cpu, k kill, r renice, 1 per-CPU
top -b -n 1          # batch mode (scripting)
htop                 # friendlier
pstree -p            # tree with PIDs
pstree -aps 1234     # ancestor chain for PID 1234
```

#### Killing processes

`kill` sends a signal to a PID; it does not inherently “kill.” Signals request actions such as terminate, reload, stop, continue, or dump core. Use `pgrep` to verify selection, send `SIGTERM` for orderly cleanup, wait and inspect logs/state, and reserve `SIGKILL` for a process that cannot respond. Name/pattern tools can match more processes than intended, especially with `-f`.

```
kill [-SIG] PID
killall [-SIG] NAME
pkill [-SIG] PATTERN
pgrep PATTERN
```

Important signals (you must memorize numbers):

| # | Name | Meaning | Catchable? |
|---|---|---|---|
| 1 | HUP | Hangup; many daemons re-read config | yes |
| 2 | INT | Ctrl+C | yes |
| 3 | QUIT | Ctrl+\, dumps core | yes |
| 9 | KILL | Forced kill | **no** |
| 15 | TERM | Polite termination (default) | yes |
| 17/19/23 | STOP | Pause (uncatchable, OS-dependent #) | no |
| 18 | CONT | Continue paused | yes |
| 19 | STOP (x86) | — | no |

```bash
kill 1234                # default SIGTERM
kill -9 1234             # SIGKILL
kill -HUP $(pidof sshd)
killall -9 firefox
pkill -f 'python myscript.py'
pgrep -u www-data -lf
```

**TRAP:** `kill -9` does not let a process clean up. Use `SIGTERM` first.

#### Priorities — `nice`, `renice`

Niceness biases the CPU scheduler among competing runnable tasks; it is not a CPU limit and cannot solve disk or memory contention. Linux nice values range −20 (more favorable CPU priority) to +19 (less favorable). Default is 0. Ordinary users can normally make their own work less favorable but require privilege to increase scheduling priority. Verify the result with `ps` and measure whether CPU contention actually exists.

```bash
nice -n 10 long_job          # start at niceness 10
nice -n -5 ./fast            # only root can use negative
renice -n 5 -p 1234          # change running process
renice -n 5 -u alice         # all of user alice's
ps -eo pid,ni,comm           # see niceness column
```

#### Background, foreground, jobs

Job control is maintained by an interactive shell and refers to pipelines started from that shell, not every process on the host. `&`, `fg`, `bg`, and `%job` manipulate shell jobs; `Ctrl+Z` sends a terminal stop signal. `nohup` changes hangup handling and redirection, while `disown` changes the shell's job table/HUP behavior—neither turns a program into a supervised service. Use systemd or another supervisor for persistent production work.

```bash
long_cmd &              # background
jobs                    # current shell's background/stopped
jobs -l                 # with PIDs
fg %1                   # bring job 1 to foreground
bg %1                   # resume in background
kill %1                 # kill job 1
Ctrl+Z                  # stop current foreground job
disown %1               # detach from shell (no SIGHUP at exit)
nohup cmd &             # immune to HUP, stdout to nohup.out
wait $!                 # wait for last bg pid
wait                    # wait for all
```

#### `/proc/<pid>/`

| File | Content |
|---|---|
| `cmdline` | argv NUL-separated |
| `comm` | Short name |
| `exe` | Symlink to executable |
| `cwd` | Symlink to working dir |
| `environ` | Env vars NUL-separated |
| `fd/` | Open file descriptors |
| `status`, `stat` | Detailed state |
| `maps` | Memory regions |
| `limits` | rlimits |

```bash
cat /proc/1234/cmdline | tr '\0' ' '
ls -l /proc/1234/cwd
ls -l /proc/1234/fd
```

---

### 3.13 Disk and Filesystem

#### `df`

`df` means **disk free**. It asks each mounted filesystem for its allocation counters and reports how much filesystem space is available. Use it when the question is “which mounted filesystem is full?” rather than “which directory contains the data?” Its unit of accounting is the filesystem, so every path on the same filesystem normally produces the same row.

The important columns are `Size`, `Used`, `Avail`, `Use%`, and `Mounted on`. `Avail` may be smaller than `Size - Used` because ext filesystems can reserve blocks for root and because filesystem metadata consumes space. A filesystem can fail writes either because data blocks are exhausted (`df -h`) or because all inodes are used (`df -i`), even when the other resource remains available.

```bash
df                              # report allocation for all mounted filesystems
df -h                           # scale block values as KiB/MiB/GiB for human reading
df -i                           # report inode counts instead of data-block capacity
df -T                           # include filesystem type, useful before choosing FS-specific tools
df --total                      # add an aggregate row; useful for a quick capacity overview
df -h /var                      # identify and report the filesystem that contains /var
df --exclude-type=tmpfs -h      # hide memory-backed tmpfs entries from a storage report
```

**How to choose:** use `df -h` for ordinary capacity incidents; add `-T` when behavior depends on ext4/XFS/Btrfs/NFS; use `df -i` when applications report “No space left on device” although block usage is low. `df` cannot identify the large directory—follow it with `du` or filesystem-specific tooling.

**Common diagnostic mismatch:** after deleting a large log, `du` may no longer see it while `df` still shows its blocks in use. A running process can retain an open file descriptor to an unlinked file. Find such files with `lsof +L1`, verify the owning service, then rotate/reload/restart it safely; do not reboot blindly.

#### `du`

`du` means **disk usage**. It walks directory entries, calls filesystem metadata operations, and totals blocks attributed to the files it can reach. Use it to answer “where inside this tree is space being consumed?” Unlike `df`, it can be slow and I/O-intensive on a large tree and its result is limited by permissions and by files visible in the namespace.

By default `du` reports allocated blocks, so sparse files can appear smaller than their logical length. `--apparent-size` instead totals logical file lengths. Hard-linked data is normally counted once during one traversal; snapshots, reflinks, compression, filesystem metadata, deleted-open files, and reserved blocks can make `du` and `df` legitimately disagree.

```bash
du -sh /var                     # one human-readable total for the complete /var tree
du -h --max-depth=1 /var        # totals for immediate children: locate the largest branch
du -ch /var/log/*.log           # show each matching log and a final grand total
du -xhd1 /                      # inspect root's first level without entering other filesystems
du -sh --apparent-size FILE     # report logical length rather than allocated disk blocks
du -ahx /var | sort -h | tail   # rank reachable files/directories by allocated size
```

`-s` suppresses per-child output and prints only a summary; `-h` changes display units; `-x` keeps the scan on one filesystem, which avoids traversing `/proc`, NFS, separate home volumes, and bind-mounted trees. `sort -h` is a separate command: it understands human units, so `900M` is ordered before `2G`. For automation, prefer stable byte units such as `du -B1` rather than parsing localized human output.

#### `mount`, `umount`

A filesystem is not accessed merely because its block device exists. `mount` attaches a filesystem's root to a directory in the current **mount namespace**, making its tree reachable through that mount point. It changes runtime kernel state; without an `/etc/fstab` entry or a generated systemd mount unit, the attachment normally disappears at reboot.

Before mounting, identify the device and filesystem with `lsblk -f`/`blkid`, create an empty mount point, and check whether it is already mounted with `findmnt`. Mounting over a non-empty directory temporarily hides the directory's original contents until unmount; it does not delete them.

```bash
mount                                   # compatibility listing; prefer findmnt for clear output
mount /dev/sdb1 /mnt                    # attach the detected filesystem at /mnt
mount -t ext4 -o defaults,noatime /dev/sdb1 /mnt
                                         # require ext4 and suppress ordinary access-time updates
mount -o remount,rw /                   # change options on an existing root mount to read-write
mount -o remount,ro /                   # request read-only mode, often before repair/recovery
mount -o loop,ro ubuntu.iso /mnt/iso    # expose an image through a loop device without modifying it
mount --bind /src /dst                  # expose the same existing subtree at a second path
mount -a                                # apply eligible fstab entries; used to test fstab before reboot
umount /mnt                             # detach cleanly after all users release the mount
umount -l /mnt                          # detach namespace now; clean references later (last resort)
umount -f /mnt                          # force selected network filesystems such as unreachable NFS
```

`-t` declares/limits the filesystem type; modern `mount` can usually detect it, but explicit type helps reject a wrong assumption. `-o` supplies comma-separated policy. `defaults` is a conventional baseline (`rw,suid,dev,exec,auto,nouser,async`), not a universal security recommendation. `noatime` reduces metadata writes; `ro` blocks ordinary writes; `nosuid`, `nodev`, and `noexec` reduce particular attack surfaces but do not form a complete sandbox.

Normal `umount` fails with “target is busy” to protect active working directories, open files, mapped executables, and nested mounts. Diagnose first:

```bash
findmnt -R /mnt                 # see the mount and any child mounts
fuser -vm /mnt                 # processes using paths on the filesystem
lsof +f -- /mnt                # open files where supported; may be expensive
```

Leave the directory in every shell, stop or reconfigure the relevant process, unmount children, then retry. Lazy unmount is useful for a broken namespace or unreachable service but can hide continued resource use. Forced unmount is mainly a network-filesystem recovery tool and can lose pending work; it is not the normal solution to a busy local disk.

#### `/etc/fstab`

`/etc/fstab` is the administrator's persistent declaration of filesystems, swap areas, and their intended mount points/options. At boot, generators and mount tooling translate these declarations into runtime mounts. `mount DEVICE_OR_POINT` can also look up the missing arguments here. Because an invalid root or required-data entry can disrupt boot, edit carefully and validate before rebooting.

Each non-comment entry has six whitespace-separated fields:

```
<device>  <mountpoint>  <type>  <options>  <dump>  <fsck-pass>
```

- **Device/source:** `/dev/...`, `UUID=...`, `LABEL=...`, `PARTUUID=...`, a pseudo-filesystem name, or a remote source such as `host:/path`. Prefer UUID/PARTUUID for disks because `/dev/sdX` names can change with discovery order. Labels are readable but must be kept unique.
- **Mount point:** directory where the tree appears. Use `none` for swap. Spaces and some special characters require fstab escaping such as `\040`; shell quoting is not the fstab grammar.
- **Type:** `ext4`, `xfs`, `vfat`, `swap`, `nfs`, `cifs`, `auto`, and so on. It determines the helper and valid options.
- **Options:** comma-separated mount and policy settings. `auto`/`noauto` controls automatic mounting; `user` permits one ordinary user to mount and that user to unmount, whereas `users` permits any user to unmount; `_netdev` tells boot logic that network availability is required. `discard` issues ongoing discard where supported, but periodic `fstrim` is often preferred to reduce continuous overhead.
- **Dump:** historical `dump(8)` selection flag, normally `0` on modern systems.
- **fsck pass:** `1` for the root filesystem, `2` for other boot-checked local filesystems, and `0` to skip. Filesystem support matters: XFS repair is not orchestrated like ext `fsck`.

Example:
```
UUID=abcd... /          ext4   defaults,noatime,errors=remount-ro  0 1
UUID=efgh... /home      ext4   defaults                            0 2
LABEL=swap   none       swap   sw                                  0 0
tmpfs        /tmp       tmpfs  defaults,nosuid,nodev,size=2G       0 0
```

Interpretation: the root entry is checked first and can remount read-only after ext4 errors; `/home` is checked after root; swap is activated rather than mounted; tmpfs stores `/tmp` in memory/swap with a 2 GiB ceiling and disables device/SUID interpretation.

Validate changes without waiting for a reboot:

```bash
findmnt --verify --verbose       # parse fstab and report semantic inconsistencies
mount -av                       # attempt all eligible entries and show what happens
findmnt --fstab                 # display the declared configuration
systemctl daemon-reload         # refresh generated mount units after fstab edits on systemd
```

Keep an existing root/console session open while testing remote or authentication-dependent mounts. `nofail` lets boot continue if a nonessential mount fails; use it only when that operational behavior is intended.

#### `findmnt`, `lsblk`, `blkid`

These tools answer different layers of the same storage question:

- `lsblk` shows the **block-device topology** obtained mainly from sysfs/udev: disks, partitions, device-mapper layers and their relationships.
- `blkid` probes or reads cached **on-device signatures** such as filesystem type, UUID and label.
- `findmnt` shows the **currently mounted namespace** and can compare it with fstab declarations.

Use all three during diagnosis: `lsblk` finds the device and layering, `blkid` confirms the identity stored on it, and `findmnt` proves where and with which options it is actually attached.

```bash
findmnt                          # tree of runtime mounts and their parent relationships
findmnt --target /home           # filesystem containing /home, even if /home is not a mount point
findmnt --mountpoint /home       # succeed only if /home itself is a mount point
findmnt -t ext4 -o SOURCE,TARGET,OPTIONS
lsblk -f                         # topology plus filesystem label, UUID and mount points
lsblk -o NAME,TYPE,SIZE,FSTYPE,LABEL,UUID,MOUNTPOINTS
blkid /dev/sda1                  # probe one device's persistent signatures
blkid -L mylabel                 # resolve a filesystem label to a device
blkid -U UUID                    # resolve an exact UUID to a device
```

`lsblk` output is not a guarantee that a device is safe to format: mounted children, swap, RAID, LVM, multipath, containers, or another namespace may use it. Combine `lsblk`, `findmnt`, `swapon --show`, `pvs`, `mdadm`, and process/container context before destructive work. In scripts, request explicit columns and machine formats (`--json`, `--pairs`, or `--raw`) because default columns can change.

#### fsck family

`fsck` is a front end that selects a filesystem-specific checker (`fsck.ext4`/`e2fsck`, etc.). It verifies and, when requested, repairs **filesystem metadata consistency**; it does not test the physical health of a disk and it is not a file-recovery or backup tool. Use SMART/NVMe health tools for hardware evidence and restore from backup when data is lost.

```bash
fsck /dev/sdb1                  # inspect signature/type and invoke the appropriate checker
fsck -n /dev/sdb1               # make no repairs; useful for an initial evidence-gathering pass
fsck -y /dev/sdb1               # approve every proposed repair; risky without review/backup
fsck -A                         # check eligible fstab filesystems according to configuration
fsck -t ext4 /dev/sdb1 -- -f    # select the device/type; pass -f to its checker
e2fsck -p /dev/sdb1             # automatically apply only repairs considered safe by e2fsck
e2fsck -f /dev/sdb1             # force a complete ext-family check even when marked clean
dumpe2fs -h /dev/sda1           # show ext superblock summary without dumping every block group
tune2fs -l /dev/sda1            # list ext filesystem parameters; query-only with -l
```

The `--` in the front-end example ends `fsck`'s options; following arguments go to the filesystem-specific checker. Do not assume every filesystem uses the same checker: XFS normally uses `xfs_repair` while unmounted, Btrfs has its own check/scrub/recovery distinctions, and a simple `fsck` may intentionally do little for some journaled/network filesystems.

**Safe repair workflow:** identify the exact device and filesystem; capture backups/SMART evidence if failure is suspected; stop writers and unmount it (or boot rescue media for root); run a no-change or preen pass; read the proposed damage; repair with the appropriate filesystem tool; mount read-only first if risk is high; inspect logs/data; then restore service. A read-only remount is safer than writable but an offline check is the normal rule because the live kernel can still hold changing state.

**WARNING:** Never run a repairing `fsck` on a mounted, writable filesystem—concurrent kernel and checker changes can create corruption. Never copy `/dev/sdX` examples literally; confirm identity through persistent attributes and topology first.

---

### 3.14 Permissions

The classical Linux permission model uses three triplets (user, group, other) of `r`, `w`, `x` bits, plus three "special" bits: **SUID**, **SGID**, **Sticky**.

#### Numeric mode

| Bit | Value | r=4, w=2, x=1 |
|---|---|---|
| Special | SUID=4, SGID=2, Sticky=1 | |
| Owner | rwx → 7 |
| Group | rwx → 7 |
| Other | rwx → 7 |

So `chmod 4755 file` = SUID + rwxr-xr-x.

#### Symbolic mode

```
chmod [ugoa][+-=][rwxXst] FILE
```

- `u` user, `g` group, `o` other, `a` all
- `+` add, `-` remove, `=` set exactly
- `X` execute if it's a directory OR already executable by anyone
- `s` SUID/SGID, `t` sticky

```bash
chmod 644 file
chmod u+x,g-w,o= file
chmod -R u+rwX,go-w dir/
chmod a+t /tmp                 # sticky on /tmp
chmod g+s /shared              # SGID dir: new files inherit group
chmod u+s /usr/bin/program     # SUID
```

#### SUID

When set on an executable file, the process runs with the file owner's UID. Used carefully for things like `/usr/bin/passwd`.

```bash
ls -l /usr/bin/passwd
# -rwsr-xr-x  1 root root ...  (the s in user-x slot indicates SUID)
```

#### SGID

On a file: runs with group of the file. On a directory: new entries inherit the directory's group, and subdirs themselves inherit SGID. Useful for shared project directories.

#### Sticky bit

On directories only: only the file's owner (or root) can delete entries, even if others can write. The canonical example is `/tmp` (drwxrwxrwt).

Display markers:
- `s` lowercase = SUID/SGID AND executable
- `S` uppercase = SUID/SGID without executable (unusual)
- `t` lowercase = sticky AND world-executable
- `T` uppercase = sticky without world-executable

#### `chown` / `chgrp`

```bash
chown alice file
chown alice:devs file
chown -R alice:devs dir/
chown --reference=otherfile file
chgrp devs file
chown -h alice symlink         # change link itself, not target
```

#### `umask`

Subtractive permission mask applied when files are created. Default for users is `0022` → files get `0644`, dirs `0755`. Files never get `x` from umask by default (max is `0666`).

```bash
umask                # show
umask 0027           # restrict group/other on creation
umask -S             # symbolic form: u=rwx,g=rx,o=
```

Persistent: set in `~/.bashrc` or `/etc/profile`.

#### ACLs — `getfacl`, `setfacl`

Extended permission lists when classical mode bits are insufficient.

```bash
getfacl file
setfacl -m u:alice:rwx file
setfacl -m g:devs:rx file
setfacl -x u:alice file               # remove specific entry
setfacl -b file                       # remove all ACLs
setfacl -m d:u:alice:rwx dir/         # default ACL: new entries inherit
setfacl -R -m u:alice:rX dir/
```

Filesystem must be mounted with `acl` option (often default on ext4).

`ls -l` shows `+` after the mode to indicate ACL present.

#### File attributes — `chattr`, `lsattr`

| Attr | Meaning |
|---|---|
| `a` | Append only |
| `i` | Immutable |
| `s` | Secure delete (zeroes on rm) |
| `S` | Synchronous writes |
| `A` | Don't update atime |
| `c` | Compressed (btrfs/ext4 fs-specific) |
| `j` | Data journaling |

```bash
chattr +i /etc/resolv.conf       # nothing can modify or delete it
lsattr /etc/resolv.conf
chattr -i /etc/resolv.conf
chattr +a /var/log/audit.log     # only appends allowed
```

**TRAP:** Even root cannot modify a `+i` file until `chattr -i` is done.

**Exercises**
- *Exercise 1:* Create `/shared/project` such that files placed there are group-owned by `devs` and group-readable by default.
- *Exercise 2:* Make `/etc/important.conf` immutable so package upgrades can't overwrite it (then undo).

**Mock Exam Questions**

**Q1.** What does mode `2755` on a directory mean?
- A) SUID + rwxr-xr-x
- B) SGID + rwxr-xr-x
- C) Sticky + rwxr-xr-x
- D) Just rwxr-xr-x

**A:** **B.** Leading `2` is SGID.

**Q2.** A file shows perms `rwSr--r--`. What is unusual about this?
- A) SUID is set but the owner cannot execute
- B) Sticky bit is set
- C) ACL is present
- D) The group has SGID

**A:** **A.** Uppercase `S` means SUID without execute, which is almost always a misconfiguration.

**Q3 (Scenario).** A directory has mode `rwxrwxrwt`. Why?

**A:** The `t` is the sticky bit. With world-write, sticky prevents users from deleting each other's files. Hallmark of `/tmp`.

**Q4.** With umask `0027`, what are the resulting permissions on a newly created regular file?
- A) `0750`  B) `0640`  C) `0600`  D) `0644`

**A:** **B.** Max file permissions are `0666` (no exec). `0666 - 0027 = 0640`.

---

### 3.15 Shell Built-ins & Features

#### `echo`, `printf`

Both write text, but `printf` has a defined format language and consistent behavior across shells, making it the preferred tool for scripts and structured output. Treat the format string as trusted code: pass untrusted values through `%s` rather than using them as the format. `echo` is convenient interactively, but handling of `-n`, `-e`, and backslashes varies.

```bash
echo hello                     # newline added
echo -n hello                  # no newline
echo -e 'a\tb\nc'              # interpret \t \n
printf '%s\n' a b c            # safer than echo, format string
printf '%-10s %5d\n' Alice 42
printf '%(%F %T)T\n' -1        # current date — bash builtin
```

**TRAP:** `echo`'s `-e` interpretation is non-portable. POSIX-pure scripts should use `printf`.

#### `read`

`read` consumes one logical line from stdin into shell variables, so it is the normal building block for interactive prompts and file loops. Use `-r` unless backslash escaping is intentionally part of the input language; quote the receiving variable later; and remember that a pipeline may run a loop in a subshell, losing variable changes in the parent shell.

```bash
read name                              # read one line into $name
read -p "Name: " name                  # with prompt
read -s pw                             # silent (for passwords)
read -r line                           # don't interpret backslashes (recommended)
read -t 5 -p "Hurry: " x               # 5-second timeout
read -n 1 ans                          # read 1 char
read -a arr <<< "one two three"        # read into array
while read -r line; do echo "$line"; done < file
```

#### `test`, `[`, `[[`

These commands convert a condition into an exit status, which `if`, `&&`, and `||` consume. `test` is a builtin; `[` is its synonym (note the required space) and **must end with `]`**. `[[ ... ]]` is the safer Bash-extended syntax with pattern matching, regex, and lazy logical operators, but it is not POSIX `sh`. Quote expansions in `[`; understand when the right side of `[[ == ]]` is a glob and `[[ =~ ]]` is a regex.

| Operator | Meaning |
|---|---|
| `-e PATH` | Exists |
| `-f PATH` | Regular file |
| `-d PATH` | Directory |
| `-L PATH` | Symlink |
| `-r/-w/-x PATH` | Readable/writable/executable by effective user |
| `-s PATH` | Non-empty |
| `-z STR` | Empty string |
| `-n STR` | Non-empty string |
| `STR1 = STR2` | Equal (use `==` only inside `[[ ]]`) |
| `STR1 != STR2` | Not equal |
| `N1 -eq N2` | Numeric equal (-ne, -lt, -le, -gt, -ge) |
| `cond1 -a cond2` (test) | AND |
| `[[ a && b ]]` | AND inside `[[ ]]` |
| `=~` | Regex (only `[[ ]]`) |

```bash
[ -f /etc/passwd ] && echo exists
[[ "$x" =~ ^[0-9]+$ ]] && echo numeric
[[ -d $1 && -w $1 ]] || { echo "bad dir"; exit 1; }
```

#### Command substitution

Command substitution runs a command and replaces the expression with its stdout after removing trailing newlines. It does not capture stderr or the exit status automatically, and unquoted results undergo word splitting/globbing. Store the status immediately when failure matters and quote the expansion (`"$(command)"`) unless splitting is explicitly intended.

```bash
date=$(date +%F)
files=`ls`        # backticks: legacy, avoid nesting
echo "today is $(date)"
```

#### Arithmetic

Shell arithmetic evaluates integer expressions. In Bash, `(( expression ))` also returns success when the numeric result is nonzero, which makes `((i++))` surprising under `set -e` when the old value is zero. It is not floating-point arithmetic and values derived from untrusted text need validation before evaluation.

```bash
echo $((1 + 2 * 3))
i=$((i + 1))
let "i = i + 1"
((i++))                       # bash; non-zero result -> exit 0, else 1 (!)
expr 1 + 2                    # spaces required
expr 5 \* 4                   # escape *
```

#### Brace expansion, globbing, wildcards

| Pattern | Matches |
|---|---|
| `*` | Any chars (not leading `.` by default) |
| `?` | One char |
| `[abc]` | One of a, b, c |
| `[!abc]` or `[^abc]` | Anything else |
| `{1..5}` | Brace expansion: 1 2 3 4 5 |
| `{a,b,c}` | a b c |
| `{a..z}` | a b ... z |
| `**` | Recursive (requires `shopt -s globstar`) |

```bash
echo file{1..3}.txt           # file1.txt file2.txt file3.txt
mkdir -p project/{src,bin,doc}/{old,new}
cp file{,.bak}                # cp file file.bak
ls *.{jpg,png,gif}
shopt -s extglob              # extended patterns
ls !(*.log)                   # everything except *.log
ls +(*.c|*.h)                 # one or more of these
```

**TRAP:** Brace expansion happens **before** any other expansion. Quoting it disables it: `echo "{1..3}"` prints literally `{1..3}`.

**Exercises**
- *Exercise 1:* Create `~/backup/2026-{01..12}/` in one command.
- *Exercise 2:* Test whether a path is a writable directory in a single `[[ ]]` expression.

**Mock Exam Questions**

**Q1.** Which form supports `=~` for regex matching?
- A) `[ ... ]`  B) `[[ ... ]]`  C) `test ...`  D) `(( ... ))`

**A:** **B.** Only the bash-extended `[[ ]]` supports `=~`.

**Q2.** `echo {a,b}{1,2}` outputs:
- A) `a1 a2 b1 b2`
- B) `a,b1,2`
- C) `ab12`
- D) `{a,b}{1,2}`

**A:** **A.** Cartesian product.

**Q3 (Scenario).** Why does `[ "$x" = "" ]` sometimes print an error even though `x` is unset?

**A:** With set -u, accessing $x errors. Without quotes (`[ $x = "" ]`), if x is empty the test becomes `[ = "" ]` — a syntax error. Always quote variables in `[ ]`, or use `[[ ]]`.

---

## Chapter 4: Devices, Filesystems & FHS

### 4.1 `/dev`: block, character, and special files

`/dev` is populated by **devtmpfs** (kernel) plus **udev** (userspace) rules. Two device categories:

- **Block devices** — random-access, buffered (disks, SSDs). `ls -l` shows leading `b`.
- **Character devices** — byte stream (terminals, serial, audio). Leading `c`.

Each device has a **major** and **minor** number:
- *Major*: which driver to dispatch to.
- *Minor*: which specific device inside that driver.

```bash
ls -l /dev/sda /dev/tty1
# brw-rw---- 1 root disk    8,  0 ...  /dev/sda
# crw-rw---- 1 root tty     4,  1 ...  /dev/tty1
cat /proc/devices            # list of registered majors
```

#### `mknod`

Creates a device file with explicit major/minor.

```bash
mknod /dev/mydisk b 8 16
mknod /dev/myttybackup c 4 1
mknod /tmp/p p              # named pipe (FIFO)
```

Modern systems rarely need this — udev creates nodes automatically.

#### Important `/dev` entries

| Path | Use |
|---|---|
| `/dev/null` | Discard sink, read returns EOF |
| `/dev/zero` | Endless zero bytes |
| `/dev/random`, `/dev/urandom` | Random bytes |
| `/dev/tty`, `/dev/console` | Controlling terminal |
| `/dev/ttyN` | Virtual consoles |
| `/dev/pts/N` | Pseudoterminals (ssh, terminal emulators) |
| `/dev/stdin`, `/dev/stdout`, `/dev/stderr` | Symlinks to fd 0/1/2 |
| `/dev/fd/N` | Symlink to fd N |
| `/dev/sda`, `/dev/sdaN` | SCSI/SATA/USB disks/partitions |
| `/dev/nvme0n1`, `/dev/nvme0n1pN` | NVMe |
| `/dev/loopN` | Loopback devices |
| `/dev/mapper/*` | DM/LVM/LUKS mapped devices |
| `/dev/mem`, `/dev/kmem` | Physical/kernel memory |

### 4.2 udev — Dynamic Device Management

udev (now part of systemd) watches the kernel's uevent socket. It applies rules to create symlinks, set permissions, and run programs when devices appear/disappear.

#### Rule files

- `/lib/udev/rules.d/` — distribution defaults
- `/etc/udev/rules.d/` — administrator overrides (higher precedence by name)
- `/run/udev/rules.d/` — runtime

Files are named `NN-name.rules` (e.g., `99-mycam.rules`); lower number = applied earlier.

#### Rule format

A rule is one line of `KEY=="VALUE", KEY=="VALUE", KEY="VALUE"`.

- `==` — match
- `!=` — non-match
- `=` — set
- `+=` — append
- `:=` — set, no later override

Common keys:

| Key | Source |
|---|---|
| `KERNEL` | Kernel device name (sda, ttyUSB0) |
| `SUBSYSTEM` | block, net, tty, usb, ... |
| `DRIVER` | Kernel driver |
| `ATTR{name}` | Sysfs attribute |
| `ENV{name}` | Environment variable |
| `ACTION` | add, remove, change |
| `NAME` | Replaces device name (rare) |
| `SYMLINK` | Add /dev symlink |
| `OWNER`, `GROUP`, `MODE` | Permissions |
| `RUN+="prog"` | Run program |

Example:

```
# /etc/udev/rules.d/99-mythumb.rules
SUBSYSTEM=="block", ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5567", SYMLINK+="mythumb"
```

#### Tools

```bash
udevadm monitor                      # watch events live
udevadm monitor --property
udevadm info -a -n /dev/sda          # walk attributes upward (useful for writing rules)
udevadm info -q all -n /dev/sda
udevadm trigger                      # replay uevents
udevadm control --reload-rules
udevadm test /sys/block/sda          # dry-run rule processing
```

**Exercise:** Write a rule that creates `/dev/myusb` when a specific USB stick is inserted.

**Mock Q.** Which command reloads the udev rule files in memory without rebooting?
- A) `udevadm reload`  B) `udevadm control --reload-rules`  C) `systemctl reload udev`  D) `udevd -r`

**A:** **B.**

### 4.3 `/proc` — kernel/process pseudo-filesystem

| File | Meaning |
|---|---|
| `/proc/cpuinfo` | Per-CPU info (model, MHz, flags, cache) |
| `/proc/meminfo` | RAM/swap accounting |
| `/proc/loadavg` | 1/5/15-min load + running/total/last pid |
| `/proc/uptime` | uptime, idle |
| `/proc/version` | Kernel version, gcc used, build date |
| `/proc/cmdline` | Kernel command-line at boot |
| `/proc/modules` | Loaded modules (same as `lsmod`) |
| `/proc/filesystems` | Supported FS types |
| `/proc/mounts` | Live mount list |
| `/proc/swaps` | Swap areas |
| `/proc/partitions` | Block devices |
| `/proc/devices` | char/block major→driver |
| `/proc/interrupts` | IRQ counters |
| `/proc/iomem`, `/proc/ioports` | I/O resources |
| `/proc/net/*` | Network stats: `/proc/net/tcp`, `/proc/net/route`, `/proc/net/dev` |
| `/proc/sys/...` | Tunables (also via `sysctl`) |

```bash
grep ^processor /proc/cpuinfo | wc -l       # logical CPUs
grep MemAvailable /proc/meminfo
awk '{print $1}' /proc/loadavg
cat /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/ip_forward      # enable forwarding for this boot
```

### 4.4 `/sys` — sysfs

Exports the kernel device model. Each directory mirrors a kernel object.

Key trees:

- `/sys/block/<dev>/` — disks
- `/sys/class/net/<iface>/` — network interfaces
- `/sys/class/power_supply/` — batteries, AC
- `/sys/class/thermal/` — thermal zones
- `/sys/devices/` — physical topology
- `/sys/module/<name>/parameters/` — runtime kernel module parameters
- `/sys/firmware/efi/` — UEFI runtime
- `/sys/kernel/security/` — LSM exposure

```bash
cat /sys/class/net/eth0/address       # MAC
cat /sys/class/net/eth0/operstate
cat /sys/class/power_supply/BAT0/capacity
echo none > /sys/block/sda/queue/scheduler   # set I/O scheduler (per boot)
```

### 4.5 The Filesystem Hierarchy Standard (FHS)

Every Linux administrator must know this layout.

| Dir | Purpose | Notes |
|---|---|---|
| `/` | Root | Self-contained at boot |
| `/bin` | Essential user binaries | `ls`, `cp`, etc. Modern distros symlink to `/usr/bin` |
| `/sbin` | Essential admin binaries | `init`, `fsck`. Often symlink to `/usr/sbin` |
| `/lib`, `/lib32`, `/lib64` | Essential libraries / kernel modules | `/lib/modules/<ver>/` |
| `/usr` | Read-only user-space | The bulk of installed software |
| `/usr/bin`, `/usr/sbin`, `/usr/lib` | Non-essential equivalents |
| `/usr/local/` | Locally compiled software | Survives package upgrades |
| `/usr/share/` | Architecture-independent data | docs, man pages, icons |
| `/usr/src/` | Source code (kernel, headers) |
| `/etc` | System config | No binaries here |
| `/var` | Variable data | logs, mail, spools, dbs |
| `/var/log` | Logs |
| `/var/spool/` | Print, mail, cron queues |
| `/var/lib/` | App state (dpkg, mysql, etc.) |
| `/var/cache/` | Cacheable data (regenerable) |
| `/var/run` / `/run` | PIDs, sockets, runtime |
| `/var/tmp/` | Temporary, may survive reboot |
| `/tmp` | Temporary, may be cleared at boot |
| `/home` | Users' home dirs |
| `/root` | Root's home |
| `/boot` | Kernel, initrd, GRUB |
| `/dev` | Device files |
| `/proc` | procfs |
| `/sys` | sysfs |
| `/mnt` | Temporary mount points (admin) |
| `/media` | Removable media (auto-mount) |
| `/opt` | Third-party self-contained software (`/opt/<vendor>/<product>`) |
| `/srv` | Service data (web roots, FTP) |

**TRAP:** Distinction between `/tmp` (cleared at boot, typically tmpfs) and `/var/tmp` (persistent). Files in `/var/tmp` can survive reboots.

**TRAP:** `/usr/local/` is not affected by package management. Locally compiled software typically installs here (`./configure --prefix=/usr/local`).

### 4.6 Virtual filesystems

| FS | Backed by | Purpose |
|---|---|---|
| `tmpfs` | RAM (+swap) | Fast scratch (`/tmp`, `/run`, `/dev/shm`) |
| `devtmpfs` | Kernel | Pre-udev `/dev` population |
| `sysfs` | Kernel | Mounted at `/sys` |
| `procfs` | Kernel | `/proc` |
| `cgroup`, `cgroup2` | Kernel | Resource control hierarchy |
| `securityfs` | Kernel | LSM (SELinux, AppArmor) |
| `debugfs` | Kernel | Debugging (`/sys/kernel/debug`) |

```bash
mount -t tmpfs -o size=512M tmpfs /mnt/ram
mount | grep tmpfs
```

**Exercises**
- *Exercise 1:* Identify the bytes free in your largest tmpfs without using `df`.
- *Exercise 2:* Persistently set `vm.swappiness=10`.

**Mock Exam Questions**

**Q1.** Which directory should hold persistent variable data such as a database server's data files?
- A) `/var/lib`  B) `/srv`  C) `/usr/var`  D) `/etc/lib`

**A:** **A.** `/var/lib/<package>` is the FHS-correct location.

**Q2.** Locally compiled software typically installs to:
- A) `/usr/bin`  B) `/opt`  C) `/usr/local`  D) `/etc/local`

**A:** **C.** (`/opt` is more common for vendor-shipped self-contained bundles.)

**Q3 (Scenario).** After reboot a file in `/tmp` has vanished. Why is this expected?

**A:** Many distros mount `/tmp` as tmpfs (RAM-backed), or use a `systemd-tmpfiles` cleanup at boot. Use `/var/tmp` for files needing to survive reboot.

---

## Chapter 5: Shell Scripting (Bash) — Complete Guide

### 5.1 Shebang and Execution

```bash
#!/usr/bin/env bash
echo "Hello, $1"
```

- `#!` ("shebang") on line 1 tells the kernel which interpreter to invoke.
- `/usr/bin/env bash` finds bash via PATH — portable.
- `/bin/bash` is fine if you know bash is there.
- `#!/bin/sh` selects POSIX-strict shell; many bashisms break.

```bash
chmod +x script.sh
./script.sh                # uses shebang
bash script.sh             # forces bash; shebang ignored
bash -n script.sh          # syntax check only
bash -x script.sh          # trace
```

### 5.2 Variables

```bash
name="Alice"               # no spaces around =
echo "$name"
echo "${name}_log"         # braces required to delimit
NAME=Alice cmd             # set only for this command

# Special vars:
$0    # script name
$1..$9  ${10}  # positional args
$#    # number of args
$@    # all args, separately quoted
$*    # all args, single string
$?    # last command exit status
$$    # current PID
$!    # last background PID
$_    # last arg of previous command
PIPESTATUS  # array of exit codes for last pipeline
```

`"$@"` vs `"$*"`: when quoted, `"$@"` expands to `"$1" "$2" "$3"` (preserving separation), `"$*"` expands to `"$1 $2 $3"` (joined by IFS first char).

### 5.3 String Operations (parameter expansion)

| Expression | Meaning |
|---|---|
| `${var:-default}` | If unset/empty, use `default` |
| `${var:=default}` | As above AND assign |
| `${var:?msg}` | Error and exit if unset/empty |
| `${var:+alt}` | If set, expand to `alt` else empty |
| `${#var}` | Length |
| `${var:offset}` | Substring from offset |
| `${var:offset:len}` | Substring |
| `${var#prefix}` | Remove shortest prefix match |
| `${var##prefix}` | Remove longest prefix |
| `${var%suffix}` | Remove shortest suffix |
| `${var%%suffix}` | Remove longest suffix |
| `${var/old/new}` | Replace first |
| `${var//old/new}` | Replace all |
| `${var/#old/new}` | Replace if at start |
| `${var/%old/new}` | Replace if at end |
| `${var^^}` | Uppercase all |
| `${var,,}` | Lowercase all |
| `${var^}` / `${var,}` | First-letter case toggle |

```bash
path=/usr/local/bin/script.sh
echo "${path##*/}"           # script.sh
echo "${path%/*}"            # /usr/local/bin
echo "${path%.*}"            # /usr/local/bin/script
echo "${path##*.}"           # sh
name=alice
echo "Hello ${name^^}!"      # Hello ALICE!
```

### 5.4 Arrays

#### Indexed

```bash
arr=(one two three)
arr[3]=four
echo "${arr[0]}"
echo "${arr[@]}"             # all elements
echo "${#arr[@]}"            # count
echo "${!arr[@]}"            # indices
arr+=(five)
unset 'arr[1]'
```

#### Associative (bash 4+)

```bash
declare -A user
user[name]=alice
user[uid]=1000
echo "${user[name]}"
for k in "${!user[@]}"; do echo "$k=${user[$k]}"; done
```

### 5.5 Arithmetic

```bash
i=$((1 + 2))
((i++))
((i+=5))
((i > 3)) && echo big

# expr (POSIX), spaces and escapes needed
n=$(expr 5 \* 4)

# bc for floating point
echo "scale=4; 22/7" | bc
```

### 5.6 Conditionals

```bash
if [ "$x" -gt 10 ]; then
    echo big
elif [ "$x" -eq 10 ]; then
    echo equal
else
    echo small
fi

# case
case "$choice" in
    yes|y|Y) echo accepted ;;
    no|n|N)  echo declined ;;
    *)       echo unknown; exit 1 ;;
esac
```

### 5.7 Loops

```bash
# for-in
for f in *.log; do
    echo "found $f"
done

# C-style
for ((i=0; i<10; i++)); do
    echo "$i"
done

# while
i=0
while [ $i -lt 5 ]; do
    echo $i
    ((i++))
done

# until
until ping -c1 host >/dev/null 2>&1; do
    sleep 1
done

# reading a file line by line
while IFS= read -r line; do
    echo ">> $line"
done < input.txt

# break / continue with N (skip out of nested)
for outer in a b c; do
    for inner in 1 2 3; do
        [[ $inner == 2 ]] && continue 2
        echo "$outer $inner"
    done
done
```

**TRAP:** `for line in $(cat file)` splits on whitespace. Use `while read` for line-oriented input.

### 5.8 Functions

```bash
greet() {
    local name="${1:-World}"
    echo "Hello $name"
    return 0
}

greet
greet Alice
ret=$(greet Bob)              # capture stdout

# Pass array
print_arr() {
    local arr=("$@")
    for x in "${arr[@]}"; do echo "$x"; done
}
print_arr "${nums[@]}"
```

- `return N` sets the function's exit status (0–255).
- Function output is its stdout. Capture with `$()`.

### 5.9 I/O

```bash
echo "info"
printf "%s %d\n" "lines" 42
read -p "Name: " name
cmd >/dev/null 2>&1
exec 3<file.txt          # open file on fd 3
while read -r line <&3; do echo "$line"; done
exec 3<&-                # close fd 3
```

### 5.10 Error Handling

```bash
set -e            # exit on any non-zero (except in conditions)
set -u            # error on undefined variable
set -o pipefail   # a pipeline's status is the first non-zero
set -E            # ERR trap inherited by functions
set -x            # trace
trap 'echo "Cleanup"; rm -f "$tmp"' EXIT
trap 'echo "Got SIGINT"; exit 130' INT
```

Reset: `set +e`, `set +x`, etc. Combine: `set -euo pipefail` at top of every robust script.

**TRAP:** `set -e` does *not* trigger inside `if`, `while`, `&&`, `||` left-hand contexts. Common mistake.

### 5.11 Debugging

```bash
bash -n script.sh           # syntax check, no run
bash -x script.sh           # trace
bash -xv script.sh          # verbose
PS4='+ [${LINENO}] '        # nicer trace prefix
set -x; ...; set +x
```

Use `shellcheck script.sh` (external) to lint.

### 5.12 Regex in scripts

```bash
[[ "$ip" =~ ^[0-9]+(\.[0-9]+){3}$ ]] && echo "ipv4-ish"
echo "${BASH_REMATCH[0]}"   # full match
echo "${BASH_REMATCH[1]}"   # first capture
```

### 5.13 Example: backup script

```bash
#!/usr/bin/env bash
set -euo pipefail

SRC=/data
DEST=/backup
DATE=$(date +%F)
ARCHIVE="$DEST/data-$DATE.tar.gz"

mkdir -p "$DEST"
tar -czf "$ARCHIVE" -C "$(dirname "$SRC")" "$(basename "$SRC")"

# Keep last 7
find "$DEST" -name 'data-*.tar.gz' -mtime +7 -delete

logger -t backup "Wrote $ARCHIVE"
```

### 5.14 Example: log parser

```bash
#!/usr/bin/env bash
LOG=${1:-/var/log/auth.log}
awk '
    /Failed password/ {
        for (i=1; i<=NF; i++) if ($i == "from") { print $(i+1); next }
    }
' "$LOG" | sort | uniq -c | sort -nr | head
```

### 5.15 Example: system monitor

```bash
#!/usr/bin/env bash
while :; do
    clear
    echo "=== $(date) ==="
    echo "Load: $(cut -d' ' -f1-3 /proc/loadavg)"
    echo "Mem (MiB): $(free -m | awk '/Mem:/ {print $3"/"$2}')"
    echo "Top 5 CPU:"
    ps -eo pid,user,%cpu,comm --sort=-%cpu | head -6
    sleep 5
done
```

### 5.16 Example: user creator

```bash
#!/usr/bin/env bash
set -euo pipefail

USERS_FILE=${1:?Usage: $0 USERSFILE}
while IFS=: read -r user uid group; do
    [[ -z $user || $user == \#* ]] && continue
    if id "$user" &>/dev/null; then
        echo "$user already exists"
        continue
    fi
    useradd -u "$uid" -g "$group" -m -s /bin/bash "$user"
    echo "$user:ChangeMe123" | chpasswd
    chage -d 0 "$user"        # force change at next login
done < "$USERS_FILE"
```

**Exercises**
- *Exercise 1:* Write a script that takes a directory path and prints the 10 largest files inside it.
- *Exercise 2:* Write a script that watches a file (passed as $1) and beeps (writes `\a` to /dev/tty) whenever the line count grows.

**Mock Exam Questions**

**Q1.** `${name:-default}` evaluates to:
- A) `default` always
- B) `default` if `name` is unset or empty; otherwise `$name`
- C) `default` only if `name` is unset
- D) Sets `name` to `default`

**A:** **B.** (Use `:=` to also assign.)

**Q2.** Why does this fail under `set -e`? `cmd | grep foo; echo done`
- A) `cmd` may set non-zero
- B) `set -e` does not catch failures within a pipeline unless `set -o pipefail`
- C) `echo done` does not propagate
- D) `grep` always errors

**A:** **B.** Without `pipefail`, only the last command's status counts, and `set -e` looks at that.

**Q3 (Scenario).** A script reads a list with `for line in $(cat file)` and treats each word, not each line, as an item. How fix?

**A:** Use `while IFS= read -r line; do ... done < file`. Word-splitting on `$()` is the culprit.

---

## Chapter 6: User & Group Management

### 6.1 `/etc/passwd`

One line per user, 7 colon-separated fields:

```
alice:x:1000:1000:Alice Smith,,,:/home/alice:/bin/bash
```

| Field | Meaning |
|---|---|
| 1 | Username |
| 2 | Password (`x` = look in shadow; `*`/`!` = locked) |
| 3 | UID |
| 4 | Primary GID |
| 5 | GECOS / comment (name, room, phone — comma-separated) |
| 6 | Home directory |
| 7 | Login shell |

**TRAP:** UID 0 is root. UID < 1000 (RHEL) or < 1000 (Debian since wheezy) are system users. UID = 65534 is `nobody` (or `nfsnobody`).

### 6.2 `/etc/shadow`

```
alice:$y$j9T$abc...:19500:0:99999:7:::
```

| Field | Meaning |
|---|---|
| 1 | Username |
| 2 | Hashed password (algorithm prefixes: `$1$` MD5, `$5$` SHA-256, `$6$` SHA-512, `$y$` yescrypt) |
| 3 | Last change (days since epoch) |
| 4 | Min days between changes |
| 5 | Max days (password must change after) |
| 6 | Warn days before expiry |
| 7 | Inactive: days after expiry until disabled |
| 8 | Expiration date (days since epoch) |
| 9 | Reserved |

Special password field values:
- `*` — account exists but no password set (no login)
- `!` or `!!` — account locked (still can use SSH key)
- `!hash` — locked but hash preserved

Permissions: `-rw-r-----  root:shadow` (or `root:root`).

### 6.3 `/etc/group` and `/etc/gshadow`

```
devs:x:1001:alice,bob
```

| Field | Meaning |
|---|---|
| 1 | Group name |
| 2 | Password (rarely used; `x` → gshadow) |
| 3 | GID |
| 4 | Comma-separated members (supplementary) |

`/etc/gshadow` holds group passwords (used by `newgrp`).

### 6.4 `useradd`, `usermod`, `userdel`

```bash
useradd alice                            # minimal
useradd -m -s /bin/bash -G wheel,docker alice
useradd -u 1500 -g devs -G sudo -c "Alice" -m -d /home/alice -s /bin/bash alice
useradd -r postgres                      # system user
useradd -e 2026-12-31 alice              # account expiration
useradd -D                               # show defaults
useradd -D -s /bin/zsh                   # change default shell for new users
```

Important `useradd` flags:

| Flag | Meaning |
|---|---|
| `-m` | Create home from skeleton |
| `-M` | Don't create home |
| `-d DIR` | Home dir |
| `-s SHELL` | Login shell |
| `-u UID` | Specific UID |
| `-g GID` | Primary group |
| `-G g1,g2` | Supplementary groups |
| `-c "GECOS"` | Comment |
| `-e DATE` | Expiration (YYYY-MM-DD) |
| `-f DAYS` | Inactive days after password expiry |
| `-r` | System user (UID below SYS_UID_MAX) |
| `-k DIR` | Skel dir (default `/etc/skel`) |
| `-N` | Don't create user-private group |

```bash
usermod -aG docker alice         # ADD to docker group (CRITICAL: -a)
usermod -G docker alice          # REPLACE all supplementary groups with just docker!
usermod -L alice                 # Lock (prefixes ! to hash)
usermod -U alice                 # Unlock
usermod -s /bin/zsh alice
usermod -l newname oldname
usermod -d /new/home -m alice    # move home
usermod -e 2026-12-31 alice
```

**TRAP — the #1 most-tested mistake:** `usermod -G groups user` *replaces* the user's supplementary groups. Almost always you want `usermod -aG`. Without `-a` you'll silently remove the user from every other group.

```bash
userdel alice                    # delete user, keep home
userdel -r alice                 # also remove home and mail spool
userdel -f alice                 # force even if logged in
```

### 6.5 `groupadd`, `groupmod`, `groupdel`

```bash
groupadd devs
groupadd -g 1500 devs
groupadd -r systemgrp
groupmod -n developers devs        # rename
groupmod -g 2000 developers        # change GID
groupdel developers
gpasswd -a alice devs              # add user to group
gpasswd -d alice devs              # remove
gpasswd -A alice devs              # alice becomes group admin
gpasswd devs                       # set group password
```

### 6.6 `passwd`, `chage`

```bash
passwd                       # change own
passwd alice                 # root: change someone else
passwd -l alice              # lock
passwd -u alice              # unlock
passwd -d alice              # delete password (empty - dangerous)
passwd -e alice              # expire immediately
passwd -S alice              # status: PS=password set, LK=locked, NP=no password
passwd --stdin alice         # RHEL-only; reads new pw from stdin
```

`chage` manages password aging:

```bash
chage -l alice                          # list
chage -m 7 -M 90 -W 14 -I 7 alice       # min/max/warn/inactive
chage -E 2026-12-31 alice               # expiration date
chage -E -1 alice                       # remove expiration
chage -d 0 alice                        # force change at next login
```

Defaults live in `/etc/login.defs`:

| Key | Meaning |
|---|---|
| `PASS_MAX_DAYS` | Max age |
| `PASS_MIN_DAYS` | Min age |
| `PASS_WARN_AGE` | Warn before expiry |
| `UID_MIN`/`UID_MAX` | Range for regular users |
| `SYS_UID_MIN`/`SYS_UID_MAX` | Range for system users |
| `CREATE_HOME` | Default for `useradd -m` |
| `USERGROUPS_ENAB` | Auto-create user-private group |

### 6.7 `su` and `sudo`

```bash
su                  # become root, current $PATH/env (with bash's behavior)
su -                # full login shell with target user's env (recommended)
su - alice          # become alice with her env
su - -c "id" alice  # run one command
```

`sudo` evaluates rules in `/etc/sudoers` (edit only with `visudo` — checks syntax). Per-user/group snippets in `/etc/sudoers.d/*`.

Sudoers syntax:

```
# User_Alias / Runas_Alias / Host_Alias / Cmnd_Alias may be defined
Cmnd_Alias NETCMDS = /sbin/ip, /usr/bin/ss
%admins ALL=(ALL:ALL) ALL
alice   ALL=(ALL) NOPASSWD: NETCMDS
bob     ALL=(ALL) /usr/bin/systemctl restart nginx
```

Format per line: `USER  HOSTS=(RUNAS_USER:RUNAS_GROUP)  TAGS:  CMNDS`

Important tags:
- `NOPASSWD:` — no password required
- `PASSWD:` — require password (default)
- `NOEXEC:` — block exec*()
- `SETENV:` — preserve env

```bash
sudo -l                  # what can I run?
sudo -u alice cmd        # run as alice
sudo -i                  # interactive root shell (login)
sudo -s                  # root shell (non-login)
sudo -E cmd              # preserve environment (must allow with env_keep)
sudo -k                  # invalidate cached creds
visudo                   # edit /etc/sudoers safely
visudo -c                # check syntax
visudo -f /etc/sudoers.d/myrule
```

**TRAP:** `NOPASSWD: ALL` is dangerous. Restrict to specific commands. Beware of allowing editors (`vi`, `less`) that can shell-out — use `sudoedit` instead.

### 6.8 PAM — Pluggable Authentication Modules

PAM externalizes authentication. Each service has a stack of modules in `/etc/pam.d/<service>`.

Module types:

| Type | What it does |
|---|---|
| `auth` | Verify identity |
| `account` | Verify account is allowed to log in (expiry, hours) |
| `password` | Change credentials |
| `session` | Setup/teardown around the session (mounts, logging) |

Control flags:

| Flag | Meaning |
|---|---|
| `required` | Must succeed; if fail, continue stack but ultimately fail |
| `requisite` | Must succeed; on fail, stop immediately |
| `sufficient` | If success, return (unless prior `required` failed) |
| `optional` | Result rarely matters |
| `include FILE` | Include another stack |
| `substack FILE` | Like include but errors don't skip the calling stack |
| `[key=value ...]` | Fine-grained control |

Common modules:

| Module | Use |
|---|---|
| `pam_unix.so` | Standard /etc/shadow auth |
| `pam_securetty.so` | Restrict root to listed TTYs |
| `pam_nologin.so` | Block non-root when `/etc/nologin` exists |
| `pam_listfile.so` | Allow/deny based on a file |
| `pam_limits.so` | Apply `/etc/security/limits.conf` |
| `pam_env.so` | Set env from `/etc/environment` |
| `pam_tally2.so` / `pam_faillock.so` | Lock after failed attempts |
| `pam_cracklib.so` / `pam_pwquality.so` | Enforce password strength |
| `pam_ldap.so` / `pam_sss.so` | LDAP / SSSD auth |
| `pam_krb5.so` | Kerberos |
| `pam_mkhomedir.so` | Auto-create home dir |

Sample `/etc/pam.d/sshd`:

```
auth     required   pam_securetty.so
auth     required   pam_nologin.so
auth     include    system-auth
account  required   pam_unix.so
session  required   pam_limits.so
session  include    system-auth
```

### 6.9 nsswitch.conf

`/etc/nsswitch.conf` tells glibc where to look for various databases.

```
passwd:  files systemd
shadow:  files
group:   files systemd
hosts:   files dns
networks: files
services: files
protocols: files
```

Order matters. `files` = `/etc/<db>`. Other sources: `ldap`, `sss`, `nis`, `mdns4`, `wins`.

**Exercises**
- *Exercise 1:* Create user `dev1` with UID 2001, home `/srv/dev1`, primary group `devs`, supplementary `docker`, shell `/bin/bash`, and force a password change at first login.
- *Exercise 2:* Configure sudo so that `bob` can `systemctl restart nginx` without a password but nothing else.

**Mock Exam Questions**

**Q1.** Which file holds password hashes on a modern Linux system?
- A) `/etc/passwd`  B) `/etc/shadow`  C) `/etc/gshadow`  D) `/etc/security/pwd`

**A:** **B.**

**Q2.** `usermod -G docker alice` does what?
- A) Adds alice to docker, keeping her other supplementary groups
- B) Replaces alice's supplementary groups with just docker
- C) Makes docker her primary group
- D) Fails because she might still be a member of other groups

**A:** **B.** This is the classic LPIC trap. Use `-aG` to append.

**Q3.** Which `chage` flag forces a password change at next login?
- A) `chage -E 0 user`  B) `chage -d 0 user`  C) `chage -M 0 user`  D) `chage -W 0 user`

**A:** **B.** Setting last-change-date to 0 (= 1970-01-01) makes the password instantly expired.

**Q4 (Scenario).** A user has been added to the `docker` group with `usermod -aG docker alice`, but typing `docker ps` still says "permission denied". Why?

**A:** Group membership is determined at session start. She must log out and back in (or run a new shell with `newgrp docker`).

**Q5.** Which PAM type runs at password change time?
- A) `auth`  B) `account`  C) `password`  D) `session`

**A:** **C.** PAM stack types: auth (verify identity), account (whether allowed), password (changing it), session (around login).

---

## Chapter 7: Networking Fundamentals

### 7.1 OSI Model — Linux Mapping

| Layer | Name | Linux example |
|---|---|---|
| 7 | Application | HTTP, SSH, DNS |
| 6 | Presentation | TLS, compression |
| 5 | Session | Sockets API |
| 4 | Transport | TCP, UDP — `ss`, `netstat` |
| 3 | Network | IPv4, IPv6, ICMP — `ip route`, `iptables` |
| 2 | Data Link | Ethernet, ARP — `ip link`, `ip neigh`, `arp` |
| 1 | Physical | Cabling, drivers — `ethtool` |

### 7.2 IPv4 Addressing and Subnetting

An IPv4 address is 32 bits, usually written as 4 octets. CIDR appends `/N` for the netmask: `/24` = `255.255.255.0`.

Quick subnet table:

| CIDR | Netmask | Hosts | Notes |
|---|---|---|---|
| /30 | 255.255.255.252 | 2 | Point-to-point |
| /29 | 255.255.255.248 | 6 | |
| /28 | 255.255.255.240 | 14 | |
| /27 | 255.255.255.224 | 30 | |
| /26 | 255.255.255.192 | 62 | |
| /25 | 255.255.255.128 | 126 | |
| /24 | 255.255.255.0 | 254 | Most common LAN |
| /23 | 255.255.254.0 | 510 | |
| /22 | 255.255.252.0 | 1022 | |
| /16 | 255.255.0.0 | 65534 | |
| /8 | 255.0.0.0 | 16M | |

Reserved/private:
- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16
- 127.0.0.0/8 — loopback
- 169.254.0.0/16 — link-local (APIPA)
- 224.0.0.0/4 — multicast

IPv6 prefixes you should know:
- `::1/128` — loopback
- `fe80::/10` — link-local
- `fc00::/7` — unique-local (private)
- `2000::/3` — global unicast
- `ff00::/8` — multicast

### 7.3 `ip` — the Modern Tool

```
ip [OPTIONS] OBJECT COMMAND [ARGS]
```

`OBJECT` ∈ {link, addr, route, neigh, rule, tunnel, netns, monitor, maddr, mroute, xfrm}.

#### `ip link` — layer 2

`ip link` queries or changes network-interface properties below IP addressing: administrative up/down state, MTU, MAC address, and virtual link types. “UP” means administratively enabled; it does not prove carrier, an IP address, a route, DNS, or application reachability. Use `ip -s link`, `ethtool`, and logs to separate link errors from higher-layer failures. Changes made with `ip` are runtime-only unless also declared in the system's persistent network manager.

```bash
ip link                         # all interfaces
ip -br link                     # brief
ip link show eth0
ip link set eth0 up
ip link set eth0 down
ip link set eth0 mtu 9000
ip link set eth0 address 00:11:22:33:44:55
ip link add veth0 type veth peer name veth1
ip link add link eth0 name eth0.10 type vlan id 10
ip link add br0 type bridge
```

#### `ip addr` — layer 3 addresses

`ip addr` manages the kernel's address objects on interfaces. Adding an address also creates a connected route for its prefix; it does not create a default gateway or DNS configuration. `flush` can remove every matching address and disconnect the host, so filter carefully and keep console access when working remotely. IPv6 addresses may have tentative/deprecated states that affect usability.

```bash
ip addr                         # all
ip -4 addr                      # IPv4 only
ip addr show eth0
ip addr add 192.168.1.10/24 dev eth0
ip addr add 192.168.1.10/24 broadcast + dev eth0
ip addr del 192.168.1.10/24 dev eth0
ip addr flush dev eth0
```

#### `ip route`

The routing table tells the kernel which next hop and output interface to use for a destination. Longest prefix wins first; metric/preferences break relevant ties; policy rules may select a different table before lookup. `ip route get ADDRESS` is more diagnostic than merely listing routes because it asks the kernel to resolve a concrete path including source address. `replace` is useful for idempotent changes, whereas `add` fails if the route already exists.

```bash
ip route                        # routing table
ip route show
ip route get 8.8.8.8            # which route would be used?
ip route add 10.0.0.0/24 via 192.168.1.1
ip route add 10.0.0.0/24 dev eth1
ip route add default via 192.168.1.1
ip route del 10.0.0.0/24
ip route replace 10.0.0.0/24 via 192.168.1.2
ip route flush table main
```

#### `ip neigh` — ARP table

The neighbor table maps on-link network addresses to link-layer addresses: ARP for IPv4 and Neighbor Discovery for IPv6. Entries have states such as `REACHABLE`, `STALE`, `DELAY`, `PROBE`, `FAILED`, or `INCOMPLETE`. An incomplete/failed entry points to a layer-2/VLAN/address-resolution problem, not DNS. Static entries bypass discovery and must be maintained deliberately.

```bash
ip neigh
ip neigh show dev eth0
ip neigh add 192.168.1.5 lladdr 00:11:22:33:44:55 dev eth0
ip neigh flush all
```

#### `ip rule` — policy routing

Policy rules choose a routing table based on source, mark, interface and other selectors before normal route lookup. Use them for multi-homing, source-specific gateways, or traffic classes—not as a replacement for ordinary destination routes. Rule priority is evaluation order; document custom table names in `/etc/iproute2/rt_tables` and add both rule and routes persistently.

```bash
ip rule                                   # default table priorities
ip rule add from 10.0.0.0/24 table 100
ip route add default via 10.0.0.1 table 100
```

### 7.4 `ifconfig` — Legacy but Examined

```bash
ifconfig                         # all up interfaces
ifconfig -a                      # including down
ifconfig eth0
ifconfig eth0 up
ifconfig eth0 down
ifconfig eth0 192.168.1.10 netmask 255.255.255.0
ifconfig eth0 mtu 9000
ifconfig eth0 hw ether 00:11:22:33:44:55
ifconfig eth0:0 192.168.2.10/24  # virtual alias
```

| `ip` equivalent | `ifconfig` |
|---|---|
| `ip addr` | `ifconfig` |
| `ip link set X up` | `ifconfig X up` |
| `ip addr add ... dev X` | `ifconfig X IP netmask MASK` |
| `ip -s link` | `ifconfig` (with stats) |

### 7.5 NetworkManager — `nmcli`, `nmtui`

NetworkManager distinguishes a **device** (current interface) from a **connection profile** (persistent desired configuration). `nmcli device` answers what hardware is managed now; `nmcli connection` answers what profiles can be activated. Modify a named profile, activate it, then verify kernel state with `ip` and resolver state with `resolvectl`/`getent`. Changing a profile without reactivation may not alter the live interface.

```bash
nmcli                                  # status summary
nmcli device                           # devices
nmcli connection                       # saved connections
nmcli connection show                  # detailed
nmcli connection up eth0
nmcli connection down eth0
nmcli connection add type ethernet con-name home ifname eth0 \
       ip4 192.168.1.10/24 gw4 192.168.1.1
nmcli connection modify home ipv4.dns "1.1.1.1 8.8.8.8"
nmcli connection reload
nmcli device wifi connect 'SSID' password 'PASSWD'
nmcli radio wifi off
nmtui                                  # ncurses TUI
```

### 7.6 Static Configuration Files

#### Debian/Ubuntu (ifupdown) — `/etc/network/interfaces`

```
auto eth0
iface eth0 inet static
    address 192.168.1.10
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 1.1.1.1 8.8.8.8

iface eth1 inet dhcp
```

```bash
ifup eth0
ifdown eth0
ifup -a
```

#### Modern Debian/Ubuntu — Netplan YAML in `/etc/netplan/*.yaml`

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: false
      addresses: [192.168.1.10/24]
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [1.1.1.1, 8.8.8.8]
```

Apply with `netplan apply`.

#### RHEL/CentOS legacy — `/etc/sysconfig/network-scripts/ifcfg-eth0`

```
DEVICE=eth0
BOOTPROTO=static
ONBOOT=yes
IPADDR=192.168.1.10
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
DNS1=1.1.1.1
```

### 7.7 DNS Resolution

`/etc/resolv.conf`:

```
nameserver 1.1.1.1
nameserver 8.8.8.8
search example.com lab.example.com
options ndots:2 timeout:2 attempts:2
```

On systemd-resolved systems, this file is a symlink to `/run/systemd/resolve/stub-resolv.conf`; configure via `/etc/systemd/resolved.conf` or `resolvectl`.

`/etc/hosts`: static name→IP mapping checked before DNS (per nsswitch order).

```
127.0.0.1   localhost
127.0.1.1   myhost.example.com myhost
::1         ip6-localhost
```

DNS tools:

```bash
dig example.com                          # full record set
dig +short example.com
dig @8.8.8.8 example.com
dig MX example.com
dig AAAA example.com
dig -x 8.8.8.8                           # reverse PTR
dig +trace example.com                   # follow delegation
dig +noall +answer example.com

host example.com
host -t MX example.com
host 8.8.8.8

nslookup example.com

getent hosts example.com                 # uses nsswitch order
getent ahosts example.com                # IPv4+IPv6 lookup
resolvectl query example.com             # systemd-resolved
```

### 7.8 Network Diagnostics

#### `ping`

`ping` sends ICMP echo requests and measures replies/loss/round-trip time. It proves only that this ICMP exchange works; firewalls may block it while TCP services work, and a reply does not prove an application is healthy. Use numeric targets to separate DNS from reachability, bounded `-c` in scripts, and MTU probing to diagnose path-MTU issues.

```bash
ping example.com
ping -c 4 example.com
ping -i 0.2 -c 100 host
ping -W 2 host
ping -s 1472 -M do host                 # MTU probing (don't fragment)
ping6 ipv6.google.com
```

#### `traceroute`, `tracepath`, `mtr`

These infer successive hops by sending probes with increasing TTL/hop-limit and observing expiration messages. Missing hops can mean filtering or rate limiting rather than packet loss at that router. `mtr` repeats the experiment to show trends; loss shown at an intermediate hop is meaningful only if it continues to later hops. Choose TCP/ICMP probes resembling the real application when UDP probes are filtered.

```bash
traceroute example.com
traceroute -n example.com
traceroute -T -p 443 example.com         # TCP
traceroute -I example.com                # ICMP
tracepath example.com
mtr example.com
mtr -rwc 100 example.com                 # report mode
```

#### `netstat` (legacy) and `ss` (modern)

`ss` queries kernel socket tables and is the preferred way to determine which local addresses/ports are listening, which connections exist, and which process owns them. `-l` means listening, `-n` prevents slow/misleading name resolution, and `-p` may require privilege. A listening socket proves a process bound the port; it does not prove firewall reachability or application correctness. `netstat` remains exam-relevant but comes from legacy net-tools.

```bash
ss -tulpn                       # TCP+UDP, listening, processes, numeric
ss -anp                         # all connections, processes
ss -s                           # summary
ss -t state established
ss dport = :443
netstat -tulpn
netstat -rn
netstat -i
```

#### `nmap`

`nmap` sends active probes to discover hosts, ports and selected service fingerprints. Use it from the same network perspective as the affected client; a local scan and a remote scan test different firewalls/routes. States such as open, closed and filtered describe observed responses, not absolute truth. Scan only systems and ranges you are authorized to test.

```bash
nmap 192.168.1.0/24                # ping sweep + top ports
nmap -sn 192.168.1.0/24            # just discovery
nmap -p 22,80,443 host
nmap -p- host
nmap -sS host                       # SYN scan (root)
nmap -sU -p 53,123 host
nmap -sV -O host
nmap -A host
```

#### `tcpdump`

`tcpdump` captures packets visible at an interface and applies a BPF capture/display filter. Use `-nn` to keep addresses and ports numeric, `-i any` for broad host diagnosis, `-s 0` when full payload capture is justified, and `-w` to preserve evidence for Wireshark. Captures can contain credentials and personal data; limit scope, protect files, and correlate packet timestamps with application logs.

```bash
tcpdump -i eth0
tcpdump -i any -nn 'port 53'
tcpdump -i eth0 'host 192.168.1.5 and port 80'
tcpdump -i eth0 -w out.pcap
tcpdump -r out.pcap
tcpdump -A -s0 'port 80'
tcpdump 'tcp[tcpflags] & tcp-syn != 0'
```

### 7.9 Ports & Protocols

| Port | Service |
|---|---|
| 20/21 | FTP data / control |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS (UDP & TCP) |
| 67/68 | DHCP server/client |
| 69 | TFTP |
| 80 | HTTP |
| 110 | POP3 |
| 123 | NTP |
| 137-139 | NetBIOS |
| 143 | IMAP |
| 161/162 | SNMP / trap |
| 389 | LDAP |
| 443 | HTTPS |
| 465 | SMTPS |
| 514 | syslog |
| 587 | SMTP submission |
| 636 | LDAPS |
| 873 | rsync |
| 993 | IMAPS |
| 995 | POP3S |
| 2049 | NFS |
| 3306 | MySQL |
| 3389 | RDP |
| 5432 | PostgreSQL |
| 5900 | VNC |
| 6379 | Redis |
| 8080 | HTTP alt |

`/etc/services` is the canonical map.

### 7.10 Firewall basics — iptables, nftables

iptables operates on **tables** (filter, nat, mangle, raw, security), each with built-in **chains**.

Default table: `filter`. Chains: `INPUT`, `OUTPUT`, `FORWARD`.

```bash
iptables -L -n -v
iptables -t nat -L -n -v
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -P INPUT DROP
iptables -D INPUT 5
iptables -F
iptables -X
iptables -N MYCHAIN
iptables-save > /etc/iptables/rules.v4
iptables-restore < /etc/iptables/rules.v4
```

Targets: `ACCEPT`, `DROP`, `REJECT`, `LOG`, `MASQUERADE`, `SNAT`, `DNAT`, `RETURN`. (Deep dive in Chapter 13.)

nftables (modern):

```bash
nft list ruleset
nft add table inet filter
nft add chain inet filter input '{ type filter hook input priority 0; policy drop; }'
nft add rule inet filter input tcp dport 22 accept
```

**Exercises**
- *Exercise 1:* Configure eth0 with a static address using only `ip` for this boot.
- *Exercise 2:* Use `ss` to list all listening TCP ports and the owning process.

**Mock Exam Questions**

**Q1.** Which file contains the static host-to-IP map consulted *before* DNS?
- A) `/etc/dns`  B) `/etc/hosts`  C) `/etc/resolv.conf`  D) `/etc/nsswitch.conf`

**A:** **B.** Order is decided by `nsswitch.conf`, but `hosts:` typically lists `files dns`.

**Q2.** Which command adds an IP without removing existing ones?
- A) `ifconfig eth0 192.168.1.10/24`
- B) `ip addr add 192.168.1.10/24 dev eth0`
- C) `ip addr replace 192.168.1.10/24 dev eth0`
- D) `ip link set eth0 ip 192.168.1.10/24`

**A:** **B.**

**Q3 (Scenario).** A new VM cannot resolve names but can ping IPs. Where do you investigate?

**A:** `/etc/resolv.conf`, `/etc/nsswitch.conf` (should include `dns`), and firewall (port 53). `getent hosts example.com` shows what nsswitch returns.

**Q4.** Which command shows TCP listening sockets including the process names?
- A) `ss -tln`  B) `ss -tlnp`  C) `netstat -tln`  D) `tcpdump`

**A:** **B.** `-p` adds processes (root for full info).

---

## Chapter 8: System Logging & Time

### 8.1 syslog and rsyslog

Facilities: `auth`, `authpriv`, `cron`, `daemon`, `kern`, `lpr`, `mail`, `news`, `syslog`, `user`, `uucp`, `local0`..`local7`.

Priorities (severity), most → least urgent: `emerg`, `alert`, `crit`, `err`, `warning`, `notice`, `info`, `debug`.

Selector form: `FACILITY.PRIORITY`. Comparators: `*` (all), `=` (exact only), `!` (negate).

`/etc/rsyslog.conf` (and `/etc/rsyslog.d/*.conf`):

```
*.info;mail.none;authpriv.none;cron.none       /var/log/messages
authpriv.*                                     /var/log/secure
mail.*                                         -/var/log/maillog
cron.*                                         /var/log/cron
*.emerg                                        :omusrmsg:*
local7.*                                       /var/log/boot.log

# Remote:
*.* @logserver.example.com:514                 # UDP (single @)
*.* @@logserver.example.com:514                # TCP (double @@)
```

The leading `-` means "do not fsync each line".

```bash
logger "Hello syslog"
logger -p mail.warning "Test mail warning"
logger -t myapp -i "tagged message with PID"
logger -n logserver.example.com -P 514 "remote"
systemctl restart rsyslog
```

### 8.2 systemd journal — `journalctl`

systemd-journald stores logs in `/run/log/journal/` (volatile) or `/var/log/journal/` (persistent, if directory exists).

| Flag | Meaning |
|---|---|
| `-b` / `-b -1` | Current / previous boot |
| `--list-boots` | List recent boots |
| `-k` | Kernel only |
| `-u UNIT` | One unit |
| `-p PRI` | Priority filter |
| `--since`/`--until` | Time range |
| `-f` | Follow |
| `-r` | Reverse |
| `-n N` | Last N lines |
| `-o json|verbose|short-iso` | Format |
| `--disk-usage` | Total size |
| `--vacuum-size=` / `--vacuum-time=` | Trim |
| `_PID=` `_UID=` `_COMM=` | Field matches |

```bash
journalctl -u sshd --since today
journalctl -u nginx -f
journalctl -p err -b
journalctl _PID=1234
journalctl --since "2 hours ago" --until "1 hour ago"
journalctl --list-boots
```

Persistent journal:

```bash
mkdir -p /var/log/journal
systemd-tmpfiles --create --prefix /var/log/journal
systemctl restart systemd-journald
```

Configuration: `/etc/systemd/journald.conf`. Key options: `Storage=`, `SystemMaxUse=`, `MaxFileSec=`, `ForwardToSyslog=`.

### 8.3 `logrotate`

| Directive | Meaning |
|---|---|
| `daily`/`weekly`/`monthly`/`yearly` | How often |
| `size 10M` | Rotate when size reached |
| `rotate N` | Keep N old |
| `compress` / `nocompress` | gzip old logs |
| `delaycompress` | Compress one cycle later |
| `missingok` | Don't error if missing |
| `notifempty` | Skip empty logs |
| `create MODE OWNER GROUP` | New empty log |
| `copytruncate` | For apps holding the fd |
| `dateext` | Use date in filename |
| `sharedscripts` | Run postrotate once per block |
| `prerotate/postrotate ... endscript` | Hook scripts |

```
/var/log/myapp/*.log {
    daily
    rotate 14
    compress
    delaycompress
    notifempty
    missingok
    create 0640 myapp adm
    sharedscripts
    postrotate
        systemctl reload myapp >/dev/null 2>&1 || true
    endscript
}
```

```bash
logrotate -d /etc/logrotate.conf       # dry run, verbose
logrotate -f /etc/logrotate.conf       # force, ignoring schedule
```

### 8.4 NTP — Time Sync

#### `chronyd`

`chronyd` continuously estimates clock drift and disciplines the system clock using configured sources; `chronyc` queries/controls the daemon. Use `tracking` to judge local synchronization and error estimates, `sources -v` to see selection/reachability, and `sourcestats` to inspect measurement quality. A reachable source is not necessarily the selected source, and stepping a clock can disrupt applications—use `makestep` only under the configured/approved policy.

```
pool 2.pool.ntp.org iburst
makestep 1.0 3
rtcsync
```

```bash
chronyc tracking
chronyc sources -v
chronyc sourcestats
chronyc makestep
systemctl enable --now chronyd
```

#### `ntpd` (legacy)

`ntpd` implements the classic NTP daemon and remains exam-relevant. `ntpq -p` shows peers, selection markers, reach and delay/offset/jitter. Large offsets, zero reach, firewall issues on UDP/123, DNS, and bad upstream strata are different failure classes. Do not run multiple time-disciplining daemons against the same system clock.

```
server 0.pool.ntp.org iburst
driftfile /var/lib/ntp/drift
```

```bash
ntpq -p
ntpdate -u pool.ntp.org
```

#### `timedatectl`

`timedatectl` presents system clock, RTC, timezone and systemd time-sync state. It is a management/status interface, not proof that a particular daemon has converged; follow it with `chronyc tracking` or the daemon-specific query. Changing timezone alters display/civil-time interpretation, while changing the system clock alters the underlying time seen by applications.

```bash
timedatectl
timedatectl set-timezone Europe/Berlin
timedatectl set-time "2026-06-11 12:00:00"
timedatectl set-ntp true
timedatectl list-timezones
```

### 8.5 Hardware clock vs system clock

```bash
date
date -u
date '+%F %T'
date --set='2026-06-11 12:00:00'
date -d '2 days ago' +%F
date -d @1700000000
hwclock
hwclock --systohc
hwclock --hctosys
hwclock --utc --systohc
hwclock --localtime --systohc
```

**TRAP:** On dual-boot with Windows, Linux defaults to UTC RTC while Windows expects local time. Fix with `timedatectl set-local-rtc 1` or change Windows.

**Exercises**
- *Exercise 1:* Configure rsyslog to forward `auth.*` over TCP 5140 to `central.example.com`.
- *Exercise 2:* Build a logrotate config for `/var/log/myapp/access.log`, daily, 30 kept, compressed, copytruncate.

**Mock Exam Questions**

**Q1.** Which priority is most severe?
- A) `crit`  B) `alert`  C) `emerg`  D) `err`

**A:** **C.**

**Q2.** In rsyslog syntax `mail.*  -/var/log/maillog`, what does the leading `-` mean?
- A) Ignore matches
- B) Negate the selector
- C) Don't fsync each write
- D) Send to a remote host

**A:** **C.**

**Q3 (Scenario).** `journalctl -b -1` returns "no persistent journal was found". Why?

**A:** The journal is volatile. Create `/var/log/journal/` and restart journald to persist logs across boots.

**Q4.** Which command tells the RTC to be UTC?
- A) `timedatectl set-local-rtc 0`
- B) `hwclock --localtime`
- C) `date -u`
- D) `ntpdate -u`

**A:** **A.**

---

## Chapter 9: SSH & Basic Security

### 9.1 SSH Protocol — How It Works

SSHv2 handshake:
1. TCP to port 22.
2. Version banner exchange.
3. Key exchange (DH/curve25519/ECDH) → shared secret.
4. Server signs the KEX hash with host private key; client verifies against `known_hosts`.
5. Symmetric encryption activated.
6. User authentication: publickey, password, GSSAPI, keyboard-interactive.
7. Channels: exec, sftp, port-forward.

### 9.2 `ssh`, `scp`, `sftp`

```bash
ssh user@host
ssh -p 2222 host
ssh -i ~/.ssh/id_ed25519 host
ssh -X host                    # X11 forwarding
ssh -Y host                    # trusted X11
ssh -A host                    # agent forwarding
ssh -t host 'sudo cmd'         # force TTY
ssh -N -L 8080:internal:80 jumphost
ssh -J jump host               # ProxyJump
ssh -o StrictHostKeyChecking=accept-new host
ssh -vvv host                  # debug
ssh -q host cmd                # quiet

scp file user@host:/tmp/
scp -r dir user@host:/tmp/
scp -P 2222 -i key file host:/tmp/
scp user@host1:/file user@host2:/file
scp -3 src dst                  # tunnel via local host

sftp user@host
# inside: ls, cd, lcd, get, put, mget, mput, rm, mkdir
sftp -i key -P 2222 user@host
```

### 9.3 SSH Key Management

```bash
ssh-keygen -t ed25519 -C "alice@laptop"
ssh-keygen -t rsa -b 4096
ssh-keygen -p -f ~/.ssh/id_ed25519           # change passphrase
ssh-keygen -y -f ~/.ssh/id_ed25519           # extract public key
ssh-keygen -lf ~/.ssh/id_ed25519.pub         # fingerprint
ssh-keygen -F host                            # check known_hosts entry
ssh-keygen -R host                            # remove a known_hosts entry
ssh-keygen -E sha256 -lf key.pub

ssh-copy-id user@host
ssh-copy-id -i ~/.ssh/id_ed25519.pub -p 2222 user@host
```

Key types: **ed25519** preferred (small, fast). **rsa** ≥ 3072 acceptable. **ecdsa** OK. **dsa** obsolete.

Files (under `~/.ssh/`):

| File | Purpose | Perms |
|---|---|---|
| `id_*` | Private key | 600 |
| `id_*.pub` | Public key | 644 |
| `authorized_keys` | Server: allowed public keys | 600 |
| `known_hosts` | Client: trusted server keys | 644 |
| `config` | Client per-host config | 600 |

`~/.ssh/` directory must be 700.

#### `~/.ssh/config`

```
Host *
    ServerAliveInterval 60
    ControlMaster auto
    ControlPath ~/.ssh/cm-%r@%h:%p
    ControlPersist 10m
    HashKnownHosts yes

Host bastion
    HostName bastion.example.com
    User alice
    IdentityFile ~/.ssh/keys/bastion

Host *.internal
    ProxyJump bastion
    User admin
```

#### `authorized_keys` line options

```
command="/usr/bin/rsync --server",no-pty,no-agent-forwarding,no-port-forwarding ssh-ed25519 AAAA... rsync-only
from="10.0.0.0/8" ssh-ed25519 AAAA... internal-only
```

### 9.4 `sshd_config` — Key Directives

`/etc/ssh/sshd_config`:

| Directive | Recommended |
|---|---|
| `Port` | 22 or custom |
| `ListenAddress` | Optional bind IP |
| `PermitRootLogin` | `no` or `prohibit-password` |
| `PasswordAuthentication` | `no` (once keys work) |
| `PubkeyAuthentication` | `yes` |
| `AuthorizedKeysFile` | `.ssh/authorized_keys` |
| `ChallengeResponseAuthentication` | `no` |
| `UsePAM` | `yes` |
| `PermitEmptyPasswords` | `no` |
| `X11Forwarding` | `yes` if needed |
| `AllowAgentForwarding` | `no` unless required |
| `AllowTcpForwarding` | restrict for tunnels |
| `ClientAliveInterval`/`ClientAliveCountMax` | Keepalive |
| `AllowUsers` / `DenyUsers` | Per-user |
| `AllowGroups` / `DenyGroups` | Per-group |
| `Match User alice` | Conditional block |
| `Banner` | `/etc/issue.net` |
| `Subsystem sftp` | `internal-sftp` |
| `LoginGraceTime` | `30` |
| `MaxAuthTries` | `3` |
| `MaxSessions` | `5` |

```bash
sshd -t                  # test config
sshd -T                  # dump effective config
systemctl restart sshd
```

### 9.5 SSH Tunneling

#### Local forwarding (`-L`)

Local forwarding makes the SSH client listen locally and asks the SSH server side to connect to a destination. Use it to reach a remote/internal service through the SSH host: traffic to the local listening port is encrypted only across the SSH segment. Bind to loopback unless other local-network clients intentionally need access, and remember destination authorization/firewalls are evaluated from the server side.

```
ssh -L LPORT:RHOST:RPORT user@sshserver
```

Listen on client at LPORT; tunnel to RHOST:RPORT as seen from the server.

```bash
ssh -L 8080:localhost:80 jumphost
ssh -L 5432:db.internal:5432 user@bastion
```

#### Remote forwarding (`-R`)

Remote forwarding makes the SSH server listen and sends accepted traffic back through the tunnel to a destination reachable from the client side. Use it to expose a client-side service to the remote environment. Server `GatewayPorts` controls non-loopback exposure; an accidental wildcard bind can publish a private service, so verify with `ss` on the remote host.

```
ssh -R RPORT:LHOST:LPORT user@sshserver
```

Listen on server at RPORT; tunnel to LHOST:LPORT as seen from the client.

```bash
ssh -R 8080:localhost:80 user@public.example.com
```

For other interfaces on the server, `sshd_config` needs `GatewayPorts yes`.

#### Dynamic forwarding (`-D`) — SOCKS5

Dynamic forwarding creates a local SOCKS proxy; each SOCKS-aware application chooses destinations through the SSH connection. It is not a host-wide VPN and DNS may still leak locally unless the application proxies name resolution. Use it for flexible application traffic, then verify both route perspective and DNS behavior.

```
ssh -D 1080 user@host
ssh -D 1080 -N -f user@host
curl --socks5 localhost:1080 https://example.com
```

#### Combined

```
ssh -L 8080:internal:80 -R 9090:localhost:9090 -D 1080 -N user@host
```

### 9.6 GPG

```bash
gpg --full-generate-key
gpg --gen-key
gpg --list-keys
gpg --list-secret-keys
gpg --fingerprint USER@example.com
gpg --export -a USER > pub.asc
gpg --export-secret-keys -a USER > sec.asc
gpg --import pub.asc

gpg -c file                          # symmetric (password)
gpg -e -r recipient file             # asymmetric encrypt
gpg -d file.gpg > file               # decrypt
gpg --sign file                      # binary signature
gpg --clearsign file                 # signed text (readable)
gpg --detach-sign file               # signature in separate .sig

gpg --send-keys KEYID --keyserver hkps://keys.openpgp.org
gpg --recv-keys KEYID
gpg --refresh-keys

gpg --edit-key KEYID                 # interactive trust/sign/expire
```

### 9.7 File Integrity

```bash
md5sum file > file.md5
md5sum -c file.md5
sha256sum file > file.sha256
sha256sum -c file.sha256
sha512sum file > file.sha512
```

Avoid MD5 for security. Use SHA-256 or SHA-512.

### 9.8 TCP Wrappers — `/etc/hosts.allow`, `/etc/hosts.deny` (legacy/exam context)

Order: allow checked first. Match-and-allow stops. If neither matches, access is granted.

```
# /etc/hosts.allow
sshd: 192.168.1.0/24 .trusted.example.com
vsftpd: ALL

# /etc/hosts.deny
ALL: ALL
```

**TRAP:** Modern OpenSSH ≥ 6.7 dropped libwrap, so TCP wrappers no longer affect SSH on some distros. Exam may still ask the format.

**Exercises**
- *Exercise 1:* Configure SSH so only members of `wheel` may log in, password auth disabled, root cannot log in directly.
- *Exercise 2:* Tunnel a remote MySQL at `db.internal:3306` to local 3307 via `bastion`.

**Mock Exam Questions**

**Q1.** Default permissions on `~/.ssh/authorized_keys` must be:
- A) `0644`  B) `0600`  C) `0755`  D) `0640`

**A:** **B.** OpenSSH rejects loose permissions for safety.

**Q2.** Which option forwards a local TCP port through SSH to a remote target?
- A) `-L`  B) `-R`  C) `-D`  D) `-N`

**A:** **A.** `-L LPORT:RHOST:RPORT`.

**Q3.** Which file does the *server* use to store authorized user public keys?
- A) `known_hosts`  B) `authorized_keys`  C) `ssh_host_*_key`  D) `ssh_config`

**A:** **B.** `authorized_keys` per user. `known_hosts` is on the client.

**Q4 (Scenario).** ssh warns `REMOTE HOST IDENTIFICATION HAS CHANGED!`. Safest action?

**A:** Stop, suspect MITM. If you legitimately re-keyed the server, `ssh-keygen -R host`, reconnect, and verify the new fingerprint out-of-band.

**Q5.** Which SSH option creates a SOCKS5 proxy?
- A) `-L`  B) `-D`  C) `-R`  D) `-T`

**A:** **B.** Dynamic forwarding (`-D`) opens a local SOCKS5 proxy that the SSH server then relays to anywhere reachable.

---

# PART 2 — LPIC-2 (Exams 201 + 202)

---

## Chapter 10: Linux Kernel

### 10.1 Version Naming

The Linux kernel follows `MAJOR.MINOR.PATCH[-LOCALVERSION]` (e.g., `6.6.32-generic`).

- `MAJOR.MINOR` — release series. After 3.x the MAJOR is bumped semi-arbitrarily; "stable" branches exist per series.
- `PATCH` — bugfix release within series.
- `LOCALVERSION` (after `-`) — distribution string from `CONFIG_LOCALVERSION` and `extraversion`.

Sources: `kernel.org` distributes `linux-X.Y.tar.xz`. Stable tarballs are signed.

```bash
uname -r                    # 6.6.32-generic
uname -a                    # everything
cat /proc/version           # version, gcc, build date
```

### 10.2 Building from Source

```bash
cd /usr/src
tar -xJf linux-6.6.32.tar.xz
cd linux-6.6.32

# Start from running kernel's config:
cp /boot/config-$(uname -r) .config
make oldconfig                  # answer prompts for new options
# Or interactive:
make menuconfig                 # ncurses
make nconfig                    # newer ncurses
make xconfig                    # Qt
make gconfig                    # GTK
make defconfig                  # use sane defaults

make -j$(nproc)                 # compile kernel + modules
make modules_install            # → /lib/modules/<ver>/
make install                    # copies vmlinuz, system.map, builds initramfs, updates GRUB

make clean                      # remove .o files
make mrproper                   # also remove .config (factory reset)
make help                       # all targets
```

For Debian-style packaging: `make bindeb-pkg` → produces .deb packages in `..`.

`/usr/src/linux` is the conventional symlink. `/lib/modules/<ver>/build` typically points back to it.

### 10.3 `/boot` Contents

| File | Role |
|---|---|
| `vmlinuz-<ver>` | bzImage-format compressed kernel |
| `initrd.img-<ver>` or `initramfs-<ver>.img` | Initial RAM filesystem |
| `System.map-<ver>` | Symbol → address (debugging) |
| `config-<ver>` | The `.config` used to build this kernel |
| `grub/` or `efi/EFI/<distro>/` | Bootloader |

### 10.4 Kernel Modules

```bash
lsmod                              # currently loaded
lsmod | grep nvme
modinfo nvme                       # dependencies, parameters, license
modinfo -p nvme                    # only parameters
modprobe nvme                      # load (resolves deps)
modprobe -r nvme                   # unload (and unused deps)
modprobe -c | less                 # show effective config
modprobe -n -v nvme                # dry run
insmod /path/to/foo.ko             # raw load (no dep resolution)
rmmod foo                          # raw unload
depmod -a                          # rebuild modules.dep
```

`/etc/modprobe.d/*.conf`:

```
# Blacklist a driver
blacklist nouveau

# Pass parameters
options snd_hda_intel power_save=1 power_save_controller=Y

# Define a useful alias
alias eth0 e1000e

# Disable load entirely (even on demand)
install nouveau /bin/true
```

After changes, regenerate initramfs if module load happens early:

```bash
update-initramfs -u            # Debian/Ubuntu
dracut -f                       # RHEL/Fedora
```

`/etc/modules-load.d/*.conf` lists modules to load at boot (one per line). `/etc/modules` does the same on Debian.

### 10.5 initramfs / initrd

The kernel must mount root, but it may need drivers (RAID, LVM, NVMe, encryption) loaded first. The bootloader loads an **initramfs** — a cpio archive of a minimal root with `/init`. The kernel unpacks it into a tmpfs and runs `/init`, which loads modules, decrypts/assembles, then `switch_root` to the real root.

Debian/Ubuntu uses `initramfs-tools`:

```bash
update-initramfs -u                    # update current kernel's initramfs
update-initramfs -u -k 6.6.32-generic
update-initramfs -c -k all             # create for all installed kernels
lsinitramfs /boot/initrd.img-$(uname -r) | head
unmkinitramfs /boot/initrd.img /tmp/x
```

RHEL/Fedora uses `dracut`:

```bash
dracut -f                              # force regenerate
dracut -f -v /boot/initramfs-6.6.32.img 6.6.32
dracut --list-modules
lsinitrd /boot/initramfs-$(uname -r).img
```

### 10.6 Kernel Parameters — `sysctl`

`/proc/sys/<group>/...` exposes runtime knobs. `sysctl` is the manipulating tool.

```bash
sysctl -a                                  # everything
sysctl -a | grep ip_forward
sysctl net.ipv4.ip_forward                 # show
sysctl -w net.ipv4.ip_forward=1            # set for this boot
sysctl -p                                  # reload /etc/sysctl.conf and /etc/sysctl.d/
sysctl --system                            # apply all sysctl.d snippets
```

Persistent: edit `/etc/sysctl.conf` or drop a file in `/etc/sysctl.d/99-local.conf`:

```
net.ipv4.ip_forward=1
net.ipv4.conf.all.rp_filter=1
vm.swappiness=10
fs.file-max=2097152
kernel.sysrq=1
```

Common tunables to know:

| Key | Use |
|---|---|
| `net.ipv4.ip_forward` | Enable IPv4 routing |
| `net.ipv6.conf.all.forwarding` | Enable IPv6 routing |
| `net.ipv4.conf.all.rp_filter` | Reverse-path filtering |
| `net.ipv4.tcp_syncookies` | SYN-flood protection |
| `net.ipv4.icmp_echo_ignore_broadcasts` | Ignore broadcast pings |
| `vm.swappiness` | RAM/swap tradeoff (0–100) |
| `vm.overcommit_memory` | malloc strategy |
| `fs.file-max` | System-wide max open files |
| `kernel.pid_max` | Max PID |
| `kernel.sysrq` | Enable magic SysRq |

### 10.7 sysfs and udev in depth

(See Chapter 4 for udev rule syntax.) Key extra knowledge for LPIC-2:

- `udevadm info -a -p $(udevadm info -q path -n /dev/sda)` walks the sysfs chain — copy `ATTRS{...}` values into your rule.
- `udevadm trigger --action=add` re-issues events without unplug.
- `RUN+=` actions are short-lived; long programs must be daemonized via systemd.

**Exercises**
- *Exercise 1:* Identify whether the running kernel was built with `CONFIG_PREEMPT_RT` by reading `/boot/config-$(uname -r)`.
- *Exercise 2:* Set `vm.swappiness=10` persistently using a sysctl.d snippet.

**Mock Exam Questions**

**Q1.** Which command rebuilds the module dependency information?
- A) `modprobe -d`  B) `depmod -a`  C) `update-modules`  D) `dracut -f`

**A:** **B.** `depmod -a` updates `/lib/modules/<ver>/modules.dep`.

**Q2.** Where is the kernel's runtime configuration exposed?
- A) `/etc/proc/sys`  B) `/sys/proc/`  C) `/proc/sys/`  D) `/dev/kmem`

**A:** **C.**

**Q3 (Scenario).** A new SATA controller's driver only loads on demand and the system can't see the root disk at boot. Fix?

**A:** Add the module to the initramfs. Either `echo MODULE_NAME >> /etc/initramfs-tools/modules` (Debian) or `echo 'add_drivers+=" MODULE_NAME "' > /etc/dracut.conf.d/storage.conf` (RHEL), then regenerate the initramfs.

---

## Chapter 11: System Startup & Recovery

### 11.1 systemd unit files in depth

A unit file is INI-style with sections: `[Unit]`, `[Service]`/`[Socket]`/`[Mount]`/`[Timer]`/`[Path]`/`[Target]`, and `[Install]`.

Unit lookup directories (lowest → highest precedence):
1. `/usr/lib/systemd/system/` — packaged
2. `/etc/systemd/system/` — admin overrides
3. `/run/systemd/system/` — runtime

#### `[Unit]` directives

| Key | Meaning |
|---|---|
| `Description=` | Free text |
| `Documentation=` | URLs / man pages |
| `Requires=` | Hard dep; failure of dep stops this |
| `Wants=` | Soft dep |
| `Requisite=` | Like Requires but does NOT start it |
| `After=` / `Before=` | Ordering only |
| `Conflicts=` | Stop the other |
| `ConditionPathExists=` | Run only if path exists |

#### `[Service]` directives

| Key | Meaning |
|---|---|
| `Type=` | simple, exec, forking, oneshot, notify, dbus, idle |
| `ExecStart=` | Command |
| `ExecStartPre=` / `ExecStartPost=` | Hooks |
| `ExecReload=` | What `reload` does |
| `ExecStop=` | What `stop` runs |
| `Restart=` | no, on-success, on-failure, on-abort, always, on-watchdog |
| `RestartSec=` | Delay before restart |
| `User=` / `Group=` | Drop privs |
| `WorkingDirectory=` | cwd |
| `Environment=` `EnvironmentFile=` | Env |
| `PIDFile=` | For `Type=forking` |
| `RemainAfterExit=` | For `Type=oneshot` keep "active" |
| `StandardOutput=` `StandardError=` | journal, syslog, file, null |
| `TimeoutStartSec=` `TimeoutStopSec=` | Timeouts |
| `KillMode=` | control-group, mixed, process, none |
| `LimitNOFILE=` etc. | rlimits |
| `Nice=` | Niceness |
| `PrivateTmp=` | Per-unit /tmp |
| `ProtectSystem=` | strict, full, true |
| `NoNewPrivileges=` | Prevent setuid escalation |

#### `[Install]`

| Key | Meaning |
|---|---|
| `WantedBy=` | Where this unit is enabled (multi-user.target.wants/) |
| `RequiredBy=` | Stronger dep |
| `Also=` | Co-enable these |
| `Alias=` | Symlink to this name |

#### Example service

```ini
[Unit]
Description=My App
After=network-online.target
Requires=network-online.target

[Service]
Type=simple
User=myapp
Group=myapp
WorkingDirectory=/var/lib/myapp
EnvironmentFile=/etc/default/myapp
ExecStart=/usr/local/bin/myapp --config /etc/myapp.conf
Restart=on-failure
RestartSec=5
StandardOutput=journal
StandardError=journal
PrivateTmp=true
NoNewPrivileges=true

[Install]
WantedBy=multi-user.target
```

Save as `/etc/systemd/system/myapp.service`, then:

```bash
systemctl daemon-reload
systemctl enable --now myapp
journalctl -u myapp -f
```

### 11.2 systemd timers (cron alternative)

A `.timer` unit triggers a same-named `.service`.

`/etc/systemd/system/backup.timer`:

```ini
[Unit]
Description=Daily backup

[Timer]
OnCalendar=daily
Persistent=true
RandomizedDelaySec=30m

[Install]
WantedBy=timers.target
```

`OnCalendar=` syntax: `*-*-* HH:MM:SS`, `daily`, `weekly`, `Mon..Fri *-*-* 09:00`, etc. Check with `systemd-analyze calendar daily`.

Other timer keys:

| Key | Meaning |
|---|---|
| `OnBootSec=` | Time after boot |
| `OnStartupSec=` | Time after systemd start |
| `OnActiveSec=` | Relative to enable |
| `OnUnitActiveSec=` | After last activation |
| `OnUnitInactiveSec=` | After last inactivation |
| `AccuracySec=` | Coalescing window |
| `Persistent=true` | If missed (system off), run at next boot |

```bash
systemctl list-timers --all
systemctl start backup.timer
systemd-analyze calendar "*-*-* 02:30"
```

#### Timers vs cron

| | cron | systemd timer |
|---|---|---|
| Lives in | `/etc/cron*`, `crontab -e` | `.timer` + `.service` units |
| Logs | mail / syslog | journal |
| Missed runs | lost (anacron handles) | `Persistent=true` |
| Granularity | minute | sub-second possible |

### 11.3 SysVinit Scripts (still on exam)

`/etc/init.d/<service>` shell scripts with LSB headers:

```bash
#!/bin/sh
### BEGIN INIT INFO
# Provides:          myservice
# Required-Start:    $network $local_fs
# Required-Stop:     $network $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: My Service
### END INIT INFO
case "$1" in
    start) ... ;;
    stop) ... ;;
    restart) ... ;;
    status) ... ;;
esac
```

Run levels and `/etc/rc.d/rcN.d/` (or `/etc/rcN.d/`) contain symlinks `Sxxname` (start) and `Kxxname` (kill).

```bash
service myservice start             # Debian/RHEL wrapper
/etc/init.d/myservice start         # direct
chkconfig --list                    # RHEL
chkconfig myservice on              # enable at runlevels 2-5
chkconfig --level 35 myservice on
chkconfig --level 0123456 myservice off

update-rc.d myservice defaults      # Debian
update-rc.d myservice remove
update-rc.d -f myservice remove     # force
```

### 11.4 GRUB Rescue, Single-User, Emergency Boot

At GRUB menu press `e` to edit:

| Edit to | Effect |
|---|---|
| Append `single` or `1` | Single user (legacy SysV) |
| Append `systemd.unit=rescue.target` | systemd rescue |
| Append `systemd.unit=emergency.target` | emergency (only /, RO) |
| Append `init=/bin/bash` with `rw` | Pure shell, no init |

Press `Ctrl+X` to boot.

GRUB rescue prompt (if config is missing):

```
grub rescue> ls
grub rescue> ls (hd0,gpt2)/
grub rescue> set root=(hd0,gpt2)
grub rescue> set prefix=(hd0,gpt2)/boot/grub
grub rescue> insmod normal
grub rescue> normal
```

Then once booted, repair: `grub-install /dev/sda` (BIOS) or with `--efi-directory` (UEFI), `update-grub`.

### 11.5 Kernel Panic Troubleshooting

When the kernel panics, it freezes (or reboots if `panic=N` set). Steps:

1. Capture screen with phone or kdump.
2. Look at last lines for "Call Trace:" — note the addresses.
3. Match symbols using `System.map-<ver>`.
4. Reproduce by booting an older kernel from GRUB.
5. Common causes: bad memory (run memtest86+), failed disk, wrong root= in cmdline, missing initramfs module.

```
panic=10                         # auto-reboot after 10s on panic
oops=panic                       # treat oops as panic
```

### 11.6 fsck on Boot

`/etc/fstab` field 6 (`<pass>`):
- 0 — skip
- 1 — root, checked first
- 2 — other filesystems, parallel

Force fsck at next boot:

```bash
touch /forcefsck                            # legacy systemd ignores
fsck.mode=force fsck.repair=yes (cmdline)   # systemd-fsck
shutdown -F -r now                          # SysV
```

`tune2fs -c 30 /dev/sdb1` sets max-mount-count between forced checks.

**Exercises**
- *Exercise 1:* Write a `.service` + `.timer` pair that runs `/usr/local/bin/cleanup` every Sunday at 04:00 and re-runs if missed.
- *Exercise 2:* Recover from a forgotten root password using GRUB.

**Mock Exam Questions**

**Q1.** Which `[Service]` type expects the program to fork and exit immediately, leaving a child running?
- A) simple  B) forking  C) oneshot  D) notify

**A:** **B.** `forking` plus a `PIDFile=` was the historic daemon pattern.

**Q2.** Which directive enables a unit to run at next boot if the system was off when the schedule fired?
- A) `OnBootSec=`  B) `RandomizedDelaySec=`  C) `Persistent=true`  D) `AccuracySec=`

**A:** **C.**

**Q3 (Scenario).** A `.service` file edit isn't taking effect. Why?

**A:** systemd caches unit files; you must `systemctl daemon-reload` after edits. (And restart the unit for new ExecStart to take effect.)

**Q4.** Which target gives a minimal single-user-style environment with networking and most filesystems?
- A) `rescue.target`  B) `emergency.target`  C) `multi-user.target`  D) `graphical.target`

**A:** **A.** Rescue mounts local filesystems and offers a root shell; emergency is more bare.

---

## Chapter 12: Storage — RAID, LVM, Filesystems

### 12.1 Software RAID with `mdadm`

RAID levels:

| Level | Min disks | Capacity | Fault tolerance | Use case |
|---|---|---|---|---|
| 0 | 2 | n × min | 0 | Performance only |
| 1 | 2 | min | n−1 | Reliability |
| 5 | 3 | (n−1) × min | 1 | Capacity + redundancy |
| 6 | 4 | (n−2) × min | 2 | Large arrays |
| 10 | 4 | (n/2) × min | 1+ (depends on layout) | Performance + redundancy |

#### Create

`mdadm --create` writes RAID metadata and begins constructing a new array from member devices. It is destructive to existing signatures/data, so confirm every member with `lsblk`, `wipefs -n`, persistent IDs, and backups before execution. RAID level determines capacity, fault tolerance, write behavior, and minimum devices; RAID is availability against selected device failures, not a backup against deletion, corruption, theft, or site loss.

```bash
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm --create /dev/md1 --level=5 --raid-devices=3 --spare-devices=1 \
       /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

Common flags: `-l LEVEL`, `-n COUNT`, `-x SPARES`, `-c CHUNK` (default 512K), `-e VERSION` (metadata version 0.90/1.0/1.1/1.2; default 1.2), `--name=`.

#### Watch / verify

`/proc/mdstat` gives the kernel's compact live array/resync view; `mdadm --detail` explains array state and member roles; `--examine` reads RAID metadata from one candidate member even when the array is not assembled. Use them together: the array view answers “is service degraded/resyncing?” and member metadata answers “does this device belong here?” A resync percentage alone does not prove application data correctness.

```bash
cat /proc/mdstat                # status, sync progress
mdadm --detail /dev/md0
mdadm --examine /dev/sdb1       # superblock info on a member
watch -n1 cat /proc/mdstat
```

#### Persist configuration

```bash
mdadm --detail --scan >> /etc/mdadm/mdadm.conf       # Debian
mdadm --detail --scan >> /etc/mdadm.conf             # RHEL
update-initramfs -u
```

#### Manage members

Member replacement is an ordered state transition: mark a known-bad active member failed, remove it, add the verified replacement, and monitor rebuild to completion. Never fail the wrong member in an already-degraded array. `--grow` changes geometry and can run for a long time; maintain backups, power stability and monitoring. `--zero-superblock` erases membership metadata and should be used only after confirming the device is no longer needed by any array.

```bash
mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md0 --remove /dev/sdb1
mdadm --manage /dev/md0 --add /dev/sdf1
mdadm --grow /dev/md0 --raid-devices=4
mdadm --stop /dev/md0
mdadm --assemble --scan                # reassemble at boot
mdadm --zero-superblock /dev/sdb1      # wipe metadata before reuse
```

#### Monitor

```bash
mdadm --monitor --daemonise --mail root@localhost
```

`/etc/mdadm/mdadm.conf` directives: `MAILADDR`, `PROGRAM`, `AUTO`, `ARRAY ... metadata=1.2 UUID=...`.

### 12.2 LVM — Logical Volume Manager

Layered abstraction: **Physical Volume (PV)** → **Volume Group (VG)** → **Logical Volume (LV)**.

```
+-----+ +-----+ +-----+
| PV1 | | PV2 | | PV3 |     ← block devices (partitions or whole disks)
+--+--+ +--+--+ +--+--+
    \      |      /
     \     |     /
      +----v----+
      |   VG1   |             ← pool of extents from PVs
      +----+----+
           |
   +---+---+---+
   | LV| LV| LV|              ← carved-out logical volumes
   +---+---+---+
```

#### PVs

A Physical Volume places LVM metadata on a block device and divides usable space into physical extents. `pvcreate` prepares it for LVM and may overwrite signatures; `pvs`/`pvdisplay` query allocation; `pvmove` relocates allocated extents while the VG remains active so a device can be removed safely. `pvremove` removes LVM metadata—it is not the first step for a PV still holding live extents.

```bash
pvcreate /dev/sdb1                   # mark as a PV
pvcreate /dev/sdb /dev/sdc           # whole disks fine
pvs                                  # one-line per PV
pvdisplay                            # detailed
pvdisplay /dev/sdb1
pvscan
pvremove /dev/sdb1                   # erase metadata
pvmove /dev/sdb1                     # move extents off this PV (before remove from VG)
pvmove /dev/sdb1 /dev/sdc1           # move to a specific PV
```

#### VGs

A Volume Group pools extents from one or more PVs. `vgextend` adds capacity; before `vgreduce`, all allocated extents must be moved away unless data loss is explicitly intended. Activation (`vgchange -ay`) exposes its LVs as device-mapper devices; deactivation requires that filesystems, swap, and other users have released them. Extent size affects allocation granularity and some maximums but cannot be casually changed later.

```bash
vgcreate datavg /dev/sdb1 /dev/sdc1
vgcreate -s 16M datavg /dev/sdb1     # extent size 16 MiB (default 4 MiB)
vgs
vgdisplay datavg
vgextend datavg /dev/sdd1            # add a PV
vgreduce datavg /dev/sdb1            # remove a PV (must be pvmove-d first)
vgrename oldname newname
vgremove datavg
vgchange -an datavg                  # deactivate
vgchange -ay datavg                  # activate
```

#### LVs

A Logical Volume is a virtual block device carved from VG extents. Creating/extending the LV changes block-device capacity but does not automatically create or grow the filesystem unless a helper such as `-r` is used. Always reason about layers in order: underlying storage → PV → VG → LV → encryption/filesystem → mount. Growing is usually online-capable; shrinking is riskier, filesystem-specific, and XFS cannot shrink.

```bash
lvcreate -L 20G -n www datavg                  # by size
lvcreate -l 100%FREE -n data datavg            # use all free extents
lvcreate -l 50%VG -n backup datavg
lvcreate -L 10G --thin -n thinpool datavg      # thin pool
lvcreate -V 100G --thin -n thinvol datavg/thinpool   # thin LV

# Filesystem on top
mkfs.ext4 /dev/datavg/www
mount /dev/datavg/www /var/www

# Resize
lvextend -L +5G /dev/datavg/www
lvextend -l +100%FREE /dev/datavg/www
lvresize -r -L 30G /dev/datavg/www              # -r also resizes FS (online for ext4/xfs grow)

lvreduce -L 10G /dev/datavg/www                 # SHRINK — must shrink FS first (xfs cannot shrink!)
lvremove /dev/datavg/www

lvs
lvdisplay /dev/datavg/www
```

#### Filesystem resize companions

The LV and the filesystem maintain separate size metadata. For growth, enlarge the block device first, then grow the filesystem (`resize2fs` for ext, `xfs_growfs` on the mounted XFS path). For supported ext shrink, shrink the unmounted filesystem first and only then reduce the LV; reversing that order truncates filesystem data. Prefer `lvresize -r` when its fsadm integration supports the exact stack, but still back up and verify.

```bash
resize2fs /dev/datavg/www              # ext2/3/4 (online grow ok)
xfs_growfs /var/www                    # XFS, mountpoint, grow only
btrfs filesystem resize +5G /mnt/btrfs
```

#### Snapshots

An LVM snapshot records the original blocks that change after snapshot creation, providing a point-in-time view of one LV. It is not an independent backup: it shares the origin's storage/failure domain, consumes copy-on-write space, and becomes invalid if that space fills. Use it to create a consistent short-lived backup source after coordinating application/filesystem consistency, then remove it promptly and monitor `Data%`.

A snapshot LV captures the state at creation; original LV continues. Copy-on-write means only changes consume space in the snapshot.

```bash
lvcreate -L 5G -s -n www_snap /dev/datavg/www       # 5G COW area
mount -o ro /dev/datavg/www_snap /mnt/snap
# When done:
umount /mnt/snap
lvremove /dev/datavg/www_snap

# Merge snapshot back (rollback)
lvconvert --merge /dev/datavg/www_snap
```

If a snapshot fills up its allocated space, it becomes invalid. Monitor with `lvs`.

#### Thin provisioning

Thin provisioning presents virtual LVs larger than currently allocated physical storage and assigns blocks on write. It improves flexibility and snapshot efficiency but turns capacity monitoring into a correctness requirement: exhaustion of thin-pool data or metadata can suspend/fail writes across many volumes. Monitor both percentages, configure automatic extension with real free VG space, and do not confuse virtual capacity with guaranteed storage.

```bash
lvcreate -L 100G --thinpool tp datavg
lvcreate -V 50G --thin -n vol1 datavg/tp
lvcreate -V 50G --thin -n vol2 datavg/tp
```

Two 50 GiB thin LVs sharing a 100 GiB pool. Over-allocate carefully.

### 12.3 Swap Management

```bash
mkswap /dev/sdb2                     # format as swap
mkswap -L swap /dev/sdb2
swapon /dev/sdb2                      # enable
swapon --show
swapoff /dev/sdb2

# Swap file:
fallocate -l 2G /swapfile && chmod 600 /swapfile
mkswap /swapfile && swapon /swapfile

# Persistent in /etc/fstab:
UUID=...   none    swap    sw,pri=10   0  0
```

Priority: higher numbers used first; equal priorities are striped.

### 12.4 Disk Encryption — LUKS

LUKS (Linux Unified Key Setup) stores key material in a header on the device; an unlocked LUKS device exposes a mapper at `/dev/mapper/<name>`.

```bash
cryptsetup luksFormat /dev/sdb1                      # initialize, prompts for passphrase
cryptsetup luksFormat --type luks2 /dev/sdb1
cryptsetup luksOpen /dev/sdb1 secret                 # → /dev/mapper/secret
cryptsetup luksClose secret
cryptsetup status secret
cryptsetup luksDump /dev/sdb1
cryptsetup luksAddKey /dev/sdb1
cryptsetup luksRemoveKey /dev/sdb1
cryptsetup luksChangeKey /dev/sdb1
cryptsetup luksHeaderBackup /dev/sdb1 --header-backup-file luks.hdr
cryptsetup luksHeaderRestore /dev/sdb1 --header-backup-file luks.hdr
cryptsetup benchmark
```

Format and mount:

```bash
mkfs.ext4 /dev/mapper/secret
mount /dev/mapper/secret /mnt/secret
```

Auto-unlock at boot — `/etc/crypttab`:

```
# <name>  <device>           <key-file>  <options>
secret    UUID=abcd-...      none        luks
data      /dev/sdc1          /etc/keys/data.key  luks
```

If `<key-file>` is `none`, the user is prompted. Use `/dev/urandom`-generated keyfiles for unattended boot.

### 12.5 iSCSI (Initiator)

iSCSI tunnels SCSI commands over TCP. Server is the **target**, client is the **initiator**.

```bash
yum install iscsi-initiator-utils       # RHEL
apt install open-iscsi                   # Debian

cat /etc/iscsi/initiatorname.iscsi       # IQN, set to unique value

iscsiadm -m discovery -t st -p 192.168.1.50          # discover targets
iscsiadm -m node                                       # list known
iscsiadm -m node -T iqn.2026.com.example:lun0 -p 192.168.1.50 -l   # login
iscsiadm -m session                                    # active sessions
iscsiadm -m node -T ... -p 192.168.1.50 -u            # logout
iscsiadm -m node -T ... -p 192.168.1.50 -o delete     # forget
```

After login the LUN appears as a normal block device (e.g., `/dev/sdb`). Use `lsscsi -i` to identify.

Persistent automatic login: `iscsiadm -m node -T ... -p ... --op update -n node.startup -v automatic`.

For multipath, configure `multipath-tools` (`/etc/multipath.conf`) and the device appears as `/dev/mapper/mpathX`.

**Exercises**
- *Exercise 1:* Build a RAID 1 over two new disks, then convert it to RAID 5 by `--grow`.
- *Exercise 2:* Snapshot an ext4 LV, mount the snapshot read-only, and tar its contents elsewhere.

**Mock Exam Questions**

**Q1.** Which file shows current MD array status and sync progress?
- A) `/proc/mdadm`  B) `/proc/mdstat`  C) `/sys/block/md0/sync_state`  D) `/var/log/mdmon`

**A:** **B.**

**Q2.** Which command grows the *filesystem* on top of an extended LV?
- A) `lvresize -r`  B) `resize2fs` (ext) or `xfs_growfs` (xfs)  C) `mkfs --grow`  D) `growfs`

**A:** Both A and B are correct, but **B** describes the underlying tool. `lvresize -r` is the convenience that calls them.

**Q3 (Scenario).** A snapshot LV shows `100%` data usage in `lvs`. Implications?

**A:** The snapshot becomes invalid — further writes to origin make snapshot inconsistent and unmounted. Either extend with `lvextend` proactively, or remove the snapshot.

**Q4.** Which RAID level provides redundancy and uses parity across all members?
- A) 0  B) 1  C) 5  D) 10

**A:** **C.**

**Q5.** Which file maps LUKS-encrypted devices for boot-time unlocking?
- A) `/etc/fstab`  B) `/etc/crypttab`  C) `/etc/luks.conf`  D) `/etc/cryptsetup.conf`

**A:** **B.**

---

## Chapter 13: Networking Advanced

### 13.1 Policy Routing — Multiple Tables

The kernel has 256 routing tables (numeric IDs). The reserved tables: `local` (255), `main` (254), `default` (253), `unspec` (0). `ip rule` lists routing **rules** that direct lookups to specific tables.

```bash
ip rule                                        # default: 0 from all lookup local; 32766 lookup main; 32767 lookup default
ip rule add from 10.0.0.0/24 table 100 prio 100
ip rule add to 8.8.8.8 table 200 prio 200
ip rule add fwmark 0x1 table 100               # iptables -j MARK can drive choice
ip rule del prio 100
echo '100 vpn' >> /etc/iproute2/rt_tables     # name table 100 "vpn"
ip route add default via 10.8.0.1 table vpn
```

### 13.2 Bonding and Teaming

Bond combines two or more NICs into one logical interface.

Modes (mode= name):

| Num | Name | Behavior |
|---|---|---|
| 0 | balance-rr | Round-robin (needs switch support, link aggregation) |
| 1 | active-backup | One up at a time |
| 2 | balance-xor | Hash-based, needs static LAG |
| 3 | broadcast | All ports send each frame |
| 4 | 802.3ad | LACP — standard link aggregation |
| 5 | balance-tlb | Adaptive transmit only |
| 6 | balance-alb | Adaptive both directions |

```bash
modprobe bonding
ip link add bond0 type bond mode active-backup miimon 100
ip link set eth0 down && ip link set eth0 master bond0
ip link set eth1 down && ip link set eth1 master bond0
ip link set bond0 up
ip addr add 192.168.1.10/24 dev bond0
cat /proc/net/bonding/bond0
```

systemd-networkd or NetworkManager are typical to persist.

Teaming uses `teamd` (userspace). Same concept, JSON config in `/etc/teamd/`. Use `teamdctl bond0 state`.

### 13.3 VLANs (802.1Q)

```bash
ip link add link eth0 name eth0.10 type vlan id 10
ip link set eth0.10 up
ip addr add 192.168.10.5/24 dev eth0.10

# Remove
ip link delete eth0.10
```

Switch port must be configured as trunk allowing VLAN 10. Native VLAN traffic is untagged.

### 13.4 Bridges

Software switch.

```bash
ip link add br0 type bridge
ip link set br0 up
ip link set eth0 master br0
ip link set tap0 master br0
ip addr add 192.168.1.10/24 dev br0
# Old: brctl addbr / addif
brctl show
brctl showmacs br0
bridge link
bridge fdb show
```

Common in VMs (libvirt makes `virbr0`).

### 13.5 iptables Deep Dive

#### Tables

| Table | Purpose | Chains |
|---|---|---|
| `filter` (default) | Accept/drop | INPUT, OUTPUT, FORWARD |
| `nat` | Address translation | PREROUTING, INPUT, OUTPUT, POSTROUTING |
| `mangle` | Modify packets | PREROUTING, INPUT, FORWARD, OUTPUT, POSTROUTING |
| `raw` | Skip conntrack | PREROUTING, OUTPUT |
| `security` | SELinux marking | INPUT, OUTPUT, FORWARD |

#### Packet flow (simplified)

```
incoming → raw/PREROUTING → conntrack → mangle/PRE → nat/PRE (DNAT)
   → routing decision
        → local: mangle/INPUT → filter/INPUT → local process
        → forward: mangle/FORWARD → filter/FORWARD
              → mangle/POST → nat/POST (SNAT/MASQ) → outgoing
outgoing locally: raw/OUTPUT → mangle/OUTPUT → nat/OUTPUT → filter/OUTPUT → mangle/POST → nat/POST
```

#### Common rules

```bash
# Default policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Allow loopback and established
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# SSH and HTTP/HTTPS
iptables -A INPUT -p tcp -m multiport --dports 22,80,443 -j ACCEPT

# Rate-limit SSH brute force
iptables -A INPUT -p tcp --dport 22 -m conntrack --ctstate NEW \
         -m limit --limit 6/min --limit-burst 3 -j ACCEPT

# Log dropped
iptables -A INPUT -m limit --limit 5/min -j LOG --log-prefix "DROP: "

# NAT — masquerade outbound through wan
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 203.0.113.5

# Port forward 80 → internal 8080
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 10.0.0.5:8080
iptables -A FORWARD -p tcp -d 10.0.0.5 --dport 8080 -m conntrack --ctstate NEW -j ACCEPT

# Save/restore
iptables-save > /etc/iptables/rules.v4
iptables-restore < /etc/iptables/rules.v4
ip6tables -L                # IPv6 counterpart
```

Persistence (Debian): `iptables-persistent` package; rules in `/etc/iptables/rules.v4` and `rules.v6`, loaded by `netfilter-persistent`.

### 13.6 nftables

```bash
nft list ruleset
nft add table inet filter
nft 'add chain inet filter input { type filter hook input priority 0 ; policy drop ; }'
nft 'add chain inet filter forward { type filter hook forward priority 0 ; policy drop ; }'
nft 'add chain inet filter output { type filter hook output priority 0 ; policy accept ; }'
nft add rule inet filter input iif lo accept
nft add rule inet filter input ct state established,related accept
nft add rule inet filter input tcp dport { 22, 80, 443 } accept
nft add rule inet filter input log prefix "DROP " limit rate 5/minute
```

Persist: `nft list ruleset > /etc/nftables.conf` and `systemctl enable nftables`.

Migration from iptables: `iptables-translate -A INPUT -p tcp --dport 22 -j ACCEPT`.

### 13.7 PAM in Networking Context

Services like ssh, vsftpd, dovecot consume PAM. Common modules in this context:

- `pam_listfile.so` — restrict to users in a file (`/etc/vsftpd/users.allow`).
- `pam_succeed_if.so` — match conditions (e.g., `user ingroup ftp`).
- `pam_access.so` — `/etc/security/access.conf` rules (`+ : alice : 10.0.0.0/8`).
- `pam_time.so` — `/etc/security/time.conf` time-of-day restrictions.

### 13.8 nsswitch.conf Deep Dive

Sources commonly used:

| Source | Notes |
|---|---|
| `files` | Local files |
| `dns` | Only for `hosts:`, `networks:` |
| `ldap` | via `nss_ldap` |
| `sss` | SSSD (preferred for AD/LDAP) |
| `mdns4_minimal` | Avahi/Bonjour |
| `wins` | NetBIOS name service |
| `nis` | Legacy Network Information Service |

Action tags can override defaults:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns
```

Actions: `success`, `notfound`, `unavail`, `tryagain` → `return`, `continue`, `merge`.

**Exercises**
- *Exercise 1:* Set up policy routing so that 10.0.0.0/24 uses a VPN gateway while everything else uses the default ISP route.
- *Exercise 2:* Build an iptables ruleset for a simple home router with NAT, port-forward for SSH on 2222 → 22 of an internal box, and DROP by default.

**Mock Exam Questions**

**Q1.** Which iptables chain is traversed before routing decisions on packets entering the system?
- A) INPUT  B) PREROUTING  C) FORWARD  D) OUTPUT

**A:** **B.** PREROUTING is the entry point; routing decides INPUT vs FORWARD.

**Q2.** Which bonding mode requires LACP from the switch?
- A) active-backup  B) balance-rr  C) 802.3ad  D) broadcast

**A:** **C.**

**Q3 (Scenario).** Why does `ip rule add table vpn` fail with "Argument 'vpn' is wrong"?

**A:** The name `vpn` isn't defined yet. Add it to `/etc/iproute2/rt_tables` first (`echo "100 vpn" >> /etc/iproute2/rt_tables`), or use the numeric ID directly.

---

## Chapter 14: Backup & Recovery

### 14.1 `tar` Strategies

#### Full backup

```bash
tar -czf /backup/full-$(date +%F).tar.gz \
    --listed-incremental=/backup/full.snar \
    /home /etc
```

The snapshot file (`-g FILE` or `--listed-incremental=FILE`) records inode metadata. An *empty* snapshot file makes the next run a full backup; subsequent runs become incrementals against it.

#### Incremental

```bash
# Same command, same .snar file — the file changes after each run
tar -czf /backup/inc-$(date +%F).tar.gz \
    --listed-incremental=/backup/full.snar \
    /home /etc
```

Restore: extract full, then each incremental in order, with `-g /dev/null` to suppress side effects:

```bash
tar -xzf full.tar.gz -g /dev/null
tar -xzf inc-2026-06-11.tar.gz -g /dev/null
```

#### Differential

A *differential* is "everything since last full". Implement by keeping a snapshot file dedicated to the differential set and never updating it after the full.

### 14.2 `rsync`

```
rsync [OPTIONS] SRC... DEST
```

| Flag | Meaning |
|---|---|
| `-a` | Archive (= `-rlptgoD`) |
| `-v` | Verbose |
| `-z` | Compress in transit |
| `-h` | Human-readable |
| `-P` | Progress + partial (resume) |
| `--partial` | Keep partial on interrupt |
| `--delete` | Delete dest files not in source |
| `--delete-after` / `--delete-excluded` | Variants |
| `--dry-run` / `-n` | Preview |
| `--exclude=PAT` / `--exclude-from=FILE` | Skip |
| `--include=PAT` | Force include (combine with `--exclude='*'`) |
| `--link-dest=DIR` | Hardlink unchanged files (deduped snapshots) |
| `--bwlimit=KBPS` | Throttle |
| `--checksum` / `-c` | Compare by hash, not size+mtime |
| `--rsh='ssh -p 2222'` or `-e 'ssh ...'` | Specify remote shell |
| `-x` | Don't cross filesystem boundaries |
| `-u` | Skip files newer on dest |
| `--itemize-changes` / `-i` | Show what changed |

**TRAP:** Trailing slashes matter.
- `rsync -a src/ dst/` copies *contents of src* into dst.
- `rsync -a src dst/` copies *src as subdirectory* of dst.

```bash
rsync -avz --delete /var/www/ backup:/srv/www/
rsync -av --link-dest=/backup/2026-06-10 /data/ /backup/2026-06-11/   # hardlink-snapshot
rsync -e 'ssh -p 2222' -avz src/ user@host:/dest/
rsync -av --exclude='node_modules' --exclude='.git' src/ dest/
rsync --bwlimit=1000 -av src/ dest/
```

Daemon mode: configure `/etc/rsyncd.conf` and reach via `rsync://host/module/path`.

### 14.3 `dd` for backups

```bash
# Clone disk-to-disk
dd if=/dev/sda of=/dev/sdb bs=4M status=progress conv=sync

# Disk image with progress
dd if=/dev/sda of=disk.img bs=4M status=progress

# Compress on the fly
dd if=/dev/sda bs=4M status=progress | gzip > sda.img.gz

# Restore
gunzip -c sda.img.gz | dd of=/dev/sda bs=4M

# Wipe (random or zero)
dd if=/dev/urandom of=/dev/sdX bs=1M status=progress

# Create empty 1 GB file
dd if=/dev/zero of=empty.bin bs=1M count=1024

# Skip and seek
dd if=src of=dst bs=512 skip=2048 seek=4096 count=1024
```

Important operands: `if=` input, `of=` output, `bs=` block size, `count=` blocks, `skip=` skip blocks of input, `seek=` skip blocks of output (sparse writes), `conv=` (`noerror`, `sync`, `notrunc`, `fsync`, `fdatasync`), `status=progress`.

### 14.4 `cpio`

```bash
find /home -depth -print0 | cpio --null -o -H newc > home.cpio
cpio -idv < home.cpio                 # extract
cpio -tv < home.cpio                  # list
```

`-H FORMAT`: `newc` is the modern initramfs format. `-o` create, `-i` extract, `-p` pass-through.

### 14.5 Backup tools — Amanda, Bacula

**Amanda** (Advanced Maryland Automatic Network Disk Archiver):
- Central server, many clients, tape-centric.
- Components: `amdump`, `amrestore`, `amlabel`, `amcheck`.
- Config in `/etc/amanda/`.

**Bacula**:
- Director (orchestrator), Storage Daemon (writes), File Daemon (client), Console (UI).
- Strong scheduling and catalog (database) of backups.

For LPIC-2: know the names, their roles, and that both are network-aware backup systems superior to ad-hoc tar.

### 14.6 Backup Strategy — 3-2-1 Rule

- **3** copies of data
- on **2** different media
- with **1** stored off-site

Combine with versioning (incremental/differential) and periodic full-restore drills.

### 14.7 File Recovery

| Tool | Use |
|---|---|
| `debugfs` | Interactive ext2/3/4 forensics, undelete |
| `extundelete` | Undelete ext3/4 files |
| `testdisk` | Recover lost partitions |
| `photorec` | Carve files by signature from raw devices |
| `ddrescue` | Robust copy of failing disks |

```bash
debugfs /dev/sda1
debugfs:  lsdel
debugfs:  undel <inode> /tmp/recovered

extundelete /dev/sda1 --restore-file path/to/file
ddrescue /dev/sda disk.img mapfile
```

**Exercises**
- *Exercise 1:* Use rsync with `--link-dest` to keep daily snapshots of `/data` in `/backup/YYYY-MM-DD`, deduplicating unchanged files.
- *Exercise 2:* Create a tar full + nightly incremental scheme using `--listed-incremental`.

**Mock Exam Questions**

**Q1.** What does the trailing slash difference matter in `rsync`?
- A) Nothing
- B) `src/` copies contents into dest; `src` (no slash) creates `dest/src`
- C) Reverse of B
- D) Only affects `--delete`

**A:** **B.**

**Q2.** Which dd operand offsets the output by N blocks?
- A) `skip=N`  B) `seek=N`  C) `count=N`  D) `bs=N`

**A:** **B.**

**Q3 (Scenario).** A tape backup chain consists of one full and 6 incrementals. Restore order?

**A:** Apply the full first, then each incremental in chronological order. With `--listed-incremental=/dev/null` to avoid mutating snapshot files during restore.

---

## Chapter 15: DNS Server (BIND)

### 15.1 DNS Concepts

- **Recursive resolver** — answers any query by chasing referrals from roots down.
- **Authoritative server** — answers definitively for the zones it owns.
- **Stub resolver** — `libc`'s built-in client.
- **Forwarder** — sends queries to another resolver (e.g., ISP) instead of recursing.
- **Zone** — administrative unit (a portion of the namespace).
- **Delegation** — parent zone uses NS records to point to child zone servers.

Record types:

| Type | Holds |
|---|---|
| A | IPv4 address |
| AAAA | IPv6 address |
| CNAME | Canonical name alias |
| MX | Mail exchanger (with priority) |
| NS | Name server for the zone |
| SOA | Start Of Authority (zone metadata) |
| PTR | Pointer (used in reverse zones) |
| TXT | Free text (SPF, DKIM, verification) |
| SRV | Service location (proto, port, target) |
| CAA | Allowed CAs |
| DS / DNSKEY / RRSIG / NSEC / NSEC3 | DNSSEC |
| TLSA | DANE: certificate pinning in DNS |

### 15.2 BIND — `named.conf`

`/etc/named.conf` (RHEL) or `/etc/bind/named.conf` (Debian).

```
options {
    directory "/var/named";
    listen-on { 127.0.0.1; 192.168.1.1; };
    listen-on-v6 { ::1; };
    allow-query { localhost; 192.168.1.0/24; };
    recursion yes;
    forwarders { 1.1.1.1; 8.8.8.8; };
    dnssec-validation auto;
};

logging {
    channel default_debug {
        file "data/named.run";
        severity dynamic;
    };
};

zone "example.com" IN {
    type master;
    file "example.com.zone";
    allow-transfer { 192.168.1.2; };
    also-notify { 192.168.1.2; };
};

zone "1.168.192.in-addr.arpa" IN {
    type master;
    file "192.168.1.zone";
};

zone "." IN {
    type hint;
    file "named.ca";
};
```

Important zone types:
- `master` — authoritative, primary
- `slave` — authoritative, secondary (zone transfers from master)
- `forward` — forward queries for this zone elsewhere
- `hint` — root hints
- `stub` — like slave but only NS records

### 15.3 Zone File Format

```
$TTL 86400
@   IN  SOA  ns1.example.com. hostmaster.example.com. (
                  2026061101  ; serial (YYYYMMDDnn)
                  3600        ; refresh
                  900         ; retry
                  604800      ; expire
                  86400 )     ; minimum TTL / negative cache
    IN  NS    ns1.example.com.
    IN  NS    ns2.example.com.
    IN  MX 10 mail.example.com.
    IN  A     192.168.1.10

ns1     IN  A     192.168.1.2
ns2     IN  A     192.168.1.3
www     IN  A     192.168.1.10
www     IN  AAAA  2001:db8::10
mail    IN  A     192.168.1.20
ftp     IN  CNAME www
_sip._tcp IN SRV 10 60 5060 sipserver.example.com.
```

**TRAP:** Bare names (no trailing dot) are appended with the zone's `$ORIGIN`. `www` becomes `www.example.com.` Fully-qualified names need the trailing dot.

Reverse zone:

```
$TTL 86400
@   IN  SOA  ns1.example.com. hostmaster.example.com. (
                  2026061101 3600 900 604800 86400 )
    IN  NS    ns1.example.com.

2   IN  PTR   ns1.example.com.
10  IN  PTR   www.example.com.
20  IN  PTR   mail.example.com.
```

### 15.4 Primary and Secondary

Primary holds the master copy. Secondary fetches via AXFR (full transfer) or IXFR (incremental).

Master config:

```
zone "example.com" IN {
    type master;
    file "example.com.zone";
    allow-transfer { 192.168.1.3; };
    notify yes;
};
```

Slave config:

```
zone "example.com" IN {
    type slave;
    masters { 192.168.1.2; };
    file "slaves/example.com.zone";
};
```

Increment the SOA serial whenever you change a zone; slaves use serial to decide if a transfer is needed.

### 15.5 DNS Views (Split Horizon)

Provide different answers to internal vs external clients.

```
acl internal { 192.168.1.0/24; };
view "internal" {
    match-clients { internal; };
    recursion yes;
    zone "example.com" { type master; file "example.com.internal"; };
};
view "external" {
    match-clients { any; };
    recursion no;
    zone "example.com" { type master; file "example.com.external"; };
};
```

### 15.6 DNSSEC

Adds cryptographic signatures so resolvers verify authenticity.

Keys: **KSK** (key-signing key, longer-lived, parent has its DS) and **ZSK** (zone-signing key, shorter-lived).

```bash
cd /var/named
dnssec-keygen -a RSASHA256 -b 2048 -fk example.com           # KSK
dnssec-keygen -a RSASHA256 -b 1024    example.com            # ZSK
# Append the .key files into the zone:
cat Kexample.com*.key >> example.com.zone
# Sign
dnssec-signzone -o example.com -k Kexample.com.+008+12345 example.com.zone Kexample.com.+008+67890.key
# named uses example.com.zone.signed
```

In `named.conf`: `dnssec-enable yes;` (older), `dnssec-validation auto;` for resolver-side checking. `inline-signing yes;` automates signing.

Publish the DS record to the parent (registrar).

### 15.7 Debugging

```bash
named-checkconf                            # syntax of named.conf
named-checkconf -z                         # also load all zone files
named-checkzone example.com example.com.zone

dig @localhost example.com
dig @localhost example.com SOA
dig @localhost +trace example.com
dig +short -x 192.168.1.10

rndc reload                                # reload config + zones
rndc reload example.com
rndc reconfig
rndc refresh example.com                   # slave: ask master
rndc retransfer example.com                # slave: force AXFR
rndc flush                                 # clear cache
rndc stats                                 # dump stats to /var/named/data/named_stats.txt
rndc status
```

`rndc.conf` and `rndc.key` are auto-generated by `rndc-confgen`.

**Exercises**
- *Exercise 1:* Author a zone file for `lab.local` with two NS, a mail server, web with IPv4+IPv6, and reverse PTRs in 192.168.50.0/24.
- *Exercise 2:* Configure a slave for the same zone and verify with `dig AXFR`.

**Mock Exam Questions**

**Q1.** Which SOA field is most important for slave synchronization?
- A) Refresh  B) Serial  C) Retry  D) Minimum

**A:** **B.** Slaves compare serials to decide whether to transfer.

**Q2.** Which BIND zone type points at root hints?
- A) `forward`  B) `master`  C) `hint`  D) `stub`

**A:** **C.**

**Q3 (Scenario).** After editing `example.com.zone` you forgot to bump the serial. What is the symptom on slaves?

**A:** Slaves see same serial and skip transfer. Their data stays stale. Fix: bump serial, `rndc reload example.com`, `rndc notify example.com` or wait for refresh.

**Q4.** Which tool validates the syntactic correctness of a zone file?
- A) `named-zone`  B) `named-checkzone`  C) `bind-validate`  D) `rndc lint`

**A:** **B.**

---

## Chapter 16: Web Servers

### 16.1 Apache (httpd)

Main configs:
- RHEL: `/etc/httpd/conf/httpd.conf`, includes `/etc/httpd/conf.d/*.conf` and `conf.modules.d/`.
- Debian: `/etc/apache2/apache2.conf`, with `mods-available/`, `mods-enabled/`, `sites-available/`, `sites-enabled/`, `conf-available/`, `conf-enabled/`. Helpers: `a2enmod`, `a2dismod`, `a2ensite`, `a2dissite`.

Test and reload:

```bash
apachectl configtest                # alias for httpd -t
apachectl -S                        # virtualhost dump
systemctl reload apache2|httpd
```

#### Virtual hosts

Name-based:

```apache
<VirtualHost *:80>
    ServerName www.example.com
    ServerAlias example.com
    DocumentRoot /var/www/example
    ErrorLog ${APACHE_LOG_DIR}/example_error.log
    CustomLog ${APACHE_LOG_DIR}/example_access.log combined
    <Directory /var/www/example>
        Options -Indexes +FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

<VirtualHost *:80>
    ServerName www.other.com
    DocumentRoot /var/www/other
</VirtualHost>
```

IP-based (rare today):

```apache
<VirtualHost 192.168.1.10:80>
    ServerName site1.example.com
</VirtualHost>
<VirtualHost 192.168.1.11:80>
    ServerName site2.example.com
</VirtualHost>
```

For multiple SSL sites on one IP, SNI is required (modern clients support it).

#### `.htaccess` and `AllowOverride`

Per-directory overrides honored only when `AllowOverride` allows it. Possible values: `None`, `All`, or specific categories: `AuthConfig`, `FileInfo`, `Indexes`, `Limit`, `Options[=opt,opt]`, `Nonfatal=Override`.

```apache
<Directory /var/www/example>
    AllowOverride AuthConfig Indexes
</Directory>
```

`.htaccess` example:

```apache
RewriteEngine On
RewriteRule ^old/(.*)$ /new/$1 [L,R=301]
AuthType Basic
AuthName "Restricted"
AuthUserFile /etc/httpd/.htpasswd
Require valid-user
```

Generate password file:

```bash
htpasswd -c /etc/httpd/.htpasswd alice
htpasswd /etc/httpd/.htpasswd bob       # add another
```

#### Important modules

| Module | Purpose |
|---|---|
| `mod_ssl` | TLS |
| `mod_rewrite` | URL rewriting |
| `mod_proxy`, `mod_proxy_http`, `mod_proxy_fcgi` | Reverse proxy |
| `mod_status` | `/server-status` |
| `mod_info` | `/server-info` |
| `mod_headers` | Add/strip HTTP headers |
| `mod_security` | WAF |
| `mod_php` / `mod_wsgi` | Embedded interpreters |
| `mod_authn_*` / `mod_authz_*` | Authentication backends |

```bash
a2enmod ssl rewrite headers proxy proxy_http
```

#### Access control (Apache 2.4)

```apache
Require all granted
Require all denied
Require user alice bob
Require group editors
Require ip 192.168.1.0/24
Require not ip 10.0.0.5
<RequireAll>
    Require ip 10.0.0.0/8
    Require valid-user
</RequireAll>
```

#### Logging

Format strings in `httpd.conf`:

```apache
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
CustomLog logs/access_log combined
ErrorLog logs/error_log
LogLevel warn
```

#### SSL/TLS configuration

```apache
<VirtualHost *:443>
    ServerName www.example.com
    DocumentRoot /var/www/example
    SSLEngine on
    SSLCertificateFile /etc/letsencrypt/live/example.com/fullchain.pem
    SSLCertificateKeyFile /etc/letsencrypt/live/example.com/privkey.pem
    SSLProtocol all -SSLv3 -TLSv1 -TLSv1.1
    SSLCipherSuite HIGH:!aNULL:!MD5
    SSLHonorCipherOrder on
</VirtualHost>
```

#### `mod_proxy` example

```apache
ProxyPass        /api  http://backend:8080/api
ProxyPassReverse /api  http://backend:8080/api
<Proxy *>
    Require all granted
</Proxy>
```

### 16.2 Nginx

Config: `/etc/nginx/nginx.conf`, includes `/etc/nginx/conf.d/*.conf` and `sites-enabled/*`.

Test and reload:

```bash
nginx -t
systemctl reload nginx
nginx -s reload
```

#### Server blocks (virtual hosts)

```nginx
server {
    listen 80;
    server_name www.example.com example.com;
    return 301 https://www.example.com$request_uri;
}

server {
    listen 443 ssl http2;
    server_name www.example.com;
    root /var/www/example;
    index index.html;

    ssl_certificate     /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;

    access_log /var/log/nginx/example.access.log;
    error_log  /var/log/nginx/example.error.log;

    location / {
        try_files $uri $uri/ =404;
    }

    location /api/ {
        proxy_pass http://backend/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

#### Location matching priority

1. `= exact`
2. `^~ prefix` (no regex; longest first)
3. `~ regex` (case-sensitive) and `~* regex` (case-insensitive), first match in config order
4. Longest matching prefix

#### Upstream and load balancing

```nginx
upstream backend {
    least_conn;                          # algorithm: round_robin (default), least_conn, ip_hash, hash $key
    server app1.local:8080 weight=2 max_fails=3 fail_timeout=10s;
    server app2.local:8080;
    server app3.local:8080 backup;
    keepalive 32;
}

server {
    listen 80;
    location / {
        proxy_pass http://backend;
        proxy_http_version 1.1;
        proxy_set_header Connection "";
    }
}
```

#### Static file caching

```nginx
location ~* \.(jpg|jpeg|png|gif|css|js)$ {
    expires 30d;
    add_header Cache-Control "public, immutable";
    access_log off;
}
```

### 16.3 Let's Encrypt / Certbot

```bash
certbot --apache -d example.com -d www.example.com
certbot --nginx -d example.com
certbot certonly --standalone -d example.com           # standalone web server
certbot certonly --webroot -w /var/www/example -d example.com
certbot renew --dry-run
certbot certificates
certbot delete --cert-name example.com
```

Auto-renewal: certbot installs a systemd timer (`certbot.timer`).

### 16.4 Apache vs Nginx

| | Apache | Nginx |
|---|---|---|
| Architecture | Process/thread (MPM: prefork, worker, event) | Event-driven, async |
| Dynamic content | Embedded modules (mod_php) | Reverse proxy to FPM/uwsgi |
| `.htaccess` | Yes | No (everything is in main config) |
| Configuration | Apache-specific directives | Block / directive nesting |
| When | Easier per-directory rules, mature ecosystem | High-concurrency static, reverse proxy |

**Exercises**
- *Exercise 1:* Configure Apache with two name-based virtual hosts that share one IP.
- *Exercise 2:* In Nginx, redirect all HTTP to HTTPS and serve PHP via `fastcgi_pass unix:/run/php/php8.2-fpm.sock`.

**Mock Exam Questions**

**Q1.** Which Apache directive sets which `.htaccess` features are honored?
- A) `Options`  B) `AllowOverride`  C) `Require`  D) `Directory`

**A:** **B.**

**Q2.** In Nginx, which directive selects backend pools?
- A) `upstream`  B) `backend`  C) `proxy_servers`  D) `cluster`

**A:** **A.**

**Q3 (Scenario).** Nginx logs report `502 Bad Gateway` on `/api`. First diagnostic step?

**A:** Verify the upstream is reachable from the Nginx host (`curl http://backend:8080/api` from the host); then check Nginx `error.log` — most often the upstream is down, the port is blocked, or TLS verify failed when proxying to HTTPS.

---

## Chapter 17: File Sharing Services

### 17.1 Samba (SMB/CIFS)

Configuration: `/etc/samba/smb.conf` with `[global]` plus per-share sections.

```ini
[global]
    workgroup = WORKGROUP
    server string = Samba Server
    security = user
    map to guest = bad user
    log file = /var/log/samba/log.%m
    max log size = 1000
    server min protocol = SMB2

[homes]
    comment = Home Directories
    browseable = no
    read only = no
    valid users = %S

[public]
    path = /srv/samba/public
    browseable = yes
    guest ok = yes
    read only = yes

[secure]
    path = /srv/samba/secure
    valid users = @smbusers
    read only = no
    create mask = 0660
    directory mask = 0770
```

Test and reload:

```bash
testparm                        # parse + dump effective config
testparm -s                     # silent
smbcontrol all reload-config
systemctl restart smbd nmbd
```

#### Users — `smbpasswd`, `pdbedit`

Samba uses its own user database, but maps to local Unix users.

```bash
useradd -s /sbin/nologin alice
smbpasswd -a alice                       # set Samba password
smbpasswd -d alice                       # disable
smbpasswd -e alice                       # enable
smbpasswd -x alice                       # delete

pdbedit -L                                # list all
pdbedit -L -v alice                       # verbose
pdbedit -a -u alice                       # add
pdbedit -x -u alice                       # delete
```

#### Joining a Windows domain

```ini
[global]
    workgroup = MYDOMAIN
    security = ads
    realm = MYDOMAIN.LOCAL
    kerberos method = secrets and keytab
    winbind use default domain = yes
    template homedir = /home/%U
    template shell = /bin/bash
    idmap config * : backend = tdb
    idmap config * : range = 3000-7999
    idmap config MYDOMAIN : backend = rid
    idmap config MYDOMAIN : range = 10000-999999
```

Then `net ads join -U Administrator`. Configure `nsswitch.conf` with `winbind`/`sss` and PAM accordingly.

#### Client tools

```bash
smbclient -L //server -U alice               # list shares
smbclient //server/share -U alice            # interactive
smbclient //server/share -U alice -c 'get file.txt'
mount -t cifs //server/share /mnt -o username=alice,password=secret,uid=1000,gid=1000
smbstatus                                    # active sessions and locks
```

### 17.2 NFS

Two major variants:
- **NFSv3** — stateless, separate `mountd`, `lockd`, `statd` daemons; uses RPC and `rpcbind`/`portmap`.
- **NFSv4** — stateful, single port 2049, integrated with Kerberos optional, supports ACLs and pseudo-filesystem.

#### Server: `/etc/exports`

```
/srv/nfs/public    192.168.1.0/24(ro,sync,no_subtree_check)
/srv/nfs/data      192.168.1.10(rw,sync,no_subtree_check,no_root_squash)
/srv/nfs/users     *.example.com(rw,sync,root_squash,sec=krb5p)
```

Important options:

| Option | Meaning |
|---|---|
| `ro` / `rw` | Read-only / read-write |
| `sync` / `async` | Force fsync vs let cache delay |
| `root_squash` | Map root to nobody (default) |
| `no_root_squash` | Root keeps root (rare; risky) |
| `all_squash` | Map all to anon |
| `anonuid=N`, `anongid=N` | Identity for squashed access |
| `no_subtree_check` | Skip subtree integrity check (recommended for v3) |
| `sec=sys|krb5|krb5i|krb5p` | Auth flavor |
| `fsid=N` | Manual FS ID (needed for some pseudo-FS setups) |
| `crossmnt` | Cross mount points |

```bash
exportfs -arv                       # re-export
exportfs -u clienthost:/path        # unexport
exportfs -s                         # current exports
showmount -e localhost              # list exports (v3 only)
```

Required services: `nfs-server` (or `nfs-kernel-server`), `rpcbind` for v3, `nfs-idmapd` for v4.

#### Client

```bash
mount -t nfs server:/srv/nfs/data /mnt
mount -t nfs4 server:/data /mnt
mount -o nfsvers=4.2,rw,hard,intr server:/data /mnt

# /etc/fstab
server:/srv/data   /mnt/data   nfs   defaults,_netdev,nofail   0  0
```

Common options: `hard` (block on outage, retry forever — default) vs `soft` (return errors), `intr` (interruptible), `rsize=`, `wsize=`, `timeo=`, `nfsvers=`, `noac` (no attribute caching).

#### `autofs`

Mount on demand.

```
# /etc/auto.master
/mnt/auto   /etc/auto.misc   --timeout=60
```

```
# /etc/auto.misc
data    -fstype=nfs4,rw   server:/srv/data
```

`systemctl restart autofs`. Access `/mnt/auto/data` triggers the mount.

#### Kerberos with NFS

Set `sec=krb5p` in exports (privacy = signing + encryption). Client and server need keytabs (`/etc/krb5.keytab`) with `nfs/host.fqdn@REALM` principals. Enable `rpc.gssd` / `rpc.svcgssd`.

### 17.3 FTP — vsftpd

`/etc/vsftpd/vsftpd.conf` (RHEL) or `/etc/vsftpd.conf` (Debian).

Important options:

```
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
chroot_local_user=YES
allow_writeable_chroot=YES
listen=YES
listen_ipv6=NO
pam_service_name=vsftpd
userlist_enable=YES
userlist_file=/etc/vsftpd/user_list
userlist_deny=NO              # only listed users may login (when NO)

# Passive
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=40100

# TLS
ssl_enable=YES
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.key
force_local_data_ssl=YES
force_local_logins_ssl=YES
```

Active vs Passive:
- **Active**: client opens command channel; server opens *back* data channel from port 20. Breaks behind NAT.
- **Passive**: client opens both channels; server returns a passive port. NAT-friendly. Server must allow the passive port range through firewall.

#### Virtual users (PAM with userdb)

```bash
db_load -T -t hash -f users.txt /etc/vsftpd/vusers.db
```

`/etc/pam.d/vsftpd`:

```
auth    required    pam_userdb.so db=/etc/vsftpd/vusers
account required    pam_userdb.so db=/etc/vsftpd/vusers
```

In `vsftpd.conf`: `guest_enable=YES`, `guest_username=virtual_ftp`, `user_sub_token=$USER`, `local_root=/srv/ftp/$USER`.

#### proftpd

Apache-style config in `/etc/proftpd/proftpd.conf` with `<VirtualHost>`, `<Anonymous>`, `<Limit>` blocks. Modules: `mod_sftp`, `mod_tls`, `mod_quotatab`.

#### SFTP vs FTPS vs FTP

| | FTP | FTPS | SFTP |
|---|---|---|---|
| Transport | Plain TCP | TLS (explicit or implicit) | Inside SSH |
| Ports | 21 (ctrl) + dynamic (data) | 21 (explicit) or 990 (implicit) | 22 |
| Servers | vsftpd, proftpd | vsftpd, proftpd | OpenSSH (`Subsystem sftp`) |
| Firewall friendly | No | No (data port range) | Yes |

Chroot SFTP — `/etc/ssh/sshd_config`:

```
Match Group sftponly
    ChrootDirectory /srv/sftp/%u
    ForceCommand internal-sftp
    AllowTcpForwarding no
    X11Forwarding no
```

Chroot directory must be owned by root and contain no write-by-other dirs at the chroot root.

**Exercises**
- *Exercise 1:* Export `/srv/data` over NFSv4 with `sec=krb5p`, allow only the `prod.local` domain.
- *Exercise 2:* Create a Samba share `[backup]` writable by group `bk`, hidden from browse list.

**Mock Exam Questions**

**Q1.** Which Samba option maps unknown users to guest access?
- A) `guest ok = yes`
- B) `map to guest = bad user`
- C) `security = share`
- D) `null passwords = yes`

**A:** **B.** Inside `[global]`. The share also needs `guest ok = yes`.

**Q2.** Which NFS export option keeps the connected client's root identity?
- A) `root_squash`  B) `all_squash`  C) `no_root_squash`  D) `anonuid=0`

**A:** **C.** Beware — usually a bad idea on shared infrastructure.

**Q3 (Scenario).** A user can log in via SFTP but is dropped immediately. The chroot fails. What's most likely wrong?

**A:** The chroot dir must be owned by root and not group/other writable. Either fix ownership/perms, or put writable subdirs *inside* the chroot.

**Q4.** Which vsftpd setting prevents users from breaking out of their home directory?
- A) `secure_chroot_dir=YES`
- B) `chroot_local_user=YES`
- C) `local_enable=NO`
- D) `userlist_deny=YES`

**A:** **B.**

---

## Chapter 18: Mail Services

### 18.1 Protocols

| Protocol | Role | Port | TLS port |
|---|---|---|---|
| SMTP | Server-to-server transport / submission | 25 | 587 (submission, STARTTLS), 465 (SMTPS) |
| POP3 | Client downloads mail | 110 | 995 (POP3S) |
| IMAP | Client browses on server | 143 | 993 (IMAPS) |

STARTTLS = command issued on the plaintext port to upgrade to TLS. SMTPS/IMAPS/POP3S = TLS from the first byte.

### 18.2 Postfix

Two key configs: `/etc/postfix/main.cf` (server settings) and `/etc/postfix/master.cf` (daemons and pipes).

```bash
postfix check                # syntax
postfix reload
postconf -n                  # show non-default settings
postconf myhostname          # query one
postconf -e 'inet_interfaces = all'   # set persistently
postmap /etc/postfix/transport       # build .db from hash: source
newaliases                            # rebuild /etc/aliases.db
```

#### `main.cf` essentials

```
myhostname = mail.example.com
mydomain   = example.com
myorigin   = $mydomain
inet_interfaces = all
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks = 127.0.0.0/8 192.168.1.0/24
relayhost =
home_mailbox = Maildir/

smtpd_banner = $myhostname ESMTP
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

# TLS
smtpd_tls_cert_file=/etc/letsencrypt/live/mail.example.com/fullchain.pem
smtpd_tls_key_file=/etc/letsencrypt/live/mail.example.com/privkey.pem
smtpd_use_tls=yes
smtpd_tls_security_level=may
smtp_tls_security_level=may

# Virtual domains
virtual_mailbox_domains = example.org
virtual_mailbox_base    = /var/vmail
virtual_mailbox_maps    = hash:/etc/postfix/vmailbox
virtual_alias_maps      = hash:/etc/postfix/virtual
virtual_minimum_uid     = 1000
virtual_uid_maps        = static:5000
virtual_gid_maps        = static:5000
```

`/etc/postfix/virtual`:

```
postmaster@example.org admin
billing@example.org    bob@gmail.com,carol@yahoo.com
@example.org           catchall@example.com
```

Then `postmap /etc/postfix/virtual && systemctl reload postfix`.

#### Relay configuration

To relay through a smarthost:

```
relayhost = [smtp.provider.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
```

`/etc/postfix/sasl_passwd`:

```
[smtp.provider.com]:587 user@example.com:password
```

`postmap /etc/postfix/sasl_passwd && chmod 600 /etc/postfix/sasl_passwd*`.

#### Queue management

```bash
postqueue -p              # list queue (same as mailq)
postqueue -f              # flush queue (try delivery now)
postqueue -i QUEUEID      # try one
postsuper -d QUEUEID      # delete one
postsuper -d ALL deferred # delete all deferred
postsuper -h QUEUEID      # hold
postsuper -H QUEUEID      # release
mailq
```

### 18.3 Dovecot (IMAP/POP3)

`/etc/dovecot/dovecot.conf` and `conf.d/*`.

```
protocols = imap pop3 lmtp
mail_location = maildir:~/Maildir
ssl = required
ssl_cert = </etc/letsencrypt/live/mail.example.com/fullchain.pem
ssl_key  = </etc/letsencrypt/live/mail.example.com/privkey.pem

passdb {
    driver = pam
}
userdb {
    driver = passwd
}

service auth {
    unix_listener /var/spool/postfix/private/auth {
        mode = 0660
        user = postfix
        group = postfix
    }
}
```

Mailbox formats:
- **mbox** — one file per folder; whole file locked on writes.
- **Maildir** — one file per message (`new/`, `cur/`, `tmp/`). Far better for concurrent access.

```bash
doveadm reload
doveadm user alice                # show resolved user
doveadm mailbox list -u alice
doveadm fetch -u alice subject mailbox INBOX
```

### 18.4 Email Authentication — SPF, DKIM, DMARC

| Mechanism | Where | Purpose |
|---|---|---|
| SPF | TXT record at the sending domain | Lists IPs/hosts permitted to send mail for the domain |
| DKIM | TXT record at `<selector>._domainkey.<domain>` | Public key for verifying message signatures added by the sender |
| DMARC | TXT record at `_dmarc.<domain>` | Tells receivers what to do when SPF/DKIM fail, plus reporting |

SPF example:

```
example.com.  IN  TXT  "v=spf1 mx ip4:203.0.113.0/24 include:_spf.google.com -all"
```

`-all` = hard fail, `~all` = soft fail, `?all` = neutral.

DKIM example: configured via `opendkim`. Generate keys with `opendkim-genkey -d example.com -s mail`. Publish the `mail._domainkey.example.com` TXT record.

DMARC example:

```
_dmarc.example.com. IN TXT "v=DMARC1; p=reject; rua=mailto:dmarc@example.com; pct=100; adkim=s; aspf=s"
```

### 18.5 Spam Filtering

- **SpamAssassin** — rule-based scoring + Bayesian learning. `spamc | spamd`. Score threshold often 5.0.
- **Amavisd-new** — coordinator that pipes Postfix → SpamAssassin and ClamAV.
- **ClamAV** — antivirus.

### 18.6 Troubleshooting

```bash
tail -F /var/log/maillog                 # RHEL
tail -F /var/log/mail.log                # Debian
journalctl -u postfix -u dovecot -f

# Test SMTP by hand
telnet mail.example.com 25
EHLO test
MAIL FROM:<a@example.com>
RCPT TO:<b@example.com>
DATA
Subject: test

hello
.
QUIT

# With TLS
openssl s_client -connect mail.example.com:587 -starttls smtp
openssl s_client -connect mail.example.com:993
```

**Exercises**
- *Exercise 1:* Configure Postfix as a satellite relay using a Gmail SMTP smarthost with SASL.
- *Exercise 2:* Publish SPF, DKIM, and DMARC records for `example.com` and validate them with `dig` and `opendkim-testmsg`.

**Mock Exam Questions**

**Q1.** Which file lists local-domain mail destinations?
- A) `/etc/postfix/main.cf` (the `mydestination` parameter)
- B) `/etc/aliases`
- C) `/etc/postfix/virtual`
- D) `/etc/mailname`

**A:** **A.**

**Q2.** Mail in the deferred queue can be forced to a new delivery attempt with:
- A) `postqueue -f`  B) `postfix reload`  C) `mail -q`  D) `newaliases`

**A:** **A.**

**Q3 (Scenario).** Outbound mail is rejected at the receiver with "DMARC: fail". What three records should you verify?

**A:** SPF (TXT at root), DKIM (`<selector>._domainkey.<domain>` TXT), DMARC (`_dmarc.<domain>` TXT). DMARC fails if both SPF *and* DKIM fail. Often the cause is a missing/misaligned `mfrom` domain or unsigned mail.

---

## Chapter 19: Remote Access & VPN

### 19.1 SSH Advanced

(SSH basics covered in Chapter 9.)

#### ProxyJump

```
Host db
    HostName db.internal
    ProxyJump bastion
```

Equivalent CLI: `ssh -J bastion db`. Multiple hops: `-J host1,host2`.

Older equivalent (still seen): `ProxyCommand ssh bastion -W %h:%p`.

#### Agent forwarding

```bash
ssh-agent bash
ssh-add ~/.ssh/id_ed25519
ssh -A user@host
```

Inside the forwarded session, `ssh-add -l` shows the original agent's keys; further `ssh` from that host uses your agent. **Risk:** root on the intermediate host can use your keys; only forward to fully-trusted hosts.

#### ControlMaster (multiplexing)

```
Host *
    ControlMaster auto
    ControlPath ~/.ssh/cm-%r@%h:%p
    ControlPersist 10m
```

First connection creates a master socket; subsequent `ssh`s reuse it — no new TCP/TLS handshake. Huge speedup for tools running many short SSH calls (Ansible, Mosh).

### 19.2 OpenVPN

OpenVPN tunnels IP traffic over TLS-based protocol on UDP (default 1194) or TCP. Two ways to operate: with TLS certificates (most common) or with a static shared key.

#### PKI with `easy-rsa`

```bash
make-cadir /etc/openvpn/easyrsa
cd /etc/openvpn/easyrsa
./easyrsa init-pki
./easyrsa build-ca nopass
./easyrsa gen-dh
./easyrsa build-server-full server nopass
./easyrsa build-client-full client1 nopass
openvpn --genkey secret /etc/openvpn/ta.key
```

#### Server config — `/etc/openvpn/server.conf`

```
port 1194
proto udp
dev tun
ca   /etc/openvpn/easyrsa/pki/ca.crt
cert /etc/openvpn/easyrsa/pki/issued/server.crt
key  /etc/openvpn/easyrsa/pki/private/server.key
dh   /etc/openvpn/easyrsa/pki/dh.pem
tls-auth /etc/openvpn/ta.key 0
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist /var/log/openvpn/ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 1.1.1.1"
keepalive 10 120
cipher AES-256-GCM
auth SHA256
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/status.log
verb 3
```

Enable IP forwarding and NAT on the server:

```bash
sysctl -w net.ipv4.ip_forward=1
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

`systemctl enable --now openvpn-server@server`.

#### Client config

```
client
dev tun
proto udp
remote vpn.example.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
tls-auth ta.key 1
cipher AES-256-GCM
auth SHA256
ca ca.crt
cert client1.crt
key client1.key
verb 3
```

`openvpn --config client.ovpn` to connect.

#### Routing

`server 10.8.0.0/24` gives the VPN its subnet. `push "route 192.168.1.0 255.255.255.0"` instructs clients to route LAN traffic through the VPN.

### 19.3 IPsec — strongSwan / Libreswan

IPsec works at IP layer. Two databases:
- **SAD (Security Association Database)** — keys and parameters.
- **SPD (Security Policy Database)** — which traffic gets protected.

Two phases:
- **IKE (Phase 1)** — establish a secure channel for negotiating.
- **IPsec/Child SA (Phase 2)** — protect actual data.

strongSwan config — `/etc/swanctl/conf.d/site.conf` (modern) or `/etc/ipsec.conf` (legacy).

```
connections {
    site-to-site {
        version = 2
        proposals = aes256-sha256-modp2048
        local_addrs  = 203.0.113.1
        remote_addrs = 198.51.100.1
        local  { auth = psk; id = vpn1 }
        remote { auth = psk; id = vpn2 }
        children {
            net {
                local_ts  = 10.1.0.0/24
                remote_ts = 10.2.0.0/24
                esp_proposals = aes256-sha256
                start_action = trap
            }
        }
    }
}
secrets {
    ike-psk { id = vpn1; secret = "supersecret" }
}
```

`swanctl --load-all && swanctl --initiate --child net`. Status: `swanctl --list-sas`.

### 19.4 Fail2ban

Reads logs, applies temporary firewall bans when patterns appear.

`/etc/fail2ban/jail.local`:

```ini
[DEFAULT]
bantime  = 1h
findtime = 10m
maxretry = 5
banaction = iptables-multiport

[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
backend = systemd

[postfix-sasl]
enabled = true
filter  = postfix-sasl
logpath = /var/log/mail.log
```

```bash
fail2ban-client status
fail2ban-client status sshd
fail2ban-client set sshd unbanip 1.2.3.4
fail2ban-client reload
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```

**Exercises**
- *Exercise 1:* Set up an OpenVPN server with one client certificate; verify the client can reach the server's LAN.
- *Exercise 2:* Configure Fail2ban to ban SSH brute-force attempts after 3 failures in 5 minutes for 1 hour.

**Mock Exam Questions**

**Q1.** Which OpenVPN option in the server config makes clients route all traffic through the VPN?
- A) `route-gateway 10.8.0.1`
- B) `push "redirect-gateway def1"`
- C) `topology subnet`
- D) `tun-mtu 1500`

**A:** **B.**

**Q2.** SSH agent forwarding is most risky because:
- A) It exposes private keys to disk
- B) Root on the intermediate host can use your agent
- C) It enables port forwarding
- D) It bypasses known_hosts checking

**A:** **B.**

**Q3 (Scenario).** Fail2ban appears to do nothing despite repeated failed logins. First check?

**A:** `fail2ban-client status sshd` to verify the jail is enabled and counting; if 0 matches, check `logpath` (correct file? backend `systemd` vs file?) and run `fail2ban-regex` against the log.

---

# PART 3 — LPIC-3 (Exams 300, 303, 305, 306)

---

## Chapter 20: LDAP & Directory Services (Exam 300)

### 20.1 Core Concepts

LDAP (Lightweight Directory Access Protocol) provides hierarchical reads/writes to a tree of entries.

- **DIT (Directory Information Tree)** — hierarchy of entries.
- **Entry** — unit of data; collection of attributes; identified by its **DN (Distinguished Name)**.
- **RDN (Relative Distinguished Name)** — the leftmost part of the DN, unique among siblings.
- **objectClass** — defines what attributes an entry must/may have. Examples: `top`, `person`, `inetOrgPerson`, `posixAccount`, `posixGroup`, `organizationalUnit`, `dcObject`.
- **Attribute** — name and one or more values. Common attributes: `cn` (common name), `sn` (surname), `givenName`, `uid`, `uidNumber`, `gidNumber`, `homeDirectory`, `loginShell`, `mail`, `userPassword`.
- **Schema** — definitions of objectClasses and attributes.

Naming convention:

```
dn: uid=alice,ou=People,dc=example,dc=com
```

Reads top-to-bottom from right: dc=com → dc=example → ou=People → uid=alice.

### 20.2 OpenLDAP

Modern OpenLDAP uses **cn=config** (a.k.a. OLC, online configuration) instead of `slapd.conf`.

```bash
slapcat -n 0                       # dump cn=config
slapcat -n 1                       # dump first user DB
slapcat -b 'dc=example,dc=com'
slapadd -l data.ldif -b dc=example,dc=com    # offline import
slapindex                          # rebuild indexes
slaptest -F /etc/ldap/slapd.d      # validate config
```

Backends: `mdb` (modern default — LMDB), `hdb` (older Berkeley DB), `ldif` (text), `monitor` (statistics), `relay`, `meta`.

#### Modify config online

```ldif
# enable-tls.ldif
dn: cn=config
changetype: modify
add: olcTLSCertificateFile
olcTLSCertificateFile: /etc/ldap/ssl/server.crt
-
add: olcTLSCertificateKeyFile
olcTLSCertificateKeyFile: /etc/ldap/ssl/server.key
```

```bash
ldapmodify -Y EXTERNAL -H ldapi:/// -f enable-tls.ldif
```

### 20.3 LDIF Format

Plain-text representation:

```ldif
dn: dc=example,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
dc: example
o: Example Org

dn: ou=People,dc=example,dc=com
objectClass: organizationalUnit
ou: People

dn: uid=alice,ou=People,dc=example,dc=com
objectClass: inetOrgPerson
objectClass: posixAccount
objectClass: shadowAccount
uid: alice
cn: Alice Smith
sn: Smith
givenName: Alice
uidNumber: 10001
gidNumber: 10000
homeDirectory: /home/alice
loginShell: /bin/bash
mail: alice@example.com
userPassword: {SSHA}<hash>
```

Modify operations:

```ldif
dn: uid=alice,ou=People,dc=example,dc=com
changetype: modify
replace: mail
mail: alice.smith@example.com
-
add: telephoneNumber
telephoneNumber: +1-555-0100
-
delete: description
```

### 20.4 LDAP Tools

```bash
ldapsearch -x -b 'dc=example,dc=com' '(uid=alice)'
ldapsearch -x -H ldap://ldap.example.com -b 'dc=example,dc=com' \
    -D 'cn=admin,dc=example,dc=com' -W '(objectClass=posixAccount)' uid uidNumber

ldapsearch -Y EXTERNAL -H ldapi:/// -b cn=config        # SASL EXTERNAL via Unix socket

ldapadd -x -D 'cn=admin,dc=example,dc=com' -W -f new.ldif
ldapmodify -x -D 'cn=admin,...' -W -f modify.ldif
ldapdelete -x -D 'cn=admin,...' -W 'uid=alice,ou=People,dc=example,dc=com'

ldappasswd -x -D 'cn=admin,...' -W -s newpw 'uid=alice,ou=People,dc=example,dc=com'

ldapwhoami -x -D 'uid=alice,...' -W
```

Common flags:
- `-x` simple bind, `-Y MECH` SASL
- `-D BIND-DN`
- `-W` prompt for password, `-w PASS`, `-y FILE`
- `-H URI` (ldap://, ldaps://, ldapi:///)
- `-b BASE-DN` search base
- `-s base|one|sub` scope
- `-LLL` LDIF output, no comments
- `-Z` start TLS; `-ZZ` require it

LDAP filter syntax:

```
(uid=alice)
(&(objectClass=posixAccount)(uidNumber>=1000))
(|(cn=*Smith*)(sn=Smith))
(!(loginShell=/bin/false))
(mail=*@example.com)
```

### 20.5 ACLs in OpenLDAP

```
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymous auth by * none
olcAccess: {1}to * by self write by users read by anonymous auth
```

Each ACL: `to <what> by <who> <perm>`. Permissions: `none`, `disclose`, `auth`, `compare`, `search`, `read`, `write`, `manage`. Multiple `by` clauses processed left-to-right; first match wins.

### 20.6 Replication — syncrepl

```ldif
dn: olcDatabase={1}mdb,cn=config
changetype: modify
add: olcSyncrepl
olcSyncrepl: rid=001
  provider=ldap://master.example.com
  bindmethod=simple
  binddn="cn=replicator,dc=example,dc=com"
  credentials=secret
  searchbase="dc=example,dc=com"
  type=refreshAndPersist
  retry="60 +"
  schemachecking=on
```

Modes:
- `refreshOnly` — periodic poll
- `refreshAndPersist` — open connection, push updates

Mirror mode: two masters with `olcMirrorMode: TRUE` and `olcServerID` set on each — only one is read-write at a time (failover).

For full multi-master (rare), see N-way multi-master configurations with `syncprov` overlay.

### 20.7 Samba 4 as Active Directory DC

Samba 4 implements an AD DC: LDAP + Kerberos + DNS in one daemon (`samba`).

```bash
samba-tool domain provision --use-rfc2307 --realm=EXAMPLE.LOCAL --domain=EXAMPLE \
    --server-role=dc --dns-backend=SAMBA_INTERNAL --adminpass='StrongPw'

systemctl disable --now smbd nmbd winbind     # the 'samba' daemon supersedes these for DC role
systemctl enable --now samba

kinit administrator
samba-tool user create alice
samba-tool group create devs
samba-tool group addmembers devs alice
samba-tool domain info 127.0.0.1
samba-tool dns add localhost example.local www A 192.168.1.10 -U Administrator
```

DNS for the realm must be set up; clients point DNS to the DC. Forward zones for the realm name must be authoritative.

### 20.8 Joining Linux Clients to AD

Two main client stacks:

**winbind** (older, Samba-based):

```ini
# /etc/samba/smb.conf
[global]
workgroup = EXAMPLE
realm = EXAMPLE.LOCAL
security = ads
idmap config * : backend = tdb
idmap config * : range = 3000-7999
idmap config EXAMPLE : backend = rid
idmap config EXAMPLE : range = 10000-999999
template homedir = /home/%U
template shell = /bin/bash
kerberos method = secrets and keytab
winbind use default domain = yes
winbind enum users = no
winbind enum groups = no
```

```bash
net ads join -U Administrator
systemctl enable --now winbind
```

Edit `/etc/nsswitch.conf`: add `winbind` after `files` for `passwd`, `group`. Add `pam_winbind.so` to PAM stacks.

**SSSD** (modern, recommended):

```bash
realm discover example.local
realm join example.local -U Administrator
authselect select sssd with-mkhomedir --force      # RHEL helper
```

`/etc/sssd/sssd.conf`:

```ini
[sssd]
domains = example.local
config_file_version = 2
services = nss, pam

[domain/example.local]
id_provider = ad
auth_provider = ad
access_provider = ad
ad_domain = example.local
krb5_realm = EXAMPLE.LOCAL
override_homedir = /home/%u@%d
default_shell = /bin/bash
use_fully_qualified_names = false
ldap_id_mapping = true
```

Tools:

```bash
sss_cache -E                             # invalidate cache
sssctl domain-list
sssctl domain-status example.local
realm list
id alice@example.local
getent passwd alice
```

### 20.9 Kerberos

Kerberos terminology:

- **KDC** — Key Distribution Center, comprising **AS** (Authentication Service) and **TGS** (Ticket Granting Service).
- **Principal** — entity name `name[/instance]@REALM`.
- **TGT** — Ticket Granting Ticket — obtained at login.
- **Service ticket** — obtained from TGS using TGT.
- **Keytab** — file containing principal + key, used by services.

`/etc/krb5.conf`:

```
[libdefaults]
default_realm = EXAMPLE.LOCAL
dns_lookup_realm = false
dns_lookup_kdc = true
ticket_lifetime = 24h

[realms]
EXAMPLE.LOCAL = {
    kdc = kdc.example.local
    admin_server = kdc.example.local
}

[domain_realm]
.example.local = EXAMPLE.LOCAL
example.local  = EXAMPLE.LOCAL
```

User commands:

```bash
kinit alice                           # get TGT
kinit -V alice                        # verbose
klist                                 # list tickets
klist -kt /etc/krb5.keytab            # list keys in keytab
kdestroy                              # remove cache
kpasswd                               # change password
ktutil                                # build/extract keytabs interactively
kvno service/host@REALM               # get service ticket
```

Admin commands (on KDC):

```bash
kadmin.local
kadmin.local:  addprinc alice
kadmin.local:  addprinc -randkey host/srv1.example.local
kadmin.local:  ktadd -k /etc/krb5.keytab host/srv1.example.local
kadmin.local:  listprincs
kadmin.local:  modprinc -maxlife 2days alice

kdb5_util create -r EXAMPLE.LOCAL -s        # initialize KDC database
systemctl enable --now krb5kdc kadmin
```

### 20.10 Integrating Kerberos with LDAP

Bind to LDAP using GSSAPI:

```bash
kinit alice
ldapsearch -Y GSSAPI -H ldap://ldap.example.com -b 'dc=example,dc=com'
```

OpenLDAP server needs Kerberos principal `ldap/host.example.com@REALM` in `/etc/krb5.keytab`, readable by slapd.

### 20.11 PAM + SSSD/LDAP/Kerberos

Typical PAM stack (system-auth):

```
auth     required      pam_env.so
auth     sufficient    pam_unix.so try_first_pass nullok
auth     sufficient    pam_sss.so use_first_pass
auth     required      pam_deny.so

account  required      pam_unix.so
account  sufficient    pam_sss.so

password sufficient    pam_unix.so sha512 shadow try_first_pass use_authtok
password sufficient    pam_sss.so use_authtok
password required      pam_deny.so

session  required      pam_unix.so
session  optional      pam_sss.so
session  optional      pam_mkhomedir.so
```

**Exercises**
- *Exercise 1:* Build a small OpenLDAP DIT with one OU `People` containing two users; search for them with `ldapsearch`.
- *Exercise 2:* Join a Linux box to an AD domain using SSSD; verify with `id user@DOMAIN`.

**Mock Exam Questions**

**Q1.** Which OpenLDAP backend is the recommended modern default?
- A) bdb  B) hdb  C) mdb  D) ldif

**A:** **C.** LMDB-based, supersedes hdb.

**Q2.** Kerberos TGT is requested from which service?
- A) TGS  B) AS  C) KDC overall  D) kadmind

**A:** **B.** The AS (Authentication Service) issues the TGT; the TGS issues service tickets using that TGT.

**Q3 (Scenario).** `getent passwd alice@example.local` returns nothing despite `realm list` showing the host is joined. Where do you look?

**A:** `/etc/nsswitch.conf` — confirm `sss` is in the `passwd:` line. Then `sssctl domain-status`. Then `sss_cache -E`. Also check `use_fully_qualified_names` matches your query.

**Q4.** Which LDIF `changetype` is required to modify an existing entry's attribute?
- A) `add`  B) `modify`  C) `replace`  D) `update`

**A:** **B.** Inside `modify`, you use `add:`, `replace:`, `delete:` per attribute.

---

## Chapter 21: Security (Exam 303)

### 21.1 Cryptography Fundamentals

- **Symmetric encryption** — one shared key (AES, ChaCha20). Fast, used for bulk data.
- **Public-key cryptography** — separate public/private keys. RSA can encrypt or sign depending on the protocol; ECDSA and Ed25519 are signature schemes; finite-field DH and ECDH/X25519 are key-agreement schemes. Do not call every public-key algorithm “encryption.”
- **Hashing** — one-way function (SHA-256, SHA-3, BLAKE2). For integrity, not encryption.
- **HMAC** — keyed hash for authenticity.
- **KDF** — Key Derivation Function (PBKDF2, scrypt, Argon2, bcrypt) — turn a password into a key with intentional cost.

### 21.2 PKI

- **CA** — Certificate Authority; issues certificates.
- **CSR** — Certificate Signing Request; what you send to the CA.
- **Certificate** — public key + identity, signed by CA.
- **CRL** — Certificate Revocation List.
- **OCSP** — online status check; faster than CRL.
- **Chain of trust** — leaf → intermediate(s) → root.

### 21.3 OpenSSL

```bash
# Random
openssl rand -hex 32

# Hashes / checksums
openssl dgst -sha256 file
openssl sha256 file

# Key generation
openssl genrsa -out priv.pem 4096
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:4096 -out priv.pem
openssl ecparam -genkey -name prime256v1 -out ec.pem
openssl pkey -in priv.pem -pubout -out pub.pem
openssl rsa  -in priv.pem -pubout -out pub.pem

# CSR
openssl req -new -key priv.pem -out req.csr \
    -subj "/C=US/ST=CA/L=SF/O=Example/CN=www.example.com"
openssl req -in req.csr -noout -text                # decode

# Self-signed
openssl req -x509 -newkey rsa:4096 -keyout priv.pem -out cert.pem -days 365 -nodes \
    -subj "/CN=test.local"

# Sign a CSR with your CA
openssl x509 -req -in req.csr -CA ca.pem -CAkey ca.key -CAcreateserial \
    -out cert.pem -days 365 -sha256 -extfile ext.cnf

# Inspect cert
openssl x509 -in cert.pem -noout -text
openssl x509 -in cert.pem -noout -subject -issuer -dates
openssl x509 -in cert.pem -noout -fingerprint -sha256

# Verify chain
openssl verify -CAfile ca.pem cert.pem
openssl verify -CAfile chain.pem cert.pem

# Test TLS endpoint
openssl s_client -connect www.example.com:443 -servername www.example.com
openssl s_client -connect mail.example.com:25 -starttls smtp

# Convert
openssl x509 -in cert.crt -out cert.pem -outform PEM
openssl rsa -in priv.key -out priv.pem
openssl pkcs12 -export -in cert.pem -inkey priv.pem -out bundle.p12 -name "mycert"
openssl pkcs12 -in bundle.p12 -nodes -out unbundled.pem
```

### 21.4 GnuPG Deep Dive

(Basics in Chapter 9.) Trust model:

- **Web of trust** — you sign keys of people you've verified; others trust your signatures by your reputation.
- **Trust levels**: `unknown`, `never`, `marginal`, `full`, `ultimate` (only your own keys).
- A key is **valid** if signed by an ultimately-trusted key (yours) or by sufficiently many marginally-trusted ones.

Best-practice key generation: separate subkeys for signing, encryption, authentication; primary key only for certification.

```bash
gpg --quick-gen-key 'Alice <alice@example.com>' ed25519 default 1y
gpg --quick-add-key KEYID cv25519 encr 1y
gpg --quick-add-key KEYID ed25519 sign 1y
gpg --quick-add-key KEYID ed25519 auth 1y

gpg --list-sigs KEYID
gpg --sign-key OTHER-KEYID
gpg --lsign-key OTHER-KEYID                # local signature (not exported)
gpg --send-keys KEYID --keyserver hkps://keys.openpgp.org
gpg --search-keys 'alice@example.com'
```

### 21.5 SELinux

Modes (set via `/etc/selinux/config` or runtime):

| Mode | Effect |
|---|---|
| `enforcing` | Policy enforced |
| `permissive` | Violations logged only |
| `disabled` | SELinux off entirely (requires reboot to re-enable) |

```bash
getenforce
setenforce 1                    # enforcing
setenforce 0                    # permissive
sestatus                        # full status
```

SELinux context format: `user_u:role_r:type_t:level`. The **type** is what most policies check.

```bash
ls -Z /etc/passwd
ps -eZ | head
id -Z                           # current process context
```

Common contexts: `unconfined_u:object_r:user_home_t:s0`, `system_u:system_r:httpd_t:s0`.

Tools:

```bash
chcon -t httpd_sys_content_t /srv/www/index.html    # temp context change
restorecon -Rv /srv/www                              # restore from policy
semanage fcontext -a -t httpd_sys_content_t '/srv/www(/.*)?'
restorecon -Rv /srv/www                              # apply policy

semanage port -l | grep ssh
semanage port -a -t ssh_port_t -p tcp 2222

getsebool -a | grep httpd
setsebool -P httpd_can_network_connect on            # -P = persistent

ausearch -m AVC -ts recent                            # find denials
ausearch -m AVC -ts recent | audit2why               # explain likely cause first
ausearch -m AVC -ts recent | audit2allow -M myhttpd  # generate a narrowly scoped candidate
semodule -i myhttpd.pp                                # install module
semodule -l                                           # list modules
semodule -r myhttpd                                   # remove
```

**TRAP:** A common mistake is troubleshooting "permission denied" without checking `getenforce`. Run `ausearch -m AVC` first. Never install an `audit2allow -a` policy blindly: most denials are fixed by correct labels, an existing boolean, or application configuration. Read the generated `.te` file and test the least privilege rule.

### 21.6 AppArmor

Per-binary path-based MAC, common on Ubuntu/SUSE. Profiles in `/etc/apparmor.d/`.

Modes: **enforce** and **complain**.

```bash
aa-status
aa-enforce /etc/apparmor.d/usr.sbin.nginx
aa-complain /etc/apparmor.d/usr.sbin.nginx
aa-disable /etc/apparmor.d/usr.sbin.nginx
aa-genprof /usr/bin/myapp                # generate a profile interactively
aa-logprof                                # learn from logs and update
apparmor_parser -r /etc/apparmor.d/profile
```

Profile snippet:

```
#include <tunables/global>
/usr/sbin/nginx {
    #include <abstractions/base>
    #include <abstractions/nis>
    capability dac_override,
    capability net_bind_service,
    capability setgid,
    capability setuid,
    capability sys_resource,
    network inet stream,
    network inet6 stream,
    /etc/nginx/** r,
    /var/log/nginx/* w,
    /var/cache/nginx/** rw,
    /var/run/nginx.pid w,
    /usr/share/nginx/** r,
    /var/www/** r,
}
```

### 21.7 Connection Tracking (conntrack)

`/proc/net/nf_conntrack` (or `/proc/net/ip_conntrack` on older kernels) lists active flows.

```bash
conntrack -L                            # list
conntrack -L -p tcp --dport 22
conntrack -E                            # follow events
conntrack -D --orig-src 1.2.3.4         # delete flow
```

State machine: `NEW`, `ESTABLISHED`, `RELATED`, `INVALID`, `UNTRACKED`. Used by iptables/nftables for stateful filtering.

### 21.8 IDS/IPS — Snort, Suricata

- **Snort** — venerable signature-based IDS/IPS. Rules in `/etc/snort/rules/*.rules`.
- **Suricata** — modern, multi-threaded, supports same rule format as Snort.

```bash
snort -A console -c /etc/snort/snort.conf -i eth0
suricata -i eth0 -c /etc/suricata/suricata.yaml
```

Rules look like:

```
alert tcp any any -> $HOME_NET 22 (msg:"SSH brute force"; flow:established,to_server; \
       threshold: type both, track by_src, count 5, seconds 60; sid:1000001;)
```

### 21.9 File Auditing — auditd

`auditd` is the kernel-level audit subsystem. Rules in `/etc/audit/rules.d/*.rules`.

```bash
auditctl -l                       # list active rules
auditctl -e 1                     # enable
auditctl -w /etc/passwd -p wa -k passwd-changes
auditctl -a always,exit -F arch=b64 -S execve -F auid>=1000 -k user-cmds
ausearch -k passwd-changes
ausearch -m USER_LOGIN
aureport                          # summary report
aureport --auth
aureport --failed
```

`-w PATH -p [rwxa] -k KEY` watches a path. `-a always,exit -S syscall` traces syscalls.

### 21.10 Security Scanning

- **OpenVAS / Greenbone** — full vulnerability scanner.
- **Lynis** — host-side audit tool (`lynis audit system`).
- **OSCAP / OpenSCAP** — SCAP compliance scanning.

### 21.11 Rootkit Detection

```bash
rkhunter --update
rkhunter --check
chkrootkit
```

### 21.12 Advanced Network Security Tools

```bash
nmap -sV -O -A target              # version + OS + scripts
nmap --script vuln target
nmap -sU -sV target                # UDP version detection

wireshark                          # GUI
tshark -i eth0 -f 'tcp port 80'
tshark -r capture.pcap -Y 'http.request'
tshark -i eth0 -w out.pcap

# Decrypt TLS in Wireshark by capturing SSLKEYLOGFILE
SSLKEYLOGFILE=/tmp/sslkeys.log firefox
# Wireshark → Preferences → Protocols → TLS → (Pre)-Master-Secret log filename
```

**Exercises**
- *Exercise 1:* Generate a self-signed CA and use it to sign a server certificate; verify the chain with `openssl verify`.
- *Exercise 2:* Diagnose an SELinux AVC denial in `httpd`, then craft a policy module with `audit2allow`.

**Mock Exam Questions**

**Q1.** Which SELinux mode logs denials but does not enforce them?
- A) `disabled`  B) `permissive`  C) `enforcing`  D) `passive`

**A:** **B.**

**Q2.** Which command persistently changes the type label of a directory tree?
- A) `chcon -R -t httpd_sys_content_t /srv/www`
- B) `semanage fcontext -a -t httpd_sys_content_t '/srv/www(/.*)?' && restorecon -R /srv/www`
- C) `setsebool -P httpd_anon_write on`
- D) `audit2allow -M`

**A:** **B.** `chcon` is wiped by a relabel; `semanage fcontext` is the persistent way.

**Q3 (Scenario).** A web server denies access to a custom directory. SELinux is enforcing. What is the most efficient first step?

**A:** `ausearch -m AVC -ts recent` to see if it's an AVC denial. If so, label the path correctly (`semanage fcontext` + `restorecon`) or toggle the relevant boolean (`setsebool -P`).

**Q4.** OCSP differs from CRL primarily in:
- A) OCSP is encrypted, CRL is not
- B) OCSP is a real-time per-certificate check; CRL is a periodically published list
- C) OCSP requires DNSSEC
- D) CRL is only for code signing

**A:** **B.**

---

## Chapter 22: Virtualization & Containers (Exam 305)

### 22.1 Virtualization Concepts

- **Type 1 (bare-metal hypervisor)** — runs directly on hardware (KVM (Linux turns into a Type 1), VMware ESXi, Xen).
- **Type 2 (hosted)** — runs as an app inside an OS (VirtualBox, VMware Workstation).
- **Full virtualization** — guest unmodified, hypervisor traps privileged instructions (with hardware assist: Intel VT-x, AMD-V).
- **Paravirtualization** — guest OS is modified to call hypervisor for performance (Xen PV).
- **HVM** — full virtualization with hardware extensions.
- **Containers** — share host kernel; isolate process trees, namespaces, cgroups.

### 22.2 KVM/QEMU

KVM is a kernel module that turns Linux into a hypervisor. QEMU is the userland that emulates devices.

```bash
lsmod | grep kvm                              # kvm + kvm_intel/kvm_amd
egrep -c '(svm|vmx)' /proc/cpuinfo            # > 0 means hardware-assisted virt available
modprobe kvm_intel                            # or kvm_amd
apt install qemu-kvm libvirt-daemon-system virtinst bridge-utils
```

#### `virsh` — the libvirt CLI

`virsh` queries and changes objects managed by libvirt: domains, networks, storage pools, volumes and snapshots. Distinguish persistent configuration from live state—`define` stores a domain for later starts, `create` starts a transient domain, and many edits need explicit `--live`/`--config` scope. Verify both with `dominfo`/`dumpxml` and guest functionality; a “running” domain is not proof the OS or service is healthy.

```bash
virsh list --all
virsh start vmname
virsh shutdown vmname             # ACPI graceful
virsh destroy vmname              # force off
virsh reboot vmname
virsh suspend vmname              # pause
virsh resume vmname
virsh define vm.xml               # register (no start)
virsh undefine vmname              # unregister
virsh create vm.xml               # one-shot start (no persist)
virsh dominfo vmname
virsh dumpxml vmname               # current XML
virsh edit vmname                  # edit (with daemon-reload)
virsh autostart vmname
virsh console vmname

# Snapshots
virsh snapshot-create-as vmname snap1
virsh snapshot-list vmname
virsh snapshot-revert vmname snap1
virsh snapshot-delete vmname snap1

# Live migration
virsh migrate --live vmname qemu+ssh://target/system
virsh migrate --live --copy-storage-all vmname qemu+ssh://target/system

# Storage pools/volumes
virsh pool-list --all
virsh pool-define-as default dir --target /var/lib/libvirt/images
virsh pool-build default
virsh pool-start default
virsh pool-autostart default
virsh vol-create-as default disk.qcow2 20G --format qcow2

# Networks
virsh net-list --all
virsh net-define net.xml
virsh net-start default
```

#### `virt-install`

`virt-install` assembles a libvirt domain definition and launches an installation from explicit CPU, memory, disk, network and install-source choices. It does not install a safe guest automatically: storage paths/capacity, bridge exposure, firmware mode, console access and unattended credentials are administrator decisions. Use `--print-xml`/dry planning where available and keep base images immutable when using copy-on-write children.

```bash
virt-install \
    --name vm1 --ram 2048 --vcpus 2 \
    --disk path=/var/lib/libvirt/images/vm1.qcow2,size=20,format=qcow2 \
    --network network=default \
    --graphics none --console pty,target_type=serial \
    --location 'http://archive.ubuntu.com/ubuntu/dists/jammy/main/installer-amd64/' \
    --extra-args 'console=ttyS0,115200n8 serial'
```

#### Domain XML highlights

```xml
<domain type='kvm'>
  <name>vm1</name>
  <memory unit='MiB'>2048</memory>
  <vcpu>2</vcpu>
  <os>
    <type arch='x86_64' machine='q35'>hvm</type>
    <boot dev='hd'/>
  </os>
  <devices>
    <disk type='file' device='disk'>
      <driver name='qemu' type='qcow2'/>
      <source file='/var/lib/libvirt/images/vm1.qcow2'/>
      <target dev='vda' bus='virtio'/>
    </disk>
    <interface type='network'>
      <source network='default'/>
      <model type='virtio'/>
    </interface>
    <graphics type='vnc' port='-1'/>
  </devices>
</domain>
```

Network modes:
- **bridged** — guest gets an IP on the host's LAN; needs `br0` on host.
- **NAT** — guest behind libvirt's `virbr0`, masqueraded.
- **host-only** — host ↔ guest, no external.
- **isolated** — guest ↔ guest only.

### 22.3 Xen

```bash
xl list
xl create /etc/xen/vm1.cfg
xl destroy vm1
xl console vm1
xl shutdown vm1
xl save vm1 vm1.state
xl restore vm1.state
xl migrate vm1 target
```

Domains: **dom0** (privileged, hosts drivers), **domU** (guests). PV (paravirtual) guests use special kernel; HVM uses full virt.

### 22.4 Docker

#### Concepts

- **Image** — read-only layered filesystem template.
- **Container** — running (or stopped) instance of an image, with a writable layer.
- **Volume** — host-managed persistent storage.
- **Bind mount** — host path mounted into container.
- **Network** — virtual network (bridge, host, overlay, macvlan).

#### Command reference

Docker commands operate on different object lifecycles: images are immutable templates, containers are runtime instances with a writable layer, volumes persist data independently, and networks provide connectivity. `run` combines create+start; `exec` starts another process in an existing container; `stop` requests graceful termination before kill; `rm` removes container metadata/writable state but not automatically every volume/image. Inspect mounts, published ports, user, capabilities and health rather than treating “Up” as application health.

```bash
docker pull nginx:1.27
docker images
docker rmi IMAGE

docker run -d --name web -p 80:80 nginx
docker run -it --rm ubuntu bash
docker run -d --restart unless-stopped \
    -v /srv/data:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=secret \
    --network mynet \
    -p 3306:3306 \
    mysql:8

docker ps
docker ps -a
docker stop NAME
docker start NAME
docker restart NAME
docker rm NAME
docker logs -f NAME
docker exec -it NAME bash
docker inspect NAME
docker top NAME
docker stats
docker cp NAME:/path /host
docker commit NAME image:tag

docker network create mynet
docker network ls
docker network inspect mynet
docker network connect mynet NAME

docker volume create data
docker volume ls
docker volume inspect data
docker volume rm data

docker build -t myapp:1.0 .
docker history myapp:1.0
docker tag myapp:1.0 registry.example.com/myapp:1.0
docker push registry.example.com/myapp:1.0
docker save myapp:1.0 | gzip > myapp.tgz
gunzip -c myapp.tgz | docker load

docker system df
docker system prune -a --volumes      # nuke unused
```

#### Dockerfile

| Instruction | Purpose |
|---|---|
| `FROM` | Base image |
| `RUN` | Build-time shell command |
| `COPY` / `ADD` | Files into image (ADD also extracts tars and fetches URLs — prefer COPY) |
| `ENV` | Environment variable |
| `ARG` | Build-time variable |
| `WORKDIR` | Set cwd |
| `USER` | Switch user |
| `EXPOSE` | Document port (does not publish) |
| `CMD` | Default command (overridable) |
| `ENTRYPOINT` | Always run; args appended |
| `VOLUME` | Declare a volume mount point |
| `HEALTHCHECK` | Liveness command |
| `LABEL` | Metadata |
| `STOPSIGNAL` | Default kill signal |
| `ONBUILD` | Trigger for downstream builds |
| `SHELL` | Change RUN's shell |

```dockerfile
FROM python:3.12-slim AS base
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY src/ .
EXPOSE 8000
USER nobody
HEALTHCHECK --interval=30s CMD curl -fsS http://localhost:8000/health || exit 1
ENTRYPOINT ["python", "main.py"]
```

Multi-stage build:

```dockerfile
FROM golang:1.22 AS build
WORKDIR /src
COPY . .
RUN CGO_ENABLED=0 go build -o /app

FROM scratch
COPY --from=build /app /app
ENTRYPOINT ["/app"]
```

#### Docker Compose

Compose declares a multi-container application model—services, networks, volumes, configs and dependencies—and reconciles it on one engine. `docker compose config` renders merged/interpolated configuration before mutation; `up -d` creates/updates runtime objects; `down` removes the project containers/networks but retains named volumes unless explicitly requested. `depends_on` ordering does not universally mean the dependency is ready; use health checks and application retry logic.

```yaml
services:
  web:
    image: nginx:1.27
    ports: ["80:80"]
    volumes: ["./html:/usr/share/nginx/html:ro"]
    depends_on: [api]
    restart: unless-stopped
  api:
    build: ./api
    environment:
      DB_HOST: db
    networks: [back]
  db:
    image: postgres:16
    volumes: ["pgdata:/var/lib/postgresql/data"]
    networks: [back]
    environment:
      POSTGRES_PASSWORD_FILE: /run/secrets/db_password
    secrets: [db_password]
networks:
  back: {}
volumes:
  pgdata: {}
secrets:
  db_password:
    file: ./secrets/db_password.txt
```

```bash
docker compose up -d
docker compose ps
docker compose logs -f
docker compose down
docker compose down -v          # also remove volumes
docker compose pull
docker compose build
```

#### Security

- Drop capabilities: `--cap-drop=ALL --cap-add=NET_BIND_SERVICE`.
- `--read-only` root FS, mount tmpfs where writes needed.
- `--no-new-privileges` to prevent setuid escalation.
- `--user=10000:10000` non-root.
- Use specific image tags or digests, scan with `trivy` or `docker scan`.

### 22.5 Podman (Rootless)

Drop-in CLI compatible with Docker, daemonless, with native rootless support.

```bash
podman pull nginx
podman run -d -p 8080:80 nginx
podman ps
# Modern persistent approach: create ~/.config/containers/systemd/web.container (Quadlet), then:
systemctl --user daemon-reload
systemctl --user enable --now web.service
# `podman generate systemd` remains relevant on older installations but is deprecated upstream.
```

### 22.6 LXC / LXD

System containers (more like lightweight VMs than app containers).

```bash
lxd init                                  # interactive setup
lxc launch ubuntu:24.04 c1
lxc list
lxc exec c1 -- bash
lxc file push file.txt c1/root/
lxc snapshot c1 snap1
lxc restore c1 snap1
lxc stop c1
lxc delete c1
```

Profile and config are stored in LXD's database.

### 22.7 Kubernetes Fundamentals

- **Pod** — smallest unit, one or more containers sharing network and storage.
- **ReplicaSet** — ensures N replica pods.
- **Deployment** — manages ReplicaSets, rolling updates.
- **Service** — stable network endpoint (ClusterIP, NodePort, LoadBalancer).
- **Namespace** — isolation for objects.
- **ConfigMap / Secret** — configuration and secret data.
- **Ingress** — HTTP/HTTPS routing (needs an Ingress controller).
- **PersistentVolume / PVC** — storage abstraction.
- **DaemonSet** — one pod per node.
- **StatefulSet** — ordered, identity-bearing pods.
- **Job / CronJob** — batch and scheduled tasks.

```bash
kubectl get pods
kubectl get pods -A                         # all namespaces
kubectl get pods -n kube-system
kubectl get deploy,svc,ingress
kubectl describe pod NAME
kubectl logs POD [-c container]
kubectl logs -f POD
kubectl exec -it POD -- sh
kubectl apply -f manifest.yaml
kubectl delete -f manifest.yaml
kubectl rollout status deploy/myapp
kubectl rollout undo deploy/myapp
kubectl scale deploy/myapp --replicas=5
kubectl port-forward svc/myapp 8080:80
kubectl top nodes
kubectl top pods
```

Sample deployment + service:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata: { name: web }
spec:
  replicas: 3
  selector: { matchLabels: { app: web } }
  template:
    metadata: { labels: { app: web } }
    spec:
      containers:
        - name: nginx
          image: nginx:1.27
          ports: [{ containerPort: 80 }]
---
apiVersion: v1
kind: Service
metadata: { name: web }
spec:
  selector: { app: web }
  ports: [{ port: 80, targetPort: 80 }]
  type: ClusterIP
```

### 22.8 OpenStack Components (overview)

| Component | Role |
|---|---|
| Keystone | Identity (users, projects, tokens) |
| Nova | Compute (VMs) |
| Neutron | Networking (virtual nets, routers, sec groups) |
| Cinder | Block storage |
| Glance | Image service |
| Swift | Object storage |
| Horizon | Web UI |
| Heat | Orchestration (templates) |
| Magnum | Container infra |
| Ironic | Bare-metal provisioning |

### 22.9 Cloud-init

Userdata scripts/YAML executed at first boot of a cloud instance.

```yaml
#cloud-config
hostname: web01
users:
  - name: alice
    sudo: ALL=(ALL) NOPASSWD:ALL
    ssh_authorized_keys:
      - ssh-ed25519 AAAA...
package_update: true
packages: [nginx, fail2ban]
write_files:
  - path: /etc/motd
    content: Welcome!
runcmd:
  - systemctl enable --now nginx
```

Useful files: `/var/log/cloud-init.log`, `/var/log/cloud-init-output.log`, `/var/lib/cloud/`.

**Exercises**
- *Exercise 1:* Create a libvirt VM from a cloud-init-enabled image, using a NoCloud datasource ISO.
- *Exercise 2:* Build a multi-stage Dockerfile that produces a 10-MB image of a Go binary.

**Mock Exam Questions**

**Q1.** Which libvirt network mode masquerades guests behind the host's IP?
- A) bridged  B) NAT  C) host-only  D) isolated

**A:** **B.**

**Q2.** What's the chief functional difference between `CMD` and `ENTRYPOINT` in a Dockerfile?
- A) None
- B) `CMD` is fixed; `ENTRYPOINT` can be overridden
- C) `ENTRYPOINT` always runs; arguments to `docker run` are appended. `CMD` provides default args (or default command) that are overridden
- D) `ENTRYPOINT` is only for build

**A:** **C.**

**Q3 (Scenario).** A pod is in `CrashLoopBackOff`. First three diagnostics?

**A:** `kubectl describe pod` (events, last exit code, container status), `kubectl logs POD` (and `--previous` for the failed instance), `kubectl get events --sort-by=.metadata.creationTimestamp`.

---

## Chapter 23: High Availability & Storage Clusters (Exam 306)

### 23.1 HA Concepts

- **SPOF (Single Point of Failure)** — a single component whose failure brings down the service. Eliminating SPOFs is the goal of HA.
- **Fencing (STONITH)** — "Shoot The Other Node In The Head". If a node misbehaves, force it offline (IPMI power-off, network port, etc.) to prevent split-brain.
- **Quorum** — majority needed to operate. With n nodes, you need ⌊n/2⌋+1 for quorum.
- **Split-brain** — partitioned cluster where each side thinks it's the only one — risk of data corruption.
- **Heartbeat / Membership** — protocol that nodes use to detect each other's presence (Corosync, ring 0/ring 1).

### 23.2 Pacemaker + Corosync

Corosync handles cluster membership and messaging; Pacemaker is the resource manager built on top.

#### Setup

```bash
# On all nodes
yum install pacemaker corosync pcs
systemctl enable --now pcsd
passwd hacluster
pcs host auth node1 node2 -u hacluster

# From one node
pcs cluster setup mycluster node1 node2
pcs cluster start --all
pcs cluster enable --all
pcs status
```

#### Resources

Pacemaker resources are managed services/addresses/filesystems described through resource agents. Creating one delegates start, stop and monitor actions to the cluster; it does not copy application data or make an unsafe service cluster-aware. Inspect agent metadata, choose correct monitor intervals/timeouts, and test start/stop/monitor manually before relying on recovery.

```bash
pcs resource list                     # available agents
pcs resource create VirtualIP ocf:heartbeat:IPaddr2 ip=192.168.1.100 cidr_netmask=24 op monitor interval=30s
pcs resource create WebSrv systemd:nginx op monitor interval=30s
pcs resource group add web VirtualIP WebSrv      # group: must run together, in order
pcs resource clone WebSrv                          # run on all nodes
pcs resource update VirtualIP ip=192.168.1.101
pcs resource delete VirtualIP
pcs resource move WebSrv node2
pcs resource clear WebSrv                          # remove location constraint from move
```

#### Constraints

Constraints express policy rather than imperative moves: location preferences choose nodes, colocation ties placement, and ordering sequences actions. Scores and direction matter, and over-constraining can leave resources intentionally stopped. Use `pcs constraint config` plus simulation/status to explain why the scheduler chose a placement before forcing it.

```bash
pcs constraint location WebSrv prefers node1=100
pcs constraint colocation add WebSrv with VirtualIP
pcs constraint order VirtualIP then WebSrv
pcs constraint list
```

#### STONITH

STONITH/fencing gives the cluster proof that an uncertain node cannot access shared resources. It is a data-integrity prerequisite, not an optional reboot convenience. Configure independent credentials/path, map devices to nodes correctly, and perform an approved real fence test; listing a device successfully does not prove it can isolate the failed node during a partition.

```bash
pcs property set stonith-enabled=true
pcs stonith create fence_node1 fence_ipmilan ipaddr=192.168.1.11 lanplus=1 login=admin passwd=... pcmk_host_list=node1
pcs stonith status
```

In labs without real fencing you can `pcs property set stonith-enabled=false` — never do this in production.

#### Pacemaker via `crm` (SUSE)

```bash
crm configure show
crm configure edit
crm status
crm node standby node1
crm node online node1
crm resource start WebSrv
```

### 23.3 DRBD — Distributed Replicated Block Device

DRBD replicates a block device across two (or more) nodes synchronously or asynchronously.

Protocols:
- **A** — async; ACK after sending to TCP buffer.
- **B** — semi-sync; ACK after received by peer kernel.
- **C** — sync; ACK after committed on peer disk. *Most common in HA.*

`/etc/drbd.conf` typically includes `/etc/drbd.d/*.res`.

```
resource r0 {
    protocol C;
    device    /dev/drbd0;
    disk      /dev/sdb1;
    meta-disk internal;
    on node1 { address 192.168.1.11:7788; }
    on node2 { address 192.168.1.12:7788; }
}
```

```bash
drbdadm create-md r0                   # create metadata on both nodes
drbdadm up r0                          # start
drbdadm primary --force r0             # on one node only, initial sync
mkfs.ext4 /dev/drbd0                   # only after primary
mount /dev/drbd0 /mnt/data

drbdadm status
cat /proc/drbd                          # kernel view
drbdadm secondary r0
drbdadm primary r0
drbdadm disconnect r0
drbdadm connect r0
drbdadm verify r0                      # online verification
```

Roles per node: **Primary** (can mount), **Secondary** (replicating, not mounted). With Pacemaker, only one node is Primary at a time (or both with dual-primary + cluster FS).

#### Pacemaker integration

```
pcs resource create DrbdData ocf:linbit:drbd drbd_resource=r0 op monitor interval=30s
pcs resource promotable DrbdData promoted-max=1 promoted-node-max=1 clone-max=2
pcs resource create DataFS Filesystem device=/dev/drbd0 directory=/mnt/data fstype=ext4
pcs constraint colocation add DataFS with DrbdData-clone INFINITY with-rsc-role=Master
pcs constraint order promote DrbdData-clone then start DataFS
```

### 23.4 HAProxy

Layer-4/Layer-7 load balancer.

```
global
    log /dev/log local0
    maxconn 50000
    user haproxy
    group haproxy
    daemon
    stats socket /run/haproxy/admin.sock mode 660 level admin

defaults
    log     global
    mode    http
    option  httplog
    option  dontlognull
    timeout connect 5s
    timeout client  30s
    timeout server  30s
    retries 3

frontend http_in
    bind *:80
    bind *:443 ssl crt /etc/haproxy/certs/example.pem
    redirect scheme https if !{ ssl_fc }
    default_backend webservers
    acl is_api path_beg /api
    use_backend api_servers if is_api

backend webservers
    balance roundrobin
    option httpchk GET /healthz
    server web1 10.0.0.11:80 check
    server web2 10.0.0.12:80 check
    server web3 10.0.0.13:80 check backup

backend api_servers
    balance leastconn
    server api1 10.0.0.21:8080 check
    server api2 10.0.0.22:8080 check

listen stats
    bind *:8404
    stats enable
    stats uri /stats
    stats refresh 5s
    stats auth admin:secret
```

Algorithms: `roundrobin`, `static-rr`, `leastconn`, `source`, `uri`, `url_param`, `hdr(name)`, `random`.

Health checks: `check`, `option httpchk`, `httpchk GET /path`.

```bash
haproxy -c -f /etc/haproxy/haproxy.cfg     # syntax check
systemctl reload haproxy
echo "show servers state" | socat /run/haproxy/admin.sock stdio
```

### 23.5 Keepalived — VRRP

Virtual Router Redundancy Protocol: a virtual IP floats between routers.

```
vrrp_instance VI_1 {
    state MASTER
    interface eth0
    virtual_router_id 51
    priority 150
    advert_int 1
    authentication {
        auth_type PASS
        auth_pass secret
    }
    virtual_ipaddress {
        192.168.1.100/24
    }
    track_script {
        chk_haproxy
    }
}

vrrp_script chk_haproxy {
    script "pidof haproxy"
    interval 2
    weight -20
}
```

`state BACKUP` and lower `priority` on the other node. The peer with the higher *effective* priority owns the VIP.

### 23.6 GlusterFS

Scale-out NAS combining storage from multiple servers (peers) into volumes.

Volume types:
- **Distribute** — files split across bricks (no redundancy).
- **Replica N** — each file mirrored on N bricks.
- **Disperse** — erasure-coded.
- **Distributed-Replicate**, **Distributed-Disperse** — combinations.

```bash
# On each peer
systemctl enable --now glusterd

# From peer1
gluster peer probe peer2
gluster peer status

# Create volume (replica 2 across 2 bricks)
gluster volume create gv0 replica 2 \
    peer1:/data/brick1/gv0 peer2:/data/brick1/gv0
gluster volume start gv0
gluster volume info gv0
gluster volume status gv0

# Mount on a client
yum install glusterfs-client
mount -t glusterfs peer1:/gv0 /mnt/gv0
# /etc/fstab:
peer1:/gv0   /mnt/gv0   glusterfs   defaults,_netdev   0  0

# Expand
gluster volume add-brick gv0 replica 2 peer3:/data/brick1/gv0 peer4:/data/brick1/gv0
gluster volume rebalance gv0 start

# Heal
gluster volume heal gv0 info
gluster volume heal gv0 full
```

### 23.7 Ceph

Object-based, scale-out storage. Components:

| Daemon | Role |
|---|---|
| **MON** | Monitors — maintain cluster map, quorum |
| **OSD** | Object Storage Daemon — one per disk |
| **MDS** | Metadata Server — only for CephFS |
| **MGR** | Manager — metrics, dashboard |
| **RGW** | RADOS Gateway — S3/Swift API |

Interfaces:
- **RBD** — RADOS Block Device (block storage).
- **CephFS** — POSIX filesystem.
- **RGW** — object storage via S3/Swift.

```bash
ceph -s                                # cluster status
ceph health detail
ceph osd tree
ceph osd df
ceph df
ceph pool ls
ceph pool create rbdpool 128 128
ceph osd pool application enable rbdpool rbd

# RBD
rbd create rbdpool/disk1 --size 10G
rbd map rbdpool/disk1
rbd showmapped
mkfs.ext4 /dev/rbd0
mount /dev/rbd0 /mnt/rbd

# CephFS
ceph fs volume create myfs
mount -t ceph mon1:6789:/ /mnt/cephfs -o name=admin,secret=AQ...
```

Cluster bootstrap with `cephadm`:

```bash
cephadm bootstrap --mon-ip 10.0.0.10
ceph orch apply mon 3
ceph orch host add node2 10.0.0.11
ceph orch device ls
ceph orch apply osd --all-available-devices
```

### 23.8 Cluster Filesystems (OCFS2, GFS2)

Both let multiple nodes mount the same block device simultaneously (e.g., over SAN/DRBD dual-primary).

- **OCFS2** — Oracle Cluster FS, uses its own DLM (`o2cb`).
- **GFS2** — Red Hat, integrates with Pacemaker + DLM.

```bash
mkfs.gfs2 -p lock_dlm -t cluster_name:fsname -j 3 /dev/drbd0
mount -t gfs2 /dev/drbd0 /mnt/shared

mkfs.ocfs2 -L data /dev/sdb1
mount -t ocfs2 /dev/sdb1 /mnt/data
```

Required: cluster manager configured, DLM running, fencing in place.

### 23.9 Shared Storage — iSCSI Multipath, FC

```bash
# Multipath
yum install device-mapper-multipath
mpathconf --enable --with_multipathd y
multipath -ll
multipath -v3
```

`/etc/multipath.conf`:

```
defaults {
    user_friendly_names yes
    find_multipaths yes
}
blacklist {
    devnode "^sd[a]$"
}
```

Devices appear as `/dev/mapper/mpathX`. Use that name in `/etc/fstab` or LVM PV creation.

**Exercises**
- *Exercise 1:* Build a 2-node Pacemaker cluster with a floating VIP that follows nginx.
- *Exercise 2:* Replicate `/dev/sdb1` between two hosts with DRBD protocol C and verify failover.

**Mock Exam Questions**

**Q1.** Which DRBD protocol acknowledges only after data is on disk on the peer?
- A) A  B) B  C) C  D) D

**A:** **C.**

**Q2.** In an HA cluster, the *purpose* of fencing is:
- A) Encrypting cluster traffic
- B) Forcibly removing a misbehaving node so it cannot corrupt shared state
- C) Limiting which clients can connect
- D) Splitting work between nodes

**A:** **B.**

**Q3 (Scenario).** Two HA nodes lose their interconnect. Both decide they are primary. What's the term, and what mechanism prevents it?

**A:** Split-brain. Prevention: STONITH/fencing plus quorum (often a witness/quorum disk in 2-node setups).

**Q4.** Which Ceph component serves S3-compatible object APIs?
- A) MDS  B) RGW  C) MON  D) OSD

**A:** **B.**

**Q5.** Which HAProxy directive enables HTTP-mode health checks?
- A) `tcp-check`  B) `option httpchk GET /path`  C) `monitor-uri /path`  D) `httpcheck`

**A:** **B.**

---

# PART 4 — Objective-Aligned Completion & Professional Labs

### Objective coverage map

Use this map as a navigation aid; use the current LPI page for the authoritative per-objective weight and partial command list.

| Exam | Official topic families | Primary coverage |
|---|---|---|
| 101-500 | 101 architecture; 102 installation/packages; 103 GNU commands; 104 devices/filesystems/FHS | Chapters 1–4, 24 |
| 102-500 | 105 shells/scripts; 106 interfaces/desktops; 107 administration; 108 services; 109 networking; 110 security | Chapters 5–9, 25 |
| 201-450 | 200 capacity; 201 kernel; 202 startup; 203 filesystems/devices; 204 storage; 205 networking; 206 maintenance | Chapters 10–14, 26 |
| 202-450 | 207 DNS; 208 web; 209 file sharing; 210 network clients; 211 mail; 212 security | Chapters 15–19, 27 |
| 300-300 | Samba basics/AD/shares/clients; Linux identity and file sharing | Chapters 20, 28 |
| 303-300 | Cryptography; host security; access control; network security; threats/vulnerability assessment | Chapters 9, 13, 19, 21, 29 |
| 305-300 | Full virtualization; container virtualization; VM deployment/provisioning | Chapters 22, 30 |
| 306-300 | HA cluster management; HA cluster storage | Chapters 23, 30 |

**Study rule:** when an objective has a higher official weight, allocate proportionally more lab and question time. A long chapter is not evidence of a high exam weight.

## Chapter 24: How Commands Work — Intent, Data Flow, Verification, and Safety

Memorizing flags is fragile. An administrator first identifies the **state to observe or change**, then chooses the narrowest command, predicts its output and side effects, verifies the result through an independent view, and keeps a rollback path.

### 24.1 The command reasoning card

For every command, answer seven questions:

| Question | Why it matters |
|---|---|
| Intent | What problem does the command solve? |
| Input | Arguments, stdin, files, kernel API, or network? |
| Output | Human text, machine format, stdout, stderr, or exit status? |
| Authority | Regular user, root, capability, group, or remote credential? |
| Side effect | Query-only, temporary runtime change, or persistent change? |
| Verification | Which independent command proves the desired state? |
| Rollback | How is the old state restored? |

Example—`ip route replace default via 192.0.2.1 dev eth0`:

- **Intent:** select the next hop for destinations with no more-specific route.
- **Why `replace`:** unlike `add`, it is useful in repeatable scripts because it creates or updates the route.
- **Input:** destination `default`, gateway, and output interface.
- **Side effect:** changes the running kernel routing table only; it does not edit NetworkManager/netplan configuration.
- **Verify:** `ip route get 1.1.1.1` shows the route the kernel would actually choose.
- **Rollback:** restore the previous route captured with `ip -json route show default`.

### 24.2 Syntax is parsed in layers

```bash
LC_ALL=C find /var/log -type f -mtime -7 -print0 2>errors.log |
  xargs -0r grep -Hn -- 'authentication failure' >matches.txt
```

1. The shell expands variables/globs and creates redirections/pipes.
2. `find` walks the directory tree and emits NUL-delimited paths.
3. `2>errors.log` separates traversal errors from data.
4. `xargs -0` reconstructs arguments without breaking on spaces/newlines; `-r` avoids an empty invocation.
5. `grep -- PATTERN` uses `--` to end option parsing, so a pattern beginning with `-` is safe.
6. Exit statuses still matter: `grep` returns 0 for a match, 1 for no match, and >1 for an error.

**Logic:** pipes transport bytes, not “files” or structured objects. Quote expansions unless intentional splitting is required. Prefer NUL delimiters for filenames.

### 24.3 Query, runtime change, persistent change

Many Linux tasks have three distinct commands:

| Layer | Example | Meaning |
|---|---|---|
| Query | `sysctl net.ipv4.ip_forward` | Read current kernel state. |
| Runtime change | `sysctl -w net.ipv4.ip_forward=1` | Change until reboot/reconfiguration. |
| Persistence | file in `/etc/sysctl.d/*.conf` + `sysctl --system` | Declare desired boot-time state and apply it. |

The same model applies to `ip` versus NetworkManager configuration, `mount` versus `/etc/fstab`, `setenforce` versus `/etc/selinux/config`, and `systemctl start` versus `systemctl enable`.

### 24.4 Discovery commands

| Command | Job and logic |
|---|---|
| `type -a NAME` | Ask the shell whether NAME is an alias, function, builtin, or executable; use before assuming a man page describes what runs. |
| `command -V NAME` | Portable-ish shell description of command resolution. |
| `help BUILTIN` | Bash documentation for builtins such as `read`, `test`, and `printf`. |
| `man 1 command` | User command manual; sections 5 and 8 cover file formats and admin commands. |
| `apropos keyword` | Search manual descriptions when the command name is unknown. |
| `info coreutils 'command invocation'` | Detailed GNU documentation and edge cases. |
| `command --help` | Quick option reminder; not a replacement for the full manual. |

### 24.5 Machine-readable output

Do not parse decorative text if a stable format exists:

```bash
ip -json address show | jq -r '.[] | .ifname'
lsblk --json -o NAME,TYPE,FSTYPE,MOUNTPOINTS
systemctl show ssh.service -p ActiveState -p SubState --value
findmnt --json --target /var
```

`-json`/`--json` asks the producer for structure; `jq` selects fields. In scripts, set `LC_ALL=C` when parsing legacy text so translations do not alter keywords.

### 24.6 Safe mutation workflow

1. Capture state: `nft list ruleset > before.nft`.
2. Validate candidate: `nft --check -f candidate.nft`.
3. Ensure recovery: local console or timed rollback.
4. Apply atomically where supported: `nft -f candidate.nft`.
5. Verify behavior: `ss`, `ping`, `curl`, counters, and logs.
6. Persist only after runtime validation.

**Exercise:** choose `mount`, `useradd`, `systemctl`, and `nft`. Write a reasoning card for one query and one mutation from each family.

---

## Chapter 25: LPIC-1 Objective Completion — Scheduling, Localization, Desktops, and Printing

### 25.1 `cron`, `at`, and systemd timers

`cron` is for repeating calendar schedules. A user edits their installed table with `crontab -e`; the command validates and installs it rather than editing the spool file directly.

```bash
crontab -l                              # query the current user's table
crontab -e                              # edit/install safely
systemctl status cron.service           # Debian name; crond.service on many RPM systems
journalctl -u cron --since today        # verify executions where cron logs to journal
```

The five fields are minute, hour, day-of-month, month, day-of-week. The command runs with a small environment and a non-interactive shell, so use absolute paths and redirect output.

```cron
17 2 * * * /usr/local/sbin/backup-home >>/var/log/backup-home.log 2>&1
```

`at` schedules one job once:

```bash
printf '%s\n' '/usr/local/sbin/reindex' | at 23:30
atq                                     # list queued jobs; first column is job ID
at -c JOB_ID                            # inspect the captured environment and script
atrm JOB_ID                             # remove before execution
```

Use a systemd timer when the job needs dependency ordering, randomized delay, missed-run catch-up, resource limits, or journal integration. `systemctl list-timers --all` shows next/last activation; `systemctl cat name.timer` reveals the schedule.

### 25.2 Locales and character conversion

A locale controls language, collation, character classes, number formats, currency, and dates.

```bash
locale                                  # effective values after LANG/LC_* precedence
locale -a                               # names actually generated on this host
LC_ALL=C sort names.txt                 # byte-oriented deterministic order for scripts
localectl status                        # systemd host locale/keymap overview
iconv -f ISO-8859-1 -t UTF-8 old.txt >new.txt
file --mime-encoding old.txt            # heuristic input-encoding evidence
```

`LANG` supplies defaults; an individual `LC_TIME` overrides one category; `LC_ALL` overrides every category and is best used temporarily. `iconv` converts bytes—it cannot repair text whose original encoding is unknown. Verify with `iconv -f UTF-8 -t UTF-8 new.txt >/dev/null` and inspect application semantics.

### 25.3 X11, Wayland, display managers, and accessibility

LPIC-1 emphasizes concepts and configuration locations. X11 clients connect to an X server selected by `DISPLAY`; Wayland compositors combine display server and window manager roles.

```bash
printf '%s\n' "$XDG_SESSION_TYPE"       # commonly x11, wayland, or tty
loginctl show-session "$XDG_SESSION_ID" -p Type -p Remote
xdpyinfo | head                          # query X server capabilities; requires X session
xrandr --query                           # X11 outputs/modes; not a universal Wayland tool
systemctl status display-manager.service # alias to GDM, SDDM, LightDM, etc.
```

Key files/concepts: `/etc/X11/xorg.conf`, `/etc/X11/xorg.conf.d/`, `~/.xinitrc`, `xhost`, `xauth`, `XDG_*`, keyboard repeat/layout, screen reader, high contrast, sticky keys, and on-screen keyboard. `xhost +` disables meaningful X access control; prefer per-user cookies through `xauth` or SSH X forwarding.

### 25.4 CUPS printing

CUPS accepts jobs, filters them, queues them, and speaks printer protocols. A **queue** is the administrator-facing destination; the physical printer may be remote.

```bash
lpstat -t                              # full scheduler/queue/default status
lpinfo -v                              # discover device URIs/backends (admin context)
lpoptions -p office -l                 # capabilities/options advertised by a queue
lp -d office -n 2 report.pdf           # submit two copies; prints a job ID
lpstat -W not-completed -o office      # verify queued/active jobs
cancel office-42                       # cancel by the ID returned at submission
cupsctl --debug-logging                # temporary troubleshooting; disable afterward
journalctl -u cups --since '10 min ago'
```

`lpadmin` changes persistent queue configuration; `lp` merely submits a job. Validate `/etc/cups/cupsd.conf` changes with a controlled restart and keep access rules narrow.

**Scenario lab:** create a PDF printer queue in a disposable VM, submit a job, inspect its ID/state, cancel another job, and explain which commands queried versus changed state.

---

## Chapter 26: LPIC-2 Exam 201 Completion — Capacity, Boot, Filesystems, and Maintenance

### 26.1 Capacity planning: observe before tuning

Use multiple views because a single percentage rarely identifies a bottleneck.

```bash
uptime                                  # load averages: runnable + uninterruptible tasks
vmstat 1 10                             # CPU, run queue, paging, and block I/O samples
iostat -xz 1 10                         # per-device latency, queue, utilization (sysstat)
pidstat -dur 1 10                       # per-process CPU, disk, and memory activity
sar -n DEV 1 10                         # historical/current interface rates
ss -s                                   # socket population summary
```

- `vmstat` first row is an average since boot; later rows are interval samples. High `r` suggests CPU pressure; high `b` and I/O wait suggest blocked storage work; sustained `si/so` means swapping.
- `iostat -x` explains devices. `await` is request latency; `%util` needs device context and is not a universal saturation proof, especially for parallel NVMe.
- `sar` reads data collected by `sysstat`; without collection enabled, history does not exist.

The logic is symptom → resource demand → queue/latency → responsible process → trend. Record baselines and graph percentiles/capacity growth; do not tune `swappiness` merely because swap is nonzero.

### 26.2 SMART, NVMe, and filesystem health

```bash
smartctl --scan-open                     # discover devices smartmontools can open
smartctl -a /dev/sda                    # identity, health, attributes, error/self-test logs
smartctl -t short /dev/sda              # start device test; returns estimated completion
smartctl -l selftest /dev/sda           # read result later
nvme smart-log /dev/nvme0               # NVMe health counters
```

SMART “PASSED” is not proof of future health. Watch reallocated/pending sectors, media errors, temperature, wear, and change over time. A self-test runs inside the device; it does not replace backup or filesystem checking.

```bash
btrfs filesystem usage /mnt
btrfs subvolume list /mnt
btrfs subvolume snapshot -r /mnt/data /mnt/snaps/data-$(date +%F)
btrfs scrub start -Bd /mnt               # verify checksums; repair only with redundant good copy
xfsdump -l 0 -f /backup/home.xfs /home   # filesystem-aware XFS full dump
xfsrestore -f /backup/home.xfs /restore  # restore to a mounted target
```

A Btrfs snapshot shares blocks; it is not an independent backup. XFS dump levels support incremental chains and require restore metadata discipline.

### 26.3 DKMS and kernel modules

DKMS rebuilds an out-of-tree module for each installed kernel:

```bash
dkms status                              # module/version/kernel/build state
dkms add ./module-source                 # register source containing dkms.conf
dkms build -m vendor -v 1.2 -k "$(uname -r)"
dkms install -m vendor -v 1.2 -k "$(uname -r)"
modinfo vendor                           # verify path, version, parameters, signature
modprobe vendor                          # dependency-aware runtime load
```

`insmod file.ko` loads exactly one path and does not resolve dependencies; `modprobe NAME` uses module metadata and `/etc/modprobe.d/`, so it is normally the administrative tool.

### 26.4 Alternate bootloaders and PXE

- SYSLINUX boots FAT filesystems; EXTLINUX supports ext-family filesystems; ISOLINUX targets ISO media; PXELINUX historically boots over PXE.
- systemd-boot reads Boot Loader Specification entries from the EFI System Partition; `bootctl status` queries the active setup and `bootctl install` changes the ESP.
- U-Boot is common on embedded systems and uses environment variables/scripts.

PXE logic: firmware obtains network configuration and a boot filename via DHCP, downloads a network boot program (TFTP/HTTP depending on firmware), then fetches kernel/initrd/config. BIOS and UEFI need compatible boot binaries.

### 26.5 Maintenance communication

```bash
wall < maintenance.txt                   # write to logged-in terminals
shutdown -r +15 'Kernel maintenance'     # schedule reboot and notify users
systemctl list-jobs                      # see pending systemd work
```

`/etc/issue` is pre-login local text, `/etc/issue.net` may be used by remote login services, and `/etc/motd` is post-login information. Never place secrets in banners.

**Scenario lab:** induce storage pressure in a disposable VM, collect `vmstat`, `iostat`, `pidstat`, and `sar`, identify the process/device, then write an evidence-based diagnosis rather than a tuning guess.

---

## Chapter 27: LPIC-2 Exam 202 Completion — DHCP, Proxy, SQL, and Client Services

### 27.1 DHCP server

DHCP leases configuration through Discover → Offer → Request → Ack. A relay forwards broadcasts between subnets.

```conf
# /etc/dhcp/dhcpd.conf
authoritative;
default-lease-time 3600;
max-lease-time 86400;
subnet 192.0.2.0 netmask 255.255.255.0 {
  range 192.0.2.100 192.0.2.199;
  option routers 192.0.2.1;
  option domain-name-servers 192.0.2.53;
}
host printer { hardware ethernet 02:00:00:00:00:42; fixed-address 192.0.2.42; }
```

```bash
dhcpd -t -cf /etc/dhcp/dhcpd.conf        # parse/check without starting service
journalctl -u isc-dhcp-server -f         # watch lease decisions/errors
tcpdump -ni eth0 -vv 'udp port 67 or 68' # prove protocol exchange on the wire
```

The config declares policy; the lease file records dynamic state. Check syntax before restart and ensure only one authoritative DHCP server serves a broadcast domain.

### 27.2 Squid proxy

Squid is an HTTP proxy/cache. ACLs define sets; `http_access` evaluates rules top-to-bottom and stops at the first match.

```conf
acl localnet src 192.0.2.0/24
acl SSL_ports port 443
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access deny all
```

```bash
squid -k parse                           # validate configuration
squid -z                                 # create cache directories when required
squid -k reconfigure                     # reload without a full stop
tail -f /var/log/squid/access.log        # verify client decisions/status codes
```

An open proxy is abuse infrastructure. End every policy with an explicit deny and test from allowed and denied clients.

### 27.3 SQL fundamentals for administrators

LPIC-2 expects basic data manipulation, not database engineering:

```sql
SELECT id, email FROM users WHERE active = TRUE ORDER BY id LIMIT 20;
INSERT INTO users (email, active) VALUES ('a@example.com', TRUE);
UPDATE users SET active = FALSE WHERE id = 42;
DELETE FROM sessions WHERE expires_at < CURRENT_TIMESTAMP;
```

`WHERE` selects rows; omitting it from `UPDATE`/`DELETE` targets every row. In a transaction, inspect first and roll back if counts are wrong.

```bash
psql -d appdb -c 'SELECT current_database(), current_user;'
mysql --database appdb -e 'SHOW TABLES;'
```

These clients send SQL to a server; they do not make a backup by redirecting table output. Use `pg_dump`/`pg_restore` or `mysqldump` and verify a restore.

### 27.4 `xinetd` and socket activation

`xinetd` listens on behalf of simple network services and starts a server per policy. Key fields are `socket_type`, `protocol`, `wait`, `user`, `server`, `server_args`, `only_from`, and `disable`. Modern systemd socket units implement the same broad activation idea.

```bash
xinetd -dontfork -stayalive -d           # foreground debug; use only in a lab
systemctl list-sockets --all              # which systemd sockets activate services
systemctl status ssh.socket ssh.service   # distinguish listener from worker service
```

### 27.5 Pure-FTPd and FTP reasoning

FTP uses a control connection and a separate data connection; NAT/firewalls make passive port ranges important. Plain FTP exposes credentials unless TLS is correctly configured; prefer SFTP when SSH semantics fit.

```bash
pure-ftpd --help                          # implementation options vary by packaging
ss -ltnp | grep ':21 '
openssl s_client -connect ftp.example:21 -starttls ftp
```

For anonymous upload, separate upload and download directories, deny execution, prevent listing if required, enforce quotas, and scan/move uploaded content before publication.

**Scenario lab:** build a two-client DHCP network and Squid proxy in isolated VMs. Validate configs before restart, capture DHCP packets, and prove the proxy allows only the intended subnet.

---

## Chapter 28: LPIC-3 Exam 300 Completion — Samba, FreeIPA, CIFS, and NFSv4

Exam 300 is a mixed-environment administration exam. Knowing LDAP syntax alone is insufficient: you must operate Samba file servers and AD domains, map Windows/POSIX identities and ACLs, manage clients, and understand FreeIPA trusts.

### 28.1 Samba validation, live state, and maintenance

```bash
testparm -s                              # parse smb.conf and print effective settings
smbstatus --shares                       # live clients, shares, PIDs, and locks
smbcontrol all reload-config             # ask running daemons to reload without restart
smbcontrol smbd debug 3                  # temporary runtime debug level for smbd
journalctl -u smbd -u nmbd -u winbind --since today
```

**Logic:** `testparm` proves syntax/effective configuration, not filesystem permission or client authentication. `smbstatus` observes runtime state. `smbcontrol` sends messages to daemons. Use all three in that order when a correct-looking configuration does not serve clients.

Samba stores important state in TDB databases. Back them up consistently:

```bash
tdbbackup -s .bak /var/lib/samba/*.tdb   # create validated copies with suffix
tdbbackup -v /var/lib/samba/private/idmap.ldb
samba-tool domain backup online --targetdir=/backup --server=dc1
samba-tool domain backup restore --backup-file=FILE --targetdir=/restore
```

`tdbbackup` protects individual databases; `samba-tool domain backup` captures AD DC state with domain-aware semantics. VM snapshots are not a substitute for supported AD backup and can interact with replication identity.

### 28.2 Shares, POSIX modes, and Windows ACLs

```ini
[projects]
  path = /srv/samba/projects
  read only = no
  valid users = @project
  force group = project
  create mask = 0660
  directory mask = 2770
  inherit acls = yes
  vfs objects = acl_xattr
  map acl inherit = yes
  store dos attributes = yes
  smb encrypt = desired
```

The final permission is the intersection of share authorization, Samba masks/forced identity, filesystem mode/ACL, and MAC policy such as SELinux. Diagnose each layer separately.

```bash
namei -l /srv/samba/projects/file        # permissions on every path component
getfacl /srv/samba/projects
smbcacls //server/projects path -U admin # view Windows-facing ACL
sharesec //server/projects               # share security descriptor
getfattr -d -m- /srv/samba/projects/file # extended attributes, including ACL storage
```

Granting `SeDiskOperatorPrivilege` lets designated administrators manage share ACLs without full domain administration:

```bash
net rpc rights grant 'EXAMPLE\File Admins' SeDiskOperatorPrivilege -U 'EXAMPLE\Administrator'
net rpc rights list accounts -U 'EXAMPLE\Administrator'
```

### 28.3 AD DC, replication, and GPO

```bash
samba-tool drs showrepl                 # inbound/outbound replication status
samba-tool dbcheck --cross-ncs          # AD database consistency report
samba-tool dns query dc1 example.test @ ALL -U Administrator
samba-tool gpo listall
samba-tool gpo create 'Workstation Baseline'
samba-tool gpo show GPO-GUID
```

`drs showrepl` answers “are directory changes replicating?”; `dbcheck` examines local database consistency; DNS checks validate records AD depends on. Do not “fix” replication by deleting databases before preserving logs and backups.

### 28.4 Linux CIFS clients

```bash
smbclient -L //server -U alice           # enumerate shares and test authentication
smbclient //server/projects -U alice     # interactive file operations
mount -t cifs //server/projects /mnt/projects \
  -o credentials=/root/.smb-projects,vers=3.1.1,seal
cifscreds add server                     # cache credentials in a user keyring
getcifsacl /mnt/projects/file
setcifsacl -a 'ACL:EXAMPLE\alice:ALLOWED/0x0/FULL' /mnt/projects/file
cifsiostat 1                             # per-mount CIFS throughput/latency
```

Credential files should be root-owned mode `0600`. `uid=`/`gid=` may control a client-side presentation when the server does not provide Unix ownership; they do not replace server authorization.

### 28.5 FreeIPA

```bash
ipa-server-install                       # create integrated LDAP/Kerberos/DNS/CA server
ipa-client-install --mkhomedir           # join a client and configure identity/auth
ipactl status                            # state of the IPA service stack
ipa user-add alice --first Alice --last Admin
ipa group-add-member ops --users=alice
ipa host-add web01.example.test
ipa service-add HTTP/web01.example.test
ipa-getkeytab -s ipa.example.test -p HTTP/web01.example.test -k /etc/http.keytab
ipa hbacrule-add allow-web-ops
ipa hbacrule-add-user allow-web-ops --groups=ops
ipa hbacrule-add-host allow-web-ops --hosts=web01.example.test
```

The principal identifies a service; the keytab stores its long-term key and must be protected. HBAC decides which identities may access which hosts/services. `ipa permission-*`, `privilege-*`, and `role-*` compose delegated administration.

AD integration uses `ipa-adtrust-install`, DNS reachability, time synchronization, ID ranges, and trust commands:

```bash
ipa trust-add ad.example.test --type=ad --admin Administrator --password
ipa trust-fetch-domains ad.example.test
ipa idrange-find
```

### 28.6 NFSv4, ID mapping, ACLs, and Kerberos

NFSv4 uses a pseudo-filesystem and supports richer ACLs. Kerberos security flavors are `krb5` (authentication), `krb5i` (integrity), and `krb5p` (privacy/encryption).

```exports
/srv/nfs4 192.0.2.0/24(ro,fsid=0,crossmnt,sec=krb5p)
/srv/nfs4/projects 192.0.2.0/24(rw,sec=krb5p)
```

```bash
exportfs -rav                           # re-read exports and report changes
exportfs -v                             # effective exports/options
mount -t nfs4 -o sec=krb5p server:/projects /mnt/projects
nfs4_getfacl /mnt/projects
nfs4_setfacl -e /mnt/projects           # edit NFSv4 ACL; syntax differs from POSIX ACL
nfsstat -m                              # client mount options actually negotiated
```

**Scenario lab:** break access deliberately at one of four layers—share ACL, filesystem ACL, identity mapping, or SELinux—then prove which layer failed using `testparm`, `smbclient`, `namei/getfacl`, and audit logs.

---

## Chapter 29: LPIC-3 Exam 303 Completion — PKI, Host Hardening, and Access Control

### 29.1 Build and operate a small CA

A CA is lifecycle and policy, not merely `openssl req -x509`. Protect the offline root, issue through an intermediate, constrain names/usages, maintain serial/index state, publish revocation, and practise recovery.

```bash
openssl req -new -newkey rsa:3072 -nodes -keyout server.key -out server.csr
openssl req -in server.csr -noout -text   # inspect requested subject/extensions
openssl ca -config intermediate.cnf -extensions server_cert -in server.csr -out server.crt
openssl verify -purpose sslserver -CAfile root.crt -untrusted intermediate.crt server.crt
openssl ca -config intermediate.cnf -revoke server.crt
openssl ca -config intermediate.cnf -gencrl -out intermediate.crl
openssl crl -in intermediate.crl -noout -text
openssl ocsp -issuer intermediate.crt -cert server.crt -url http://ocsp.example.test
```

`req` creates a key/CSR; `ca` applies CA database and policy; `verify` builds/checks a chain for a purpose; `crl` inspects a signed revocation list; `ocsp` asks for current status. File permissions, backups, expiry monitoring, and private-key custody are part of the system.

### 29.2 S/MIME and OpenPGP

```bash
openssl smime -sign -in message.txt -signer alice.crt -inkey alice.key -out signed.eml
openssl smime -verify -in signed.eml -CAfile mail-ca.crt -out verified.txt
openssl smime -encrypt -aes256 -in message.txt -out encrypted.eml bob.crt
openssl smime -decrypt -in encrypted.eml -recip bob.crt -inkey bob.key
```

Signing proves origin/integrity under certificate trust; encryption protects content for recipients. It does not hide all mail metadata.

### 29.3 OpenSSH certificates

OpenSSH certificates let hosts/users trust a CA rather than distributing every public key:

```bash
ssh-keygen -t ed25519 -f user_ca
ssh-keygen -s user_ca -I alice-2026 -n alice,ops -V +8h alice.pub
ssh-keygen -Lf alice-cert.pub             # inspect principals, validity, options
```

Server configuration trusts the CA with `TrustedUserCAKeys /etc/ssh/user_ca.pub`; `AuthorizedPrincipalsFile` restricts allowed certificate principals. Keep the CA key offline or in a controlled signer, use short validity, record serial/identity, and publish revocation through `RevokedKeys`/KRL where appropriate.

### 29.4 Capabilities and service sandboxing

Linux capabilities split root privilege into narrower units:

```bash
getcap -r /usr/bin /usr/sbin 2>/dev/null  # audit file capabilities
setcap cap_net_bind_service=+ep ./server  # allow low-port bind without full root
getpcaps PID                              # process capabilities
capsh --print                             # current shell capability sets
```

Capabilities remain powerful and interact with bounding, permitted, effective, inheritable, and ambient sets. Prefer service-manager confinement over casually modifying system binaries.

```ini
[Service]
User=app
NoNewPrivileges=yes
PrivateTmp=yes
ProtectSystem=strict
ProtectHome=yes
ReadWritePaths=/var/lib/app
CapabilityBoundingSet=CAP_NET_BIND_SERVICE
AmbientCapabilities=CAP_NET_BIND_SERVICE
RestrictAddressFamilies=AF_UNIX AF_INET AF_INET6
SystemCallFilter=@system-service
```

```bash
systemd-analyze security app.service     # score/explain exposure (guidance, not proof)
systemctl edit app.service               # create drop-in, preserve vendor unit
systemctl daemon-reload
systemctl restart app.service
journalctl -u app.service -b             # verify sandbox did not block required behavior
```

### 29.5 Namespaces, cgroups, and seccomp

Namespaces isolate views (PID, mount, network, UTS, IPC, user, cgroup, time); cgroups account/limit resources; seccomp filters syscalls. None alone is a complete security boundary.

```bash
lsns                                     # namespaces and member processes
nsenter -t PID -n ip address             # inspect target network namespace
systemd-cgls                             # hierarchy and processes
systemd-cgtop                            # live resource view
unshare --user --map-root-user --mount-proc --pid --fork sh
```

`nsenter` changes the observer's namespace context and usually needs privilege. `unshare` creates new namespaces for the command; user namespace mappings can grant “root inside” without host root, subject to host policy.

### 29.6 OpenSCAP workflow

```bash
oscap info benchmark.xml
oscap xccdf eval --profile PROFILE --results results.xml --report report.html benchmark.xml
oscap xccdf generate fix --profile PROFILE --fix-type bash benchmark.xml >remediate.sh
```

`info` discovers content/profiles; `eval` measures; `generate fix` produces candidate remediation. Review every fix, test in staging, account for local exceptions, and rescan. Compliance is not equivalent to absence of vulnerabilities.

**Scenario lab:** harden a simple systemd web service, demonstrate it still serves content, prove denied filesystem access in the journal, and compare `systemd-analyze security` before/after.

---

## Chapter 30: LPIC-3 Exams 305/306 Completion — Provisioning, Isolation, and HA Operations

### 30.1 QEMU images and libvirt diagnosis

```bash
qemu-img info disk.qcow2                  # format, virtual/actual size, backing file
qemu-img create -f qcow2 -F qcow2 -b base.qcow2 child.qcow2
qemu-img check child.qcow2                # consistency check; avoid repair without backup
virsh domblklist vm --details             # map guest targets to host storage
virsh domiflist vm                        # map guest interfaces to networks/bridges
virsh qemu-monitor-command vm --hmp info-block
virsh domstats vm --vcpu --balloon --block --interface
```

`qemu-img` operates on image metadata and should not modify an image actively used by a VM unless the operation explicitly supports it. `virsh` asks libvirt for managed state; monitor commands bypass some abstraction and are diagnostic tools.

### 30.2 Repeatable provisioning with Vagrant and Packer

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.network "private_network", ip: "192.0.2.10"
  config.vm.provision "shell", inline: "apt-get update && apt-get -y install nginx"
end
```

`vagrant up` creates/converges a development VM, `vagrant ssh` enters it, `vagrant snapshot save clean` provides a lab rollback, and `vagrant destroy -f` removes it. Packer instead builds versioned machine images from a template; validate and pin source image checksums before building.

```bash
packer init .
packer fmt -check .
packer validate -var-file=lab.pkrvars.hcl .
packer build -var-file=lab.pkrvars.hcl .
```

### 30.3 Open vSwitch

```bash
ovs-vsctl show
ovs-vsctl add-br br-lab
ovs-vsctl add-port br-lab vnet0
ovs-ofctl show br-lab
ovs-ofctl dump-flows br-lab
```

`ovs-vsctl` changes the OVS configuration database; `ovs-ofctl` inspects/programs OpenFlow behavior. Verify Linux links with `ip link` and packet paths with `tcpdump`; a port existing in OVS does not prove end-to-end reachability.

### 30.4 Resource agents, quorum, and fencing

Pacemaker resource agents implement actions such as `start`, `stop`, `monitor`, and metadata under a standard. Inspect before creating resources:

```bash
pcs resource standards
pcs resource agents ocf:heartbeat
pcs resource describe ocf:heartbeat:IPaddr2
ocf-tester -n resource-name /usr/lib/ocf/resource.d/heartbeat/custom
pcs status --full
pcs config
crm_mon -Arf1
```

Quorum answers whether a partition is allowed to manage resources. Fencing/STONITH forcibly isolates an uncertain node so two sides cannot write shared state. A cluster without tested fencing may be highly available at corrupting data.

```bash
pcs quorum status
corosync-quorumtool -s
pcs stonith config
stonith_admin --list-installed
stonith_admin --reboot NODE              # destructive: only during an approved fencing test
```

Use maintenance mode for planned work rather than disabling random resources:

```bash
pcs property set maintenance-mode=true
pcs status
# perform work and verify node/service health
pcs property set maintenance-mode=false
```

### 30.5 LVS/IPVS and geo-clusters

IPVS is an in-kernel layer-4 load balancer; `ipvsadm` configures virtual services and real servers:

```bash
ipvsadm -A -t 192.0.2.100:443 -s rr
ipvsadm -a -t 192.0.2.100:443 -r 192.0.2.11:443 -m
ipvsadm -a -t 192.0.2.100:443 -r 192.0.2.12:443 -m
ipvsadm -Ln --stats --rate
```

`-A` creates the virtual service, `-a` adds a real server, `-s rr` chooses round-robin scheduling, and `-m` selects NAT forwarding. Verify counters and backend health; IPVS alone does not remove failed servers without a health-management layer such as Keepalived.

Booth coordinates ticket ownership between geographically separated Pacemaker sites. A ticket constraint controls which site may run a resource; arbitrators help avoid two-site split brain. Test WAN loss, site loss, and ticket expiry in a lab before production.

**Scenario lab:** create a two-node Pacemaker lab plus a fencing simulator, prove resource movement, enter/leave maintenance mode, break quorum communication, and explain why the observed fencing decision protects storage.

---

## Chapter 31: Safe Scenario Labs and LPIC-3 Exam Preparation

### 31.1 Standard lab topology

Use snapshots and host-only networks:

```text
client1 192.0.2.11 ─┐
client2 192.0.2.12 ─┼─ router/dns/dhcp 192.0.2.1
server1 192.0.2.21 ─┤
server2 192.0.2.22 ─┘
```

Each lab must record: objective ID, starting snapshot, intended state, commands with reasoning cards, expected evidence, injected fault, diagnosis, rollback, and lessons. Never use production DNS domains, routable address space, or host disks.

### 31.2 Capstone labs

1. **LPIC-1 workstation:** users/groups, ACL shared directory, cron/at/timer jobs, locale conversion, CUPS queue, SSH keys, logs, and a recovery checklist.
2. **LPIC-2 site:** DHCP + caching DNS + Squid + Apache + NFS/Samba + Postfix, routed through a stateful firewall. Break one service at a time and diagnose from client symptoms to logs/packets/config.
3. **Exam 300:** Samba AD DC, member file server, Linux client, FreeIPA conceptual comparison, Windows/POSIX ACL translation, backup and replication failure.
4. **Exam 303:** intermediate CA, SSH CA, SELinux/AppArmor policy, audit rules, systemd hardening, OpenSCAP assessment, and incident evidence bundle.
5. **Exam 305:** cloud image built by Packer, provisioned VM, libvirt network/storage investigation, rootless container with resource/security controls.
6. **Exam 306:** Pacemaker/Corosync service with fencing, DRBD or shared lab storage, HAProxy/Keepalived, quorum loss, maintenance, and recovery.

### 31.3 LPIC-3 diagnostic questions

**Exam 300**

1. Which command checks `smb.conf` before reload? **`testparm -s`**—it parses and prints effective configuration.
2. Which command diagnoses AD replication? **`samba-tool drs showrepl`**—it reports replication partners and failures.
3. Why can `valid users` succeed while file open fails? The filesystem ACL/mode or MAC policy can still deny access.
4. What does `sec=krb5p` add over `krb5i`? Privacy (encryption), in addition to authentication/integrity.
5. Which FreeIPA object delegates administrative actions? Permissions combine into privileges, which combine into roles.

**Exam 303**

1. Which command verifies a TLS server chain for purpose? `openssl verify -purpose sslserver ...`.
2. ECDSA versus ECDH? ECDSA signs; ECDH agrees on key material.
3. Why is `audit2allow -a` dangerous? It can convert unrelated/misconfiguration denials into excessive policy.
4. What prevents a service from gaining new privilege through exec? `NoNewPrivileges=yes` (subject to kernel semantics).
5. Does a passing OpenSCAP profile prove security? No; it proves evaluated rules for that content/profile at that time.

**Exam 305**

1. What does a qcow2 backing file enable? Copy-on-write children referencing a base image.
2. What must precede `qemu-img` mutation of a VM disk? Stop/coordinate the VM and back up; concurrent mutation can corrupt it.
3. Namespace versus cgroup? Namespace isolates a view; cgroup accounts/limits resources.
4. Why use Packer? To reproducibly build immutable/versioned machine images.
5. `ovs-vsctl` versus `ovs-ofctl`? Configuration database/topology versus OpenFlow datapath inspection/programming.

**Exam 306**

1. Why is fencing required? To prove an uncertain node cannot access shared resources before recovery elsewhere.
2. What is quorum? The cluster partition's authority to make resource-management decisions.
3. What does an OCF monitor action do? Reports resource health at configured intervals/depth.
4. What does IPVS provide? Layer-4 virtual service load balancing; health orchestration is separate.
5. Why use maintenance mode? It pauses cluster recovery actions coherently during planned administration.

### 31.4 Exam method

- Study by objective weight, not chapter length.
- For every utility know its intent, important options, input/config file, output, and nearest confusing alternative.
- Practise fill-in answers with exact command/file spelling.
- In scenarios, identify whether the question asks for observation, runtime change, persistence, verification, or recovery.
- Reject unsafe distractors: force flags, editing generated files, checking a mounted writable filesystem, disabling MAC/firewall, or killing before inspecting.

---

## Chapter 32: Official Objective Master Checklist

This chapter is the **coverage contract** for the handbook. Check an item only after you can explain it, use its principal commands, interpret failure output, and complete its lab without copying. The baseline is LPI's published objectives: LPIC-1 5.0, LPIC-2 4.5, and LPIC-3 3.0. A weight estimates relative exam emphasis; it is not a guaranteed question count.

### 32.1 LPIC-1 101-500

| Objective (weight) | Required outcome | Coverage |
|---|---|---|
| 101.1 (2) | Detect/configure hardware, modules, hotplug | Ch. 1, 24 |
| 101.2 (3) | Trace firmware, bootloader, kernel, init startup | Ch. 1, 11 |
| 101.3 (3) | Change targets/runlevels and shut down safely | Ch. 1, 11 |
| 102.1 (2) | Design partitions, swap, LVM and mount layout | Ch. 2, 4, 12 |
| 102.2 (2) | Install and recover GRUB 2 | Ch. 2, 11 |
| 102.3 (1) | Inspect and configure shared libraries | Ch. 2 |
| 102.4 (3) | Query/install/remove Debian packages | Ch. 2 |
| 102.5 (3) | Query/install/remove RPM/DNF/YUM packages | Ch. 2 |
| 102.6 (1) | Recognize Linux guests and cloud images | Ch. 2, 22 |
| 103.1 (4) | Use shell syntax, quoting, history and variables | Ch. 3, 5, 24 |
| 103.2 (3) | Transform text with core filters | Ch. 3 |
| 103.3 (4) | Copy, move, remove, archive and glob safely | Ch. 3 |
| 103.4 (4) | Use streams, redirection, pipes and `tee` | Ch. 3, 24 |
| 103.5 (4) | Create, monitor, signal and background processes | Ch. 3 |
| 103.6 (2) | Interpret and change process priority | Ch. 3 |
| 103.7 (3) | Use BRE/ERE and `grep`/`sed` patterns | Ch. 3 |
| 103.8 (3) | Perform basic editing with vi | Ch. 3 |
| 104.1 (2) | Partition disks and create filesystems/swap | Ch. 4 |
| 104.2 (2) | Check, tune and monitor filesystem integrity | Ch. 4 |
| 104.3 (3) | Mount manually and persistently with correct options | Ch. 4 |
| 104.5 (3) | Manage modes, ownership, special bits and umask | Ch. 4, 6 |
| 104.6 (2) | Explain inode-based hard links and symlinks | Ch. 4 |
| 104.7 (2) | Use FHS, `find`, `locate`, `whereis`, `which` | Ch. 3, 4 |

### 32.2 LPIC-1 102-500

| Objective (weight) | Required outcome | Coverage |
|---|---|---|
| 105.1 (4) | Customize shell environment and profiles | Ch. 5 |
| 105.2 (4) | Write, test and debug portable basic scripts | Ch. 5, 24 |
| 106.1 (2) | Understand/configure X11 and remote display access | Ch. 25 |
| 106.2 (1) | Understand desktops, display/window managers | Ch. 25 |
| 106.3 (1) | Identify accessibility settings and tools | Ch. 25 |
| 107.1 (5) | Administer users/groups and account databases | Ch. 6 |
| 107.2 (4) | Schedule with cron, at and systemd timers | Ch. 25 |
| 107.3 (3) | Configure locales, time zones and encodings | Ch. 8, 25 |
| 108.1 (3) | Maintain time with NTP/chrony and RTC | Ch. 8 |
| 108.2 (4) | Configure/query syslog, rsyslog and journal | Ch. 8 |
| 108.3 (3) | Understand MTA roles, aliases and mail queues | Ch. 18 |
| 108.4 (2) | Manage CUPS queues and jobs | Ch. 25 |
| 109.1 (4) | Explain IPv4/IPv6, TCP/UDP, ports and subnetting | Ch. 7 |
| 109.2 (4) | Configure persistent host networking | Ch. 7 |
| 109.3 (4) | Diagnose interfaces, routes, sockets and reachability | Ch. 7, 24 |
| 109.4 (2) | Configure client resolver and NSS behavior | Ch. 7 |
| 110.1 (3) | Audit security settings, sessions, limits and sudo | Ch. 6, 9 |
| 110.2 (3) | Secure hosts with passwords, shadow and service control | Ch. 6, 9 |
| 110.3 (3) | Use GnuPG encryption, signing and trust | Ch. 9, 21 |

### 32.3 LPIC-2 201-450 and 202-450

| Exam | Objectives and official weights | Coverage |
|---|---|---|
| 201 | 200.1(6), 200.2(2); 201.1(2), 201.2(3), 201.3(4) | Ch. 10, 26 |
| 201 | 202.1(3), 202.2(4), 202.3(2) | Ch. 11, 26 |
| 201 | 203.1(4), 203.2(3), 203.3(2) | Ch. 4, 12, 26 |
| 201 | 204.1(3), 204.2(2), 204.3(3) | Ch. 12, 26 |
| 201 | 205.1(3), 205.2(4), 205.3(4) | Ch. 13, 26 |
| 201 | 206.1(2), 206.2(3), 206.3(1) | Ch. 14, 26 |
| 202 | 207.1(3), 207.2(3), 207.3(2) | Ch. 15 |
| 202 | 208.1(4), 208.2(3), 208.3(2), 208.4(2) | Ch. 16, 27 |
| 202 | 209.1(5), 209.2(3) | Ch. 17 |
| 202 | 210.1(2), 210.2(3), 210.3(2), 210.4(4) | Ch. 20, 27 |
| 202 | 211.1(4), 211.2(2), 211.3(2) | Ch. 18 |
| 202 | 212.1(3), 212.2(2), 212.3(4), 212.4(3), 212.5(2) | Ch. 9, 13, 17, 19, 27 |

The objective names, in order, are: capacity measurement/prediction; kernel components/compilation/runtime; startup/recovery/alternate bootloaders; filesystem operation/maintenance/options; RAID/device access/LVM; basic/advanced networking/troubleshooting; source builds/backups/user notification; DNS configuration/zones/security; Apache/HTTPS/Squid/Nginx; Samba/NFS; DHCP/PAM/LDAP client/OpenLDAP server; mail servers/delivery/mailbox access; router/FTP/SSH/security tasks/OpenVPN.

### 32.4 LPIC-3 300-300

| Topic | Objectives (weight) |
|---|---|
| Samba basics | 301.1 Concepts/architecture (2); 301.2 configuration (4); 301.3 maintenance (2); 301.4 troubleshooting (3) |
| Samba and AD | 302.1 AD DC (5); 302.2 name resolution (2); 302.3 user management (4); 302.4 domain membership (4); 302.5 local users (2) |
| Shares | 303.1 file shares (4); 303.2 share security (3); 303.3 DFS (1); 303.4 printing (2) |
| Clients | 304.1 Linux authentication (5); 304.2 Linux CIFS (3); 304.3 Windows clients (3) |
| Linux identity/sharing | 305.1 FreeIPA install/maintenance (2); 305.2 entities (4); 305.3 AD integration (2); 305.4 NFS (3) |

### 32.5 LPIC-3 303-300, 305-300 and 306-300

| Exam | Complete objective set with weights |
|---|---|
| 303 | 331.1 PKI(5), 331.2 X.509 applications(4), 331.3 encrypted filesystems(3), 331.4 DNS cryptography(5); 332.1 hardening(5), 332.2 HIDS(5), 332.3 resource control(3); 333.1 DAC(3), 333.2 MAC(5); 334.1 network hardening(4), 334.2 NIDS(4), 334.3 packet filtering(5), 334.4 VPN(4); 335.1 threats(2), 335.2 penetration testing(3) |
| 305 | 351.1 concepts(6), 351.2 Xen(3), 351.3 QEMU(4), 351.4 libvirt(9), 351.5 images(3); 352.1 container concepts(7), 352.2 LXC(6), 352.3 Docker(9), 352.4 orchestration(3); 353.1 cloud tools(2), 353.2 Packer(2), 353.3 cloud-init(3), 353.4 Vagrant(3) |
| 306 | 361.1 HA concepts(6), 361.2 load balancing(8), 361.3 failover(8); 362.1 DRBD(6), 362.2 shared storage access(3), 362.3 clustered filesystems(4); 363.1 GlusterFS(5), 363.2 Ceph(8); 364.1 hardware/resource HA(2), 364.2 advanced RAID(2), 364.3 advanced LVM(3), 364.4 network HA(5) |

---

## Chapter 33: Exam 300 Advanced Operations Supplement

### 33.1 Samba databases, registry, and maintenance

Samba stores state in TDB/LDB databases. Do not treat these as text files.

```bash
testparm -s                         # parse smb.conf and show effective settings
smbcontrol all reload-config        # ask running processes to reload safely
net conf list                       # read registry-backed service configuration
net conf addshare docs /srv/docs    # persist a registry-backed share
samba-regedit                       # interactive registry database editor
tdbbackup -s .bak /var/lib/samba/*.tdb
tdbdump FILE.tdb                    # diagnostic dump; may expose sensitive data
ldbsearch -H /var/lib/samba/private/sam.ldb '(sAMAccountName=alice)'
rpcclient -U Administrator SERVER   # exercise RPC independently of a GUI client
```

`tdbbackup` creates consistent backup copies and validates readability; `tdbrestore` restores a dump when recovery is justified. Stop the relevant service and preserve the original before repair. `net registry`/`net conf` manipulate registry-backed settings; `samba-regedit` provides a registry view. Verify configuration with both `testparm` and a real `smbclient` request.

### 33.2 AD DC lifecycle and diagnosis

```bash
samba-tool domain provision --use-rfc2307 --realm=EXAMPLE.COM --domain=EXAMPLE
samba-tool domain join EXAMPLE.COM DC -U Administrator
samba-tool domain info 192.0.2.10
samba-tool domain level show
samba-tool fsmo show
samba-tool drs showrepl
samba-tool dbcheck --cross-ncs
samba-tool ntacl sysvolcheck
samba-tool user syncpasswords --cache-ldb-initialize
```

Provision creates the directory, DNS and Kerberos identity of the first DC; joining as `DC` adds a replication partner. AD depends on DNS SRV records and close time synchronization. FSMO roles are single-master duties, not evidence that other directory data is single-master. `drs showrepl` checks replication, `dbcheck` checks directory consistency, and `ntacl sysvolcheck` compares SYSVOL ACL expectations. Back up with `samba-tool domain backup online`; test restore into an isolated network.

Know sites/subnets, global catalog, trusts, forest/domain functional levels, tombstones, SPNs, keytabs, SIDs, GUIDs, DNs and UPNs. A duplicate SPN can break Kerberos even when passwords and DNS look correct.

```bash
samba-tool user create alice
samba-tool group addmembers 'Domain Admins' alice
samba-tool domain passwordsettings show
samba-tool domain passwordsettings pso list
samba-tool spn list alice
samba-tool sites list
samba-tool domain trust list
```

### 33.3 Domain members, id mapping, and NSS/PAM

`winbindd` maps AD identities into Unix NSS/PAM views. The idmap backend choice is architectural: `tdb` allocates locally, `rid` derives IDs from RID, `ad` reads RFC2307 attributes, and `autorid` allocates ranges for multiple domains. Never change a production mapping scheme casually: file ownership is stored as numeric IDs.

```bash
net ads join -U Administrator       # establish machine account and keytab/trust
net ads testjoin                    # verify machine trust
wbinfo --ping-dc                    # verify winbind-to-DC path
wbinfo -t                           # verify workstation trust secret
wbinfo -u                           # enumerate domain users when permitted
getent passwd 'EXAMPLE\\alice'      # test complete NSS path, not only winbind
pam-auth-update                     # Debian PAM profile selection
authselect current                  # RHEL-family managed NSS/PAM profile
sssctl config-check                 # validate SSSD configuration
sssctl domain-status example.com
```

Use `wbinfo` to isolate winbind and `getent` to test NSS end to end. For SSSD, `/etc/sssd/sssd.conf` must be root-owned and mode 0600. `pam_mkhomedir` creates homes at first login; `pam_faillock` tracks failed authentication. PAM order and control flags are security logic, not decoration.

### 33.4 DFS, printing, CIFS, and NFSv4

A DFS root gives clients a stable namespace whose links refer to other shares. Samba uses `msdfs root = yes` and link-like entries such as `msdfs:server\\share`. Printing requires CUPS integration, printer shares, spool permissions and driver strategy; diagnose CUPS first, then Samba publication, then client drivers.

```bash
smbclient -L //server -U alice      # enumerate server-visible shares
smbclient //server/docs -U alice    # test SMB without mounting
mount -t cifs //server/docs /mnt -o credentials=/root/.smbcred,vers=3.1.1
cifscreds add server                # cache credentials without fstab plaintext
nfs4_getfacl /srv/project
nfs4_setfacl -a 'A:g:devs@:rwaDxtTnNcCy' /srv/project
showmount -e server                 # useful for v3; incomplete view of an NFSv4 pseudo-tree
```

SMB share authorization and Unix filesystem/MAC authorization all have to allow the operation. NFSv4 uses a pseudo-root, stateful locking, identities such as `name@domain`, and richer ACLs. Kerberos flavors are `krb5` (authentication), `krb5i` (+integrity), and `krb5p` (+privacy).

---

## Chapter 34: Exam 303 Security Operations Supplement

### 34.1 DNSSEC and encrypted storage

DNSSEC authenticates DNS data; it does not encrypt queries. A ZSK signs ordinary RRsets, a KSK signs the DNSKEY set, and the parent publishes a DS digest to extend the chain of trust. RRSIG carries signatures; NSEC/NSEC3 proves non-existence.

```bash
dnssec-keygen -a ECDSAP256SHA256 -n ZONE example.com
dnssec-signzone -S -o example.com db.example.com
delv @192.0.2.53 www.example.com A   # validate and explain trust chain
dig +dnssec +multi example.com DNSKEY
dig +trace example.com DS
rndc signing -list example.com
```

For encryption, decide the layer: LUKS/dm-crypt protects a block device; eCryptfs encrypts per-file content/metadata and is retained in the objective for legacy understanding; Clevis can bind LUKS unlocking to TPM2 or Tang policy.

```bash
cryptsetup luksDump /dev/mapper/labdisk
cryptsetup luksHeaderBackup /dev/mapper/labdisk --header-backup-file lab.header
cryptsetup open /dev/mapper/labdisk securelab
clevis luks list -d /dev/mapper/labdisk
mount -t ecryptfs /srv/plain /srv/private    # legacy lab only
```

Header backup is recovery material and must be encrypted/offline. Verify that ciphertext is unreadable while closed and that recovery works before trusting it.

### 34.2 HIDS, NIDS, vulnerability work, and evidence

| Tool | Purpose and logic | Primary verification |
|---|---|---|
| AIDE | Baseline and compare filesystem metadata/hashes | Review changed-object report against approved change |
| auditd | Record policy-selected kernel audit events | `ausearch`, `aureport`, backlog/lost counters |
| fail2ban | Convert repeated log evidence into temporary bans | jail status plus firewall rule and expiry |
| rkhunter/chkrootkit | Heuristic rootkit indicators | Correlate; never treat one alert as proof |
| Suricata | Decode traffic and apply IDS/IPS rules | `suricata -T`, EVE JSON, counters |
| Zeek | Produce protocol/behavior logs | `zeekctl status`, `conn.log`, notice logs |
| nmap | Discover hosts/services and selected fingerprints | Confirm from target socket/config |
| OpenVAS/Greenbone | Authenticated/unauthenticated vulnerability assessment | Manually validate finding and remediation |
| arpwatch | Detect new or changed IP-to-MAC observations | Confirm against DHCP/switch inventory; changes may be legitimate |
| dsniff/Ettercap | Authorized lab analysis of credentials/MITM exposure | Packet evidence and endpoint configuration |
| ssldump | Decode inspectable TLS sessions when key exchange permits | Compare with `openssl s_client` and capture metadata |
| SSLsplit | Authorized TLS interception using a controlled CA | Confirm client trust path and remove lab CA afterward |
| stunnel | Wrap a plaintext TCP service in TLS | Test both wrapped listener and backend; inspect certificate |
| Tripwire | Policy-based filesystem integrity monitoring | Initialize trusted baseline, then review signed reports |

```bash
aide --init && aide --check
auditctl -w /etc/sudoers -p wa -k sudoers-change
ausearch -k sudoers-change -i
suricata -T -c /etc/suricata/suricata.yaml
zeek -r capture.pcap
nmap -sS -sV -O --reason 192.0.2.0/28
arpwatch -i eth0
ssldump -i eth0 -k server.key 'port 443'  # legacy RSA lab; modern PFS usually prevents decryption
stunnel /etc/stunnel/service.conf
```

Only scan or intercept systems you own or are explicitly authorized to test. `dsniff`, Ettercap and SSLsplit are dual-use assessment tools: isolate the lab, install interception CAs only on lab clients, and remove them afterward. Preserve packet captures and logs read-only, record hashes and timestamps, and distinguish observation from remediation.

### 34.3 Resource control, DAC, MAC, and network controls

DAC uses ownership, mode bits, ACLs and capabilities. MAC adds policy independent of owner discretion (SELinux labels/types; AppArmor path-based profiles). Cgroups limit/account resources; PAM limits apply to eligible login sessions; shell `ulimit` changes the current process and descendants.

```bash
getfacl -p FILE; namei -l /path/to/FILE
getcap FILE; getpcaps PID
prlimit --pid PID
systemctl set-property app.service MemoryMax=512M CPUQuota=50%
getenforce; matchpathcon /srv/app/file; ausearch -m AVC -ts recent
aa-status; aa-logprof
```

Network-hardening order: enumerate listeners (`ss -lntup`), identify owner/config, remove unnecessary service, bind narrowly, authenticate/encrypt, filter, then monitor. Packet filters decide on packet/connection attributes; application proxies understand higher-level protocols.

```bash
nft --check -f /etc/nftables.conf
nft monitor trace
iptables-save                         # know legacy interface and migration implications
ip xfrm state; ip xfrm policy        # IPsec kernel state/policy
openvpn --config client.conf
wg show                               # WireGuard awareness and runtime state
```

For a penetration test, define written scope, time, allowed techniques, data handling and emergency contacts. Follow discovery → validation → controlled exploitation → evidence → cleanup → retest. Never confuse a scanner's severity with business risk.

---

## Chapter 35: Exam 305 Virtualization and Containerization Supplement

### 35.1 Xen, QEMU, libvirt, and image decisions

Xen's privileged control domain is Dom0; guests are DomU. PV guests cooperate with the hypervisor, HVM guests use hardware virtualization, and PVH combines relevant properties. `xl` talks to the Xen toolstack.

```bash
xl info; xl list; xl dmesg
xl create guest.cfg
xl console GUEST
xl shutdown GUEST
```

QEMU provides machine/device emulation; KVM supplies kernel hardware acceleration; libvirt supplies a management API and persistent domain/network/storage definitions. `virsh start` starts an existing persistent domain, while `virsh create XML` creates a transient running domain. `define` persists XML; `undefine` removes that definition, not necessarily every disk.

```bash
virt-host-validate
virsh list --all; virsh dominfo VM
virsh dumpxml VM >vm.xml
virsh net-list --all; virsh pool-list --all
virsh snapshot-list VM
qemu-img info --backing-chain child.qcow2
qemu-img convert -p -O raw source.qcow2 target.raw
```

Raw is simple/predictable; qcow2 supports sparse allocation, backing files, snapshots and optional compression/encryption with overhead. Never mutate an actively used image offline.

### 35.2 LXC and container internals

LXC is system-container tooling: it runs a userspace that resembles a small Linux system while sharing the host kernel. Namespaces isolate views; cgroups control resources; capabilities/seccomp/MAC narrow privilege; overlay filesystems layer images. A container is not a VM and cannot supply a different kernel.

```bash
lxc-checkconfig
lxc-create -n lab -t download
lxc-start -n lab -d
lxc-info -n lab
lxc-attach -n lab
lxc-stop -n lab; lxc-destroy -n lab
```

Know `/var/lib/lxc/NAME/config`, network veth/bridge setup, UID/GID maps for unprivileged containers, and why device mounts/privileged mode weaken isolation.

### 35.3 Docker and orchestration reasoning

```bash
docker image inspect IMAGE
docker container inspect CONTAINER
docker exec -it CONTAINER sh
docker logs --since 10m CONTAINER
docker stats --no-stream
docker network inspect NET
docker volume inspect VOL
docker compose config                 # render/validate merged model
```

An image is immutable content plus metadata; a container adds a writable layer and runtime configuration. Bind mounts expose a host path; named volumes have engine-managed lifecycle. `EXPOSE` documents a port; publishing (`-p`) creates host reachability. `CMD` supplies defaults; `ENTRYPOINT` selects the executable. Multi-stage builds reduce final contents, but secrets must use build-secret mechanisms and must not be copied into layers.

Orchestrators reconcile desired state: scheduling, service discovery, health, rollout, secrets and persistent storage. Understand Kubernetes Pods, Deployments, Services, ConfigMaps, Secrets and volumes; Docker Swarm services/stacks; and the difference between liveness and readiness.

```bash
kubectl get pods -o wide
kubectl describe pod NAME
kubectl logs NAME --previous
kubectl rollout status deployment/APP
docker service ls; docker service ps SERVICE
```

### 35.4 Cloud management, cloud-init, Packer, and Vagrant

IaaS managers such as OpenStack manage compute, network and storage resources; tools such as Terraform declare infrastructure; cloud-init performs first-boot instance customization. Packer builds images; Vagrant coordinates reproducible development machines. These layers solve different problems.

```yaml
#cloud-config
users:
  - name: ops
    groups: [sudo]
    ssh_authorized_keys: ["ssh-ed25519 AAAA..."]
packages: [nginx]
runcmd:
  - [systemctl, enable, --now, nginx]
```

```bash
cloud-init schema --config-file user-data
cloud-init status --long
cloud-init analyze blame
cloud-init clean --logs                 # lab image preparation; changes next boot behavior
packer validate .; vagrant validate
```

---

## Chapter 36: Exam 306 High Availability and Storage Supplement

### 36.1 Load balancing and failover

Keepalived can run VRRP for a floating address and health-driven IPVS configuration. HAProxy provides L4/L7 proxying and rich health checks. Pacemaker/Corosync manages resources and membership; fencing protects shared state. These are complementary, not interchangeable.

```bash
keepalived --config-test
ip -br address; ipvsadm -Ln --stats
haproxy -c -f /etc/haproxy/haproxy.cfg
echo 'show stat' | socat stdio /run/haproxy/admin.sock
corosync-cfgtool -s; corosync-quorumtool -s
pcs resource config; pcs constraint config
crm_simulate -Ls
```

Understand active/passive versus active/active, shared-disk versus shared-nothing, stickiness, colocation and ordering constraints, failure counts, migration thresholds, quorum devices and watchdog/SBD fencing. Test the actual fence path; a configured but ineffective STONITH agent is not safety.

### 36.2 DRBD and shared storage access

DRBD replicates a block device between nodes. Primary/Secondary describes write authority; protocol C acknowledges after remote disk commit. Dual-primary requires a cluster-aware filesystem and strict fencing.

```bash
drbdadm dump all; drbdadm status
drbdsetup status --verbose --statistics
drbdadm create-md RESOURCE
drbdadm up RESOURCE
drbdadm primary --force RESOURCE          # destructive initialization: lab only
```

Read `/proc/drbd` on older versions and resource files under `/etc/drbd.d/`. Know split-brain policies and why manual survivor selection must follow evidence. For shared SAN access, understand iSCSI initiator/target sessions, WWIDs, device mapper multipath and persistent reservations.

```bash
iscsiadm -m discovery -t sendtargets -p 192.0.2.30
iscsiadm -m session -P 3
multipath -ll
sg_persist --in --read-keys /dev/mapper/mpatha
```

### 36.3 Clustered and distributed filesystems

GFS2/OCFS2 permit coordinated access to shared block storage and require functioning membership/locking/fencing. GlusterFS aggregates bricks into distributed/replicated volumes. Ceph uses MONs for maps/quorum, OSDs for data, MGRs for management, and optionally MDS for CephFS; RADOS underlies RBD and CephFS.

```bash
gfs2_tool sb /dev/mapper/vg-lv all
mount -t gfs2 -o locktable=cluster:data /dev/vg/lv /data
gluster peer status; gluster volume info
gluster volume status; gluster volume heal VOL info
ceph -s; ceph health detail
ceph osd tree; ceph osd df
ceph quorum_status; ceph pg stat
rbd info POOL/IMAGE
```

In Ceph diagnosis, start with health detail, quorum, OSD topology/capacity, then placement groups. Do not mark an OSD lost or force PG repair before understanding data-redundancy consequences.

### 36.4 Single-node availability

Availability also depends on redundant power, paths, NICs and storage. RAID improves availability, not backup. Know hot spares, write-intent bitmaps, reshape, consistency policy and failure replacement.

```bash
mdadm --detail /dev/md0
cat /proc/mdstat
mdadm --examine /dev/sdX1
mdadm --manage /dev/md0 --fail /dev/sdX1 --remove /dev/sdX1
lvs -a -o +devices,segtype,data_percent,metadata_percent
lvconvert --type raid1 -m1 vg/lv
lvconvert --type thin-pool vg/pool
```

LVM RAID provides redundancy inside an LV; thin pools overcommit and require monitoring of both data and metadata; snapshots are not independent backups. Network HA includes bonding/teaming, LACP switch coordination, multipath routing, VRRP and redundant DNS/routes. Verify failure behavior, not merely configuration syntax.

---

## Chapter 37: Distribution-Aware Labs and Final Readiness Gate

### 37.1 Translate concepts across distributions

| Intent | Debian/Ubuntu | RHEL-family | Verification |
|---|---|---|---|
| Install | `apt install PKG` | `dnf install PKG` | package query + binary version |
| Apache service | `apache2` | `httpd` | `systemctl status`, `curl` |
| SSH service | commonly `ssh` | commonly `sshd` | `ss -lntp`, `ssh -v` |
| Firewall | nftables/ufw variants | firewalld/nftables | `nft list ruleset` plus traffic test |
| PAM profiles | `pam-auth-update` | `authselect` | inspect generated stack; test spare session |
| SELinux/AppArmor | often AppArmor | usually SELinux | `aa-status` / `getenforce` |
| Network persistence | netplan/ifupdown/NM | NetworkManager profiles | reboot or profile reactivate, then `ip` |

Never infer package, service or path names blindly. Use `systemctl list-unit-files`, package search, `command -v`, `man`, and the installed configuration include tree.

### 37.2 Runnable lab protocol

For every high-risk lab, use two disposable VMs, snapshots and console access. Record this worksheet:

```text
Objective ID:
Initial state and snapshot:
Intent / expected state:
Read-only discovery commands:
Candidate configuration and syntax check:
Mutation command:
Independent functional verification:
Injected fault and observed evidence:
Rollback and proof of restoration:
What would differ on the other distribution family:
```

Minimum practical gates:

1. **101/102:** recover GRUB, repair a broken fstab from rescue mode, build a pipeline safe for hostile filenames, write a defensive Bash script, diagnose DNS and permissions.
2. **201/202:** locate a CPU/I/O/network bottleneck, build/recover mdraid+LVM on loop devices, compile a kernel module, operate DNS/web/mail/file-sharing services, route and filter a lab network.
3. **300:** provision an isolated AD DC/member/client; break DNS, time, trust, idmap and ACLs one at a time; back up and restore.
4. **303:** operate a CA and DNSSEC zone; configure LUKS, MAC, audit, IDS and VPN; validate a scan finding and document evidence.
5. **305:** manage Xen concepts and a libvirt VM/image/network; build LXC and Docker labs; diagnose cloud-init/Packer/Vagrant failures.
6. **306:** demonstrate load-balancer failover, quorum and fencing; build DRBD and one distributed-storage lab; diagnose degraded Ceph/Gluster state.

### 37.3 Final readiness gate

You are ready to book **one specific exam** only when all of these are true:

- Every objective row for that exam is marked explain/use/troubleshoot—not merely “read.”
- You score at least 85% twice on fresh, timed, objective-weighted practice sets.
- You can state the purpose, important input/config, output, side effect and verification for every utility in the official partial command list.
- You can solve representative failures from symptoms without immediately reading a solution.
- You have repeated destructive labs from a clean snapshot and proven rollback.
- You re-check the official objective page and exam code immediately before scheduling.

This handbook is objective-complete for the versions stated above, but no handbook can guarantee every live question or a passing score. LPI's official objectives are the authority if wording or versions change.

---

# Final Section: Exam Preparation

## Mock Exam 1 — LPIC-1 (Exam 101)

### Questions

1. Which command shows the kernel ring buffer with estimated human-readable wall-clock timestamps? — A) `dmesg -t` B) `dmesg -T` C) `dmesg -h` D) `journalctl -T`
2. The GRUB menu file `grub.cfg` should be edited by — A) Directly with vi B) Running `update-grub` after editing `/etc/default/grub` C) Running `grub-mkpasswd` D) Editing `/boot/grub.lst`
3. Which `find` expression matches files larger than 50 MB modified less than 7 days ago? — A) `-size +50M -mtime -7` B) `-size 50M -mtime 7` C) `-size +50M -mtime +7` D) `-size -50M -mtime -7`
4. If a process has umask `0022`, what mode does a newly created regular file normally receive from base mode `0666`? — A) 0666 B) 0600 C) 0644 D) 0755
5. Which permission bit causes new files in a directory to inherit its group? — A) SUID B) SGID C) Sticky D) ACL
6. Which `tar` flag uses bzip2 compression? — A) `-z` B) `-j` C) `-J` D) `-Z`
7. Which command shows the inode number of a file? — A) `ls -i` B) `stat -i` C) `inode` D) `file -i`
8. Which RPM verify column means "MD5 differs"? — A) `S` B) `M` C) `5` D) `T`
9. Which dpkg command lists files installed by a package? — A) `dpkg -c` B) `dpkg -L` C) `dpkg -s` D) `dpkg -I`
10. Which file holds password hashes? — A) `/etc/passwd` B) `/etc/shadow` C) `/etc/gshadow` D) `/etc/security/pwd`
11. Which command boots the system into the systemd rescue target? — A) `systemctl rescue` B) `systemctl isolate rescue.target` C) `init 1` D) Both A and B are correct
12. Which command lists all currently mounted filesystems including bind mounts? — A) `df -a` B) `findmnt` C) `mount -l` D) Both B and C
13. In `chmod 4755 file`, the leading 4 means — A) Sticky B) SUID C) SGID D) ACL on
14. Which directory holds locally compiled software (FHS)? — A) `/usr/bin` B) `/usr/local` C) `/opt` D) `/var/local`
15. Which command shows currently loaded kernel modules? — A) `modinfo` B) `lsmod` C) `modprobe -l` D) `modlist`
16. Which `sed` command deletes lines 1-3? — A) `sed '1,3d'` B) `sed '1+3d'` C) `sed '1~3d'` D) `sed '1.3d'`
17. Which `awk` built-in variable holds the number of records read so far? — A) `NF` B) `NR` C) `FILENAME` D) `RS`
18. Which redirection combines stderr into stdout? — A) `2>&1` B) `1>&2` C) `>&` D) `2>1`
19. Which file is consulted *first* for hostname resolution by default? — A) `/etc/resolv.conf` B) `/etc/hosts` C) `/etc/nsswitch.conf` D) `/etc/hostname`
20. Which `useradd` flag creates the home directory? — A) `-d` B) `-m` C) `-h` D) `-c`
21. Which command renames a group? — A) `groupmod -n new old` B) `groupmod -r new old` C) `groupmod --rename old new` D) `gpasswd -r`
22. Which command displays the routing table without DNS lookups? — A) `route` B) `ip route` C) `netstat -rn` D) Both B and C
23. Which `cron` field comes first in `* * * * *`? — A) Minute B) Hour C) Day of month D) Month
24. Which file lists user-level cron jobs on Debian? — A) `/etc/crontab` B) `/var/spool/cron/crontabs/<user>` C) `/var/cron/<user>` D) `/etc/cron.d/<user>`
25. Which option to `ps` is BSD style and most user-friendly? — A) `-ef` B) `aux` C) `-aux` D) `-eLf`
26. Which signal terminates a process without giving it a chance to clean up? — A) SIGTERM B) SIGKILL C) SIGHUP D) SIGINT
27. Which command sets the niceness of a running process? — A) `nice -n 5` B) `renice 5 -p PID` C) `priority 5 PID` D) `nicectl`
28. Which file shows CPU model and flags? — A) `/sys/cpu/info` B) `/proc/cpuinfo` C) `/dev/cpu` D) `/etc/cpuinfo`
29. Which `xargs` flag uses NUL as the input separator? — A) `-n` B) `-0` C) `-d ''` D) `-z`
30. To start a job and detach so it survives logout, use — A) `nohup cmd &` B) `cmd &!` C) `cmd > /dev/null` D) `bg cmd`
31. Which command shows the PIDs of all processes named `nginx`? — A) `pkill nginx` B) `pidof nginx` C) `pgrep nginx` D) Both B and C
32. Which command lists open file descriptors of process 1234? — A) `ls -l /proc/1234/fd` B) `lsof -p 1234` C) `fdshow 1234` D) Both A and B
33. The `tee` command sends stdin to — A) stdout only B) stdout and one or more files C) /dev/null D) only files
34. Which command extracts a tarball preserving permissions? — A) `tar -xvzf` B) `tar -xpvzf` C) `tar -xkvzf` D) `tar -xRvzf`
35. The default chmod symbolic for 644 is — A) `u=rw,g=r,o=r` B) `a=rw` C) `u=rwx,g=r,o=r` D) `u=rwx,go=r`
36. Hard links cannot — A) Span filesystems B) Have multiple names C) Survive removal of the original D) Point to files
37. Which `apt` command searches package names and descriptions? — A) `apt search` B) `apt-cache find` C) `apt locate` D) `apt grep`
38. Which `dnf` command undoes the last transaction? — A) `dnf undo` B) `dnf history undo` C) `dnf rollback` D) `dnf revert`
39. Which `parted` flag identifies the EFI System Partition? — A) `boot` B) `esp` C) `bios_grub` D) `efi`
40. Which filesystem cannot be shrunk? — A) ext4 B) xfs C) btrfs D) ext2
41. Which command shows block devices in tree form with UUIDs? — A) `lsblk -f` B) `lsdev` C) `findmnt` D) `blkid -t`
42. Which `cp` invocation requests archive-style preservation of a directory tree? — A) `cp -r src dst` B) `cp -a src dst` C) `mv src dst` D) `cp -f src dst`
43. Which command extracts only specific files from a tarball? — A) `tar -xzf archive.tar.gz path/in/archive` B) `tar -xzf archive.tar.gz -f path` C) `tar -only path` D) `tar -e path`
44. Which `find` option deletes matches without `-exec rm`? — A) `-erase` B) `-delete` C) `-purge` D) `-rm`
45. Which command lists open TCP listening sockets with their processes? — A) `ss -tlnp` B) `lsof -i tcp` C) `netstat -tlnp` D) All of the above
46. Which file controls which TTYs root can log into directly? — A) `/etc/securetty` B) `/etc/login.defs` C) `/etc/passwd` D) `/etc/pam.d/login`
47. Which `chage` flag prints account aging information? — A) `-l` B) `-L` C) `-i` D) `-c`
48. Which signal does `nginx -s reload` send? — A) SIGHUP B) SIGTERM C) SIGUSR1 D) SIGUSR2
49. Which command checks ext4 filesystem consistency? — A) `fsck.ext4` B) `e2fsck` C) Either A or B D) `xfs_repair`
50. Which is correct about `/proc/sys/`? — A) Read-only B) Settings revert on reboot unless persisted in `/etc/sysctl.conf` C) Only root can write D) Both B and C

### Answers

1. **B** — `dmesg -T` estimates wall-clock time; journal timestamps are preferable for correlation. 2. **B** — do not edit generated `grub.cfg` directly. 3. **A**. 4. **C** — `0666 & ~0022 = 0644`. 5. **B**. 6. **B**. 7. **A**. 8. **C**. 9. **B**. 10. **B**.
11. **D**. 12. **D**. 13. **B**. 14. **B**. 15. **B**. 16. **A**. 17. **B**. 18. **A**. 19. **C** — `nsswitch.conf` defines lookup order. 20. **B**.
21. **A**. 22. **D**. 23. **A**. 24. **B**. 25. **B**. 26. **B**. 27. **B**. 28. **B**. 29. **B**. 30. **A**.
31. **D**. 32. **D**. 33. **B**. 34. **B**. 35. **A**. 36. **A**. 37. **A**. 38. **B**. 39. **B**. 40. **B**.
41. **A**. 42. **B** — archive mode preserves recursive metadata subject to filesystem support and privilege. 43. **A**. 44. **B**. 45. **D**. 46. **A**. 47. **A**. 48. **A**. 49. **C**. 50. **D**.

---

## Mock Exam 2 — LPIC-1 (Exam 102)

### Questions

1. Which file lists static name→IP mappings? — A) `/etc/hosts` B) `/etc/resolv.conf` C) `/etc/nsswitch.conf` D) `/etc/network/interfaces`
2. Which command shows the IP routing table? — A) `ip route` B) `route -n` C) `netstat -rn` D) All of the above
3. Which port does SMTP use by default? — A) 25 B) 110 C) 143 D) 587
4. The CIDR /28 corresponds to netmask — A) 255.255.255.240 B) 255.255.255.224 C) 255.255.255.192 D) 255.255.255.248
5. Which modern command filters TCP sockets specifically to the established state? — A) `ss -t state established` B) `netstat -t` C) `lsof -i :*` D) `ip tcp established`
6. Which `journalctl` flag shows kernel-only messages? — A) `-k` B) `-K` C) `--kernel` D) `-K all`
7. The systemd-equivalent of runlevel 5 is — A) `rescue.target` B) `multi-user.target` C) `graphical.target` D) `default.target`
8. Which DNS record type maps name → IPv4? — A) A B) AAAA C) CNAME D) PTR
9. Which rsyslog selector matches all priorities of mail? — A) `mail.*` B) `mail.all` C) `mail` D) `*.mail`
10. Which file holds rsyslog rules typically? — A) `/etc/syslog.conf` B) `/etc/rsyslog.conf` C) `/etc/syslog/rsyslog.d` D) `/var/log/rsyslog.conf`
11. Which `logrotate` directive compresses on the NEXT rotation, not the current? — A) `compress` B) `delaycompress` C) `dateext` D) `sharedscripts`
12. Which command synchronizes the hardware clock from the system clock? — A) `hwclock --systohc` B) `hwclock --hctosys` C) `date --hctosys` D) `timedatectl set-hardware`
13. Which key generates passwordless SSH login (Server side)? — A) Server's host key B) Client's public key appended to `~/.ssh/authorized_keys` C) Client's private key on server D) PAM secret
14. Which `ssh` flag forwards a local port through the tunnel? — A) `-L` B) `-R` C) `-D` D) `-A`
15. Which `gpg` flag encrypts using a recipient's public key? — A) `-c` B) `-e -r RECIPIENT` C) `--sign` D) `--symmetric`
16. Which file holds the SSH client's *known* server keys? — A) `~/.ssh/authorized_keys` B) `~/.ssh/known_hosts` C) `/etc/ssh/ssh_host_keys` D) `~/.ssh/config`
17. Which command lists timers scheduled by systemd? — A) `systemctl list-timers` B) `systemctl list-cron` C) `systemctl timers` D) `systemctl list-units --timers`
18. Which language has UTF-8 locale named `en_US.UTF-8`? — A) C B) English (US) C) British D) German
19. Which `locale` setting affects sort order? — A) `LC_COLLATE` B) `LC_CTYPE` C) `LC_TIME` D) `LANGUAGE`
20. Which file configures timezone on systemd systems? — A) `/etc/timezone` B) `/etc/localtime` (symlink to zoneinfo) C) `/etc/zone.conf` D) `/etc/tz`
21. Which command schedules a one-time job? — A) `at 10:00` B) `cron 10:00` C) `batch 10:00` D) `schedule 10:00`
22. Which file allows or denies users from cron? — A) `/etc/cron.allow` and `/etc/cron.deny` B) `/etc/cron.conf` C) `/etc/cron.users` D) `/etc/cron/access`
23. Which `crontab` file holds the system-wide table with a user column? — A) `/etc/crontab` B) `/var/spool/cron/root` C) `/etc/cron.d/system` D) Both A and C
24. The cron entry `0 */2 * * *` runs — A) Once every 2 minutes B) Once every 2 hours on the hour C) At 0 minutes past midnight every 2 days D) Twice an hour
25. Which file in PAM denies non-root login when present? — A) `/etc/nologin` B) `/etc/login.deny` C) `/etc/passwd.lock` D) `/var/run/nologin`
26. Which command shows current sudo privileges? — A) `sudo -l` B) `sudo --list` C) Both work D) `sudoers -l`
27. Which `passwd` flag shows password status? — A) `-S` B) `-s` C) `-l` D) `-L`
28. Which sshd directive disables password authentication entirely? — A) `PasswordAuthentication no` B) `PermitPasswordLogin no` C) `UsePAM no` D) `DisablePassword yes`
29. Which file sets default UID min/max for new users? — A) `/etc/login.defs` B) `/etc/default/useradd` C) `/etc/passwd` D) `/etc/skel/useradd.conf`
30. Which printing service is most commonly used today? — A) lpd B) CUPS C) PCL D) LPRng
31. Which command lists CUPS printers? — A) `lpstat -p` B) `lpinfo -v` C) `lpc status` D) `cups-list`
32. Which command sends a job to printer `office`? — A) `lp -d office file` B) `lpr -P office file` C) Both A and B D) `print office file`
33. Which command cancels print job 12 on printer `office`? — A) `cancel office-12` B) `lprm 12` C) Both A and B (depending on tool) D) `kill 12`
34. Which file or directory holds AppArmor profiles? — A) `/etc/apparmor.d/` B) `/etc/selinux/policy` C) `/etc/security/profiles` D) `/etc/aa/`
35. Which command lists SELinux booleans? — A) `getsebool -a` B) `semanage boolean -l` C) Both A and B D) `setsebool -L`
36. Which ssh option does NOT exist? — A) `-L` B) `-D` C) `-V` D) `-Q`  (Trick: -V prints version; -Q queries algorithms)

(Answer: all exist; the LPIC trap is recognizing them.)

37. Which port is used by IMAPS? — A) 143 B) 993 C) 995 D) 465
38. Which port is used by NTP? — A) 119 B) 123 C) 137 D) 161
39. Which command lists `xinetd`-style services? — A) `xinetd -d list` B) `systemctl list-unit-files --type=socket` C) `chkconfig --list` D) Depends on the distribution
40. The `at` queue files live under — A) `/var/spool/cron/atjobs` B) `/var/spool/at/` C) `/var/at/queue` D) `/var/lib/at`
41. Which directive in `sshd_config` allows only members of group `wheel`? — A) `AllowGroups wheel` B) `RequireGroup wheel` C) `Match Group wheel` D) `Allowed wheel`
42. Which file records local supplementary-group membership such as membership in the historical `dialout` group? — A) `/etc/ppp/options` B) `/etc/ppp/peers/` C) `/etc/sudoers` D) `/etc/group`
43. Which command shows the public DNS for a domain's MX? — A) `dig MX example.com` B) `host -t MX example.com` C) Both A and B D) `nslookup -mx example.com`
44. Which `ip` command adds a default gateway? — A) `ip route add default via 192.168.1.1` B) `ip route add 0.0.0.0 192.168.1.1` C) `ip add default 192.168.1.1` D) `ip gw 192.168.1.1`
45. Which file lists swap areas in use? — A) `/proc/swaps` B) `/etc/swap` C) `/proc/sys/swap` D) `/sys/class/swap`
46. The systemd target equivalent of "single user mode" is — A) `single.target` B) `rescue.target` C) `emergency.target` D) `runlevel1.target`
47. Which command rebuilds the modules.dep file? — A) `depmod -a` B) `modprobe -d` C) `update-modules` D) `lsmod -r`
48. Which command shows the kernel command line at boot? — A) `cat /proc/cmdline` B) `dmesg \| head` C) `uname -c` D) `cat /boot/cmdline`
49. Which is correct about the `mail` priority `none` in rsyslog? — A) It matches only emerg B) It excludes mail from matching the selector C) It logs to mail only D) It silences mail entirely
50. Which command displays a user's effective UID and groups? — A) `id` B) `whoami` C) `who am i` D) `groups`

### Answers

1. **A** 2. **D** 3. **A** 4. **A** 5. **A** 6. **A** 7. **C** 8. **A** 9. **A** 10. **B**
11. **B** 12. **A** 13. **B** 14. **A** 15. **B** 16. **B** 17. **A** 18. **B** 19. **A** 20. **B**
21. **A** 22. **A** 23. **D** 24. **B** 25. **A** 26. **C** 27. **A** 28. **A** 29. **A** 30. **B**
31. **A** 32. **C** 33. **C** 34. **A** 35. **C** 36. **All listed options exist.** 37. **B** 38. **B** 39. **D** 40. **B**
41. **A** 42. **D** 43. **C** 44. **A** 45. **A** 46. **B** 47. **A** 48. **A** 49. **B** 50. **A**

---

## Mock Exam 3 — LPIC-2 (Exam 201)

### Questions

1. Which kernel-build target creates an installable Debian package? — A) `make bzImage` B) `make bindeb-pkg` C) `make pkg-deb` D) `make debian`
2. Which file documents kernel build options for the running kernel? — A) `/boot/config-$(uname -r)` B) `/proc/config.gz` (if enabled) C) Both can be valid D) `/etc/kernel.conf`
3. Which directory holds modules for the running kernel? — A) `/lib/modules/$(uname -r)` B) `/boot/modules/` C) `/etc/modules.d/` D) `/proc/modules`
4. Which tool regenerates the initramfs on Debian? — A) `update-initramfs -u` B) `dracut -f` C) `mkinitrd` D) `mkinitramfs`
5. Which sysctl sets vm.swappiness to 10? — A) `sysctl -w vm.swappiness=10` B) `echo 10 > /proc/sys/vm/swappiness` C) Both work D) `sysctl vm.swappiness 10`
6. Which `systemd` unit type triggers a service on a schedule? — A) timer B) cron C) service-timer D) job
7. Which RAID level requires at least 3 disks and tolerates one failure? — A) 0 B) 1 C) 5 D) 6
8. Which file lists active multipath devices? — A) `/proc/mdstat` B) `/sys/block/mpath` C) `/etc/multipath/bindings` D) Output of `multipath -ll`
9. Which `mdadm` flag marks a device as failed? — A) `--fail` B) `--remove` C) `--zero-superblock` D) `--detach`
10. Which command activates a volume group? — A) `vgchange -ay` B) `vgactivate` C) `vgenable` D) `vgon`
11. Which LVM command shrinks a logical volume *and* its filesystem? — A) `lvreduce -r` B) `lvresize -r -L 5G` C) `lvresize -r --resizefs` D) Either A or B if `-L` is given
12. Which filesystem supports online shrink? — A) ext4 B) xfs C) btrfs D) Both A and C
13. Which file maps LUKS containers at boot? — A) `/etc/fstab` B) `/etc/crypttab` C) `/etc/luks` D) `/etc/cryptsetup/conf`
14. Which command lists active iSCSI sessions? — A) `iscsiadm -m session` B) `iscsi list` C) `iscsictl -l` D) `iscsi-status`
15. Which iptables target alters source IP for outgoing connections through a NAT gateway? — A) DNAT B) SNAT/MASQUERADE C) REDIRECT D) MARK
16. Which iptables chain in the `nat` table processes packets before routing? — A) PREROUTING B) FORWARD C) INPUT D) OUTPUT
17. Which option in iptables matches only new connections? — A) `--ctstate NEW` B) `--syn` C) `-m conntrack --ctstate NEW` D) Both A or C (modern uses conntrack)
18. Which command saves iptables rules to a file? — A) `iptables-save > file` B) `iptables --save file` C) `iptables -W file` D) `iptables-export file`
19. Which command can move logical extents from one PV to another? — A) `pvmove` B) `vgmove` C) `lvmove` D) `lvconvert`
20. Which command displays UUIDs of block devices? — A) `lsblk -f` B) `blkid` C) Both A and B D) `uuid -l`
21. Which `tar` option enables incremental backup snapshots? — A) `--increment` B) `--listed-incremental=FILE` C) `-G` D) Both B and C
22. Which `rsync` flag deletes destination files no longer present in source? — A) `--purge` B) `--delete` C) `--clean` D) `--sync`
23. Which `rsync` flag hardlinks files unchanged from a previous backup directory? — A) `--link-dest` B) `--hardlink` C) `--snapshot` D) `--keep`
24. Which `dd` operand skips N input blocks? — A) `skip=N` B) `seek=N` C) `count=N` D) `iskip=N`
25. Which BIND zone type holds root hints? — A) `master` B) `slave` C) `hint` D) `stub`
26. Which BIND statement allows recursion for a specific subnet? — A) `allow-recursion { 10.0.0.0/8; };` B) `recursion-allow` C) `recursion-network` D) `allow-recurse`
27. Which DNS RR points names to IPv6? — A) AAAA B) A6 C) IP6 D) HOST6
28. Which command tests a zone file? — A) `dig +zone` B) `named-checkzone` C) `rndc-checkzone` D) `validate-zone`
29. Which Apache module rewrites URLs? — A) mod_rewrite B) mod_proxy C) mod_alias D) mod_url
30. Which Apache directive activates `.htaccess` for a directory? — A) `AllowOverride All` B) `htaccess on` C) `AccessFileName .htaccess` D) `OverrideAllow`
31. Which Nginx variable holds the original client IP behind a reverse proxy? — A) `$remote_addr` B) `$client_ip` C) `$x_forwarded_for` D) Need `set_real_ip_from` + `real_ip_header` configured
32. Which command tests Apache config syntax? — A) `apachectl configtest` B) `httpd -t` C) Both A and B D) `apache2ctl test`
33. Which Nginx location form matches exactly? — A) `location = /` B) `location ~ /` C) `location /` D) `location ^~ /`
34. Which Samba security mode joins an Active Directory? — A) `security = user` B) `security = ads` C) `security = domain` D) `security = share`
35. Which Samba command tests configuration? — A) `testparm` B) `smbcheck` C) `smb -t` D) `nmbd -t`
36. Which command adds a Samba password for a user? — A) `smbpasswd -a alice` B) `passwd -s alice` C) `pdbedit -p alice` D) `samba-tool user create alice`
37. Which NFSv4 option provides Kerberos encryption? — A) `sec=sys` B) `sec=krb5i` C) `sec=krb5p` D) `sec=ntlm`
38. Which file lists NFS exports? — A) `/etc/exports` B) `/etc/nfs.exports` C) `/var/lib/nfs/etab` (read-only) D) Both A (config) and C (live)
39. Which postfix command refreshes `/etc/aliases.db`? — A) `newaliases` B) `postmap aliases` C) `postalias -u` D) Both A and B (postmap on hash:/etc/aliases)
40. Which postfix command flushes the queue? — A) `postqueue -f` B) `postsuper -f` C) `postflush` D) `mailq -f`
41. Which Dovecot directive sets mailbox format? — A) `mail_location = maildir:~/Maildir` B) `mailbox_format` C) `mailspool` D) `format = maildir`
42. Which DNS record holds DKIM public keys? — A) A B) TXT under `selector._domainkey.domain` C) DKIM D) DNSKEY
43. Which OpenVPN parameter pushes a default gateway to clients? — A) `gateway` B) `push "redirect-gateway def1"` C) `route-default` D) `client-default`
44. Which command shows the running kernel version? — A) `uname -r` B) `uname -v` C) `uname -a` (prints, includes r) D) Both A and C
45. Which command lists loaded modules and their dependencies? — A) `lsmod` B) `modprobe --show-depends` C) `modinfo` D) `depmod -lv`
46. Which file enables IP forwarding persistently? — A) `/etc/sysctl.conf` (`net.ipv4.ip_forward=1`) B) `/proc/sys/net/ipv4/ip_forward` (only runtime) C) `/etc/network/interfaces` D) Both A is persistent, B is runtime
47. Which dnssec tool generates ZSK/KSK keys? — A) `dnssec-keygen` B) `dnssec-signzone` C) `named-keygen` D) `rndc keygen`
48. Which mail header is added by DKIM signing? — A) `Received-SPF` B) `DKIM-Signature` C) `X-DKIM` D) `Authentication-Results`
49. Which command compares two ldap entries? — A) `ldapcompare` B) `ldapsearch -e compare` C) `ldapdiff` D) `ldap -c`
50. Which Postfix parameter sets the default outbound relayhost? — A) `relayhost` B) `smarthost` C) `outbound_server` D) `default_relay`

### Answers

1. **B** 2. **C** 3. **A** 4. **A** 5. **C** 6. **A** 7. **C** 8. **D** 9. **A** 10. **A** 11. **D** 12. **D** (XFS cannot shrink) 13. **B** 14. **A** 15. **B** 16. **A** 17. **D** 18. **A** 19. **A** 20. **C** 21. **D** 22. **B** 23. **A** 24. **A** 25. **C** 26. **A** 27. **A** 28. **B** 29. **A** 30. **A** 31. **D** 32. **C** 33. **A** 34. **B** 35. **A** 36. **A** 37. **C** 38. **D** 39. **D** 40. **A** 41. **A** 42. **B** 43. **B** 44. **D** 45. **B** 46. **D** 47. **A** 48. **B** 49. **A** 50. **A**

---

## Mock Exam 4 — LPIC-2 (Exam 202)

### Questions

1. Which command actively requests a full zone transfer from a named authoritative server? — A) `rndc dumpdb` B) `rndc stats` C) `dig AXFR example.com @master` D) `named-checkzone -x example.com`
2. Which BIND statement restricts zone transfers? — A) `allow-transfer` B) `transfer-acl` C) `allow-axfr` D) `xfer-allow`
3. Which command requests an HTTPS-only TLS connection to test SMTP STARTTLS? — A) `openssl s_client -connect host:25 -starttls smtp` B) `nc -ssl host 25` C) `tls-test host 25` D) `gnutls-cli host:25`
4. Which Apache directive enables HTTP/2? — A) `Protocols h2 http/1.1` B) `EnableHTTP2 On` C) `H2 On` D) `mod_h2 enable`
5. Which file is the default DocumentRoot on RHEL Apache? — A) `/var/www/html` B) `/srv/http` C) `/usr/share/httpd/www` D) `/var/httpd/www`
6. Which direct Nginx CLI command requests a graceful configuration reload? — A) `nginx -s reload` B) `nginx -reload` C) `nginx --hup` D) `nginx -k reload`
7. Which Squid directive denies all then allows internal? — A) `http_access deny all` then `http_access allow internal` B) Order matters: `allow internal` before `deny all` C) Use `acl` D) Both B and C
8. Which command tests TLS cipher support of a server? — A) `nmap --script ssl-enum-ciphers -p 443 host` B) `openssl ciphers -v` C) `testssl.sh host` D) Both A and C are external tools that work
9. Which directory holds Samba's PDB user database (tdbsam)? — A) `/var/lib/samba/private/` B) `/etc/samba/` C) `/var/cache/samba` D) `/srv/samba/users`
10. Which `samba-tool` subcommand creates a user in AD? — A) `samba-tool user create` B) `samba-tool useradd` C) `net ads user create` D) `kadmin user add`
11. Which command joins a Linux box to AD via SSSD? — A) `realm join` B) `kinit && net join` C) `ad-join` D) `pam-auth-update`
12. Which file lists exported NFS filesystems on the running server (live state)? — A) `/var/lib/nfs/etab` B) `/etc/exports` (config) C) `/proc/fs/nfs` D) Both A is live, B is config
13. Which NFS option provides synchronous writes? — A) `sync` B) `async` C) `fsync` D) `direct`
14. Which command flushes the BIND cache? — A) `rndc flush` B) `rndc reload` C) `rndc clear` D) `rndc restart`
15. Which Postfix parameter restricts who may relay? — A) `smtpd_recipient_restrictions` B) `relay_allowed` C) `smtpd_sender_restrictions` D) `relay_domains`
16. Which Postfix parameter declares your local domains? — A) `mydestination` B) `local_domains` C) `mylocal` D) `mydomains`
17. Which Dovecot directive enforces TLS? — A) `ssl = required` B) `force_tls = yes` C) `tls = mandatory` D) `ssl_enforce = yes`
18. Which DKIM tool generates keys? — A) `opendkim-genkey` B) `dkim-keygen` C) `openssl dkim` D) `dkim-tool`
19. Which command lists PostgreSQL processes via systemd? — A) `systemctl status postgresql` B) `pg_ctl status` C) `psql -c "SELECT"` D) `journalctl -u postgresql`
20. Which `vsftpd` setting jails a user in their home? — A) `chroot_local_user=YES` B) `chroot=yes` C) `jailed=YES` D) `confine=YES`
21. Which command tests an OpenVPN client config without connecting? — A) `openvpn --config client.ovpn --pull-test` B) `openvpn --verb 4 --config client.ovpn` C) `openvpn --test client.ovpn` D) There is no syntactic check; logs reveal issues
22. Which file describes default routes for `ip` commands by name (e.g., `vpn`)? — A) `/etc/iproute2/rt_tables` B) `/etc/routes` C) `/etc/network/tables` D) `/proc/net/routes`
23. Which Apache directive sets per-vhost log file? — A) `CustomLog` B) `ErrorLog` C) Both A and B D) `LogFile`
24. Which Apache MPM uses event-driven scaling? — A) prefork B) worker C) event D) async
25. Which Nginx variable holds the request URI without query string? — A) `$uri` B) `$request_uri` C) `$request` D) `$path`
26. Which directive enables Nginx as a reverse proxy with WebSockets? — A) `proxy_http_version 1.1` plus `Upgrade`/`Connection` headers B) `proxy_websocket on` C) `websocket pass` D) `pass_websockets`
27. Which command checks a Squid configuration? — A) `squid -k parse` B) `squidctl test` C) `squid --config-check` D) `squid -t`
28. Which Postfix queue letter indicates `incoming`? — A) incoming B) maildrop C) active D) deferred
29. Which command lists Dovecot users? — A) `doveadm user '*'` B) `dovecot list users` C) `doveconf -d users` D) `doveadm who`
30. Which Apache directive secures cookies? — A) `Header always edit Set-Cookie ^(.*)$ "$1; Secure; HttpOnly"` B) `Cookie secure` C) `SecureCookies On` D) `mod_cookie secure`
31. Which file holds Bind9 RNDC keys? — A) `/etc/bind/rndc.key` B) `/etc/named.rndc` C) `/var/named/rndc.key` D) Both A and C (distro-dependent)
32. Which SSL certificate field identifies the domain? — A) Subject CN or SubjectAltName B) Issuer CN C) Serial D) Notes
33. Which command verifies a certificate chain locally? — A) `openssl verify -CAfile ca.pem cert.pem` B) `openssl chain verify cert.pem` C) `certutil verify` D) `gpg --verify cert.pem`
34. Which iptables command saves rules persistently on Debian? — A) `iptables-save > /etc/iptables/rules.v4` and let netfilter-persistent restore B) `service iptables save` (RHEL) C) `systemctl save iptables` D) Both A on Debian, B on RHEL
35. Which command configures kerberos tickets on a Linux client? — A) `kinit` B) `klist` C) `kadmin` D) `ktutil`
36. Which subprotocol does NFSv4 use to map UIDs? — A) `nfsidmap` (idmapd) B) `rpc-statd` C) `mountd` D) `nfsmap`
37. Which OpenLDAP overlay enforces password quality? — A) `ppolicy` B) `accesslog` C) `memberof` D) `unique`
38. Which `proftpd` directive limits anonymous uploads? — A) Inside `<Anonymous>` block, `<Limit STOR>` clauses B) `AnonRequirePassword` C) `MaxLoginAttempts` D) `DenyAnonymousWrites`
39. Which DNS record helps identify a server providing a specific service over a specific protocol? — A) SRV B) MX C) SOA D) NS
40. Which file maintains current `apt` package lists? — A) `/var/lib/apt/lists/*` B) `/var/cache/apt/archives/` C) `/etc/apt/sources.list` D) `/var/lib/dpkg/status`
41. Which command in Postfix shows queue per-message size? — A) `mailq` B) `postqueue -p` C) `qshape` (extra) D) Both A and B (same output)
42. Which RDBMS log might be relevant when configuring mail with a virtual user backend? — A) MySQL/MariaDB (slow query and general logs) B) sqlite_log C) ldap-stats D) postdb.log
43. Which Apache directive sets MaxRequestWorkers? — A) `MaxRequestWorkers` B) `MaxClients` (legacy alias) C) Both A and B (B deprecated) D) `WorkerCount`
44. Which command moves an IP/route into another routing table? — A) `ip rule add ...` (decision) then `ip route add ... table NAME` B) `ip route move` C) `ip route swap` D) `ip table mv`
45. Which file lists user-defined cron jobs centrally? — A) `/etc/crontab` (with user field) B) `/var/spool/cron/<user>` (per user) C) Both A (system-wide) and B (per-user) D) `/etc/cron.tab`
46. Which command validates ISC DHCP configuration without starting the daemon? — A) `dhcpd -t -cf /etc/dhcp/dhcpd.conf` B) `dhcpd --reload` C) `dhcpctl check` D) `named-checkconf`
47. Which command parses Squid configuration before reload? — A) `squid -k parse` B) `squid -k check-cache` C) `squidctl validate` D) `squid --dry-run`
48. What does `UPDATE users SET active=false;` do without a `WHERE` clause? — A) Updates every row B) Updates no rows C) Updates the current user D) Syntax error
49. Which command tests an SSH server configuration before restart? — A) `sshd -t` B) `ssh -t` C) `ssh-keygen -t` D) `sshd --check-hosts`
50. Which sysctl enables IPv4 forwarding at runtime? — A) `sysctl -w net.ipv4.ip_forward=1` B) `ip route forwarding on` C) `nft enable forward` D) `route -F`

### Answers

1. **C** 2. **A** 3. **A** 4. **A** 5. **A** 6. **A** 7. **D** 8. **D** 9. **A** 10. **A**
11. **A** 12. **D** 13. **A** 14. **A** 15. **A** 16. **A** 17. **A** 18. **A** 19. **A** 20. **A**
21. **B** 22. **A** 23. **C** 24. **C** 25. **A** 26. **A** 27. **A** 28. **A** 29. **A** 30. **A**
31. **D** 32. **A** 33. **A** 34. **D** 35. **A** 36. **A** 37. **A** 38. **A** 39. **A** 40. **A**
41. **D** 42. **A** 43. **C** 44. **A** 45. **C** 46. **A** 47. **A** 48. **A** 49. **A** 50. **A**

---

## Quick Reference Cheat Sheet

### Essential commands by category

**File / dir basics**
```
ls -lah   stat file   file file   touch file   mkdir -p a/b
cp -a src/ dst/   mv -n   rm -rf   ln -s tgt link   readlink -f
find . -type f -name '*.log' -mtime +7 -delete
```

**Text processing**
```
grep -Ein 'pat' file        sed -i 's/a/b/g' file
awk -F: '{print $1,$3}'     cut -d: -f1,3
sort -u -t: -k3,3n          uniq -c | sort -nr
tr 'a-z' 'A-Z'              tee out.log
diff -u a b | patch -p0
```

**Archives**
```
tar -czf out.tgz dir/         tar -xzf in.tgz -C dest
tar -czf - dir | ssh h 'cat > x.tgz'
gzip/gunzip   bzip2/bunzip2   xz/unxz
rsync -av --delete --link-dest=/PREV src/ dst/
dd if=/dev/sda of=img bs=4M status=progress
```

**Permissions**
```
chmod 750 file       chmod g+s dir       chmod a+t /tmp
chown alice:devs f   setfacl -m u:bob:rwx file
chattr +i file       umask 0027
```

**Users / groups**
```
useradd -m -s /bin/bash -G wheel,docker alice
usermod -aG sudo alice      # NEVER forget -a
passwd alice    chage -l alice    chage -d 0 alice
groupadd devs   gpasswd -a alice devs
visudo
```

**Processes**
```
ps aux   ps -ef --forest   pstree -p
top   htop   pgrep -f pat   kill -HUP PID
nice -n 10 cmd   renice 5 -p PID
nohup cmd &   jobs   fg %1   bg %1   disown %1
```

**Disks / FS**
```
lsblk -f   blkid   findmnt   df -h   du -sh *
mount -o remount,ro /   umount -l /mnt
mkfs.ext4 -L data /dev/sdX   tune2fs -l /dev/sdX
fsck -y /dev/sdX     resize2fs /dev/sdX     xfs_growfs /mnt
```

**LVM**
```
pvcreate /dev/sdX   vgcreate vg /dev/sdX   lvcreate -L 10G -n lv vg
lvextend -L +5G -r /dev/vg/lv     lvremove /dev/vg/lv
lvcreate -s -L 1G -n snap /dev/vg/lv
```

**Networking**
```
ip -br addr    ip route    ip route get 8.8.8.8
ip rule    ip neigh
ss -tulpn      ss -t state established
ping -c4 h     traceroute -n h    mtr -rwc 100 h
dig @8.8.8.8 +short example.com    dig -x 8.8.8.8
host -t MX example.com    getent hosts h
nmap -sV -p 22,80,443 h    tcpdump -i any -nn 'port 53'
```

**Firewall**
```
iptables -L -n -v                    iptables -A INPUT ...
iptables -t nat -A POSTROUTING ...   iptables-save > rules.v4
nft list ruleset                      nft add rule ...
```

**Logging**
```
journalctl -u sshd -f       journalctl -k -b -1
journalctl -p err --since "1h ago"
logger -t myapp 'msg'       tail -F /var/log/syslog
logrotate -d /etc/logrotate.conf
```

**SSH**
```
ssh-keygen -t ed25519 -C "label"     ssh-copy-id user@host
ssh -L 8080:internal:80 host          ssh -R 9000:localhost:9000 host
ssh -D 1080 -N -f host                ssh -J jump host
sshd -t                                systemctl reload sshd
```

**Systemd**
```
systemctl status|start|stop|restart|reload UNIT
systemctl enable|disable|mask|unmask UNIT
systemctl daemon-reload
systemctl list-units --failed       systemctl list-timers
journalctl -u UNIT -f
```

**Package mgmt**
```
apt update && apt upgrade           apt install pkg    apt search kw
dpkg -l   dpkg -L pkg   dpkg -S /path   dpkg -i file.deb
dnf install pkg   dnf provides /path   dnf history undo N
rpm -ivh|-Uvh|-e   rpm -qa|-qi|-ql|-qf
```

### Important file paths

| Path | Use |
|---|---|
| `/etc/passwd`, `/etc/shadow`, `/etc/group`, `/etc/gshadow` | Local accounts |
| `/etc/login.defs`, `/etc/default/useradd` | User defaults |
| `/etc/sudoers`, `/etc/sudoers.d/` | sudo |
| `/etc/ssh/sshd_config`, `~/.ssh/{config,known_hosts,authorized_keys}` | SSH |
| `/etc/pam.d/*`, `/etc/security/*` | PAM |
| `/etc/nsswitch.conf`, `/etc/resolv.conf`, `/etc/hosts` | Name resolution |
| `/etc/network/interfaces`, `/etc/netplan/*.yaml`, `/etc/sysconfig/network-scripts/ifcfg-*` | Network config |
| `/etc/fstab`, `/etc/crypttab`, `/etc/mtab` (or `/proc/mounts`) | FS mounts |
| `/etc/rsyslog.conf`, `/etc/logrotate.conf`, `/etc/systemd/journald.conf` | Logging |
| `/etc/chrony.conf`, `/etc/ntp.conf` | Time |
| `/etc/cron.{d,daily,hourly,weekly,monthly}/`, `/var/spool/cron/` | Cron |
| `/etc/systemd/system/`, `/lib/systemd/system/` | Unit files |
| `/etc/default/grub`, `/boot/grub/grub.cfg` | GRUB |
| `/etc/modprobe.d/`, `/etc/modules-load.d/`, `/lib/modules/<ver>/` | Modules |
| `/etc/iptables/rules.v4`, `/etc/nftables.conf` | Firewall persistence |
| `/etc/named.conf` / `/etc/bind/named.conf.options`, `/var/named/`, `/etc/bind/zones/` | BIND |
| `/etc/apache2/`, `/etc/httpd/`, `/etc/nginx/` | Web servers |
| `/etc/samba/smb.conf` | Samba |
| `/etc/postfix/main.cf`, `/etc/postfix/master.cf`, `/etc/aliases`, `/etc/dovecot/` | Mail |

### Common exam traps and the correct answer

| Trap | Correct |
|---|---|
| `usermod -G grp user` | Use `-aG` to add; without `-a` you replace |
| Editing `grub.cfg` directly | Edit `/etc/default/grub` + scripts, then `update-grub` |
| `find -mtime +7` | Strictly older than 7 days |
| `rsync src dst` vs `rsync src/ dst` | Slash on src = contents only |
| XFS shrink | Not supported — only grow |
| `chcon` for SELinux persistence | Wiped on relabel — use `semanage fcontext` |
| `-i` to sed without backup | Works on GNU, breaks on BSD without `''` |
| Forgetting `daemon-reload` after editing unit | systemd will use old version |
| Bonding mode 4 (LACP) | Requires switch LACP config |
| `useradd` without `-m` on RHEL | Home directory not created |
| `tar -j` vs `-J` | `-j` = bzip2, `-J` = xz |
| SUID on script | Ignored by kernel for safety |
| `nfs-server` v4 needs no `rpcbind` | Correct on most modern systems |
| `kill -9` not catchable | Use SIGTERM first |
| `read -r` vs `read` | Always `-r` to preserve backslashes |
| `cron` PATH minimal | Set PATH= at top of crontab |
| TCP wrappers and OpenSSH ≥ 6.7 | Removed; iptables/sshd_config instead |

### Regex quick reference

| Pattern | BRE | ERE | PCRE adds |
|---|---|---|---|
| `.` any char | ✓ | ✓ | ✓ |
| `*` 0+ | ✓ | ✓ | ✓ |
| `+` 1+ | `\+` | `+` | `+` |
| `?` 0 or 1 | `\?` | `?` | `?` |
| `\|` alt | `\|` (GNU) | `\|` | `\|` |
| `(...)` group | `\(...\)` | `(...)` | `(...)` |
| `{n,m}` | `\{n,m\}` | `{n,m}` | `{n,m}` |
| `^` `$` anchors | ✓ | ✓ | ✓ |
| `\d` `\w` `\s` | — | — | ✓ |
| lookaround | — | — | `(?=...)`, `(?!...)`, `(?<=...)`, `(?<!...)` |
| non-greedy | — | — | `*?` `+?` `??` |

### Permission bits reference

| Octal | Symbolic | Type |
|---|---|---|
| 4000 | `u+s` | SUID |
| 2000 | `g+s` | SGID |
| 1000 | `+t` | Sticky |
| 0700 | `u=rwx` | Owner rwx |
| 0070 | `g=rwx` | Group rwx |
| 0007 | `o=rwx` | Other rwx |
| 0644 | `u=rw,g=r,o=r` | Common file |
| 0755 | `u=rwx,g=rx,o=rx` | Common dir / exe |
| 0600 | `u=rw` | Private file |
| 0700 | `u=rwx` | Private dir |
| 4755 | `u=rwxs,go=rx` | SUID exec |
| 1777 | `a=rwx,+t` | `/tmp` |
| 2755 | `u=rwx,g=rxs,o=rx` | SGID dir |

### Port numbers reference

| Port | Proto | Service |
|---|---|---|
| 20/21 | TCP | FTP data / control |
| 22 | TCP | SSH / SFTP |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | UDP/TCP | DNS |
| 67/68 | UDP | DHCP server / client |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 111 | UDP/TCP | rpcbind |
| 119 | TCP | NNTP |
| 123 | UDP | NTP |
| 137/138/139 | UDP/UDP/TCP | NetBIOS name/dgm/session |
| 143 | TCP | IMAP |
| 161/162 | UDP | SNMP / trap |
| 179 | TCP | BGP |
| 389 | TCP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | SMB direct |
| 465 | TCP | SMTPS |
| 514 | UDP | syslog |
| 515 | TCP | LPD |
| 587 | TCP | SMTP submission |
| 636 | TCP | LDAPS |
| 873 | TCP | rsync |
| 989/990 | TCP | FTPS |
| 993 | TCP | IMAPS |
| 995 | TCP | POP3S |
| 1080 | TCP | SOCKS |
| 1194 | UDP | OpenVPN |
| 1433 | TCP | MSSQL |
| 1521 | TCP | Oracle DB |
| 1812/1813 | UDP | RADIUS auth/acct |
| 2049 | TCP | NFS |
| 2375/2376 | TCP | Docker daemon / TLS |
| 3128 | TCP | Squid |
| 3306 | TCP | MySQL |
| 3389 | TCP | RDP |
| 5432 | TCP | PostgreSQL |
| 5601 | TCP | Kibana |
| 5900 | TCP | VNC |
| 5984 | TCP | CouchDB |
| 6379 | TCP | Redis |
| 6443 | TCP | Kubernetes API |
| 6667 | TCP | IRC |
| 8080/8443 | TCP | HTTP alt / HTTPS alt |
| 9090 | TCP | Prometheus / Cockpit |
| 9200 | TCP | Elasticsearch |
| 11211 | TCP/UDP | memcached |
| 27017 | TCP | MongoDB |

### Signals reference

| # | Name | Default action |
|---|---|---|
| 1 | HUP | terminate (often: reload config) |
| 2 | INT | terminate (Ctrl-C) |
| 3 | QUIT | terminate + core dump |
| 9 | KILL | terminate (uncatchable) |
| 15 | TERM | terminate (default) |
| 18 (Linux) | CONT | continue |
| 19 (Linux) | STOP | pause (uncatchable) |
| 20 (Linux) | TSTP | Ctrl-Z |

### Useful one-liners

```bash
# Top 10 directories by size
du -h --max-depth=1 / 2>/dev/null | sort -h | tail

# 5 largest files under .
find . -type f -printf '%s %p\n' | sort -nr | head -5

# Open ports + processes
ss -tulpn

# Watch CPU usage of a single process
top -p $(pgrep -d, -f mycmd)

# Show network interfaces with one-liner IPs
ip -br addr

# Get IP of a hostname using nsswitch (not just DNS)
getent hosts host.example.com

# Rotate logs immediately for testing
logrotate -f /etc/logrotate.d/myapp

# Quickly serve current dir over HTTP
python3 -m http.server 8000

# Pipe one command's output to several
cmd | tee >(grep ERROR > errs) >(wc -l > lines) >/dev/null

# Back up a LUKS header (store the result encrypted and offline)
cryptsetup luksHeaderBackup /dev/sdb1 --header-backup-file luks.hdr

# Stream a tar over SSH without writing to disk
tar -cz /data | ssh user@host 'tar -xz -C /restore'
```

---

## Closing Notes

This handbook covers the breadth of LPIC-1, LPIC-2, and LPIC-3. To pass:

1. **Hands-on practice.** Spin up VMs (libvirt, VirtualBox) and *do* the exercises.
2. **Read `man` pages** for every command in this handbook at least once. The exam tests flags you may forget — the muscle memory of opening `man tar` matters.
3. **Drill the mock exams.** Re-attempt them until you score ≥ 90% without looking.
4. **Memorize port and signal numbers**, the SOA fields, the rsyslog priority order, and the systemd target ↔ runlevel mapping.
5. **Build at least one of each lab**: a BIND master+slave, an Apache+Nginx pair, a Postfix+Dovecot mailbox, an LVM+RAID stack, a Pacemaker cluster, a KVM guest, a Docker compose stack.

Good luck. Once you can teach a chapter to someone else, you've passed it.

---

*End of handbook.*
