# Day 6 - Linux Init Systems & Service Management

## Date

2025-06-24

## Time Studied

~2 Hours

---

# Objectives

- Understand the Linux boot process
- Learn why init systems exist
- Compare SysVinit, Upstart, and systemd
- Understand services and daemons
- Learn dependency management
- Connect Linux services to real-world server administration

---

# Resources Used

## Linux Journey

Completed:

- System V Overview
- System V Services
- Upstart Overview
- Upstart Jobs
- Systemd Overview
- Systemd Goals
- Power States

---

# Concepts Learned

## Linux Boot Process

```text
Computer Power On
↓
Bootloader
↓
Kernel
↓
Init System
↓
Services Start
↓
System Ready
```

The kernel initializes the operating system and then transfers control to the init system.

---

## Init Systems

Purpose:

- Start services
- Stop services
- Monitor services
- Manage dependencies
- Handle shutdown and reboot

Without an init system, Linux would not automatically start important services.

---

## SysVinit

Characteristics:

- Sequential startup
- Script-based service management

Limitations:

- Slow boot times
- Poor dependency management
- Difficult service monitoring

---

## Upstart

Introduced:

```text
Event Driven Startup
```

Services can start when specific events occur rather than strictly following a sequence.

Example:

```text
Network Available
↓
Start SSH
```

---

## systemd

Modern Linux distributions primarily use systemd.

Purpose:

- Manage services
- Manage dependencies
- Improve startup speed
- Monitor system state

Mental Model:

```text
systemd
=
System Manager
```

---

## Services

A service is a long-running application that operates in the background.

Examples:

```text
SSH
Docker
Nginx
MySQL
```

---

## Process vs Service

### Process

A running program.

Example:

```bash
vim notes.txt
```

Ends when the program closes.

### Service

A managed process that remains active until stopped.

Example:

```text
SSH Service
```

---

## Daemons

A daemon is a background process.

Examples:

```text
sshd
dockerd
systemd
```

Many daemon names end with:

```text
d
```

for daemon.

---

## Dependency Management

Some services require other services before they can start.

Example:

```text
Network
↓
SSH
```

systemd automatically manages these relationships.

---

## Power States

- Shutdown
- Reboot
- Suspend
- Hibernate

These states determine how the system behaves when powering down or conserving power.

---

# Real-World DevOps Connection

AWS EC2 Example:

```text
Server Boots
↓
Kernel Starts
↓
systemd Starts
↓
SSH Starts
↓
Docker Starts
↓
Application Starts
↓
Server Ready
```

Without systemd, services would not automatically start after reboot.

---

# Assessment Result

Score:

```text
7.8/10
```

### Strengths

- Understood Linux boot sequence
- Understood services and processes
- Understood why systemd exists

### Areas for Improvement

- Upstart architecture
- Daemon terminology
- Service startup flow after reboot
- Dependency relationships

---

# Personal Reflection

Today's lesson helped me understand what happens after the Linux kernel loads and how Linux systems become usable after boot.

The most interesting part was learning about the evolution of init systems from SysVinit to Upstart and finally to systemd. Understanding the weaknesses of older systems helped me appreciate why systemd became the standard.

I found dependency management particularly interesting because it highlighted how services rely on one another to function correctly.

Although some concepts required extra effort to understand, especially Upstart and daemon behavior, by the end of the session I developed a solid mental model of the Linux startup process.

I now understand that after the kernel loads, an init system takes control, starts the required services, and prepares the server for use. This concept connects directly to how modern servers, cloud instances, Docker hosts, and future Kubernetes nodes operate.

---

# Key Takeaways

- The kernel hands control to an init system.
- Init systems manage services.
- SysVinit was sequential and slower.
- Upstart introduced event-driven startup.
- systemd is the modern standard.
- Services are long-running applications.
- Daemons are background processes.
- Dependency management is critical.
- Most modern infrastructure relies on systemd.

---

# Day 6 Completion Status

- [x] SysVinit
- [x] Upstart
- [x] systemd
- [x] Services
- [x] Daemons
- [x] Dependency Management
- [x] Power States

## Next Focus

- systemctl
- Journald & Logs
- Bash Scripting
- Intermediate Git
- Docker Foundations