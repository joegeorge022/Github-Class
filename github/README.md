# GitHub Reference Guide

[← Back](../README.md)

*Complete GitHub guide for students - collaboration and project management*

## 🚀 Getting Started with GitHub

### Creating Your GitHub Account
1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Choose a username (this will be part of your profile URL)
4. Use your real email address
5. Verify your account

### Your First Repository

#### Method 1: Create on GitHub First
1. Click the "+" icon → "New repository"
2. Name your repository
3. Add a description
4. Choose Public or Private
5. Initialize with README
6. Click "Create repository"

#### Method 2: Push Existing Local Project
```bash
# In your project folder
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/username/repo-name.git
git push -u origin main
```

## 📁 Repository Management

### Cloning Repositories
```bash
# Clone a repository
git clone https://github.com/username/repository-name.git

# Clone to specific folder
git clone https://github.com/username/repo.git my-folder
```

### Repository Settings
- **Description**: Add a clear project description
- **Topics**: Add tags to help others find your project
- **README**: Always include a good README.md
- **License**: Choose an appropriate license
- **Visibility**: Public (everyone can see) vs Private (only you and collaborators)

## 🤝 Collaboration Features

### Issues
Track bugs, feature requests, and tasks:

1. **Creating Issues**
   - Click "Issues" tab → "New issue"
   - Use descriptive titles
   - Add labels (bug, enhancement, question)
   - Assign to team members
   - Reference in commits: `git commit -m "Fix login bug, closes #15"`

2. **Issue Templates**
   - Bug reports
   - Feature requests
   - Questions

### Pull Requests (PRs)
Propose changes to a repository:

#### Creating a Pull Request
1. Create a branch: `git checkout -b feature-name`
2. Make changes and commit
3. Push branch: `git push -u origin feature-name`
4. Go to GitHub → "Compare & pull request"
5. Add title and description
6. Request reviewers
7. Submit pull request

#### Pull Request Best Practices
- Clear, descriptive title
- Detailed description of changes
- Link related issues
- Keep changes focused and small
- Add screenshots for UI changes

### Forking
Copy someone else's repository to your account:

1. Click "Fork" button on any repository
2. Clone your fork: `git clone https://github.com/YOUR-USERNAME/REPO-NAME.git`
3. Add upstream remote: `git remote add upstream https://github.com/ORIGINAL-OWNER/REPO-NAME.git`
4. Keep your fork updated:
```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## 👥 Team Collaboration

### Adding Collaborators
1. Go to repository Settings
2. Click "Manage access"
3. Click "Invite a collaborator"
4. Enter username or email
5. Choose permission level

### Branch Protection Rules
Protect your main branch:
1. Settings → Branches
2. Add rule for `main`
3. Enable:
   - Require pull request reviews
   - Require status checks
   - Restrict pushes to main

### Team Workflow
```bash
# 1. Get latest changes
git pull origin main

# 2. Create feature branch
git checkout -b feature/new-feature

# 3. Work and commit
git add .
git commit -m "Add new feature"

# 4. Push and create PR
git push -u origin feature/new-feature
# Then create PR on GitHub

# 5. After PR is merged, clean up
git checkout main
git pull origin main
git branch -d feature/new-feature
```

## 📊 GitHub Features for Projects

### GitHub Pages
Host websites directly from your repository:

1. **Setup**
   - Go to Settings → Pages
   - Choose source: Deploy from branch
   - Select `main` branch
   - Your site: `https://username.github.io/repository-name`

2. **Jekyll Sites** (like this course!)
   - Add `_config.yml` with theme
   - Use markdown files
   - Automatic building and deployment

### GitHub Actions (CI/CD)
Automate workflows:
- Run tests on every push
- Deploy applications
- Check code quality
- Send notifications

Basic workflow file (`.github/workflows/test.yml`):
```yaml
name: Run Tests
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run tests
      run: npm test
```

### Project Boards
Organize work with Kanban boards:
1. Go to "Projects" tab
2. Create new project
3. Add columns (To Do, In Progress, Done)
4. Add cards from issues and PRs
5. Track progress visually

## 🔍 Exploring GitHub

### Discovering Projects
- **Trending**: See popular repositories
- **Topics**: Browse by technology or subject
- **Search**: Use advanced search filters
- **Awesome Lists**: Curated lists of resources

### Following and Starring
- **Star** repositories you find useful
- **Follow** developers whose work interests you
- **Watch** repositories for notifications

### Your GitHub Profile
Make a great first impression:

1. **Profile README**
   - Create repository named your username
   - Add README.md to showcase yourself
   - Include your skills, projects, contact info

2. **Contribution Graph**
   - Shows your daily activity
   - Green squares = commits
   - Consistency matters more than intensity

## 📋 GitHub Commands Cheat Sheet

| Action | Command/Location |
|--------|------------------|
| Clone repository | `git clone <url>` |
| Create issue | Issues tab → New issue |
| Create PR | Compare & pull request |
| Fork repository | Fork button |
| Add collaborator | Settings → Manage access |
| Enable Pages | Settings → Pages |
| Create release | Releases → Create new release |

## 🎯 Practice Exercises

### Exercise 1: Your First Repository
1. Create a new repository on GitHub
2. Clone it locally
3. Add a README.md with your project description
4. Commit and push changes
5. Edit README on GitHub web interface
6. Pull changes to local repository

### Exercise 2: Collaboration Practice
1. Fork a public repository
2. Clone your fork
3. Create a new branch
4. Make a small improvement (fix typo, add comment)
5. Push branch and create pull request
6. Practice the full contribution workflow

### Exercise 3: Issues and Project Management
1. Create issues for features you want to add
2. Use labels to categorize issues
3. Create a project board
4. Move issues through workflow stages
5. Close issues with commit messages

## 🆘 Common GitHub Issues

### "Permission denied (publickey)"
- Check SSH key setup
- Use HTTPS instead: `git remote set-url origin https://github.com/username/repo.git`

### "Repository not found"
- Check repository name and spelling
- Verify you have access to private repositories
- Ensure you're logged in

### "Merge conflicts in pull request"
- Pull latest changes from main branch
- Resolve conflicts locally
- Push resolved changes

### "Can't push to main branch"
- Branch protection rules are enabled
- Create a pull request instead
- Ask repository owner for permissions

## 💡 GitHub Best Practices

### Repository Organization
- Clear, descriptive repository names
- Comprehensive README files
- Proper folder structure
- Include LICENSE file
- Add .gitignore for your language/framework

### Commit Practices
- Atomic commits (one logical change per commit)
- Clear commit messages
- Reference issues in commits
- Use conventional commit format

### Security
- Never commit passwords or API keys
- Use GitHub Secrets for sensitive data
- Enable two-factor authentication
- Review permissions regularly

### Community Guidelines
- Be respectful in issues and PRs
- Provide constructive feedback
- Follow project contribution guidelines
- Help newcomers learn

---

**Previous:** [Git Guide](../git/) | **Back to:** [Course Home](../README.md)
