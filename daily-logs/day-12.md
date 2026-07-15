# Day 12 – Bash Automation Project 1: System Health Checker

**Date:** July 17, 2026

---

## 📌 Overview

Today marked an important milestone in my DevOps roadmap as I completed my **first real Bash automation project**. Unlike the previous days, which focused on learning individual Bash concepts and Linux commands, today's objective was to combine everything into a practical solution that solves a real operational problem.

The project involved building a **System Health Checker** capable of gathering important system information such as CPU usage, memory utilization, disk usage, system uptime, hostname, internet connectivity, and the status of essential system services.

This project demonstrated how multiple Linux commands can be orchestrated using Bash to automate routine system administration tasks.

---

## 🎯 Project Completed

### 🖥️ System Health Checker

### Features Implemented

- ✅ CPU Usage Monitoring
- ✅ Memory Usage Monitoring
- ✅ Disk Usage Monitoring
- ✅ System Uptime
- ✅ Hostname Detection
- ✅ Internet Connectivity Check
- ✅ Service Status Monitoring
  - Nginx
  - Docker
  - SSH

---

## 🧠 Concepts Reinforced

Throughout this project, I applied nearly every Bash concept I had learned so far.

### Bash Fundamentals

- Variables
- Command Substitution (`$(...)`)
- Functions
- Arrays
- Loops
- Conditional Statements
- Exit Codes

### Linux Commands

- `top`
- `free`
- `df`
- `uptime`
- `hostname`
- `ping`
- `systemctl`

### Text Processing

- `grep`
- `awk`

---

## 💻 Development Process

Instead of attempting to build the entire script at once, I divided the project into smaller logical sections.

For each feature, I followed the same workflow:

1. Implement one section.
2. Verify that it worked correctly.
3. Fix any issues found.
4. Move on to the next section.

This incremental approach made debugging significantly easier and helped isolate problems before they affected the rest of the script.

---

## 🔍 Mistakes Made & Lessons Learned

### 1. Incorrect `grep` Pattern

**Mistake**

```bash
grep "/Cpu\(s\)/"
```

I mistakenly used `/.../` syntax, confusing `grep` with `awk`.

**Solution**

```bash
grep "Cpu(s)"
```

or even better,

```bash
awk '/Cpu\(s\)/ { ... }'
```

---

### 2. Incorrect Memory Formatting

**Mistake**

```bash
print "%.2f"
```

I attempted to format floating-point output using `print`.

**Solution**

```bash
printf "%.2f"
```

`printf` is the correct function in `awk` for formatted output.

---

### 3. Using `$HOSTNAME`

**Mistake**

Initially I used:

```bash
host=$HOSTNAME
```

Although this works on many systems, it depends on the shell environment.

**Solution**

```bash
HOST=$(hostname)
```

Using the `hostname` command is more reliable and portable across Linux systems.

---

### 4. Incorrect Function Closing

**Mistake**

I accidentally closed the function using:

```bash
)
```

instead of:

```bash
}
```

This resulted in a Bash syntax error.

**Solution**

Functions in Bash must always be closed using `}`.

---

### 5. Missing Closing Quote

**Mistake**

While writing the loop, I forgot to close the quotation marks:

```bash
"${services[@]}
```

which caused a syntax error.

**Solution**

```bash
"${services[@]}"
```

Always ensure quotation marks are properly paired.

---

### 6. Learning Bash Arrays

One completely new concept for me today was using arrays.

```bash
services=("nginx" "docker" "ssh")
```

Instead of hardcoding every service inside the loop, the array acts as an input list for iteration.

The syntax:

```bash
"${services[@]}"
```

was new to me.

I learned that:

- `[@]` expands to every element of the array.
- This allows a loop to process each service individually.
- Arrays make scripts much easier to maintain because new services can be added without modifying the loop itself.

---

### 7. Missing Output

I initially calculated the disk usage but forgot to display it.

**Lesson**

Computing a value is only useful if it is actually used within the script.

---

## 🌱 Personal Reflection

Today was my first real automation project, and it felt very different from simply learning Bash commands.

Instead of memorizing syntax, I focused on solving one problem at a time. Dividing the project into small sections, validating each section before continuing, and fixing issues immediately made the entire development process much more manageable.

The mistakes I made were valuable because they weren't just syntax errors—they taught me better engineering practices. I learned when to use `hostname` instead of relying on environment variables, how arrays improve maintainability, why `printf` is required for formatted output in `awk`, and how small syntax mistakes such as missing quotes or incorrect braces can prevent an otherwise correct script from running.

The most rewarding part of today was realizing that I was no longer asking for complete solutions. Instead, I identified problems, researched the correct Linux commands, assembled the logic myself, and refined the script through debugging. That felt like a transition from learning Bash commands to actually using Bash to solve real operational problems.

---

## 📈 Progress Update

- ✅ Linux Fundamentals
- ✅ Linux Administration
- ✅ Linux Networking
- ✅ Linux Security
- ✅ Bash Scripting Foundations
- ✅ Bash Automation Project 1 – System Health Checker
- 🔜 Bash Automation Project 2 – Disk Space Monitor

---

**Day 12 Complete ✅**

**Next Goal:** Build a Disk Space Monitor capable of detecting storage thresholds, generating warnings, and introducing more intelligent automation into Bash scripts.