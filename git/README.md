# Git Reference Guide

[← Back](../README.md)

*Complete Git guide for students - everything you need to know after class*

## 📥 Download Resources

[📄 Download Git PDF Guide](../files/git.pdf){:target="_blank"} - Comprehensive Git reference for offline study

## 📖 Additional Learning Resources

- [W3Schools Git Tutorial](https://www.w3schools.com/git/){:target="_blank"} - Interactive Git learning
- [Official Git Documentation](https://git-scm.com/doc){:target="_blank"}
- [Atlassian Git Tutorials](https://www.atlassian.com/git/glossary#commands){:target="_blank"}

---

## 🚀 Initial Setup

### git config
A convenient way to set configuration options for your Git installation. You'll typically only need to use this immediately after installing Git on a new development machine.

```bash
# Set your identity (required)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Check your settings
git config --list

# Set default branch name
git config --global init.defaultBranch main
```

---

## 📁 Repository Management

### git init
Initializes a new Git repository. If you want to place a project under revision control, this is the first command you need to learn.

```bash
# Initialize a new repository
git init

# Initialize with specific branch name
git init --initial-branch=main
```

### git clone
Creates a copy of an existing Git repository. Cloning is the most common way for developers to obtain a working copy of a central repository.

```bash
# Clone a repository
git clone https://github.com/username/repository-name.git

# Clone to specific folder
git clone https://github.com/username/repo.git my-folder

# Clone specific branch
git clone -b branch-name https://github.com/username/repo.git
```

### git status
Displays the state of the working directory and the staged snapshot. You'll want to run this in conjunction with git add and git commit to see exactly what's being included in the next snapshot.

```bash
# Check repository status
git status

# Short format status
git status -s
```

---

## 💾 Saving Changes

### git add
Moves changes from the working directory to the staging area. This gives you the opportunity to prepare a snapshot before committing it to the official history.

```bash
# Add specific file
git add filename.txt

# Add all changes
git add .

# Add all JavaScript files
git add *.js

# Add files interactively
git add -i
```

### git commit
Takes the staged snapshot and commits it to the project history. Combined with git add, this defines the basic workflow for all Git users.

```bash
# Commit with message
git commit -m "Your commit message"

# Add and commit in one step
git commit -am "Your message"

# Commit with detailed message
git commit -m "Brief description" -m "Detailed explanation"
```

### git commit --amend
Passing the --amend flag to git commit lets you amend the most recent commit. This is very useful when you forget to stage a file or omit important information from the commit message.

```bash
# Amend last commit message
git commit --amend -m "New commit message"

# Amend last commit with new files
git add forgotten-file.txt
git commit --amend --no-edit
```

---

## 🌳 Branch Management

### git branch
This command is your general-purpose branch administration tool. It lets you create isolated development environments within a single repository.

```bash
# List all local branches
git branch

# List all branches (local and remote)
git branch -a

# Create new branch
git branch feature-name

# Delete branch
git branch -d feature-name

# Force delete branch
git branch -D feature-name
```

### git checkout
In addition to checking out old commits and old file revisions, git checkout is also the means to navigate existing branches. Combined with the basic Git commands, it's a way to work on a particular line of development.

```bash
# Switch to existing branch
git checkout branch-name

# Create and switch to new branch
git checkout -b feature-name

# Switch to previous branch
git checkout -

# Checkout specific commit
git checkout commit-hash
```

### git merge
A powerful way to integrate changes from divergent branches. After forking the project history with git branch, git merge lets you put it back together again.

```bash
# Merge branch into current branch
git merge feature-branch

# Merge with no fast-forward
git merge --no-ff feature-branch

# Abort merge in case of conflicts
git merge --abort
```

---

## 🔄 Remote Repository Operations

### git remote
A convenient tool for administering remote connections. Instead of passing the full URL to the fetch, pull, and push commands, it lets you use a more meaningful shortcut.

```bash
# Add remote repository
git remote add origin https://github.com/username/repo.git

# List remotes
git remote -v

# Remove remote
git remote remove origin

# Rename remote
git remote rename origin upstream
```

### git fetch
Fetching downloads a branch from another repository, along with all of its associated commits and files. But, it doesn't try to integrate anything into your local repository. This gives you a chance to inspect changes before merging them with your project.

```bash
# Fetch from origin
git fetch origin

# Fetch all remotes
git fetch --all

# Fetch specific branch
git fetch origin branch-name
```

### git pull
Pulling is the automated version of git fetch. It downloads a branch from a remote repository, then immediately merges it into the current branch. This is the Git equivalent of svn update.

```bash
# Pull from origin main
git pull origin main

# Pull and rebase
git pull --rebase origin main

# Pull all branches
git pull --all
```

### git push
Pushing is the opposite of fetching (with a few caveats). It lets you move a local branch to another repository, which serves as a convenient way to publish contributions.

```bash
# Push to origin main
git push origin main

# Push new branch and set upstream
git push -u origin feature-branch

# Push all branches
git push --all origin

# Force push (use with caution)
git push --force origin branch-name
```

---

## 📊 Inspecting Repository

### git log
Lets you explore the previous revisions of a project. It provides several formatting options for displaying committed snapshots.

```bash
# Show commit history
git log

# Compact one-line format
git log --oneline

# Show last 5 commits
git log -5

# Show commits with file changes
git log --stat

# Show commits in graph format
git log --graph --oneline --all
```

---

## ⚠️ Undoing Changes

### git reset
Undoes changes to files in the working directory. Resetting lets you clean up or completely remove changes that have not been pushed to a public repository.

```bash
# Unstage file (keep changes)
git reset filename.txt

# Reset to previous commit (keep changes)
git reset --soft HEAD~1

# Reset to previous commit (discard changes)
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard commit-hash
```

### git revert
Undoes a committed snapshot. When you discover a faulty commit, reverting is a safe and easy way to completely remove it from the code base.

```bash
# Revert specific commit
git revert commit-hash

# Revert without creating commit
git revert --no-commit commit-hash

# Revert merge commit
git revert -m 1 merge-commit-hash
```

### git clean
Removes untracked files from the working directory. This is the logical counterpart to git reset, which (typically) only operates on tracked files.

```bash
# Show what would be removed
git clean -n

# Remove untracked files
git clean -f

# Remove untracked files and directories
git clean -fd

# Interactive clean
git clean -i
```

---

## 🔧 Advanced Commands

### git rebase
Rebasing lets you move branches around, which helps you avoid unnecessary merge commits. The resulting linear history is often much easier to understand and explore.

```bash
# Rebase current branch onto main
git rebase main

# Interactive rebase
git rebase -i HEAD~3

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort
```

### git reflog
Git keeps track of updates to the tip of branches using a mechanism called reflog. This allows you to go back to changesets even though they are not referenced by any branch or tag.

```bash
# Show reflog
git reflog

# Show reflog for specific branch
git reflog branch-name

# Reset to reflog entry
git reset --hard HEAD@{2}
```

---

## 📋 Essential Commands Quick Reference

| Command | Purpose |
|---------|---------|
| `git init` | Initialize repository |
| `git clone <url>` | Copy remote repository |
| `git status` | Check working directory status |
| `git add <file>` | Stage changes |
| `git commit -m "msg"` | Commit changes |
| `git push` | Upload to remote |
| `git pull` | Download from remote |
| `git branch` | List/create branches |
| `git checkout <branch>` | Switch branches |
| `git merge <branch>` | Merge branches |
| `git log` | View commit history |

---

## 🎯 Practice Exercises

### Exercise 1: Basic Workflow
```bash
git init
echo "Hello Git!" > hello.txt
git add hello.txt
git commit -m "Add hello file"
git log --oneline
```

### Exercise 2: Branching Practice
```bash
git checkout -b feature-branch
echo "New feature" > feature.txt
git add feature.txt
git commit -m "Add feature"
git checkout main
git merge feature-branch
git branch -d feature-branch
```

### Exercise 3: Remote Repository
```bash
git remote add origin https://github.com/username/repo.git
git push -u origin main
git pull origin main
```

---

## 🆘 Common Issues & Solutions

### "Nothing to commit, working tree clean"
- No changes have been made
- All changes are already committed

### "Please tell me who you are"
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### "Repository not found"
- Check URL spelling
- Verify repository access permissions
- Ensure you're authenticated

### Merge Conflicts
1. Edit conflicted files
2. Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
3. `git add resolved-file.txt`
4. `git commit -m "Resolve merge conflict"`

---

**Next:** [GitHub Guide](../github/) | **Back to:** [Course Home](../README.md)
