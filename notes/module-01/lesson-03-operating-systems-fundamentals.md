# Lesson 03 — Operating Systems Fundamentals

- **Module:** 1 — IT Infrastructure Fundamentals
- **Status:** IN PROGRESS
- **Knowledge check:** 5/5
- **Windows PowerShell lab:** completed
- **Concept review:** 3/3
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

## WSL and Ubuntu setup — pending reboot

Initial check:
```powershell
wsl --status
```
Reported that WSL was not installed.

Installation command:
```powershell
wsl --install -d Ubuntu
```

Observed installation output:
- WSL package version 3.0.5 installed successfully.
- Windows optional feature `VirtualMachinePlatform` was enabled successfully through DISM.
- The system requested a restart for changes to take effect.
- Restart has not yet been completed at the time of this note.
- Ubuntu distribution installation/first launch and WSL 2 status are **not yet verified**.

After restarting, run:

```powershell
wsl --status
wsl --list --verbose
```

If Ubuntu first-run setup appears, create a Linux username and password. Linux password input may not display characters; this is normal. Verify the distribution version is WSL 2 before proceeding.

## Next steps

1. Restart Windows.
2. Verify WSL status and installed distributions.
3. Complete Ubuntu first-run setup if prompted.
4. Learn and practice `pwd`, `ls`, `whoami`, `uname -a`, and `cd`.
5. Complete remaining Linux lab tasks and the Lesson 03 final practical exam.

Do not mark Lesson 03 complete until its Linux lab and final assessment are passed.
