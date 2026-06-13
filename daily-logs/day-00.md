# Day 0 - Environment Setup & Git Foundations

## Date

2025-06-13

## Time Studied

~3-4 hours (estimate)

---

# Objectives

- Set up a local DevOps learning environment
- Create and organize a GitHub repository
- Configure Git for local development
- Refresh Linux filesystem navigation concepts
- Configure SSH authentication with GitHub
- Complete the first end-to-end Git workflow

---

# Repository Setup

Created GitHub repository:

```text
devops-foundations
```

Repository URL:

```text
https://github.com/RaghavN6666/devops-foundations
```

---

# Technical Notes

## Current Working Directory

### Command

```bash
pwd
```

### Purpose

Displays the current working directory.

### Example

```bash
pwd
```

Output:

```bash
/home/zen
```

### When to Use

Useful whenever you are unsure of your current location in the filesystem.

---

## Listing Files and Directories

### Command

```bash
ls
```

### Purpose

Lists files and directories in the current directory.

### Useful Variants

```bash
ls -a
```

Displays hidden files.

```bash
ls -l
```

Displays detailed file information.

```bash
ls -la
```

Displays hidden files along with detailed information.

### Observation

I noticed that certain files such as `.bashrc` were not visible with a normal `ls` command but appeared when using `ls -la`. This helped reinforce the concept of hidden files in Linux.

---

## Hidden Files

Files beginning with a dot (`.`) are hidden by default.

### Examples

```text
.bashrc
.profile
.cache
```

### Viewing Hidden Files

```bash
ls -la
```

### Why Hidden Files Exist

Many configuration files are hidden to reduce clutter and prevent accidental modification.

---

## Relative Paths

### Current Directory (`.`)

Represents the current working directory.

Example:

```bash
cd .
```

Result:

No directory change occurs because the current directory remains the same.

---

### Parent Directory (`..`)

Represents the parent directory of the current location.

Example:

```bash
cd ..
```

Result:

Moves one level upward in the filesystem hierarchy.

---

## Path Resolution Examples

### Example 1

Starting Directory:

```bash
/home/zen/devops-foundations/linux
```

Command:

```bash
cd ../git
```

Result:

```bash
/home/zen/devops-foundations/git
```

Explanation:

1. Move to the parent directory.
2. Enter the `git` directory.

---

### Example 2

Starting Directory:

```bash
/home/zen/devops-foundations/git
```

Command:

```bash
cd ../../
```

Result:

```bash
/home/zen
```

Explanation:

1. Move from `git` to `devops-foundations`.
2. Move from `devops-foundations` to `zen`.

### Key Takeaway

Relative paths are resolved from the current working directory. Understanding this concept is essential for Linux navigation, scripting, Docker, and automation workflows.

---

# Git Concepts Learned

## Git vs GitHub

### Git

A distributed version control system used to track changes in files and maintain project history.

### GitHub

A cloud-based platform used to host Git repositories and collaborate with other developers.

### Key Difference

Git is the tool.

GitHub is a service built around Git.

---

## Git Workflow

```text
Working Directory
        ↓
git add
        ↓
Staging Area (Index)
        ↓
git commit
        ↓
Local Repository
        ↓
git push
        ↓
Remote Repository (GitHub)
```

### Understanding the Workflow

- `git add` moves changes into the staging area.
- `git commit` creates a snapshot of staged changes.
- `git push` uploads local commits to GitHub.

Although I still need more practice, I now have a basic understanding of how changes move through the Git workflow.

---

## Repository Initialization

Created repository structure:

```text
devops-foundations/
│
├── daily-logs/
├── linux/
├── git/
├── networking/
├── python/
├── docker/
├── aws/
├── terraform/
├── kubernetes/
├── projects/
└── README.md
```

### Purpose

The repository is organized to document learning progress and future projects across multiple DevOps domains.

---

## Git Staging

### Command

```bash
git add .
```

### Purpose

Adds changes from the working directory to the staging area.

### Observation

Initially, I struggled to understand why Git required an additional staging step before committing. This is an area I plan to explore further.

---

## Git Commit

### Command

```bash
git commit -m "Initialize learning repository structure"
```

### Purpose

Creates a snapshot of staged changes in the local repository.

### Observation

A commit does not automatically update GitHub. It only updates the local Git repository.

---

## Git Status

### Command

```bash
git status
```

### Purpose

Displays the current state of the repository.

### Information Displayed

- Untracked files
- Modified files
- Staged files
- Current branch
- Synchronization status with remote repository

### Observation

I found `git status` extremely useful because it provides a quick overview of what Git currently knows about the project.

---

## Git Log

### Command

```bash
git log --oneline --decorate -5
```

### Purpose

Displays recent commit history in a compact format.

### Example Output

```text
82e7a00 Initialize learning repository structure
2603cb Initial commit
```

### Observation

This command helped me see that commits form a history of changes rather than simply storing the latest version of files.

---

# SSH Authentication Setup

## SSH Key Generation

### Command

```bash
ssh-keygen -t ed25519 -C "raghava.nagraj@gmail.com"
```

### Purpose

Generates a public/private key pair for secure authentication.

---

## SSH Verification

### Command

```bash
ssh -T git@github.com
```

### Output

```text
Hi RaghavN6666! You've successfully authenticated,
but GitHub does not provide shell access.
```

### Meaning

- SSH key is valid.
- GitHub recognizes the account.
- Authentication is functioning correctly.
- Git can communicate securely with GitHub.

### Practical Benefit

SSH authentication removes the need to repeatedly enter credentials when interacting with GitHub repositories.

---

# Mistakes Made

## Mistake 1

Attempted to commit before configuring Git identity.

### Error

```text
Author identity unknown
```

### Fix

```bash
git config --global user.name "RaghavN6666"
git config --global user.email "raghava.nagraj@gmail.com"
```

### Lesson Learned

Git requires user identity information to properly attribute commits.

---

## Mistake 2

Attempted GitHub authentication using password-based authentication.

### Error

```text
Password authentication is not supported for Git operations.
```

### Fix

Configured SSH authentication using public/private key pairs.

### Lesson Learned

Modern GitHub workflows commonly use SSH keys instead of passwords.

---

## Mistake 3

Attempted to navigate to:

```bash
~/path/to/devops-foundations
```

without verifying the actual filesystem location.

### Fix

Used:

```bash
pwd
ls
```

to determine the correct location.

### Lesson Learned

Always verify your environment before making assumptions.

---

# Interview Questions

## What is the difference between Git and GitHub?

### Answer

Git is a version control system used to track file changes.

GitHub is a cloud platform used to host and collaborate on Git repositories.

---

## What does `.` represent?

### Answer

The current working directory.

---

## What does `..` represent?

### Answer

The parent directory of the current working directory.

---

## What is the difference between `git status` and `git log`?

### git status

Displays the current state of the repository.

### git log

Displays commit history and previous repository activity.

---

## What is the purpose of the staging area?

### Answer

The staging area allows developers to choose which changes should be included in the next commit before creating a snapshot.

---

# Questions Raised

1. Why does Git require a staging area instead of committing changes directly?
2. How does SSH authentication work internally?
3. What is the difference between HTTPS authentication and SSH authentication?
4. How does Git determine whether a file is modified, staged, or untracked?
5. How are commits linked together internally inside Git?

---

# Personal Reflection

Today's session was more challenging than I initially expected.

At the beginning, Git felt confusing because there seemed to be multiple stages involved before changes actually reached GitHub. I often found myself wondering why Git required separate commands for adding, committing, and pushing changes.

The most valuable lesson from today was realizing that many engineering problems are solved not by memorizing commands, but by carefully reading error messages and understanding the current state of the system.

One of the most interesting moments was setting up SSH authentication. I had previously learned about hashing, authentication, and security concepts in university classes, but seeing a real implementation made those concepts feel much more practical. Seeing the successful authentication message from GitHub felt rewarding because it confirmed that I had correctly configured communication between my machine and a remote service.

I also enjoyed revisiting Linux navigation concepts. Although I had completed part of the Bandit wargame in the past, I realized that I had forgotten more than I expected. Working through path resolution exercises helped refresh those concepts and improved my confidence with filesystem navigation.

By the end of the session, I still did not fully understand Git internals, but I developed a much clearer mental model of how code moves from my local machine to GitHub through staging, committing, and pushing.

Overall, I feel more comfortable with Git and Linux than I did before starting, and I now have a structured environment ready for future learning.

---

# Key Takeaways

- Successfully configured Git and GitHub integration.
- Learned the fundamentals of Linux path navigation.
- Understood relative paths using `.` and `..`.
- Created and organized a DevOps learning repository.
- Configured SSH authentication for GitHub.
- Completed a full Git workflow from staging to pushing.
- Strengthened understanding of filesystem navigation and repository structure.
- Learned the importance of reading and understanding error messages.

---

# Self Assessment

| Skill | Rating |
|---------|---------|
| Linux | 3.5/10 |
| Git | 2/10 |
| Networking | 2/10 |
| Python | 3/10 |
| Docker | 0/10 |
| AWS | 1/10 |
| Terraform | 0/10 |
| Kubernetes | 0/10 |

---

# Next Focus Areas

- Linux fundamentals
- Git fundamentals
- Linux permissions
- Filesystem navigation mastery
- Building a stronger mental model of Git workflows

---

# Day 0 Completion Status

## Completed

- [x] Created GitHub repository
- [x] Configured Git identity
- [x] Generated SSH key
- [x] Added SSH key to GitHub
- [x] Cloned repository locally
- [x] Created project directory structure
- [x] Created first commit
- [x] Successfully pushed to GitHub

## Pending

- [ ] Linux Fundamentals (Phase 1)
- [ ] Git Fundamentals (Phase 1)
- [ ] Bandit Refresher