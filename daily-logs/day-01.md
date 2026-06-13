# Day 1 - Linux Command Line Fundamentals

## Date

2025-06-14

## Time Studied

1.5 Hours

---

# Objectives

- Refresh Linux command-line fundamentals
- Revisit filesystem navigation concepts
- Learn and practice essential Linux commands
- Understand command documentation tools
- Build confidence working inside a Linux terminal

---

# Resources Used

## Linux Journey

Completed the entire:

```text
Command Line
```

section, including:

- The Shell
- pwd
- cd
- ls
- touch
- file
- cat
- less
- history
- cp
- mv
- mkdir
- rm
- find
- help
- man
- whatis
- alias
- exit

---

# Technical Notes

## The Shell

The shell acts as an interface between the user and the operating system.

It allows users to:

- Execute commands
- Navigate the filesystem
- Manage files and directories
- Run programs
- Automate tasks through scripting

---

## pwd (Print Working Directory)

### Command

```bash
pwd
```

### Purpose

Displays the absolute path of the current working directory.

### Example

```bash
pwd
```

Output:

```bash
/home/zen
```

### Use Case

Useful when navigating complex directory structures and verifying your current location.

---

## cd (Change Directory)

### Command

```bash
cd
```

### Purpose

Moves between directories.

### Common Examples

```bash
cd ..
```

Move to parent directory.

```bash
cd .
```

Remain in current directory.

```bash
cd ~
```

Move to home directory.

```bash
cd /
```

Move to root directory.

### Key Takeaway

Linux navigation relies heavily on understanding relative and absolute paths.

---

## ls (List Directory Contents)

### Command

```bash
ls
```

### Purpose

Lists files and directories.

### Useful Variants

```bash
ls -a
```

Show hidden files.

```bash
ls -l
```

Show detailed file information.

```bash
ls -la
```

Show hidden files with detailed information.

### Observation

I learned that many Linux commands become significantly more powerful through options and flags rather than the base command alone.

---

## touch

### Command

```bash
touch file.txt
```

### Purpose

Creates an empty file if it does not exist.

### Additional Behavior

If the file already exists, the command updates the file timestamp instead of creating a duplicate.

### Example

```bash
touch notes.txt
touch notes.txt
```

The second command updates metadata rather than creating another file.

---

## file

### Command

```bash
file filename
```

### Purpose

Determines the type of a file.

### Example

```bash
file notes.txt
```

Possible Output:

```text
ASCII text
```

### Use Case

Helpful when dealing with unfamiliar files.

---

## cat

### Command

```bash
cat file.txt
```

### Purpose

Displays the contents of a file directly in the terminal.

### Best Use Cases

- Small files
- Quick file inspection
- Viewing configuration files

### Limitation

Large files become difficult to read because the entire contents are displayed at once.

---

## less

### Command

```bash
less file.txt
```

### Purpose

Allows interactive viewing of file contents.

### Useful Features

```text
Space → Next page
b     → Previous page
/     → Search
n     → Next search result
q     → Quit
```

### Why It Stood Out

This command was new to me.

Compared to `cat`, it provides significantly more control when reading large files.

---

## history

### Command

```bash
history
```

### Purpose

Displays previously executed commands.

### Example

```bash
history
```

Output:

```text
1 pwd
2 ls
3 mkdir test
...
```

### Why It Stood Out

This command was also new to me.

I found it useful because it provides a record of previous actions, which can help when debugging or repeating tasks.

---

## cp (Copy)

### Command

```bash
cp source.txt destination.txt
```

### Purpose

Copies files and directories.

### Key Point

The original file remains unchanged.

---

## mv (Move)

### Command

```bash
mv source.txt destination.txt
```

### Purpose

Moves files and directories.

### Additional Function

Can also rename files.

Example:

```bash
mv notes.txt notes-old.txt
```

---

## mkdir (Make Directory)

### Command

```bash
mkdir project
```

### Purpose

Creates a new directory.

### Meaning

```text
mkdir = Make Directory
```

---

## rm (Remove)

### Command

```bash
rm file.txt
```

### Purpose

Deletes files.

### Important Note

Deleted files are not moved to a recycle bin.

Care should be taken when using this command.

---

## find

### Command

```bash
find .
```

### Purpose

Searches for files and directories.

### Understanding

The `.` represents the current working directory.

Therefore:

```bash
find .
```

means:

```text
Search everything starting from the current directory.
```

### Current Status

This is the command I found most confusing today.

I understand the basic syntax but still need more practice with:

- Search patterns
- Filters
- Practical use cases

This will be revisited later.

---

## help

### Command

```bash
help
```

### Purpose

Displays help information for shell built-in commands.

---

## man

### Command

```bash
man command
```

### Example

```bash
man ls
```

### Purpose

Displays the complete manual page for a command.

### Use Case

Useful for understanding all available options and functionality.

---

## whatis

### Command

```bash
whatis command
```

### Example

```bash
whatis ls
```

### Purpose

Provides a short description of a command.

### Difference From man

- `whatis` = Quick summary
- `man` = Full documentation

---

## alias

### Command

```bash
alias
```

### Purpose

Creates command shortcuts.

### Example

```bash
alias ll='ls -la'
```

This allows:

```bash
ll
```

to execute:

```bash
ls -la
```

---

## exit

### Command

```bash
exit
```

### Purpose

Terminates the current shell session.

---

# Knowledge Assessment

## Questions Successfully Answered

### Difference Between cat and less

- `cat` prints file contents directly.
- `less` provides interactive navigation and search capabilities.

### touch on Existing Files

Running:

```bash
touch existing-file.txt
```

updates timestamps if the file already exists.

### Difference Between cp and mv

- `cp` copies.
- `mv` moves or renames.

### Purpose of history

Displays previously executed commands.

### Difference Between man and whatis

- `man` provides detailed documentation.
- `whatis` provides a short summary.

---

# Mistakes Made

## Mistake 1

Initially interpreted:

```bash
find .
```

as meaning:

```text
Find everything.
```

### Correct Understanding

The `.` specifically refers to the current directory.

The command searches everything beneath that location.

### Lesson Learned

Always understand what arguments mean rather than memorizing command syntax.

---

# Questions Raised

1. Why does Linux provide both `cat` and `less` when both can display file contents?
2. How does the `find` command search files internally?
3. What are the most common real-world uses of the `find` command?
4. What other useful options exist for `find`?

---

# Personal Reflection

Today's session felt like a good refresher rather than learning everything from scratch.

Many commands looked familiar because of my previous experience with Linux and the Bandit wargame, but I realized that I had forgotten a lot of the details and practical usage.

The two commands that stood out the most were:

- `less`
- `history`

I had either never used them before or never paid much attention to their usefulness.

The biggest realization today was that commands are much deeper than their basic syntax. Initially, I viewed commands like `ls`, `find`, and `cat` as single tools, but I now understand that many of their capabilities come from additional options and flags.

The command I am currently least comfortable with is `find`. While I understand the basic syntax, I do not yet have a strong understanding of when and why I would use it in real-world scenarios.

Overall, I feel much more comfortable navigating the Linux filesystem than I did before this session and have started rebuilding knowledge that had faded over time.

---

# Key Takeaways

- Refreshed Linux command-line fundamentals.
- Improved understanding of filesystem navigation.
- Learned the practical difference between `cat` and `less`.
- Learned how `history` can be used to review previous commands.
- Strengthened understanding of Linux documentation tools.
- Identified `find` as an area requiring further practice.
- Realized that command options and flags are often more important than the base command itself.

---

# Self Assessment

| Skill | Rating |
|---------|---------|
| Linux Navigation | 5/10 |
| Linux Commands | 4.5/10 |
| Git | 2/10 |
| Networking | 2/10 |
| Python | 3/10 |

---

# Next Focus Areas

- Linux permissions
- File ownership
- Advanced file searching
- Practical use cases of `find`
- Git fundamentals review

---

# Day 1 Completion Status

## Completed

- [x] Completed Linux Journey Command Line section
- [x] Practiced Linux navigation
- [x] Reviewed file operations
- [x] Learned `less`
- [x] Learned `history`
- [x] Reviewed Linux documentation tools

## Pending

- [ ] Linux permissions
- [ ] File ownership
- [ ] Advanced usage of `find`
- [ ] Git fundamentals reinforcement