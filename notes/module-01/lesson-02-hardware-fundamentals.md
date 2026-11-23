# Lesson 02 — Hardware Fundamentals

- **Module:** 1 — IT Infrastructure Fundamentals
- **Status:** PASSED
- **Final practical exam:** PASSED — 5/5

## Core components
- **CPU (Central Processing Unit):** executes program instructions and performs calculations. Terms: core, thread, clock speed, GHz.
- **RAM (Random Access Memory):** temporary working memory; volatile, so contents are normally lost when power is removed.
- **HDD (Hard Disk Drive):** magnetic storage with moving parts.
- **SSD (Solid State Drive):** flash-based storage with no moving mechanical parts.
- **Motherboard:** connects components and enables communication.
- **NIC (Network Interface Card):** provides network connectivity, such as Ethernet or Wi-Fi.

## Hardware security
- High CPU usage may be normal or malicious; investigate processes and context first.
- Sensitive information may temporarily reside in RAM.
- BitLocker/disk encryption helps protect data at rest.
- Secure Boot helps verify trusted boot components.
- TPM supports hardware-backed protection for cryptographic material and platform integrity.
- Protect and update firmware through trusted channels.
- Control physical access to endpoints and servers.
- RAID does not replace independent backups.

## Server hardware
- **ECC RAM:** detects and corrects certain memory errors.
- **RAID:** combines drives for redundancy and/or performance, depending on configuration.
- **Redundant Power Supply:** supports operation if one power supply fails.
- **Multiple NICs:** provide multiple network interfaces.
- **Remote Management:** supports remote administration of server hardware.

## PowerShell hardware discovery lab

```powershell
Get-CimInstance Win32_BaseBoard |
Format-List Manufacturer, Product, Version

Get-NetAdapter |
Format-Table Name, InterfaceDescription, Status, MacAddress, LinkSpeed

Get-PhysicalDisk |
Format-Table FriendlyName, MediaType, Size, HealthStatus
```

### Sanitized observations — ASUS VivoBook X512UA

**Motherboard**
- Manufacturer: ASUSTeK COMPUTER INC.
- Product: X512UA
- Version: 1.0

**Network adapters**
- Physical Wi-Fi: Intel(R) Dual Band Wireless-AC 8265; status Up.
- Virtual interface: Happ Tunnel; status Up; reported link speed 100 Gbps. This does not establish actual internet throughput.
- Bluetooth PAN: disconnected.
- MAC addresses intentionally omitted from this public learning note.

**Storage**
- Model: SanDisk SD9SN8W256G1102
- Media type: SSD
- Size: 256,060,514,304 bytes (approximately 256 GB decimal / 238.5 GiB)
- Windows HealthStatus: Healthy

Healthy is a positive status, not a guarantee against future failure and not proof of encryption or backups.

## Knowledge checks
- CPU/RAM/SSD-HDD: **3/3**
- Motherboard/NIC/ECC/RAID/Secure Boot: **5/5**

## Final practical exam
**Passed — 5/5.** All five scenarios were answered correctly:
1. Investigate processes and workload when CPU usage is high.
2. Recognize likely RAM pressure when several VMs run slowly on an 8 GB system.
3. Use BitLocker to protect data at rest on a lost corporate laptop.
4. Investigate an unfamiliar virtual NIC by checking its purpose, owning software, and network configuration.
5. Interpret `HealthStatus = Healthy` as the current reported health state, not a guarantee against future failure.

## Next step
Lesson 02 is complete. Next: Module 1 — Lesson 03, Operating Systems Fundamentals.
