# Git Reference Guide

*Complete Git guide for students - everything you need to know after class*

## 🚀 Getting Started

### Initial Setup (One-time only)
```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Check your settings
git config --list
```

## 📁 Repository Basics

### Creating a Repository
```bash
# Initialize a new Git repository
git init

# Clone an existing repository
git clone https://github.com/username/repository-name.git
```

### Checking Status
```bash
# See what's changed
git status

# See changes in detail
git diff
```

## 💾 Saving Changes

### The Basic Workflow
```bash
# 1. Add files to staging area
git add filename.txt          # Add specific file
git add .                     # Add all changes
git add *.js                  # Add all JavaScript files

# 2. Commit your changes
git commit -m "Your commit message"

# 3. Push to remote repository
git push origin main
```

### Useful Commit Tips
```bash
# Add and commit in one step
git commit -am "Your message"

# See your commit history
git log
git log --oneline             # Compact view
```

## 🔄 Working with Remote Repositories

### Connecting to Remote
```bash
# Add a remote repository
git remote add origin https://github.com/username/repo.git

# Check your remotes
git remote -v

# Get latest changes from remote
git pull origin main
```

## 🌳 Git Branching

### What are Branches?
Branches let you work on different features or experiments without affecting your main code. Think of them as parallel universes for your project!

### Basic Branch Commands
```bash
# Create a new branch
git branch feature-name

# Switch to a branch
git checkout feature-name

# Create and switch in one command
git checkout -b feature-name

# Modern way (Git 2.23+)
git switch feature-name
git switch -c feature-name    # Create and switch
```

### Viewing Branches
```bash
# List all local branches
git branch

# List all branches (local and remote)
git branch -a

# See current branch
git branch --show-current
```

### Branch Workflow
```bash
# 1. Create a feature branch
git checkout -b add-login-page

# 2. Make your changes and commit
git add .
git commit -m "Add login page"

# 3. Switch back to main
git checkout main

# 4. Merge your feature
git merge add-login-page

# 5. Delete the feature branch (optional)
git branch -d add-login-page
```

### Pushing Branches to GitHub
```bash
# Push new branch to GitHub
git push -u origin feature-name

# Push updates to existing branch
git push
```

## ⚠️ Handling Merge Conflicts

When Git can't automatically merge:

1. **Git will mark conflicted files:**
```bash
git status    # Shows conflicted files
```

2. **Edit conflicted files** - look for:
```
<<<<<<< HEAD
Your main branch code
=======
Your feature branch code
>>>>>>> feature-branch
```

3. **Resolve and commit:**
```bash
git add resolved-file.txt
git commit -m "Resolve merge conflict"
```

## 📋 Essential Commands Cheat Sheet

| Command | What it does |
|---------|-------------|
| `git init` | Create a new repository |
| `git clone <url>` | Copy a repository from GitHub |
| `git status` | Check what's changed |
| `git add <file>` | Stage changes for commit |
| `git commit -m "message"` | Save changes with a message |
| `git push` | Upload changes to GitHub |
| `git pull` | Download latest changes |
| `git log` | See commit history |
| `git branch` | List branches |
| `git checkout -b name` | Create and switch to branch |
| `git merge name` | Merge branch into current |

## 🎯 Quick Practice Exercises

### Exercise 1: Basic Git Workflow
1. Create a new folder and initialize Git: `git init`
2. Create a file: `echo "Hello Git!" > hello.txt`
3. Check status: `git status`
4. Add the file: `git add hello.txt`
5. Commit: `git commit -m "Add hello file"`
6. Check history: `git log --oneline`

### Exercise 2: Branching Practice
1. Create a feature branch: `git checkout -b my-feature`
2. Create a file: `echo "Feature code" > feature.txt`
3. Commit: `git add . && git commit -m "Add feature"`
4. Switch to main: `git checkout main`
5. Merge: `git merge my-feature`
6. Clean up: `git branch -d my-feature`

## 🆘 Common Issues & Solutions

### "Nothing to commit"
- You haven't made any changes, or
- You forgot to `git add` your files

### "Please tell me who you are"
- Run the initial setup commands above

### "Repository not found"
- Check the URL is correct
- Make sure you have access to the repository

### "Your branch is ahead of origin/main"
- You have local commits not pushed yet
- Run `git push` to sync with GitHub

## 💡 Best Practices

### Commit Messages
- Use present tense: "Add feature" not "Added feature"
- Be descriptive but concise
- Start with a verb: "Fix", "Add", "Update", "Remove"

### Branch Naming
- Use descriptive names: `add-user-authentication`
- Use prefixes: `feature/login`, `bugfix/header-issue`
- Keep it short but clear

### When to Commit
- After completing a logical unit of work
- Before switching branches
- At the end of your work session
- When tests pass

---

**Next:** [GitHub Guide](../github/) | **Back to:** [Course Home](../README.md)
