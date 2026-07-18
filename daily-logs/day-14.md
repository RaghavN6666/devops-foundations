# Daily Learning Log – Project 3: Intelligent Log Summarizer

**Project:** Intelligent Log Summarizer

**Objective:**
Build a Bash script that reads an application log file, categorizes log entries by severity (ERROR, WARNING, INFO), groups duplicate messages, counts their occurrences, and generates a clean summary report.

---

# What I Learned

## Unix Pipelines

I learned how to combine multiple Linux utilities together so that each command performs a single task.

Pipeline used:

```bash
grep "^ERROR" "$FILE" \
| cut -d' ' -f2- \
| sort \
| uniq -c \
| sort -nr
```

Pipeline breakdown:

- grep filters only the required log level.
- cut removes the severity field.
- sort groups identical messages together.
- uniq -c counts duplicate messages.
- sort -nr sorts the results by occurrence count.

This reinforced the Unix philosophy of solving complex problems by combining small tools.

---

## The Meaning of `cut -f2-`

Initially I wasn't sure why:

```bash
cut -d' ' -f2-
```

was used instead of:

```bash
cut -d' ' -f2
```

I learned:

- `-f2` extracts only the second field.
- `-f2-` extracts the second field **through the last field**.

Example:

Input:

```
ERROR Database connection failed
```

Using:

```bash
cut -d' ' -f2
```

Output:

```
Database
```

Using:

```bash
cut -d' ' -f2-
```

Output:

```
Database connection failed
```

Reasoning:

To count duplicate log messages correctly, the entire message must be preserved rather than just its first word.

---

## Building Reusable Functions

Instead of writing separate code for ERROR, WARNING, and INFO, I created a reusable function.

```bash
summarize_level() {
    local level=$1
    ...
}
```

Reasoning:

Every log level follows the exact same workflow.

Only the severity changes.

Using a function avoids duplicate code and makes the script easier to maintain.

---

## Local Variables

Inside the function I used:

```bash
local level=$1
```

instead of directly using `$1` throughout the function.

Reasoning:

Using a named variable improves readability and prevents accidental modification of variables outside the function.

---

## grep -q

I learned that:

```bash
grep -q
```

does not print matching lines.

It simply checks whether a match exists.

Reasoning:

Instead of displaying nothing when no messages exist, I can display:

```
No ERROR found
```

or

```
No WARNING found
```

making the report easier to understand.

---

## Redirecting Output

Originally I redirected every individual command.

Example:

```bash
echo >> sum.txt
echo "$level" >> sum.txt
...
```

Later I learned a cleaner approach.

```bash
{
    ...
} > sum.txt
```

Reasoning:

Redirecting once is cleaner than repeating `>> sum.txt` after every command.

The function now focuses only on generating output while the caller decides where that output should go.

This separates logic from presentation.

---

# Mistakes I Made

## Mistake 1

I originally attempted to use:

```bash
for i in {ERROR , WARNING, INFO}
```

Problem:

Brace expansion does not work this way.

Fix:

```bash
for i in ERROR WARNING INFO
```

Reasoning:

A normal list is the correct syntax for iterating over words.

---

## Mistake 2

I attempted to call the function like:

```bash
$summarize_level
```

Problem:

Functions are not variables.

Fix:

```bash
summarize_level "$i"
```

Reasoning:

Functions are called directly by their name.

---

## Mistake 3

I hardcoded:

```
No Errors
```

inside the function.

Problem:

The function also processes WARNING and INFO.

Fix:

```bash
echo "No $level found"
```

Reasoning:

The function became reusable for every severity level.

---

## Mistake 4

I initially redirected inside the function.

Later I changed the design to:

```bash
{
    ...
} > sum.txt
```

Reasoning:

Keeping redirection outside the function makes the function reusable.

It can now print to:

- terminal
- file
- another command through a pipe

without changing its implementation.

---

## Mistake 5

I was unsure whether the report should be printed to the terminal or saved to a file.

Decision:

Generate a report file.

Reasoning:

A summary report is usually stored for later inspection or sharing.

---

## Mistake 6

While pushing to GitHub, authentication repeatedly failed.

Error:

```
Invalid username or token
Password authentication is not supported
```

Reasoning:

The repository remote was configured using HTTPS.

GitHub no longer accepts account passwords for Git operations over HTTPS.

Fix:

Changed the remote from HTTPS to SSH.

Example:

```bash
git remote set-url origin git@github.com:RaghavN6666/Intelligent-Log-Summarizer.git
```

Result:

Git used my existing SSH key and authentication worked without asking for a username or password.

---

# Additional Concepts Learned

## Why use `ps --sort` instead of `| sort`

I originally assumed every command should be piped into `sort`.

Later I learned:

If a command already understands its own data structure, it usually provides its own sorting mechanism.

Example:

```bash
ps --sort=-%cpu
```

Reasoning:

The command already knows which column represents CPU usage.

This is cleaner and more reliable than sorting plain text afterward.

---

## Understanding `top` vs `ps`

I compared both tools.

My analogy:

- `ps` is a photograph.
- `top` is a video.

Reasoning:

Every execution of `ps` creates a new snapshot.

Running `ps` repeatedly creates a sequence of snapshots.

`top` continuously refreshes the display using new snapshots internally, producing a live view.

This helped me understand why `ps` is better for scripting while `top` is better for interactive monitoring.

---

## Designing Instead of Memorizing

While discussing Process Monitor I began thinking about:

- rotating logs
- circular buffers
- repeated snapshots

instead of simply asking which command to use.

This showed a shift from memorizing commands toward designing monitoring tools.

---

# Overall Workflow

```
Validate input
        │
        ▼
Read log file
        │
        ▼
Filter by severity
        │
        ▼
Remove severity label
        │
        ▼
Sort identical messages
        │
        ▼
Count duplicates
        │
        ▼
Sort by frequency
        │
        ▼
Generate formatted report
```

---

# Reflection

This project helped me improve my understanding of Bash scripting by emphasizing reusable functions, Unix pipelines, and clean script design rather than simply writing working code.

The biggest improvement today was learning to separate **processing logic** from **output redirection**, making the script more modular and reusable.

I also strengthened my understanding of Git authentication by identifying that the issue was not with Git itself but with using an HTTPS remote instead of SSH.