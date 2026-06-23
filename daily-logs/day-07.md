# Day 7 - Linux Logging & Process Monitoring

## Date

2025-06-25

## Time Studied

~1.5 Hours

---

# Objectives

- Understand Linux logging systems
- Learn the purpose of system logs
- Explore different log categories
- Learn process and system monitoring concepts
- Understand CPU and I/O monitoring
- Build troubleshooting foundations for Linux administration

---

# Resources Used

## Linux Journey

### Logging

Completed:

- System Logging
- syslog
- General Logging
- Kernel Logging
- Authentication Logging
- Managing Log Files

### Process Utilization

Completed:

- Tracking Processes: top
- lsof and fuser
- Process Threads
- CPU Monitoring
- I/O Monitoring

---

# Concepts Learned

## Why Logs Exist

Logs act as a historical record of system activity.

Purpose:

- Troubleshooting issues
- Tracking system events
- Recording errors
- Monitoring user activity
- Auditing system behavior

Mental Model:

```text
Problem Occurs
↓
Logs Record Event
↓
Engineer Investigates
↓
Root Cause Found
```

---

## Log Storage

Most Linux log files are stored within:

```text
/var/log
```

This directory contains various logs related to:

- System events
- Authentication
- Applications
- Kernel messages

---

## syslog

syslog acts as a centralized logging mechanism.

Purpose:

- Collect logs from multiple services
- Organize log messages
- Store events for troubleshooting

syslog serves as one of the foundational logging systems in Linux.

---

## Kernel Logging

Kernel logs contain information about:

- Hardware
- Drivers
- Kernel events
- System-level messages

These logs are useful when diagnosing low-level system problems.

---

## Authentication Logging

Authentication logs record:

- Login attempts
- Logout events
- SSH authentication
- User access activity

These logs are often the first place to investigate access-related issues.

---

## Managing Log Files

Log files continuously grow over time.

Potential issues:

- Increased storage usage
- Performance degradation
- Difficult log management

This creates the need for log rotation and cleanup strategies.

---

# Process Monitoring

## top

The top command provides real-time process information.

Displays:

- Running processes
- PID values
- CPU usage
- Memory usage
- Process status

Useful for identifying resource-intensive processes.

---

## Processes vs Threads

### Process

A running program with its own resources.

### Thread

A lightweight execution unit within a process.

Characteristics:

- Shares resources with other threads
- Lower overhead
- Enables concurrent execution

---

## CPU Monitoring

CPU monitoring helps identify:

- High CPU utilization
- Performance bottlenecks
- Resource-intensive applications

Useful during troubleshooting and performance analysis.

---

## I/O Monitoring

I/O monitoring focuses on:

- Disk reads
- Disk writes
- Storage activity

High I/O usage can create system slowdowns even when CPU utilization remains low.

---

## lsof

Command:

```bash
lsof
```

Purpose:

Displays open files and the processes using them.

Important Linux concept:

```text
Everything is a File
```

This includes:

- Files
- Network sockets
- Devices

---

## fuser

Command:

```bash
fuser
```

Purpose:

Identifies which process is currently using a specific file or resource.

Useful when troubleshooting locked files or busy resources.

---

# Commands Encountered

```bash
top

lsof

fuser
```

---

# Assessment Summary

Initial assessment revealed strong understanding of:

- Purpose of logging
- Log categories
- Monitoring concepts
- Process and thread distinctions

Areas requiring review:

- syslog responsibilities
- lsof usage
- fuser usage
- I/O monitoring details

---

# Personal Reflection

Today's session focused on Linux logging and monitoring, which felt much closer to the day-to-day responsibilities of a Linux administrator than many of the previous topics.

The most interesting realization was understanding how heavily troubleshooting depends on logs. Rather than guessing why a problem occurred, engineers can examine logs to reconstruct events and identify root causes.

I also enjoyed learning about process monitoring tools such as top and seeing how system resources can be observed in real time.

However, I felt noticeably more mentally fatigued during today's session. My semester-end examinations are approaching, and much of my daily study effort is currently dedicated to academic preparation. As a result, today's DevOps study session took place late at night after spending the day preparing for exams.

Although I completed the material, I realized during the assessment that I had rushed through some concepts and did not retain certain command-specific details as well as I normally would. Rather than forcing additional study while tired, I decided to revisit and reassess the weaker topics with a fresh mind.

This decision aligns with my long-term goal of mastery rather than speed. I would rather understand and retain concepts properly than move forward without a solid foundation.

Despite the reduced pace, I maintained consistency and continued progressing through the Linux curriculum while balancing academic responsibilities.

---

# Key Takeaways

- Logs are critical for troubleshooting.
- Most logs reside in `/var/log`.
- Kernel logs and authentication logs serve different purposes.
- Monitoring tools help identify performance bottlenecks.
- Threads are lightweight execution units within processes.
- CPU and I/O monitoring reveal different types of system issues.
- `top` is essential for process monitoring.
- `lsof` and `fuser` assist with resource investigation.
- Consistent learning is more important than rapid learning.

---

# Day 7 Completion Status

## Completed

- [x] System Logging
- [x] syslog
- [x] General Logging
- [x] Kernel Logging
- [x] Authentication Logging
- [x] Managing Log Files
- [x] top
- [x] lsof
- [x] fuser
- [x] Process Threads
- [x] CPU Monitoring
- [x] I/O Monitoring

## Review Required

- [ ] syslog
- [ ] lsof
- [ ] fuser
- [ ] I/O Monitoring

---

# Status

```text
Day 7: COMPLETE WITH REVIEW PENDING
```

Conceptual understanding achieved. Minor reinforcement required before advancing further.