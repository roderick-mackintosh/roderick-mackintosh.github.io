---
layout: post
title: Linux Skills
excerpt_separator:  <!--more-->
---

Over the years working in IT Operations and System Administration, I've built up a set of Linux skills that come in handy day to day. Here's a rundown of the areas I rely on most.

<!--more-->


### File & Directory Commands

| Command | Description |
| --- | --- |
| `ls` | List files and directories |
| `cd <dir>` | Change directory |
| `pwd` | Print working directory |
| `rm <file>` | Remove a file [DANGEROUS] |
| `rm -rf <dir>` | Remove a directory and its contents, forcefully [DANGEROUS] |
| `cp <src> <dest>` | Copy a file or directory |
| `mv <src> <dest>` | Move or rename a file or directory |
| `cat <file>` | Print file contents to the terminal |
| `less <file>` | View file contents page by page |
| `head <file>` | Show the first lines of a file |
| `tail <file>` | Show the last lines of a file |
| `tailf -f <file>` | Follow a file's contents as it grows |

The command `rm` is dangerous because it deletes the file or directory and once deleted, it's gone gone.

### System & Process Commands

| Command | Description |
| --- | --- |
| `hostname` | Show the system's hostname |
| `uptime` | Show how long the system has been running and load averages |
| `df -h` | Show disk space usage in human-readable form |
| `du -hs <dir>` | Show total size of a directory in human-readable form |
| `free -h` | Show memory usage in human-readable form |
| `top` | Display running processes and resource usage in real time |
| `ps aux` | List all running processes |
| `kill <PID>` | Terminate a process by its process ID |
| `kill -9 <PID>` | Forcefully terminate a process by its process ID |
| `history` | Show previously run commands |

### User & Permission Commands

| Command | Description |
| --- | --- |
| `whoami` | Show the current logged-in user |
| `passwd` | Change a user's password |
| `chmod <perm> <file>` | Change a file or directory's permissions |
| `chown <user>:<group> <file>` | Change a file or directory's owner and group |
| `sudo` | Run a single command with elevated privileges |
| `sudo <cmd>` | Run the specified command with elevated privileges |
| `sudo -i` | Start an interactive root shell |
| `su - <user>` | Switch to another user, loading their environment |

### Search Commands

| Command | Description |
| --- | --- |
| `grep "text" <file>` | Search for text within a file |
| `find <path> -name <file>` | Search for files by name under a path |

### Network Commands

| Command | Description |
| --- | --- |
| `ip addr` | Show network interfaces and IP addresses |
| `ping` | Test connectivity to a host |
| `nslookup` | Query DNS records for a domain |
| `telnet <IP> <Port>` | Test connectivity to a specific host and port |

### Package Management Commands (RedHat/CentOS)

| Command | Description |
| --- | --- |
| `sudo dnf search <package>` | Search for a package |
| `sudo dnf update` | Update installed packages |
| `sudo dnf install <package>` | Install a package |

### Log & Monitoring Commands (RedHat/CentOS)

| Command | Description |
| --- | --- |
| `less /var/log/messages` | View the system log file |
| `journalctl -xe` | View recent system logs with extra detail |
| `journalctl -u <service>` | View logs for a specific service |

### Service Management Command

| Command | Description |
| --- | --- |
| `sudo systemctl start <svc>` | Start a service |
| `sudo systemctl stop <svc>` | Stop a service |
| `sudo systemctl status <svc>` | Show a service's current status |
| `sudo systemctl enable <svc>` | Enable a service to start on boot |
| `sudo systemctl disable <svc>` | Disable a service from starting on boot |

### Understanding DNS Resolution on Linux

DNS resolution on Linux typically starts with `/etc/resolv.conf`, which lists the nameservers the system queries.  There is a bit more to it but at a high level, that's the main part.  
Tools like `nslookup` is useful for querying DNS

### Understanding Storage Management on Linux

Linux storage is often managed with LVM (Logical Volume Manager), which adds a flexible layer on top of raw disks. A physical volume (PV) is a disk or partition initialized for use by LVM, one or more physical volumes are combined into a volume group (VG), and space from that volume group is then carved out into logical volumes (LVs) that behave like regular partitions but can be resized more easily. Once a logical volume exists, it needs to be formatted with a file system before it can store data - common choices include XFS, which is the default on many RedHat/CentOS systems and handles large files well, and ext4, a widely used and reliable general-purpose file system.

![LVM diagram](https://miro.medium.com/v2/resize:fit:1236/format:webp/1*aVt2jO1p5vzYBEQGnGxEaw.png)

These skills have evolved through years of solving real problems in production environments, and I'll continue sharing specific examples and solutions as I encounter them.
