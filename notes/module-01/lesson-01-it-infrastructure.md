# Lesson 01 — What Is IT Infrastructure?

- **Module:** 1 — IT Infrastructure Fundamentals
- **Status:** PASSED
- **Theory exam:** 10/10
- **Practical exam:** 5/5

## 1. Definition

**IT Infrastructure** is the collection of technology components an organization uses to operate its IT services. It includes hardware, software, networks, servers, storage, cloud resources, and security systems.

## 2. Main components

1. **Servers** — systems that provide services or resources to other systems.
2. **Endpoints / Workstations** — user devices such as laptops and desktop computers.
3. **Network Infrastructure** — routers, switches, Wi-Fi access points, cabling, and related services.
4. **Operating Systems (OS)** — system software such as Windows and Linux.
5. **Cloud Infrastructure** — computing, storage, networking, and services hosted by a cloud provider.
6. **Security Infrastructure** — controls and tools such as firewalls, identity systems, endpoint protection, logging, and monitoring.

## 3. Example company environment

A small company may have:
- Windows 11 workstations for employees
- A Windows Server providing identity or file services
- A Linux server hosting a website or application
- A router connecting local networks to other networks
- A firewall enforcing traffic rules
- An internet connection

A simplified conceptual diagram:

```text
Internet
   |
Firewall
   |
Network Switch
   |-------------------|
Workstations        Servers
                    |-- Windows Server (e.g. identity/file services)
                    |-- Linux Server (e.g. web/application services)

Security monitoring collects logs and alerts from relevant systems.
```

This is a conceptual diagram, not a required physical topology. Monitoring systems receive telemetry from multiple components; they are not necessarily a network hop below the servers.

## 4. Important terminology

| English | Russian |
|---|---|
| Infrastructure | Инфраструктура |
| Server | Сервер |
| Workstation | Рабочая станция |
| Endpoint | Конечное устройство |
| Network | Сеть |
| Operating System (OS) | Операционная система |
| Storage | Хранилище |
| Database | База данных |
| Firewall | Межсетевой экран |
| Access Control | Контроль доступа |
| Authentication | Проверка подлинности / идентификация пользователя |
| Authorization | Проверка разрешений |
| Security Monitoring | Мониторинг безопасности |
| SIEM | Система сбора и анализа событий безопасности |

## 5. How a user accesses a company resource

A simplified flow:
1. The employee starts a workstation.
2. The user signs in.
3. An identity service may authenticate the user.
4. Authorization rules determine which resources the user may access.
5. Network controls allow or block the connection according to policy.
6. Relevant systems generate logs that may be collected by a SIEM.

**Authentication** answers: “Who are you?”

**Authorization** answers: “What are you allowed to do?”

A firewall filters network traffic; it does not replace application-level or file-level authorization.

## 6. Windows discovery lab

Commands used in Windows Command Prompt:

```cmd
hostname
systeminfo
ipconfig
```

Purpose:
- `hostname` — displays the computer name.
- `systeminfo` — displays operating system and hardware information.
- `ipconfig` — displays network adapter configuration.

### Sanitized observations from the learner's laptop

- OS: Windows 11 Pro, 64-bit
- CPU: Intel Core i5-8250U
- RAM: approximately 8 GB
- Wi-Fi IPv4 address: `192.168.1.7`
- Subnet mask: `255.255.255.0` (also written `/24`)
- Default gateway: `192.168.1.1`
- Local subnet: `192.168.1.0/24`

Private IP addresses are included as lab examples. Avoid publishing public IP addresses, serial numbers, product keys, email addresses, tokens, or other personal identifiers.

## 7. Basic subnet observations

With a `/24` subnet mask:
- `192.168.1.7` and `192.168.1.20` are in the same IPv4 subnet.
- Devices in the same local subnet can generally communicate directly over the local network, using mechanisms such as ARP to resolve an IPv4 address to a MAC address.
- `192.168.1.7` and `192.168.2.20` are in different `/24` subnets; communication between them normally requires routing through a router/default gateway.
- The default gateway is used to reach destinations outside the local subnet.

## 8. Security fundamentals introduced

- Keep operating systems and applications updated.
- Use least privilege and review accounts.
- Enforce MFA where possible.
- Configure firewall rules deliberately.
- Use endpoint protection.
- Collect and review security logs.
- Maintain independent backups and test restoration.
- Apply network segmentation where appropriate.

Important distinctions:
- A snapshot is not a substitute for an independent backup.
- A firewall is one layer of defense, not complete protection.
- Windows and Linux can both perform many server roles; the role depends on configuration and software.

## 9. Assessment result

### Theory — 10/10

The learner correctly answered questions covering infrastructure components, endpoints, firewall purpose, server roles, IP addresses, /24 subnet reasoning, routing, authentication, SIEM, and layered security.

### Practical — 5/5

The learner correctly:
1. Explained the roles of workstations and Windows/Linux servers.
2. Analyzed a same-subnet network scenario and described firewall filtering.
3. Distinguished authentication from authorization.
4. Explained SIEM log collection, analysis, and alerting.
5. Proposed basic hardening measures, including updates, account review, firewall rules, endpoint protection, monitoring, and backups.

## 10. Review topics

Revisit these concepts in later networking and security modules:
- ARP and MAC addresses
- Network segmentation
- Vulnerability management
- Independent backups and restore testing
- MFA and modern password/account protection practices

## Next lesson

**Lesson 02 — Hardware Fundamentals:** CPU, RAM, HDD/SSD, motherboard, NIC, server and endpoint hardware, and hardware security considerations.
