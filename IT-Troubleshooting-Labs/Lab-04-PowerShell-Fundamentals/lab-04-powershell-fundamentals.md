# Lab 04: PowerShell Fundamentals for IT Support

## Objective
Practice basic PowerShell commands used to inspect a system, list files, and test network connectivity.

## Lab Environment
- Computer: Mac mini (Apple Silicon)
- Operating system: macOS
- Shell: PowerShell 7.6.6
- Editor: Visual Studio Code

**Note:** These exercises were performed on macOS using PowerShell. Some Windows administration commands require a Windows environment.

## Commands Practiced

### 1. Check PowerShell and Operating System Information

```powershell
$PSVersionTable.OS
$PSVersionTable.PSVersion
```

**Purpose:** Identify the operating system and PowerShell version.

**Result:** Commands executed successfully and confirmed a macOS environment running PowerShell 7.6.6.

### 2. Display the Current Directory

```powershell
Get-Location
```

**Purpose:** Display the current working directory.

**IT Support Use:** Confirm the location where commands are being executed before troubleshooting files or running scripts.

**Result:** Command executed successfully.

### 3. List Files and Folders

```powershell
Get-ChildItem
Get-ChildItem -Filter "*.md"
```

**Purpose:** List directory contents and filter for Markdown files.

**IT Support Use:** Locate configuration files, documentation, logs, and other files during troubleshooting.

**Result:** Commands executed successfully. The Markdown filter displayed README.md and CONTRIBUTING.md.

### 4. Test Network Connectivity

```powershell
Test-Connection google.com -Count 4
```

**Purpose:** Send four connectivity tests to a hostname.

**IT Support Use:** Help determine whether a destination can be reached and inspect response times.

**Result:** Command completed without errors.

## Troubleshooting Lessons
- Verify the current directory before creating files or running commands.
- Use PowerShell cmdlets to inspect files and test connectivity.
- Distinguish PowerShell commands from operating-system-specific administration tools.
- A successful connectivity test confirms reachability to the tested destination at that time; it does not prove that all network services are functioning.

## Next Steps
- Practice Windows-specific PowerShell commands in a Windows environment.
- Explore processes, services, event logs, and network configuration.
- Continue documenting hands-on IT support exercises in GitHub.

## Skills Demonstrated
PowerShell fundamentals, file-system navigation, basic network connectivity testing, command-line troubleshooting, and technical documentation.
