# Lesson 03 — Operating Systems Fundamentals

- **Module:** 1 — IT Infrastructure Fundamentals
- **Status:** IN PROGRESS
- **Knowledge check:** 5/5
- **Windows PowerShell lab:** completed
- **Concept review:** 3/3
- **Linux/WSL setup:** Ubuntu 26.04.1 LTS installed and verified on WSL 2
- **Linux discovery lab:** completed
- **Linux permissions review:** first mini-exam 8/8; a new follow-up mini-exam is awaiting answers
- **Final practical exam:** pending

## What is an Operating System?

An **Operating System (OS)** is core system software that manages hardware resources and provides the environment in which applications run.

Main responsibilities:
1. **Process Management** — managing running programs.
2. **Memory Management** — allocating and managing RAM.
3. **File System Management** — organizing files and directories.
4. **Device Management** — managing hardware devices and drivers.
5. **User & Permission Management** — managing identities and access rights.

## Process, PID, and Service

- **Process:** an instance of a program that is currently executing.
- **PID (Process ID):** the identifier assigned to a process.
- **Service:** a background component that provides a system or application function.

A service may run without a visible application window. Process and Service are related concepts but are not interchangeable.

## Windows and Linux

- Windows is common on user endpoints and is also used for server workloads, including Active Directory and Group Policy.
- Linux is a family of operating systems widely used for servers, cloud platforms, containers, and infrastructure tooling.
- Their roles overlap; neither operating system is limited to one type of workload.

## Security considerations

- Malware can target both Windows and Linux.
- **Privilege Escalation:** an attacker attempts to gain permissions beyond those initially granted.
- **Unauthorized Access:** access by an identity that lacks permission.
- **Misconfiguration:** insecure or incorrect system settings.
- **Unpatched Vulnerability:** a known security weakness that has not been fixed.

Investigate unfamiliar processes using trustworthy context; do not assume an unfamiliar name automatically means malware. A service in Stopped state is not automatically a fault.

## Knowledge check and review

- Lesson knowledge check: **5/5**.
- Follow-up concept review:
  1. Unknown process should be investigated before classifying it as malware.
  2. A Stopped service is not necessarily a problem; it may be demand-started.
  3. A process is an executing program instance; a service is a background component/function.
- Review result: **3/3 correct**.

## Windows PowerShell discovery lab

Commands used:

```powershell
Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion, OsBuildNumber

Get-Process | Select-Object -First 10 ProcessName, Id, CPU

Get-Service | Select-Object -First 10 Name, Status
```

Observations:
- `Get-ComputerInfo` returned WindowsProductName = Windows 10 Pro, WindowsVersion = 2009, OsBuildNumber = 26300.
- The separate `winver` dialog reported Windows version 26H2, OS build 26300.9974. Use the `winver` dialog as the current version/build reference; the product-name field differed and has not been investigated further.
- `Get-Process` listed Windows and ASUS processes. The `CPU` field is cumulative processor time in seconds, not a live percentage.
- `Get-Service` displayed services in both Running and Stopped states. Stopped does not automatically mean broken.
- No changes were made to processes or services.

## WSL and Ubuntu setup — completed

- Installed Ubuntu using `wsl --install -d Ubuntu`.
- `wsl --list --verbose` confirmed Ubuntu is using WSL 2. A `Stopped` state when the distribution is not active is normal.
- Completed first-run provisioning and created the Linux user `igs`.
- `whoami` returned `igs`; `pwd` returned `/home/igs`.
- `uname -a` confirmed the Microsoft WSL2 Linux kernel.
- `cat /etc/os-release` identified Ubuntu 26.04.1 LTS (`resolute`).
- The Linux password is intentionally not recorded in this repository.

## Linux discovery and permissions lab — completed

Commands practiced:

```bash
whoami
pwd
uname -a
id
cat /etc/os-release
ls -la
df -h
free -h
ps aux | head
groups
ls -ld ~
stat -c '%A %a %U:%G %n' ~/.bashrc ~/.profile
```

Observations and concepts:
- The account `igs` is a regular non-root user and belongs to the `sudo` group.
- Ubuntu home-directory listing included hidden dotfiles (names beginning with a dot).
- `df -h` showed the WSL virtual root filesystem and Windows C: mounted at `/mnt/c`. The virtual disk size is not the physical SSD capacity.
- `free -h` reports memory visible to WSL, not necessarily all physical RAM in Windows.
- Process listing showed expected WSL/system processes; unfamiliar process names should be investigated, not automatically labelled malware.
- `ls -ld ~` showed `drwxr-x---` (750): owner has rwx, group has r-x, others have no permissions.
- `.bashrc` and `.profile` both showed `644` (`-rw-r--r--`): owner read/write, group and others read.
- For a regular file, `x` means execute; for a directory, `x` means search/traverse. Directory `r` and `w` govern listing and modifying directory entries, subject to other access controls.
- Linux permissions use `r=4`, `w=2`, `x=1`; for example, `750` means `rwxr-x---` and `644` means `rw-r--r--`.

Previous Linux Files & Permissions mini-exam: **8/8 correct**. A new quiz with different questions has been presented; its answers are not yet submitted and are not scored.

## Next steps

1. Complete the newly presented Linux Files & Permissions quiz and review the result.
2. Practice `mkdir`, creating a test file, reading permissions with `ls -l`, and changing permissions with `chmod` in a dedicated directory under the user's home folder.
3. Complete the Lesson 03 final practical exam.

Do not mark Lesson 03 complete until the Linux lab and final assessment are passed.
