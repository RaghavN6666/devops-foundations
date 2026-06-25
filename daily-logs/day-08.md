# Day 8 - Linux Filesystems & Learning Methodology Evolution

## Date

2025-06-26

## Time Studied

~2 Hours

---

# Objectives

- Understand Linux filesystem architecture
- Learn the Linux Filesystem Hierarchy Standard (FHS)
- Explore partitions and filesystems
- Learn mounting and filesystem management
- Understand swap space
- Learn disk usage commands
- Understand inodes and symbolic links
- Reflect on and improve my long-term learning methodology

---

# Resources Used

## Linux Journey

Completed:

- Filesystem Hierarchy
- Filesystem Types
- Anatomy of a Disk
- Disk Partitioning
- Creating Filesystems
- mount / umount
- /etc/fstab
- Swap
- Disk Usage
- Filesystem Repair
- Inodes
- Symlinks

---

# Concepts Learned

## Filesystem

A filesystem is responsible for organizing, storing, retrieving, and managing data on storage devices.

Different operating systems use different filesystem types depending on their requirements.

Examples:

- ext4
- XFS
- Btrfs
- FAT32
- NTFS

Mental Model:

```text
Disk
↓

Partition
↓

Filesystem
↓

Directories
↓

Files
```

---

# Linux Filesystem Hierarchy

## /

The root directory.

Every file and directory in Linux originates from the root.

---

## /etc

Stores configuration files for the operating system and installed applications.

Example:

```text
/etc/ssh
/etc/fstab
```

---

## /home

Contains user home directories and personal files.

---

## /var

Stores variable data such as:

- Logs
- Cache
- Mail
- Databases

---

## /dev

Contains device files representing hardware and virtual devices.

Examples:

```text
/dev/sda
/dev/null
/dev/tty
```

---

## /proc

A virtual filesystem created by the kernel.

Contains:

- Process information
- CPU information
- Memory information
- Kernel information

---

## /tmp

Stores temporary files.

---

## /usr

Contains installed applications, libraries, documentation, and utilities.

---

## /boot

Stores files required during the Linux boot process.

Examples:

- Kernel images
- Bootloader configuration

---

# Filesystem Types

Common filesystems:

Linux:

- ext4
- XFS
- Btrfs

Windows:

- FAT32
- NTFS

Different filesystems provide different capabilities depending on performance, compatibility, and reliability requirements.

---

# Disk Partitioning

A physical disk can be divided into multiple logical partitions.

Example:

```text
Disk

↓

Partition 1
Linux

↓

Partition 2
Windows

↓

Partition 3
Data
```

Each partition can contain a different filesystem.

---

# Formatting

Formatting prepares a partition by creating a filesystem on it.

This allows the operating system to organize and store files correctly.

---

# Filesystem vs Partition

Partition:

A logical section of a physical disk.

Filesystem:

The method used to organize and manage files inside a partition.

Mental Model:

```text
Disk

↓

Partition

↓

Filesystem

↓

Files
```

---

# Mounting

Linux does not assign drive letters.

Instead, filesystems are attached to directories.

Example:

```text
USB Drive

↓

Mounted

↓

/mnt/usb
```

This makes the filesystem accessible through the Linux directory tree.

---

# /etc/fstab

Stores filesystem mount configuration.

During boot:

```text
Boot

↓

Read /etc/fstab

↓

Automatically Mount Filesystems

↓

System Ready
```

---

# Swap Space

Swap is disk space used as virtual memory when RAM becomes full.

Mental Model:

```text
RAM Full

↓

Swap Used

↓

Continue Running
```

Although useful, swap is significantly slower than RAM and excessive use can reduce system performance.

---

# Disk Usage

Useful commands:

```bash
df -h

du -sh
```

### df -h

Displays available and used space for mounted filesystems.

### du -sh

Displays disk usage of specific files or directories.

---

# Inodes

An inode stores metadata about a file.

Contains:

- Owner
- Group
- Permissions
- Size
- Timestamps
- Data block locations

Important:

The inode **does not store the filename**.

Mental Model:

```text
Filename

↓

Directory Entry

↓

Inode

↓

Metadata + Data Block Locations
```

---

# Symbolic Links

A symbolic link acts as a reference to another file or directory.

Unlike copying a file, a symbolic link consumes very little additional storage because it simply points to the original.

Mental Model:

```text
Shortcut

↓

Original File
```

---

# Commands Learned

```bash
mount

umount

df -h

du -sh

fsck

ln
```

---

# Real-World DevOps Connection

Filesystem concepts form the foundation for many DevOps technologies.

Examples:

```text
Docker Volumes
↓

Linux Filesystems

AWS EBS
↓

Partitions + Mount Points

Kubernetes Persistent Volumes
↓

Filesystems

Linux Logs
↓

/var/log

Application Configuration
↓

/etc
```

Understanding the Linux filesystem makes it much easier to understand how storage is managed in containers and cloud infrastructure.

---

# Assessment Result

Score:

```text
9.0 / 10
```

### Strengths

- Strong understanding of filesystem hierarchy
- Good understanding of partitions and filesystems
- Understood mounting concepts
- Strong understanding of symbolic links
- Excellent troubleshooting approach using disk usage tools

### Areas to Improve

- /etc/fstab
- Difference between df and du
- Inode internals

---

# Learning Reflection - Evolution of My Study Method

During today's session, I reflected on how I have been learning over the past eight days.

While the theoretical foundation has helped me build strong mental models, I realized that continuously consuming theory without immediately applying it reduces my focus and retention over longer study sessions.

Rather than changing my goal of achieving mastery, I decided to improve my learning methodology.

---

## Previous Learning Workflow

```text
Theory

↓

Theory

↓

Theory

↓

Assessment
```

This approach helped establish a strong theoretical foundation but lacked consistent opportunities to immediately reinforce concepts through practice.

---

## New Learning Workflow

```text
Review Previous Concepts

↓

Learn One New Concept

↓

Complete a Guided Challenge

↓

Explain the Concept

↓

Reflect and Document
```

This structure better matches the way I naturally learn by allowing me to actively apply concepts shortly after studying them.

---

## Engineering Challenge Days

Instead of continuously studying theory, I will periodically dedicate entire study sessions to solving engineering problems using only the concepts I have already learned.

These sessions will focus on:

- Linux administration
- Troubleshooting
- Automation
- Problem-solving
- Engineering thinking

---

## Mini Projects

After each major learning milestone, I will build a practical project using the concepts learned so far.

Each project will evolve over time rather than remaining an isolated exercise.

This approach will help me:

- Reinforce knowledge
- Develop practical engineering skills
- Build a professional GitHub portfolio
- Demonstrate continuous improvement

---

## Learning Philosophy

My objective is no longer simply to complete tutorials or learning resources.

My objective is to deeply understand systems, connect concepts together, solve real engineering problems, and continuously improve through practical application.

Every future topic should answer:

1. Why does this technology exist?
2. What problem does it solve?
3. How is it used in production?
4. How does it connect with previous concepts?
5. Can I build something with it today?

This learning strategy aligns much more closely with my long-term goal of becoming an exceptional DevOps engineer.

---

# Personal Reflection

Today's lesson significantly improved my understanding of how Linux stores and organizes data. I now see the filesystem as the foundation that supports almost everything in the operating system, from user files and application configurations to logs and mounted storage devices.

The concept that stood out the most was understanding the relationship between disks, partitions, filesystems, and mount points. Viewing them as connected layers rather than isolated topics helped everything make much more sense.

The most challenging concept was understanding inodes because they introduce a different way of thinking about files. Learning that filenames are separate from the inode itself changed my perspective on how Linux internally manages files.

Beyond the technical material, today's biggest realization was about my own learning process. While reflecting on the previous eight days, I recognized that I learn most effectively when theory is quickly reinforced through practical application.

Going forward, I will continue documenting my daily progress while incorporating guided challenges, engineering problem-solving sessions, and progressively larger projects into my learning journey.

My goal remains unchanged:

**To achieve mastery through deep understanding, practical application, and continuous improvement.**

---

# Key Takeaways

- Filesystems organize and manage stored data.
- Linux follows a standardized filesystem hierarchy.
- Partitions divide physical storage into logical sections.
- Filesystems are created on partitions.
- Mounting attaches filesystems to the directory tree.
- `/etc/fstab` automates filesystem mounting during boot.
- Swap extends memory using disk space.
- `df` and `du` provide different views of disk usage.
- Inodes store metadata rather than filenames.
- Symbolic links reference existing files without duplicating data.
- Practical application strengthens long-term retention more effectively than theory alone.

---

# Day 8 Completion Status

## Completed

- [x] Filesystem Hierarchy
- [x] Filesystem Types
- [x] Disk Partitioning
- [x] Formatting
- [x] Mounting
- [x] /etc/fstab
- [x] Swap
- [x] Disk Usage
- [x] Inodes
- [x] Symbolic Links
- [x] Learning Methodology Reflection

## Next Focus

- Bash Scripting
- Guided Linux Challenges
- Engineering Challenge #1
- Mini Project #1