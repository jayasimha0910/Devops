# 🐧 Linux Directory Structure – DevOps Cheat Sheet

Linux follows a hierarchical filesystem where everything starts from the **root directory (`/`)**. Here's a breakdown of the most important directories and their purposes.

---

## 📂 Top-Level Linux Directories

| Directory | Description |
|-----------|-------------|
| `/`       | The **root directory** – everything starts here. |
| `/bin`    | Essential **user binaries** like `ls`, `cp`, `mv`. Needed during boot and single-user mode. |
| `/sbin`   | System binaries for **administration** tasks (`reboot`, `ifconfig`). Usually run by root. |
| `/etc`    | **System-wide configuration files**, e.g., `nginx.conf`, `ssh/sshd_config`. |
| `/home`   | Personal directories for users, e.g., `/home/jayasimha`. |
| `/root`   | Home directory of the `root` (admin) user. |
| `/var`    | Variable files such as **logs**, spools, and caches. |
| `/tmp`    | **Temporary files** that are deleted on reboot. |
| `/usr`    | User-installed **software and libraries**. Includes subdirs: `/usr/bin`, `/usr/lib`. |
| `/opt`    | **Optional or third-party** software, e.g., `/opt/terraform`. |
| `/lib`    | Shared **libraries** needed for binaries in `/bin` and `/sbin`. |
| `/dev`    | Special device files (e.g., `/dev/sda`, `/dev/tty`). |
| `/proc`   | Virtual filesystem with **runtime system information** (e.g., `/proc/cpuinfo`). |
| `/sys`    | Exposes **kernel and device information** to user space. |
| `/mnt`    | Temporary **mount point** for external file systems. |
| `/media`  | Mount point for **removable media** like USB drives. |
| `/boot`   | **Boot loader** and kernel files (`vmlinuz`, `initrd.img`). |

---

## 📌 Notes for DevOps

- Config files: `/etc`
- Logs: `/var/log`
- Temporary build/test artifacts: `/tmp`
- CI tools and agents: often installed in `/opt` or `/usr/local/bin`
- Troubleshooting: check `/proc`, `/var/log`, and system service configs under `/etc`

---

## 🧠 Quick Tree Overview
