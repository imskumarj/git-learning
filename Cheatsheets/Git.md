# Git & GitHub Cheatsheet

# 🚀 Git & GitHub Cheatsheet

> Your complete reference for Git version control and GitHub collaboration — organized for quick navigation!
> 

---

## 🎯 Understanding Git & GitHub

### What is Git?

Git is a **distributed version control system** that tracks changes in your code over time.

**Key Benefits:**

- 📸 Save snapshots of your project at different points
- ⏮️ Revert to previous versions if something breaks
- 🤝 Collaborate without overwriting each other's work
- 🌿 Work on multiple features simultaneously using branches
- 💼 Industry standard for professional development

### What is GitHub?

GitHub is a **cloud-based hosting service** for Git repositories.

**What GitHub Provides:**

- ☁️ Remote storage for your Git projects
- 👥 Collaboration tools (pull requests, issues, code reviews)
- 📊 Project visibility and portfolio building
- 🔄 CI/CD integration and deployment platforms

---

## ⚙️ Initial Setup (One-Time)

**Configure Your Identity**

```bash
# Set your name (appears in commit history)
git config --global [user.name](http://user.name) "Your Name"

# Set your email (appears in commit history)
git config --global [user.email](http://user.email) "[your.email@example.com](mailto:your.email@example.com)"

# Verify your configuration
git config --list
```

💡 These commands set your identity for all Git commits on your machine.

---

## 🚀 Getting Started

### Starting a New Repository

```bash
# Create a new directory
mkdir my-first-repo

# Navigate into it
cd my-first-repo

# Initialize Git (creates hidden .git folder)
git init
```

### Cloning an Existing Repository

```bash
# Clone a repository from GitHub
git clone https://github.com/username/repo-name.git

# Navigate into the cloned directory
cd repo-name
```

💡 Cloning creates a local copy with Git already initialized.

---

## 📁 The Basic Git Workflow

### The Git Workflow Triangle

**Working Directory** → `git add` → **Staging Area** → `git commit` → **Local Repository** → `git push` → **GitHub**

---

### 1. Check Status

```bash
git status
```

💡 Shows which files have been modified, added, or deleted. **Use this often!**

---

### 2. Stage Changes (Prepare for Commit)

```bash
# Stage a specific file
git add [README.md](http://README.md)

# Stage all changes in current directory
git add .

# Stage all files of a certain type
git add *.js

# Stage multiple specific files
git add file1.txt file2.txt file3.txt
```

💡 **Staging Area:** A holding area where you prepare files before committing. Think of it as selecting items before checkout at a store.

---

### 3. Commit Changes (Save Snapshot)

```bash
# Commit with message
git commit -m "Add user authentication feature"

# Commit all tracked changes (skips staging)
git commit -am "Update existing files"
```

**Commit Message Best Practices:**

- ✅ Use present tense: "Add feature" not "Added feature"
- ✅ Be descriptive but concise
- ✅ Explain *what* and *why*, not *how*

**Examples:**

- ✅ "Add user authentication feature"
- ✅ "Fix login button alignment issue"
- ✅ "Update documentation for API endpoints"
- ❌ "Update code" (too vague)
- ❌ "Fix bug" (not specific enough)

---

### 4. View History

```bash
# See all commits with full details
git log

# Compact one-line view
git log --oneline

# See last 5 commits
git log -5

# See commits with file changes
git log --stat

# Visual graph of branches
git log --graph --oneline --all
```

---

## 🔄 Undoing Changes

### Unstage Files (Remove from Staging Area)

```bash
# Unstage a specific file (keeps changes in working directory)
git reset HEAD filename.txt

# Unstage all files
git reset HEAD .
```

### Discard Changes in Working Directory

```bash
# Discard changes to a specific file
# ⚠️ CAREFUL - can't undo!
git checkout -- filename.txt

# Discard all changes (restore to last commit)
git checkout -- .
```

### Undo Commits

```bash
# Remove last commit but KEEP changes (soft reset)
git reset --soft HEAD~1

# Remove last commit and DISCARD changes (hard reset)
# ⚠️ VERY DANGEROUS - can't undo!
git reset --hard HEAD~1

# Create new commit that undoes previous commit (safe!)
git revert HEAD
```

---

## 💾 Stashing (Temporary Storage)

Use stash when you need to switch context but aren't ready to commit:

```bash
# Save changes temporarily
git stash

# Save with a descriptive message
git stash save "Work in progress on login feature"

# List all stashes
git stash list

# View stash contents
git stash show

# Bring back most recent stash (and remove from stash list)
git stash pop

# Apply stash without removing it
git stash apply

# Apply a specific stash
git stash apply stash@{2}

# Clear all stashes
git stash clear

# Drop a specific stash
git stash drop stash@{0}
```

---

## 🌐 Connecting to GitHub

### Step 1: Create Repository on GitHub

1. Go to [**github.com**](http://github.com) and sign in
2. Click **+** icon → **New repository**
3. Enter repository name (e.g., "my-first-repo")
4. Choose **Public** or **Private**
5. Don't initialize with README if you already have one locally
6. Click **Create repository**

### Step 2: Connect Local Repo to GitHub

```bash
# Add remote connection
git remote add origin https://github.com/username/repo-name.git

# Verify remote was added
git remote -v

# View remote details
git remote show origin
```

💡 **origin:** The default name for your remote repository (convention, but you can use any name).

### Step 3: Push Code to GitHub

```bash
# Push to main branch for the first time (sets upstream)
git push -u origin main

# After first push, simply use
git push

# Push a specific branch
git push origin branch-name

# Push all branches
git push --all
```

💡 **-u flag:** Sets "origin main" as the default upstream, so future pushes only need `git push`.

### Pulling Changes from GitHub

```bash
# Pull latest changes from remote
git pull origin main

# After setting upstream, simply use
git pull

# Fetch changes without merging
git fetch origin
```

---

## 🌿 Branching

### Understanding Branches

A branch is an **independent line of development**. Think of it as a parallel universe where you can experiment without affecting the main codebase.

**Common Branch Types:**

- **main/master:** The stable, production-ready branch
- **feature branches:** Where you develop new features
- **bugfix branches:** Where you fix issues
- **hotfix branches:** For urgent production fixes

---

### Creating & Switching Branches

```bash
# List all local branches (* shows current branch)
git branch

# List all remote branches
git branch -r

# List both local and remote branches
git branch -a

# Create a new branch
git branch feature-login

# Switch to a branch
git checkout feature-login

# Create AND switch to new branch (one command!)
git checkout -b feature-login

# Modern way to switch branches
git switch main

# Modern way to create & switch
git switch -c feature-login
```

💡 **Pro Tip:** Use `git checkout -b` or `git switch -c` to save time!

---

### Working with Remote Branches

```bash
# Push your branch to GitHub (first time)
git push -u origin feature-branch

# Push subsequent changes
git push

# Get latest changes from remote branch
git pull origin feature-branch

# Track a remote branch locally
git checkout --track origin/feature-branch

# Fetch all remote branches
git fetch --all
```

---

### Deleting Branches

```bash
# Delete local branch (safe - only if merged)
git branch -d feature-name

# Force delete local branch (even if not merged)
git branch -D feature-name

# Delete remote branch from GitHub
git push origin --delete feature-name
```

⚠️ **Important:** Always delete feature branches after merging to keep your repository clean!

---

### Branch Naming Conventions

Use clear, descriptive names:

| Type | Format | Example |
| --- | --- | --- |
| Feature | `feature/description` | `feature/user-login` |
| Bug Fix | `fix/description` | `fix/login-button-error` |
| Hotfix | `hotfix/description` | `hotfix/security-patch` |
| Experiment | `experiment/description` | `experiment/new-ui-design` |
| Documentation | `docs/description` | `docs/api-readme` |

---

## 🔀 Merging Branches

### Understanding Merging

Merging combines changes from one branch into another. It's how you integrate your feature work back into the main codebase.

**Types of Merges:**

- **Fast-Forward Merge:** When there are no new commits on target branch — Git simply moves the pointer forward
- **Three-Way Merge:** When both branches have new commits — Git creates a new "merge commit"
- **Squash Merge:** Combines all commits from a branch into one commit (keeps history clean)

---

### Basic Merge Commands

```bash
# Step 1: Switch to the branch you want to merge INTO (usually main)
git checkout main

# Step 2: Pull latest changes to avoid conflicts
git pull origin main

# Step 3: Merge your feature branch
git merge feature-branch

# Step 4: Push the merged changes
git push origin main
```

✅ **Best Practice:** Always pull the latest changes before merging to avoid conflicts!

---

### Syncing Feature Branch with Main

Keep your feature branch up to date:

```bash
# While on your feature branch
git checkout feature-branch

# Pull main into your feature branch
git pull origin main

# Resolve any conflicts if they occur

# Push updated feature branch
git push
```

---

## 🔀 Pull Requests (PRs)

### What is a Pull Request?

A Pull Request is a **request to merge your branch into another branch** (usually main). It's GitHub's way of enabling code review and collaboration.

**Why Use Pull Requests?**

- 👀 **Code Review:** Team members can review your changes before merging
- 💬 **Discussion:** Comment on specific lines of code
- ✅ **Quality Control:** Ensure code meets standards before going live
- 📝 **Documentation:** PRs create a history of why changes were made
- 🤖 **CI/CD Integration:** Automated tests can run before merging

---

### Pull Request Workflow (Step by Step)

**Step 1: Create a Feature Branch**

```bash
git checkout -b feature-user-authentication
```

**Step 2: Make Changes & Commit**

```bash
# Make your changes to files
git add .
git commit -m "Add user authentication feature"
```

**Step 3: Push Branch to GitHub**

```bash
# First time pushing this branch
git push -u origin feature-user-authentication

# Subsequent pushes
git push
```

**Step 4: Create Pull Request on GitHub**

1. Go to your repository on GitHub
2. Click **"Pull requests"** tab
3. Click green **"New pull request"** button
4. Select base branch (usually `main`) and compare branch (your feature branch)
5. Click **"Create pull request"**
6. Add a descriptive **title** and **description**
7. Click **"Create pull request"** again

**Step 5: Review the PR**

- Check the **"Files changed"** tab
- Review each change carefully
- Add comments if needed (even to your own PR)
- Check for any merge conflicts
- Verify all automated checks pass (if configured)

**Step 6: Merge the Pull Request**

1. Click green **"Merge pull request"** button
2. Choose merge type (usually "Create a merge commit")
3. Click **"Confirm merge"**
4. GitHub will show "Pull request successfully merged"

**Step 7: Delete the Branch**

- GitHub shows **"Delete branch"** button after merge — click it
- Or use command line:

```bash
# Delete local branch
git checkout main
git branch -d feature-user-authentication

# Delete remote branch
git push origin --delete feature-user-authentication
```

**Step 8: Update Your Local Main**

```bash
# Switch to main and pull latest
git checkout main
git pull origin main
```

---

### Good PR Practices

- ✅ **Write clear titles:** "Add user authentication" not "Fix stuff"
- ✅ **Detailed descriptions:** Explain what changed and why
- ✅ **Small PRs:** Easier to review (aim for <400 lines changed)
- ✅ **Link issues:** Reference related issues with `#issue-number`
- ✅ **Add screenshots:** For UI changes, include before/after images
- ✅ **Self-review first:** Review your own changes before requesting review
- ✅ **Respond to feedback:** Address all review comments promptly

---

## ⚠️ Merge Conflicts

### What is a Merge Conflict?

A conflict occurs when Git can't automatically merge changes because **two branches modified the same lines of code differently**.

**When Do Conflicts Happen?**

- Two people edit the same line in a file
- One person deletes a file while another modifies it
- Changes to the same section of code in different branches

---

### Identifying a Conflict

```bash
# Git will show something like this:
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

---

### What a Conflict Looks Like

```html
<<<<<<< HEAD
<h1>Welcome to My Website</h1>
=======
<h1>Welcome to Our Amazing Site</h1>
>>>>>>> feature-branch
```

- `<<<<<<< HEAD` — Your current branch's version
- `=======` — Separator
- `>>>>>>> feature-branch` — Incoming branch's version

---

### Resolving Conflicts — 3 Methods

**Method 1: Manual Resolution (Command Line)**

```bash
# 1. Open the conflicted file in your editor
# 2. Choose which version to keep (or combine both)
# 3. Remove the conflict markers (<<<<<<, =======, >>>>>>>)
# 4. Save the file

# 5. Stage the resolved file
git add index.html

# 6. Complete the merge
git commit -m "Resolve merge conflict in index.html"

# 7. Push changes
git push
```

**Method 2: GitHub Web Interface**

1. GitHub will show **"This branch has conflicts"** on your PR
2. Click **"Resolve conflicts"** button
3. Edit the file directly in GitHub's editor
4. Remove conflict markers and choose correct version
5. Click **"Mark as resolved"**
6. Click **"Commit merge"**

**Method 3: Using VS Code**

1. VS Code highlights conflicts with colors
2. Options appear: **"Accept Current Change"** | **"Accept Incoming Change"** | **"Accept Both Changes"**
3. Click your choice
4. Save file, stage, and commit

⚠️ **Golden Rule:** Never commit code with conflict markers still in it! Always test after resolving.

---

### Preventing Conflicts

- 🔄 **Pull often:** Keep your branch updated with main
- 📦 **Small commits:** Easier to resolve if conflicts occur
- 💬 **Communicate:** Let team know what you're working on
- 🔀 **Merge main into feature:** Regularly sync your branch

---

## 📝 Repository Essentials

### [README.md](http://README.md) File

The README is the **front page** of your repository. It should include:

**Essential Sections:**

- **Project Title:** Clear, descriptive name
- **Description:** What the project does and why it exists
- **Installation:** How to set up the project locally
- **Usage:** How to use the project (with examples)
- **Technologies:** Languages, frameworks, tools used
- **Contributing:** Guidelines for contributors (if applicable)
- **License:** Usage rights and restrictions

**Example README Structure:**

```markdown
# My Cloud Journey

## Description
This repository documents my 30-day cloud learning journey, including hands-on projects and notes.

## Technologies
- Git & GitHub
- AWS/Azure/GCP
- Docker & Kubernetes
- Terraform

## Installation
```

git clone https://github.com/username/my-cloud-journey.git

cd my-cloud-journey

```

## Usage
Follow along with daily notes and complete hands-on exercises.

## Progress
- Day 1: Cloud fundamentals
- Day 2: Linux basics
- Day 3: Git & GitHub

## License
MIT License
```

---

### .gitignore File

Tells Git which files/folders to **ignore** and not track.

**Essential for:**

- 🔒 Sensitive information (API keys, passwords, config files)
- 📦 Dependencies (node_modules, virtual environments)
- 🏗️ Build files (dist/, build/, *.log)
- 💻 IDE settings (.vscode/, .idea/)
- 🖥️ Operating system files (.DS_Store, Thumbs.db)

**Example .gitignore:**

```bash
# Dependencies
node_modules/
venv/
__pycache__/

# Environment variables
.env
.env.local
config.json

# Build files
dist/
build/
*.log

# IDE
.vscode/
.idea/
*.swp

# OS files
.DS_Store
Thumbs.db
```

**Create .gitignore:**

```bash
# Create file
touch .gitignore

# Add it to Git
git add .gitignore
git commit -m "Add .gitignore file"
```

💡 Use [gitignore.io](http://gitignore.io) to generate .gitignore files for your stack!

---

## ⚡ Quick Reference

### Essential Commands Cheat Sheet

```bash
# SETUP
git config --global [user.name](http://user.name) "Your Name"
git config --global [user.email](http://user.email) "[your.email@example.com](mailto:your.email@example.com)"

# STARTING
git init                            # Initialize new repo
git clone <url>                     # Clone existing repo

# BASIC WORKFLOW
git status                          # Check status
git add .                           # Stage all changes
git add <file>                      # Stage specific file
git commit -m "message"             # Commit changes
git push                            # Push to remote

# BRANCH BASICS
git branch                          # List branches
git checkout -b new-branch         # Create & switch
git switch main                     # Switch to main
git push -u origin new-branch      # Push new branch
git branch -d branch-name          # Delete local
git push origin --delete branch    # Delete remote

# VIEWING HISTORY
git log                             # View commit history
git log --oneline                   # Compact view
git log --graph --all              # Visual branch graph

# UNDOING CHANGES
git reset HEAD <file>              # Unstage file
git checkout -- <file>             # Discard changes
git reset --soft HEAD~1            # Undo last commit (keep changes)
git reset --hard HEAD~1            # Undo last commit (discard changes)

# MERGING
git checkout main                   # Switch to main
git pull origin main                # Get latest
git merge feature-branch            # Merge feature
git push origin main                # Push merged code

# STASHING
git stash                           # Save changes temporarily
git stash list                      # List all stashes
git stash pop                       # Apply and remove stash
git stash apply                     # Apply stash (keep it)

# REMOTE OPERATIONS
git remote -v                       # List remotes
git fetch origin                    # Fetch changes
git pull origin main                # Pull and merge
git push origin main                # Push to remote

# CONFLICT RESOLUTION
git status                          # Check conflicts
# Edit files to resolve
git add .                           # Stage resolved files
git commit -m "Resolve conflicts"   # Complete merge

# SYNCING FEATURE WITH MAIN
git checkout feature-branch         # Switch to feature
git pull origin main                # Pull main into feature
git push                            # Push updated feature
```

---

## 🎯 Complete Workflow Example

**Scenario:** Adding a new footer to the website

```bash
# 1. Create and switch to new branch
git checkout -b feature-add-footer

# 2. Make your changes (edit files)
# ... edit footer.html ...

# 3. Stage and commit
git add footer.html
git commit -m "Add responsive footer with social links"

# 4. Push to GitHub
git push -u origin feature-add-footer

# 5. Go to GitHub and create Pull Request
# ... create PR in browser ...

# 6. Review your changes
# ... check Files Changed tab ...

# 7. Merge the PR on GitHub
# ... click Merge button ...

# 8. Delete remote branch on GitHub
# ... click Delete branch ...

# 9. Switch to main locally
git checkout main

# 10. Pull the merged changes
git pull origin main

# 11. Delete local feature branch
git branch -d feature-add-footer

# Done! 🎉
```

---

## ✅ Best Practices

### Golden Rules

1. ✅ **Commit often** with clear, descriptive messages
2. ✅ **Pull before you push** (when collaborating)
3. ✅ **Use .gitignore** to protect sensitive data
4. ✅ **Write good README files** for every project
5. ✅ **Never commit directly to main** (use branches)
6. ✅ **Delete branches after merging** to keep repo clean
7. ✅ **Review your changes** before committing
8. ✅ **Use meaningful branch names** following conventions
9. ✅ **Pull main frequently** into feature branches to minimize conflicts
10. ✅ **Test after resolving conflicts** before pushing

### Common Mistakes to Avoid

- ❌ Committing without checking `git status` first
- ❌ Writing vague commit messages like "update" or "fix"
- ❌ Forgetting to add .gitignore before first commit
- ❌ Committing sensitive information (API keys, passwords)
- ❌ Using `git reset --hard` without understanding it
- ❌ Working directly on main branch
- ❌ Creating huge PRs (>400 lines changed)
- ❌ Not pulling latest changes before starting work
- ❌ Leaving conflict markers in code
- ❌ Force pushing to shared branches

---

## 🎓 What You've Mastered

✅ Git fundamentals and version control concepts

✅ Basic Git workflow (status → add → commit → push)

✅ Branching and merging strategies

✅ Pull Request workflow and code review

✅ Merge conflict resolution

✅ Remote repository management

✅ Stashing and undoing changes

✅ Repository best practices (.gitignore, README)

**You're now equipped to collaborate like a pro!** 🚀