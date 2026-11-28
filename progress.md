# Learning Progress

_Last updated: 2026-11-28_

## Learning profile

- Starting level: Beginner
- Target direction: Infrastructure Security Engineer, progressing toward DevSecOps Engineer
- Study time: approximately 8–10 hours per week
- Technical English: A1; build vocabulary and reading confidence gradually
- Learning style: step-by-step explanations, practical labs, knowledge checks, and practical exams
- Rule: do not move to the next lesson until the current lesson is understood and passed.

## Current environment

- Laptop: ASUS VivoBook X512UA
- OS: Windows 11 Pro, 64-bit; winver reports version 26H2, OS build 26300.9974
- CPU: Intel Core i5-8250U
- RAM: 8 GB
- Storage: 256 GB SSD
- Virtualization: firmware virtualization support and SLAT confirmed
- WSL installation: WSL package 3.0.5 installed; VirtualMachinePlatform enabled successfully. A system restart is pending. Ubuntu installation/first launch and WSL 2 verification are not yet confirmed.

### Lab constraints

- Begin with Windows built-in tools and lightweight exercises.
- Use WSL/Ubuntu for introductory Linux labs after reboot and verification.
- Run one lightweight virtual machine at a time where practical.
- Keep enough free SSD space for the OS and lab files.
- Consider a RAM upgrade only after checking the exact installed memory modules and device compatibility.
- Defer resource-intensive labs (for example, multi-node Kubernetes or a full SIEM stack) until suitable hardware or cloud labs are available.

## Completed learning

### Module 1 — IT Infrastructure Fundamentals

#### Lesson 01 — What Is IT Infrastructure?

- **Status:** PASSED
- **Theory assessment:** 10/10 (100%)
- **Practical assessment:** 5/5

Topics covered:
- IT infrastructure and its components
- Servers, workstations, endpoints
- Network infrastructure, operating systems, cloud infrastructure
- Security infrastructure and layered security
- Firewall, router, switch, authentication, authorization
- SIEM and security monitoring
- Basic Windows discovery commands: `hostname`, `systeminfo`, `ipconfig`
- IPv4 address, subnet mask, default gateway, and /24 subnet basics
- Same-subnet versus different-subnet communication

Skills demonstrated:
- Explain the role of common infrastructure components.
- Identify a laptop's IPv4 address and default gateway from command output.
- Explain why two /24 addresses may be in the same subnet.
- Distinguish authentication from authorization.
- Explain the purpose of SIEM.
- Propose basic infrastructure hardening measures.

Topics to reinforce over time:
- ARP and MAC addresses
- Network segmentation
- Vulnerability management
- Backup versus snapshot, including restore testing
- Modern password guidance, MFA, and account protection

#### Lesson 02 — Hardware Fundamentals

- **Status:** PASSED
- **Knowledge checks:** 3/3 on CPU/RAM/storage; 5/5 on motherboard/NIC/ECC/RAID/Secure Boot.
- **Hands-on lab:** completed — motherboard, network adapters, and physical storage inspected with PowerShell.
- **Final practical exam:** 5/5.

Sanitized observations:
- Motherboard: ASUSTeK COMPUTER INC., X512UA, version 1.0.
- Physical Wi-Fi NIC: Intel(R) Dual Band Wireless-AC 8265; Up.
- Virtual interface: Happ Tunnel; Up. Reported 100 Gbps is an interface-reported link speed, not proof of actual internet throughput.
- Bluetooth PAN: disconnected.
- Storage: SanDisk SD9SN8W256G1102, SSD, 256,060,514,304 bytes (about 256 GB decimal / 238.5 GiB), Windows HealthStatus Healthy.

Topics covered: CPU, cores/threads, RAM and volatile memory, HDD vs SSD, motherboard, NIC, IP vs MAC, physical vs virtual interfaces, ECC RAM, RAID, redundant power, remote management, physical security, BitLocker, Secure Boot, TPM, and firmware security.

#### Lesson 03 — Operating Systems Fundamentals

- **Status:** IN PROGRESS
- **Knowledge check:** 5/5.
- **Windows PowerShell lab:** completed.
- **Concept review:** 3/3 correct.
- **Linux/WSL lab:** setup in progress; restart pending.

Topics covered so far:
- Operating System (OS) and its role between hardware, applications, and users.
- Process Management, Memory Management, File System Management, Device Management, User & Permission Management.
- Process, Process ID (PID), and Service distinctions.
- Windows vs Linux: common uses and overlapping roles.
- Basic security risks: malware, privilege escalation, unauthorized access, misconfiguration, and unpatched vulnerabilities.
- PowerShell discovery: `Get-ComputerInfo`, `Get-Process`, and `Get-Service`.

Lab observations:
- `Get-ComputerInfo` returned WindowsProductName = Windows 10 Pro, WindowsVersion = 2009, OsBuildNumber = 26300. The separate `winver` dialog reported Windows version 26H2, OS build 26300.9974. Treat the `winver` result as the current version/build reference; the differing product-name field needs no remediation at this stage.
- `Get-Process` listed Windows/ASUS processes. The CPU column is cumulative processor time in seconds, not a live CPU percentage.
- `Get-Service` showed both Running and Stopped services. A Stopped service is not automatically a fault; some services start only when needed.
- Learner correctly explained that an unfamiliar process must be investigated before classifying it as malware, that a stopped service is not necessarily a problem, and that a process differs from a service.

WSL setup:
- Ran `wsl --status`: WSL was not installed at that time.
- Ran `wsl --install -d Ubuntu`.
- WSL package 3.0.5 installation completed successfully.
- Windows feature VirtualMachinePlatform was enabled successfully.
- Windows requested a restart for changes to take effect.
- **Next action after restart:** run `wsl --status` and `wsl --list --verbose`; complete Ubuntu first-launch setup if prompted; verify the distribution is using WSL 2. Do not mark Ubuntu as installed/ready until verified.

## Roadmap

| Stage | Focus | Status |
|---|---|---|
| 1 | IT Infrastructure Fundamentals | In progress — Lessons 01 and 02 passed; Lesson 03 in progress |
| 2 | System & Infrastructure Administration: Linux, Windows Server, AD, DNS, firewalls | Not started |
| 3 | Cybersecurity: fundamentals, hardening, IAM, vulnerabilities, SIEM | Not started |
| 4 | Programming & Automation: Python, Bash, PowerShell, Git/GitHub | Not started |
| 5 | Cloud & DevOps: AWS/Azure, Docker, CI/CD, Terraform, Ansible | Not started |
| 6 | DevSecOps: SAST, DAST, SCA, container/Kubernetes security, secrets management | Not started |
| 7 | Enterprise Security & Career Preparation | Not started |

## Next action

Resume **Module 1 — Lesson 03: Operating Systems Fundamentals** after restarting the computer:
1. Verify WSL with `wsl --status`.
2. Verify distributions with `wsl --list --verbose`.
3. Finish Ubuntu first-run setup if required.
4. Verify WSL 2, then begin basic Linux terminal commands: `pwd`, `ls`, `whoami`, `uname -a`, and `cd`.
5. Continue the lesson's Linux lab and final assessment. Do not advance to Lesson 04 until Lesson 03 is passed.

## Weekly study rhythm

A sustainable target is 8–10 hours per week:
- Concept learning and notes
- Hands-on lab practice
- Review and technical English vocabulary
- Short knowledge checks

## Portfolio plan

- [ ] IT Infrastructure Documentation
- [ ] Linux Security Basics
- [ ] Server Hardening
- [ ] Security Automation with Python
- [ ] Secure CI/CD Pipeline

## Continuation instructions

When continuing this journey, read this file and the latest lesson notes first. Resume at **Module 1, Lesson 03 — Operating Systems Fundamentals**, specifically WSL/Ubuntu verification after the pending restart. Keep the beginner-friendly pace, explain technical English terms in Russian, assign practical exercises, and assess understanding before advancing.

Do not claim professional seniority based on course completion alone; professional level also requires sustained real-world engineering experience.
