# Day 3 - Linux Processes & Process Management

## Date

2025-06-16

## Time Studied

~3.5 Hours

---

# Objectives

- Understand what a process is
- Learn how Linux manages running programs
- Understand Process IDs (PIDs)
- Learn how to inspect running processes
- Learn process termination and signals
- Understand foreground and background jobs
- Explore the `/proc` filesystem
- Practice real process management in Linux

---

# Resources Used

## Linux Journey

Completed:

- ps (Processes)
- Controlling Terminal
- Process Details
- Process Creation
- Process Termination
- Signals
- kill (Terminate)
- Niceness
- Process States
- /proc Filesystem
- Job Control

---

# Technical Notes

# What is a Process?

A process is a program that is currently being executed by the operating system.

When a program starts running, Linux allocates resources such as:

- CPU time
- Memory
- File descriptors
- Process state information

Example:

```bash
python app.py
```

When executed, Linux creates a process for the program.

---

# Process ID (PID)

Every process in Linux receives a unique identifier called a PID.

Example:

```text
PID = 1234
PID = 5678
PID = 9012
```

## Why PIDs Exist

PIDs allow Linux and users to:

- Identify processes
- Monitor processes
- Terminate processes
- Manage process behavior

Without PIDs, it would be difficult to distinguish between multiple running instances of the same application.

---

# Viewing Processes

## ps

### Command

```bash
ps
```

### Purpose

Displays information about processes associated with the current terminal session.

### Example Output

```text
PID TTY          TIME CMD
1234 pts/0    00:00:00 bash
5678 pts/0    00:00:00 ps
```

### Observation

`ps` provides a snapshot of currently running processes.

---

## ps aux

### Command

```bash
ps aux
```

### Purpose

Displays detailed information about all running processes on the system.

### Information Shown

- User
- PID
- CPU Usage
- Memory Usage
- Start Time
- Command

### Observation

This command is significantly more useful for system monitoring than the default `ps`.

---

# Process Monitoring

## top

### Command

```bash
top
```

### Purpose

Provides a real-time view of system processes and resource usage.

### Information Displayed

- CPU utilization
- Memory usage
- Running processes
- Load averages
- Process priorities

### Key Difference From ps

```text
ps  = Snapshot

top = Live Monitoring
```

### Personal Observation

This was one of the most interesting commands because it felt like viewing the operating system in real time rather than looking at static information.

---

# Process Creation

Whenever a program is executed, Linux creates a process.

Example:

```bash
sleep 300
```

Linux creates a process that remains active for 300 seconds.

### Practical Lab

Created a process using:

```bash
sleep 300
```

Then identified it using:

```bash
ps aux | grep sleep
```

and located its PID.

---

# Process Termination

Processes can be terminated using signals.

---

## kill

### Command

```bash
kill PID
```

### Purpose

Sends a termination signal to a process.

### Default Signal

```text
SIGTERM (15)
```

Meaning:

```text
Please terminate gracefully.
```

The process may:

- Save data
- Clean up resources
- Exit safely

---

## kill -9

### Command

```bash
kill -9 PID
```

### Purpose

Forces immediate process termination.

### Signal Sent

```text
SIGKILL (9)
```

Meaning:

```text
Terminate immediately.
```

The process cannot ignore or handle this signal.

---

# Signals

Signals are messages sent to processes to notify them of events or request actions.

Examples:

```text
SIGTERM
SIGKILL
SIGSTOP
SIGINT
```

## Purpose

Signals allow Linux to communicate with running processes.

Examples:

- Request shutdown
- Pause execution
- Force termination
- Interrupt execution

---

# Process States

A process can exist in multiple states.

## Running

The process is actively executing.

---

## Interruptible Sleep

The process is waiting for an event and can be interrupted.

---

## Uninterruptible Sleep

The process is waiting for a resource and cannot be interrupted immediately.

---

## Additional States

Other process states include:

```text
Stopped
Zombie
```

---

# Niceness

## Purpose

Controls process scheduling priority.

### Command

```bash
nice
```

Processes with different nice values receive different CPU scheduling priorities.

### Observation

This concept was interesting because it demonstrated how Linux decides which processes receive more CPU attention.

---

# The /proc Filesystem

## Purpose

The `/proc` filesystem is a virtual filesystem maintained by the Linux kernel.

It exposes:

- Process information
- Kernel information
- System information

### Example

Find current shell PID:

```bash
echo $$
```

Then inspect:

```bash
cat /proc/<PID>/status
```

### Observation

This was one of the most interesting topics because it exposed internal operating system information through normal files.

---

# Job Control

Linux allows processes to run in either the foreground or background.

---

## Foreground Processes

A foreground process occupies the terminal.

Example:

```bash
sleep 300
```

The terminal remains busy until the process completes or is terminated.

---

## Background Processes

A background process runs without occupying the terminal.

Example:

```bash
sleep 300 &
```

The terminal remains available for additional commands.

---

## jobs

### Command

```bash
jobs
```

### Purpose

Displays currently running background jobs.

---

## fg

### Command

```bash
fg
```

### Purpose

Moves a background job back into the foreground.

---

# Practical Exercises Completed

## Exercise 1

Created a process:

```bash
sleep 300
```

Located process using:

```bash
ps aux | grep sleep
```

Identified PID successfully.

---

## Exercise 2

Terminated process using:

```bash
kill PID
```

Verified termination.

---

## Exercise 3

Started a background process:

```bash
sleep 300 &
```

Observed using:

```bash
jobs
```

Returned process to foreground using:

```bash
fg
```

Terminated process using:

```text
Ctrl + C
```

---

## Exercise 4

Explored process priority concepts using:

```bash
nice
```

and inspected processes using:

```bash
top
```

---

## Exercise 5

Explored kernel process information using:

```bash
echo $$
cat /proc/<PID>/status
```

---

# Commands Practiced

```bash
ps
ps aux
top
kill
kill -9
jobs
fg
sleep
nice
echo $$
```

Explored:

```bash
/proc
```

filesystem contents.

---

# Mistakes Made

## Mistake 1

Initially assumed:

```bash
kill PID
```

immediately destroys a process.

### Correct Understanding

The command actually sends:

```text
SIGTERM
```

which requests graceful termination.

---

## Mistake 2

While practicing Git concepts, I attempted:

```bash
echo "test line" >> git/git-notes.md
```

from:

```bash
/home/zen
```

which resulted in:

```text
No such file or directory
```

### Cause

The relative path was resolved from the current working directory.

### Correct Understanding

The file actually existed inside:

```bash
~/devops-foundations/git/git-notes.md
```

### Lesson Learned

Always verify the current working directory before using relative paths.

Useful commands:

```bash
pwd
ls
```

---

# Knowledge Assessment

## Successfully Understood

### What is a Process?

A running program with resources allocated by the operating system.

---

### PID

Unique identifier used to manage and track processes.

---

### ps vs top

```text
ps  = Snapshot

top = Live Monitoring
```

---

### kill vs kill -9

```text
kill    = SIGTERM

kill -9 = SIGKILL
```

---

### Signals

Mechanism used by Linux to communicate with processes.

---

### Foreground vs Background Jobs

Understood how Linux manages terminal-attached and detached processes.

---

### /proc

Understood its role as a virtual filesystem exposing kernel and process information.

---

# Questions Raised

1. How does the Linux scheduler decide which process gets CPU time?
2. What happens internally when a signal is sent?
3. Why do zombie processes occur?
4. How does Linux manage thousands of processes simultaneously?
5. How do Docker containers handle process management?

---

# Personal Reflection

Today's session was noticeably more challenging than the previous two days.

Unlike Linux commands and permissions, process management required understanding how the operating system behaves internally rather than simply learning commands.

One advantage was that many concepts overlapped with topics I am currently studying in my Operating Systems course. Terms such as processes, process states, scheduling, and signals felt familiar from a theoretical perspective.

The most valuable part of today's session was connecting that theory to practical Linux commands. Commands such as `ps`, `top`, `kill`, and exploring the `/proc` filesystem helped bridge the gap between classroom concepts and real system administration tasks.

The `/proc` filesystem was particularly interesting because it exposed internal operating system information through files that could be inspected directly from the terminal.

Although the material was heavier than previous days, I was able to understand the overall flow of process creation, monitoring, and termination by the end of the session.

Overall, this session felt like the first step toward understanding how Linux operates beneath the surface.

---

# Key Takeaways

- Learned what processes are and how Linux manages them.
- Understood the purpose of PIDs.
- Learned to inspect running processes using `ps`.
- Learned to monitor processes using `top`.
- Understood process termination using `kill`.
- Learned the difference between `SIGTERM` and `SIGKILL`.
- Explored process states.
- Learned about process priorities and niceness.
- Explored the `/proc` filesystem.
- Practiced foreground and background job control.
- Reinforced understanding of Linux path resolution.

---

# Self Assessment

| Skill | Rating |
|---------|---------|
| Linux Navigation | 6.5/10 |
| Linux Permissions | 6.5/10 |
| Linux Processes | 6/10 |
| Git | 4/10 |
| Networking | 2/10 |
| Python | 3/10 |

---

# Next Focus Areas

- Package Management
- apt
- dpkg
- Software Installation
- Dependency Management
- Git Reinforcement

---

# Day 3 Completion Status

## Completed

- [x] Process Fundamentals
- [x] PID Concepts
- [x] Process Monitoring
- [x] Process Creation
- [x] Process Termination
- [x] Signals
- [x] Niceness
- [x] Process States
- [x] /proc Filesystem
- [x] Job Control
- [x] Practical Process Labs

## Pending

- [ ] Package Management
- [ ] Advanced Git Concepts
- [ ] Networking Fundamentals
- [ ] Bash Scripting
- [ ] Bandit Continuation