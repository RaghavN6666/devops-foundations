# 📅 Day 13 – DevOps Learning Log

## 📌 Topic
**Bash Scripting Project 2 – Disk Space Monitor**

### 🎯 Objective
Build a Bash-based disk monitoring tool that analyzes all mounted filesystems, classifies disk usage into health states, logs the results with timestamps, and generates a summary report.

---

## 📚 What I Learned

### ✅ Working with Disk Usage
- Used `df -h` to retrieve filesystem information.
- Used `awk` to extract only the disk usage percentage and mount point.
- Learned the difference between `NR` (Number of Records) and `NF` (Number of Fields).

### ✅ Bash Parameter Expansion
- Removed the `%` symbol from disk usage values using:

```bash
DISK=${USAGE%\%}
```

This allowed numeric comparisons using `-lt` and `-ge`.

---

### ✅ Conditional Logic
Implemented disk health classification:

- Healthy (<70%)
- Warning (70–89%)
- Critical (≥90%)

---

### ✅ Counters
Maintained statistics using arithmetic expansion:

```bash
((H++))
((W++))
((C++))
```

to count Healthy, Warning, and Critical partitions.

---

### ✅ Logging
Generated timestamped reports using:

```bash
DATE=$(date +"%Y-%m-%d %H:%M:%S")
```

and appended results to a log file for future reference.

---

### ✅ Process Substitution
Learned how to safely read command output without creating a subshell using:

```bash
done < <(df -h | awk 'NR>1 {print $5, $6}')
```

This preserved variable values after the loop completed.

---

## 🛠️ Mistakes & Fixes

### 1. Processing the Header Row
**Mistake:**

Initially processed the header from `df -h`, causing invalid values like `Use%` to be read.

**Fix:**

Skipped the first line using:

```bash
awk 'NR>1 {print $5, $6}'
```

---

### 2. Root Partition Only
**Mistake:**

Originally filtered only the root (`/`) filesystem.

**Fix:**

Modified the script to process every mounted filesystem instead of just one.

---

### 3. Comparing Strings Instead of Numbers
**Mistake:**

Tried comparing values like `63%` directly.

**Fix:**

Removed the `%` using parameter expansion:

```bash
DISK=${USAGE%\%}
```

before performing numeric comparisons.

---

### 4. Repeating Output Logic
**Mistake:**

Initially considered printing different messages inside each `if` condition.

**Fix:**

Stored the result in a `STATUS` variable and used a single `echo` statement, reducing duplicated code.

---

### 5. Subshell Issue
**Mistake:**

Used:

```bash
df -h | while read ...
```

The loop executed inside a subshell, so counters (`H`, `W`, `C`) reset to zero after the loop.

**Fix:**

Used process substitution:

```bash
done < <(df -h | awk 'NR>1 {print $5, $6}')
```

which executes the loop in the current shell.

---

### 6. Confusing Here Documents and Process Substitution
**Mistake:**

Mixed up:

```bash
<<
```

with

```bash
< <(...)
```

and also wrote incorrect syntax with spaces around `(`.

**Fix:**

Learned the correct syntax:

```bash
done < <(command)
```

and understood the difference between Here Documents, Here Strings, and Process Substitution.

---

### 7. Git Repository Confusion
**Mistake:**

Initialized Git inside the home directory (`~/`) instead of a dedicated project folder.

**Fix:**

Learned that every project should have its own directory and Git repository before connecting it to GitHub using:

```bash
git remote add origin <repository-url>
```

---

## 🧠 Methodology

Instead of writing one long script, I approached the project incrementally:

1. Retrieve filesystem information.
2. Extract only the required fields.
3. Clean the data.
4. Process each filesystem using a loop.
5. Classify disk health.
6. Store the classification in a variable.
7. Count each status.
8. Log the results.
9. Generate a final summary.
10. Debug and refactor until the script behaved correctly.

This structured approach made debugging much easier and improved the overall readability of the script.

---

## 🚀 Project Features

- Monitor all mounted filesystems
- Classify disk health
- Generate timestamped reports
- Maintain summary statistics
- Append logs instead of overwriting
- Use efficient Bash scripting techniques

---

## 💡 Key Takeaways

Today's project strengthened my understanding of:

- Bash scripting
- Linux filesystem monitoring
- Parameter expansion
- Process substitution
- Input redirection
- Loop execution behavior
- Git repository organization
- Debugging and incremental development

This project also reinforced the importance of understanding **how Bash executes commands**, not just how to write them.

---

## 📈 Reflection

This project was a major step forward from simply executing Linux commands to building a practical automation tool. Along the way, I encountered several real Bash pitfalls—including header parsing, numeric comparisons, subshell behavior, process substitution syntax, and Git repository organization—and learned how to resolve each one systematically. More importantly, I developed a structured workflow: build incrementally, test frequently, identify the root cause of errors, refactor where needed, and improve the script until it became reliable and maintainable.