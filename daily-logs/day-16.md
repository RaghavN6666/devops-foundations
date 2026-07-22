# Daily Learning Log

**Date:** 21/07/26

## Topic
Git Branching and Merging

## Objectives
- Understand the purpose of Git branches.
- Learn how to create, switch, and merge branches.
- Understand merge conflicts and how Git handles them.

## Activities Performed
- Reviewed the concept of Git branching and its role in collaborative software development.
- Created and switched between branches using `git switch` and `git checkout`.
- Practiced working on separate branches to simulate feature development.
- Merged a feature branch into the main branch using `git merge`.
- Learned the difference between fast-forward merges and three-way merges.
- Explored how Git maintains commit history after a merge.
- Discussed merge conflicts, why they occur, and the basic steps to resolve them.
- Used Git commands to check repository status and visualize commit history.

## Commands Practiced

```bash
git branch
git branch <branch-name>
git switch <branch-name>
git switch -c <branch-name>
git checkout <branch-name>
git checkout -b <branch-name>
git merge <branch-name>
git status
git log --oneline --graph --all
```

## Key Learning Points
- Git branches allow developers to work on new features independently without affecting the main branch.
- Merging combines changes from one branch into another while preserving project history.
- Git automatically merges compatible changes but requires manual conflict resolution when changes overlap.
- Viewing the commit graph helps understand branch relationships and project history.

## Reflection
Today's session helped me understand how Git branching supports organized and collaborative development. I learned how to create and merge branches confidently and gained a better understanding of how Git manages project history.

## Summary
Completed hands-on practice with Git branching and merging. Learned how to create, switch, and merge branches, understand merge conflicts, and use Git commands to inspect repository status and commit history.