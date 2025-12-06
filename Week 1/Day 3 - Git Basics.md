# Notes - Day 3

# 📚 Day 3: Git & GitHub Basics - Revision Notes

## 🎯 Core Concepts

### What is Git?

Git is a **distributed version control system** that tracks changes in your code over time. It allows you to:

- Save snapshots of your project at different points in time
- Revert to previous versions if something breaks
- Collaborate with others without overwriting each other's work
- Work on multiple features simultaneously using branches

### What is GitHub?

GitHub is a **cloud-based hosting service** for Git repositories. It provides:

- Remote storage for your Git projects
- Collaboration tools (pull requests, issues, code reviews)
- Project visibility and portfolio building
- Integration with CI/CD tools and deployment platforms

### Why Version Control Matters

- **Safety Net:** Never lose your work - you can always go back to previous versions
- **Collaboration:** Multiple people can work on the same project simultaneously
- **History Tracking:** See who made what changes and when
- **Experimentation:** Try new features without breaking the main codebase
- **Professional Standard:** Essential skill for any developer role

## ⚙️ Essential Git Commands

### Initial Setup (One-time)

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

*These commands set your identity for all Git commits on your machine.*

### Starting a New Repository

```bash
# Create a new directory
mkdir my-first-repo

# Navigate into it
cd my-first-repo

# Initialize Git
git init
```

**What happens:** Git creates a hidden `.git` folder that tracks all changes in this directory.

### The Basic Git Workflow

- **1. Check Status**
    
    ```bash
    git status
    ```
    
    Shows which files have been modified, added, or deleted. Use this often!
    
- **2. Stage Changes (Add to Staging Area)**
    
    ```bash
    # Stage a specific file
    git add README.md
    
    # Stage all changes
    git add .
    
    # Stage all files of a certain type
    git add *.js
    ```
    
    **Staging Area:** A holding area where you prepare files before committing. Think of it as selecting items before checkout at a store.
    
- **3. Commit Changes (Save Snapshot)**
    
    ```bash
    git commit -m "Initial commit"
    ```
    
    **Best practices for commit messages:**
    
    - Use present tense: "Add feature" not "Added feature"
    - Be descriptive but concise
    - Explain *what* and *why*, not *how*
    
    **Examples:**
    
    - ✅ "Add user authentication feature"
    - ✅ "Fix login button alignment issue"
    - ❌ "Update code" (too vague)
- **4. View History**
    
    ```bash
    # See all commits
    git log
    
    # Compact view
    git log --oneline
    ```
    

### Undoing Changes

- **Remove from Staging Area**
    
    ```bash
    # Unstage a file (keeps changes in working directory)
    git reset HEAD filename.txt
    
    # Unstage all files
    git reset HEAD .
    ```
    
- **Discard Changes in Working Directory**
    
    ```bash
    # Discard changes to a specific file (CAREFUL - can't undo!)
    git checkout -- filename.txt
    ```
    
- **Remove Last Commit**
    
    ```bash
    # Remove commit but keep changes
    git reset --soft HEAD~1
    
    # Remove commit and discard changes (CAREFUL!)
    git reset --hard HEAD~1
    ```
    

### Stashing (Temporary Storage)

Use stash when you need to switch context but aren't ready to commit:

```bash
# Save changes temporarily
git stash

# List all stashes
git stash list

# Bring back stashed changes
git stash pop

# Clear all stashes
git stash clear
```

## 🌐 Connecting to GitHub

### Step 1: Create a Repository on GitHub

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon → **New repository**
3. Enter repository name (e.g., "my-first-repo")
4. Choose Public or Private
5. Don't initialize with README (you already have one locally)
6. Click **Create repository**

### Step 2: Connect Local Repo to GitHub

```bash
# Add remote connection
git remote add origin https://github.com/username/my-first-repo.git

# Verify remote was added
git remote -v
```

**origin:** The default name for your remote repository (you can name it anything, but "origin" is convention).

### Step 3: Push Code to GitHub

```bash
# Push to main branch for the first time
git push -u origin main

# After first push, simply use:
git push
```

**-u flag:** Sets "origin main" as the default upstream, so future pushes only need `git push`.

### Working with Existing Projects

```bash
# Clone a repository from GitHub
git clone https://github.com/username/repo-name.git

# This creates a local copy with Git already initialized
```

## 📝 Repository Essentials

### [README.md](http://README.md) File

The README is the **front page** of your repository. It should include:

- **Project Title:** Clear, descriptive name
- **Description:** What the project does and why it exists
- **Installation:** How to set up the project locally
- **Usage:** How to use the project (with examples)
- **Technologies:** Languages, frameworks, tools used
- **Contributing:** Guidelines for contributors (if applicable)
- **License:** Usage rights and restrictions

**Example README structure:**

```markdown
# My Cloud Journey

## Description
This repository documents my 30-day cloud learning journey, including hands-on projects and notes.

## Technologies
- Git & GitHub
- AWS/Azure/GCP
- Docker & Kubernetes
- Terraform

## Progress
- Day 1: Cloud fundamentals
- Day 2: Linux basics
- Day 3: Git & GitHub

## How to Use
Clone this repo to follow along with my learning journey:
```bash
git clone https://github.com/username/my-cloud-journey.git
```

## License
MIT License
```

### .gitignore File

Tells Git which files/folders to **ignore** and not track. Essential for:

- Sensitive information (API keys, passwords, config files)
- Dependencies (node_modules, virtual environments)
- Build files (dist/, build/, *.log)
- IDE settings (.vscode/, .idea/)
- Operating system files (.DS_Store, Thumbs.db)

**Example .gitignore:**

```
# Dependencies
node_modules/
venv/

# Environment variables
.env
config.json

# Build files
dist/
build/
*.log

# IDE
.vscode/
.idea/

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

## 🌿 Branching Basics

### What are Branches?

Branches allow you to **work on different versions** of your project simultaneously:

- **main/master:** The stable, production-ready branch
- **feature branches:** Where you develop new features
- **bug-fix branches:** Where you fix issues

### Basic Branch Commands

```bash
# Create new branch
git branch feature-name

# Switch to branch
git checkout feature-name

# Create and switch in one command
git checkout -b feature-name

# List all branches
git branch

# Merge branch into main
git checkout main
git merge feature-name

# Delete branch after merging
git branch -d feature-name
```

### Why Use Branches?

- **Isolation:** Work on features without affecting the main codebase
- **Collaboration:** Multiple team members work on different features simultaneously
- **Safety:** Test changes before merging into production
- **Organization:** Keep work organized by feature/task

## 🔄 Complete Workflow Example

```bash
# 1. Initialize project
mkdir my-project
cd my-project
git init

# 2. Create first file
echo "# My Project" > README.md

# 3. Check status
git status

# 4. Stage changes
git add README.md

# 5. Commit
git commit -m "Initial commit with README"

# 6. Connect to GitHub
git remote add origin https://github.com/username/my-project.git

# 7. Push to GitHub
git push -u origin main

# 8. Create .gitignore
echo "node_modules/" > .gitignore
git add .gitignore
git commit -m "Add .gitignore file"
git push

# 9. Continue working
# Make changes to files...
git add .
git commit -m "Add new feature"
git push
```

![image.png](attachment:c6510558-ce31-4fb9-ba38-21ae061cf367:image.png)

![image.png](attachment:46af4f8d-0496-4ebd-85a0-f548f90f4a53:image.png)

![image.png](attachment:f48c7ff4-f576-4b20-b2ea-3ec741c942bc:image.png)

![image.png](attachment:a5e80364-fb10-4764-8136-9be4030d9c78:image.png)

![image.png](attachment:301c5a08-bbcd-4d57-9eb6-5c62a37b5e15:image.png)

## ✅ Day 3 Checklist

- [x]  Set up Git config (username and email)
- [x]  Create first repository locally using `git init`
- [x]  Create and stage a [README.md](http://README.md) file
- [x]  Make first commit with meaningful message
- [x]  Create repository on GitHub
- [x]  Connect local repo to GitHub using `git remote add`
- [x]  Push code to GitHub successfully
- [x]  Create and commit a .gitignore file
- [x]  Practice the Git workflow multiple times
- [x]  Document understanding of Git commands

## 🎓 Key Takeaways

<aside>
**The Git Workflow Triangle:**

**Working Directory** → (git add) → **Staging Area** → (git commit) → **Repository** → (git push) → **GitHub**

</aside>

<aside>
**Best Practices:**

- Commit often with clear messages
- Pull before you push (when collaborating)
- Use .gitignore to protect sensitive data
- Write good README files
- Never commit directly to main (use branches)
</aside>

<aside>
**Common Mistakes to Avoid:**

- ❌ Committing without checking `git status` first
- ❌ Writing vague commit messages like "update"
- ❌ Forgetting to add .gitignore before first commit
- ❌ Committing sensitive information (API keys, passwords)
- ❌ Using `git reset --hard` without understanding it
</aside>

## 📚 Additional Resources

- [Kunal Kushwaha Git/GitHub Full Course](https://www.youtube.com/watch?v=apGV9Kg7ics) (1h 12m) - Comprehensive video tutorial
- [GitHub Skills](https://skills.github.com/) - Interactive learning paths
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) - Quick reference guide
- [Learn Git Branching](https://learngitbranching.js.org/) - Visual and interactive Git tutorial