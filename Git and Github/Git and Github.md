# Git & GitHub Part 1 🚀

## 1. What is Git?

```
Git
↓
Version Control System

Tracks changes in code
Stores project history
Allows collaboration
```

---

## 2. Git Project Structure

```
Working Directory
↓
Files you edit

Staging Area
↓
Files ready to commit

Repository
↓
Permanent history
```

---

## 3. Basic Git Workflow

```
Edit File
↓
git add
↓
Staging Area
↓
git commit
↓
Repository
↓
git push
↓
GitHub
```

---

## 4. Important Commands

### Initialize Repository

```bash
git init
```

Creates a Git repository.

---

### Check Status

```bash
git status
```

Shows:

```
Modified files
Staged files
Untracked files
```

---

### Add Files

Single file:

```bash
git add file.js
```

Multiple files:

```bash
git add file1.js file2.js
```

Everything:

```bash
git add .
```

---

### View Changes

```bash
git diff
```

Shows changes not yet staged.

---

### Commit

```bash
git commit -m "Add login page"
```

Rules:

```
Present tense
Short
Descriptive
```

Examples:

```
Add login page
Fix navbar bug
Create message generator
```

---

### View History

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

### Show Current Commit

```bash
git show HEAD
```

Shows:

```
Commit info
+
Actual file changes
```

---

# Git Backtracking ⏪

## HEAD

```
HEAD
↓
Current commit
```

Usually latest commit.

---

## Discard File Changes

```bash
git checkout HEAD file.js
```

```
Deletes changes
Restores last commit version
```

---

## Unstage File

```bash
git reset HEAD file.js
```

```
Keeps changes
Removes from staging area
```

---

## Go Back to Old Commit

```bash
git reset <SHA>
```

Example:

```bash
git reset 5d69206
```

```
Moves HEAD
Back to old commit
```

---

# Useful Commands

## Temporary Save Work

```bash
git stash
```

Restore:

```bash
git stash pop
```

---

## Edit Last Commit

```bash
git commit --amend
```

Keep message:

```bash
git commit --amend --no-edit
```

---

## Git Aliases

Example:

```bash
git config --global alias.co "checkout"
```

Now:

```bash
git co main
```

instead of:

```bash
git checkout main
```

---

# GitHub Flow 🚀

## Branch

```
Independent version of code
```

Examples:

```
main
feature-login
bug-fix-navbar
```

---

## Pull Request (PR)

```
Request to merge code
into another branch
```

Usually:

```
feature branch
↓
main
```

---

## Merge

```
Combine branches
```

Usually:

```
feature branch
↓
main
```

---

# Complete Timeline (What You Actually Do)

## First Time Setup

### 1. Create Repository on GitHub

```
GitHub
↓
New Repository
↓
Create
```

---

### 2. Clone Repository

```bash
git clone <repo-url>
```

Example:

```bash
git clone <https://github.com/username/project.git>
```

---

### 3. Move Into Project

```bash
cd project
```

---

### 4. Create Files

```
script.js
README.md
etc
```

---

### 5. Check Status

```bash
git status
```

---

### 6. Stage Changes

```bash
git add .
```

---

### 7. Commit

```bash
git commit -m "Create message generator"
```

---

### 8. Push

```bash
git push origin master
```

or

```bash
git push origin main
```

---

## If Starting With Local Folder First

### 1. Create Folder

```bash
mkdir Project
cd Project
```

---

### 2. Initialize Git

```bash
git init
```

---

### 3. Add Files

```bash
git add .
```

---

### 4. Commit

```bash
git commit -m "Initial commit"
```

---

### 5. Create GitHub Repository

```
GitHub
↓
New Repository
```

---

### 6. Connect Local Repo

```bash
git remote add origin <repo-url>
```

Example:

```bash
git remote add origin <https://github.com/user/project.git>
```

---

### 7. Push

```bash
git push -u origin master
```

or

```bash
git push -u origin main
```

---

# Git vs GitHub

|Git|GitHub|
|---|---|
|Local tool|Cloud platform|
|Tracks changes|Stores repositories online|
|`git commit`|`git push`|
|Works offline|Requires internet|

---

# 30-Second Revision

```
Create Repo
↓
Clone Repo
↓
Write Code
↓
git status
↓
git add .
↓
git commit -m "message"
↓
git push
↓
GitHub

Undo:
checkout → discard changes
reset HEAD file → unstage
reset SHA → go back

Collaboration:
Branch
↓
Pull Request
↓
Review
↓
Merge
```

### Memory Formula

```
Code
↓
Add
↓
Commit
↓
Push
↓
Pull Request
↓
Merge
```

That's the complete Git + GitHub foundation you've covered so far. 🚀

# Git & GitHub Part 2 🚀

---

# 1. Branch

A branch is an independent version of your project.

```
main
 └── feature-login
```

Create:

```bash
git branch feature-login
```

List branches:

```bash
git branch
```

Current branch has `*`.

---

# 2. Switch Branch

```bash
git checkout feature-login
```

Modern:

```bash
git switch feature-login
```

---

# 3. Create + Switch

```bash
git checkout -b feature-login
```

Modern:

```bash
git switch -c feature-login
```

---

# 4. Commit on Branch

Once switched:

```bash
git add .
git commit -m "Added login page"
```

Commit belongs to the current branch.

---

# 5. Merge Branch

Switch to receiving branch:

```bash
git checkout main
```

Merge:

```bash
git merge feature-login
```

Meaning:

> Merge **feature-login** into **main**.

---

# 6. Fast-Forward Merge

If `main` has no extra commits:

```
Before

main
A──B

feature
A──B──C
```

After:

```
main
A──B──C

feature
A──B──C
```

Git simply moves the branch pointer.

No merge commit is created.

---

# 7. Merge Conflict

Occurs when two branches modify the same lines.

Example:

```
main

Hello World
```

```
feature

Hello Git
```

Git cannot decide which version to keep.

Conflict markers:

```
<<<<<<< HEAD
Hello World
=======
Hello Git
>>>>>>> feature
```

Resolve manually →

```bash
git add .
git commit -m "Resolve merge conflict"
```

---

# 8. Delete Branch

```bash
git branch -d feature-login
```

Deletes merged branch.

---

# 9. Remote Repository

A repository stored outside your computer.

Usually:

```
GitHub
```

---

# 10. Clone Repository

```bash
git clone <repository-url>
```

Example:

```bash
git clone <https://github.com/user/project.git>
```

Creates a complete local copy.

---

# 11. View Remotes

```bash
git remote -v
```

Example:

```
origin <https://github.com/user/project.git> (fetch)
origin <https://github.com/user/project.git> (push)
```

`origin` = default name of remote repository.

---

# 12. Fetch

```bash
git fetch
```

Downloads latest commits.

Does **NOT** update working files.

---

# 13. Merge Remote Changes

```bash
git merge origin/main
```

Merges downloaded remote changes into current local branch.

---

# 14. Pull

```bash
git pull
```

Equivalent to:

```bash
git fetch
git merge origin/main
```

Downloads commits **and** updates working files.

---

# 15. Push

```bash
git push origin feature-login
```

Uploads local branch to GitHub.

---

# 16. Feature Branch Workflow

```
main
├── feature-login
├── feature-payment
└── feature-dashboard
```

Every developer creates their own branch.

---

# 17. Pull Request (PR)

After pushing:

```
feature-login
      │
      ▼
Pull Request
      │
      ▼
main
```

Purpose:

- Code Review
- Discussion
- CI/CD Checks
- Approval
- Merge into `main`

---

# 18. Collaboration Workflow

```
git pull
      ↓
Create Feature Branch
      ↓
Code
      ↓
git add
      ↓
git commit
      ↓
git pull
      ↓
git push origin feature-branch
      ↓
Open Pull Request
      ↓
Review
      ↓
Merge into main
```

---

# 19. `fetch` vs `pull`

|Command|Downloads Commits|Updates Files|
|---|---|---|
|`git fetch`|✅|❌|
|`git pull`|✅|✅|

---

# 20. Local vs Remote

```
Your Computer
(Local Repository)

main
feature-login
```

↓

```
GitHub
(Remote Repository)

main
feature-login
```

---

# 21. Local vs Remote Branch

```
main
```

Your local branch.

```
origin/main
```

Git's local reference to GitHub's `main`.

---

# 22. Common Commands

### Branches

```bash
git branch

git branch feature

git checkout feature

git checkout -b feature

git branch -d feature
```

---

### Collaboration

```bash
git clone <url>

git remote -v

git fetch

git pull

git merge origin/main

git push origin <branch>
```

---

# 23. Mental Model

```
GitHub
   ▲
   │ push
   │
Local Repository
   │
   ▼
Working Directory
```

- **Working Directory** → Files you edit.
- **Local Repository** → Stores commits.
- **GitHub (Remote)** → Shared repository.

---

# 24. Key Takeaways

- A **branch** is an independent line of development.
- **Commits do not belong to branches**; branches point to commits.
- Use **feature branches** instead of working directly on `main`.
- `git fetch` downloads updates without changing your files.
- `git pull` downloads and applies updates.
- Push feature branches, then open a **Pull Request**.
- Merge approved PRs into `main`.
- Delete feature branches after merging.

---

# Git Part 2 Cheatsheet

```bash
# Branches
git branch
git branch <name>
git checkout <name>
git checkout -b <name>
git branch -d <name>

# Collaboration
git clone <url>
git remote -v
git fetch
git merge origin/main
git pull
git push origin <branch>

# Merge Conflict
git add .
git commit -m "Resolve merge conflict"
```