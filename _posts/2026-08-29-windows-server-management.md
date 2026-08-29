---
layout: post
title: Windows Server Management
excerpt_separator:  <!--more-->
---

Over the years working in IT Operations and System Administration, I've picked up a solid set of Windows Server management skills, from day-to-day administration to troubleshooting production issues. More details to come.

<!--more-->

### Services Management

Windows services can be managed through the Services console (`services.msc`) 

![run](https://www.coretechnologies.com/blog/images/run-services-413x213.png)

![services.msc](https://www.coretechnologies.com/blog/images/services-main-window-1052x573.png)

Where you can start/stop/restart a service

![manage](https://www.coretechnologies.com/blog/images/services-right-click-menu-532x275.png)

Or PowerShell.

| Command | Description |
| --- | --- |
| `Get-Service` | List services and their current status |
| `Get-Service -Name <svc>` | Show the status of a specific service |
| `Start-Service -Name <svc>` | Start a service |
| `Stop-Service -Name <svc>` | Stop a service |
| `Restart-Service -Name <svc>` | Restart a service |
| `Set-Service -Name <svc> -StartupType Automatic` | Set a service to start automatically on boot |

### Control Panel / Programs

The Control Panel's "Programs and Features" applet is useful for viewing installed software and installed updates.

![Programs and Features](https://www.top-password.com/blog/wp-content/uploads/2018/09/programs-and-features-control-panel.png)

- **Programs and Features** - lists all installed software on the server, and allows you to uninstall, repair, or change an installed program.

![Program](https://www.ghacks.net/wp-content/uploads/2020/09/windows-programs-features-control-panel.webp)

- **View installed updates** - accessible from the "Programs and Features" sidebar, this lists all applied Windows updates and hotfixes, along with their install date, which is useful when troubleshooting whether a recent update introduced an issue.

![Installed updates](https://www.ghacks.net/wp-content/uploads/2014/08/uninstall-windows-update.webp)

These can also be viewed from PowerShell.

| Command | Description |
| --- | --- |
| `Get-WmiObject -Class Win32_Product` | List installed software |
| `Get-HotFix` | List installed Windows updates and hotfixes |

### Windows Registry Editor

The Registry Editor (`regedit`) is a hierarchical database that stores low-level system and application settings. It's a powerful tool, but changes take effect immediately and mistakes can make Windows unstable, so it's best to back up a key before editing it.

![regedit](https://www.top-password.com/blog/wp-content/uploads/2016/08/regedit-via-run.png)

![registry](https://www.bleepstatic.com/images/news/tutorials/windows/r/how-to-use-registry-editor/windows-registry-editor.jpg)

The registry is organized into root keys (hives), the most commonly used being:

| Hive | Description |
| --- | --- |
| `HKEY_LOCAL_MACHINE (HKLM)` | System-wide settings that apply to all users |
| `HKEY_CURRENT_USER (HKCU)` | Settings specific to the currently logged-in user |
| `HKEY_CLASSES_ROOT (HKCR)` | File association and COM object registration data |
| `HKEY_USERS (HKU)` | Settings for all loaded user profiles on the system |
| `HKEY_CURRENT_CONFIG (HKCC)` | Information about the current hardware profile |

Registry keys can also be queried and modified from PowerShell.

| Command | Description |
| --- | --- |
| `Get-ItemProperty -Path <key>` | Read the values of a registry key |
| `Set-ItemProperty -Path <key> -Name <name> -Value <value>` | Set a registry value |
| `New-Item -Path <key>` | Create a new registry key |

### Windows Task Manager

Task Manager (`taskmgr`) is the go-to tool for a quick view of what's running on a server and how it's affecting performance.

![Task Manager](https://www.top-password.com/blog/wp-content/uploads/2019/09/task-manager-details.png)

Its tabs cover the areas most commonly checked when troubleshooting:

| Tab | Description |
| --- | --- |
| Processes | Shows running applications and background processes along with their resource usage |
| Performance | Shows real-time graphs for CPU, memory, disk, and network usage |
| Users | Shows resource usage broken down by logged-in user session |
| Details | Shows per-process details such as PID, and allows setting process priority or ending a task |
| Services | Shows services and their running state, with the ability to start/stop them |

Task Manager can also be launched and queried from PowerShell.

| Command | Description |
| --- | --- |
| `taskmgr` | Launch Task Manager |
| `Get-Process` | List running processes and their resource usage |
| `Stop-Process -Id <PID>` | Terminate a process by its process ID |

