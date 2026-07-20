# DevOps Learning Log – Day 15

**Topic:** Bash Project 4 – Process Monitor & GitHub Repository Management

---

# Objective

Today I completed my fourth Bash project, **Process Monitor**, and learned how to monitor Linux processes, generate structured reports, and troubleshoot multiple Git/GitHub issues while publishing the project.

---

# Project Completed

## Process Monitor

The goal was to create a Bash script that generates a system report containing:

- Top CPU-consuming processes
- Top Memory-consuming processes
- Total running processes
- Current system load
- Logged-in users
- Timestamp

The report is automatically saved to `sum.txt`.

---

# Concepts Learned

## 1. Understanding `ps`

I explored the different variants of the `ps` command.

### `ps`

Displays processes associated with the current terminal.

### `ps -e`

Displays every running process on the system.

### `ps -ef`

Displays all running processes using the full format.

### `ps -eo`

Allows selecting custom output columns.

Example:

```bash
ps -eo pid,user,%cpu,%mem,comm
```

This lets me choose exactly what information to display.

---

# 2. Built-in Sorting

Initially I thought about using:

```bash
ps ...
| sort
```

I learned that `ps` already supports sorting.

Example:

```bash
ps -eo pid,user,%cpu --sort=-%cpu
```

Benefits:

- Faster
- Cleaner
- No need for an additional `sort` command

I also learned that generic sorting can still be done with:

```bash
sort -k3 -nr
```

where `-k3` specifies the third column.

The important lesson was:

> Prefer built-in functionality when a tool already provides it.

---

# 3. Parameterized Functions

Instead of writing two separate functions:

```bash
cpu_report()
memory_report()
```

I created a reusable function:

```bash
report() {
    local metric=$1

    ps -eo pid,user,$metric,comm --sort=-"$metric" | head -n 6
}
```

Now I simply call:

```bash
report "%cpu"
report "%mem"
```

This reduced duplicated code significantly.

---

# 4. Importance of `local`

I learned to declare function variables using:

```bash
local metric=$1
```

instead of global variables.

Benefits:

- Prevents variable pollution
- Makes functions independent
- Improves readability

---

# 5. Choosing Correct Commands

For every section of the report I selected the appropriate Linux utility.

| Requirement | Command |
|-------------|---------|
| CPU / Memory | `ps` |
| Running Processes | `wc` |
| System Load | `uptime` |
| Logged-in Users | `who` |
| Timestamp | `date` |

---

# 6. Extracting System Load

Initially I wanted to use:

```bash
uptime | cut -d "," -f4-
```

I realized this depended on comma positions.

Instead I learned to split using a meaningful label:

```bash
uptime | awk -F'load average: ' '{print $2}'
```

Reason:

The label "load average:" is much more stable than assuming commas always appear in fixed positions.

Lesson learned:

> Parsing meaningful labels is more reliable than parsing fixed field numbers.

---

# 7. Command Selection

Initially I considered:

```bash
whoami
```

for logged-in users.

I learned:

- `whoami` returns only the current user.
- `who` displays every logged-in session.

Therefore:

```bash
who | awk '{print $1}'
```

was the correct choice.

---

# 8. Report Structure

I separated the report into sections:

- CPU
- Memory
- Running Processes
- System Load
- Logged-in Users

making the output much easier to read.

---

# Mistakes Made

## Mistake 1

I originally wrote:

```bash
func "%cpu"
```

instead of

```bash
report "%cpu"
```

### Fix

Replaced every call with the correct function name.

---

## Mistake 2

After removing my loop I accidentally left:

```bash
done
```

inside the function.

This produced invalid Bash syntax.

### Fix

Removed the unnecessary `done`.

---

## Mistake 3

Originally my output lacked the process name.

I only displayed:

```text
PID USER %CPU
```

This made it difficult to identify which process was consuming resources.

### Fix

Added:

```bash
comm
```

to the output.

Final command:

```bash
ps -eo pid,user,$metric,comm --sort=-"$metric"
```

---

## Mistake 4

I initially placed a monitoring loop inside the report function.

This caused:

- 100 CPU snapshots
- followed by 100 Memory snapshots

before displaying the rest of the report.

### Fix

Removed the loop.

Generated a single report instead.

---

# Reasoning Learned

One important design discussion today was the difference between a **Process Report** and a **Process Monitor**.

A report generates one snapshot:

```
CPU
Memory
Processes
Load
Users
```

A monitor repeatedly generates complete snapshots:

```
Iteration 1
CPU
Memory
Load

Iteration 2
CPU
Memory
Load
```

I learned that if I ever build a live monitor, the loop should surround the entire report rather than individual sections.

---

# GitHub Repository

Repository Name:

```
Process-Monitor
```

Repository Description:

> A Bash-based process monitoring tool that generates a structured system report with CPU usage, memory usage, running processes, system load, and logged-in users.

I also created a professional README documenting:

- Overview
- Features
- Technologies
- Usage
- Example Output
- Learning Outcomes
- Future Improvements

---

# Git Mistakes and Fixes

## Mistake 1

I attempted:

```bash
git push -u origin main
```

before making my first commit.

Error:

```
src refspec main does not match any
```

Reason:

The branch had no commits.

### Fix

```bash
git add .
git commit -m "Initial commit"
```

---

## Mistake 2

I attempted:

```bash
git add process-monitor.sh
```

The file did not exist.

Reason:

The actual filename was:

```
processes-monitor.sh
```

### Fix

Added the correct filename.

---

## Mistake 3

I typed:

```bash
git push -u main
```

Reason:

I confused the remote name with the branch name.

### Fix

Correct command:

```bash
git push -u origin main
```

---

## Mistake 4

Git rejected my push:

```
non-fast-forward
```

After investigating:

```bash
git fetch origin
git log --oneline origin/main
```

I discovered the GitHub repository already contained:

```
Create README.md
```

Reason:

The GitHub repository had been initialized with a README, while my local repository had an unrelated initial commit.

Git refused to overwrite the remote history.

### Solution Learned

Two options existed:

Merge both histories:

```bash
git pull --no-rebase origin main --allow-unrelated-histories
```

or overwrite the remote:

```bash
git push --force -u origin main
```

Since the remote only contained GitHub's default README, I force-pushed my local repository.

Lesson learned:

Git protects remote history by default to prevent accidental data loss.

---

# Key Takeaways

- `ps` is the correct tool for scripting process information.
- Use built-in sorting whenever available.
- Parameterized functions reduce duplicate code.
- `local` variables improve function design.
- Parse meaningful labels instead of relying on fixed positions.
- Design scripts with reusable components.
- Understand the difference between reports and monitors.
- Git push errors usually indicate history or branch issues rather than authentication problems.
- A repository initialized separately on GitHub and locally creates unrelated histories.
- Force pushing replaces remote history and should only be used when appropriate.

---

# Reflection

Today's work strengthened both my Bash scripting and Git skills. I moved beyond simply using Linux commands and focused on designing reusable functions, choosing the right tools for each task, and structuring a monitoring report cleanly. I also gained practical experience diagnosing Git errors instead of treating them as isolated commands, which improved my understanding of how local and remote repositories interact.

---

# Overall Progress

- ✅ Linux Fundamentals
- ✅ Bash Scripting (4 Projects Completed)
- ✅ Git Basics
- ✅ GitHub Repository Management
- 🚀 Next: Complete Advanced Git Topics → Docker