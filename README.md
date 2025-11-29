# Git & GitHub: A Complete Guide (Beginner → Advanced)

This README is an immersive guide to Git and GitHub for developers of all levels. It includes essential concepts, step-by-step examples, common workflows, a comprehensive command cheatsheet, and advanced topics — all with copy-paste-ready commands for PowerShell on Windows.

Use this guide as a reference while learning or working with Git and GitHub!

**How to use this file**
- **Beginner:** Start at **Getting Started** and **Basics**.
- **Intermediate:** Read **Branches & Workflows**, **Pull Requests**, and **Remote Collaboration**.
- **Advanced:** Jump to **Advanced Git**, **Repository Maintenance**, and **Automation**.

**Prerequisites**
- **Git:** Install from https://git-scm.com/.
- **GitHub account:** Create one at https://github.com/.
- **(Optional) GitHub CLI (`gh`):** Install from https://cli.github.com/ for GitHub-native commands.

**PowerShell tip:** When a command includes single quotes `'...'`, PowerShell handles them fine. Use double quotes `"..."` if you need interpolation.

**Table of Contents**
- **Getting Started**
- **Basics**
- **Branches & Workflows**
- **Pull Requests & Code Review**
- **Remotes & Collaboration**
- **Advanced Git**
- **Repository Maintenance & Large Repos**
- **GitHub CLI (`gh`)**
- **GitHub Actions (intro)**
- **Cheatsheet: Commands**
- **Troubleshooting & Tips**

**Getting Started**

- Clone an existing repository:

	`git clone https://github.com/<owner>/<repo>.git`

	PowerShell example:

	```powershell
	git clone https://github.com/octocat/Hello-World.git
	cd Hello-World
	```

- Start a new repository locally and push to GitHub:

	```powershell
	mkdir MyProject; cd MyProject
	git init
	New-Item README.md -Value "# MyProject" -ItemType File
	git add README.md
	git commit -m "chore: initial commit"
	# create repo on GitHub (use gh CLI) or create manually and add remote
	gh repo create myusername/MyProject --public --source=. --remote=origin --push
	```

**Basics**

- Check repository status:

	`git status`

- Stage and commit changes:

	```powershell
	git add <file>           # stage file
	git add .                # stage all changes
	git commit -m "message" # commit staged changes
	```

- View history and diffs:

	```powershell
	git log --oneline --graph --decorate
	git show <commit>
	git diff                 # unstaged changes
	git diff --staged        # staged vs HEAD
	```

**Branches & Workflows**

- Create, list, switch, delete branches:

	```powershell
	git branch               # list local branches
	git branch -a            # list local + remote
	git branch feature/x     # create a branch
	git switch feature/x     # switch to branch (Git 2.23+)
	git checkout -b feature/x# create+switch (older style)
	git branch -d feature/x  # delete local branch (if merged)
	git branch -D feature/x  # force delete
	```

- Merge vs Rebase (simple examples):

	Merge (preserves history):

	```powershell
	git switch main
	git merge feature/x
	```

	Rebase (linearizes history):

	```powershell
	git switch feature/x
	git rebase main
	# resolve conflicts if any, then
	git switch main
	git merge feature/x --no-ff
	```

- Common workflows:
	- **GitHub Flow:** main branch always deployable; feature branches → PRs → merge.
	- **Git Flow:** longer-lived branches (`develop`, `release`, `hotfix`) for structured releases.
	- **Trunk-based dev:** short-lived branches, frequent merges to `main`.

**Pull Requests & Code Review**

- Create a PR using the website or `gh` CLI:

	```powershell
	# Push branch then create a PR
	git push -u origin feature/x
	gh pr create --base main --head myusername:feature/x --title "Add X" --body "Description"
	```

- Review & merge PRs:

	Use GitHub UI to comment, request changes, approve, and merge (merge commit / squash / rebase). From CLI:

	```powershell
	gh pr checkout <pr-number>   # checkout PR locally
	gh pr merge <pr-number> --merge   # or --squash, --rebase
	```

**Remotes & Collaboration**

- See configured remotes:

	`git remote -v`

- Add a remote and push:

	```powershell
	git remote add origin https://github.com/<owner>/<repo>.git
	git push -u origin main
	```

- Fetch vs Pull:
	- `git fetch`: downloads refs/objects but doesn't merge.
	- `git pull`: `fetch` + `merge` (or `rebase` with `--rebase`).

**Advanced Git**

- Undo changes:

	```powershell
	git restore <file>                # restore working tree (unstaged)
	git restore --staged <file>       # unstage a file
	git reset --soft <commit>         # move HEAD, keep index
	git reset --mixed <commit>        # move HEAD, reset index
	git reset --hard <commit>         # move HEAD, reset index & working tree (DANGEROUS)
	git revert <commit>               # create a revert commit (safe for published history)
	```

- Reflog (recover lost commits):

	```powershell
	git reflog
	git checkout <reflog-commit-hash>
	```

- Cherry-pick a commit onto current branch:

	`git cherry-pick <commit>`

- Interactive rebase to edit/squash/reorder commits:

	```powershell
	git rebase -i HEAD~5  # edit last 5 commits
	```

- Bisect to find a bad commit:

	```powershell
	git bisect start
	git bisect bad         # current commit is bad
	git bisect good <tag-or-commit>
	# build/test the code; mark 'good' or 'bad' accordingly
	git bisect good        # if good
	git bisect bad         # if bad
	git bisect reset       # finish
	```

- Submodules (embedding another repo):

	```powershell
	git submodule add https://github.com/owner/other-repo.git path/to/sub
	git submodule update --init --recursive
	```

- Hooks (local automation):

	Hooks live in `.git/hooks/`. For example, to add a `pre-commit` hook:

	```powershell
	# create .git/hooks/pre-commit (make executable on non-Windows)
	# use scripts to run linters/tests before commit
	```

**Repository Maintenance & Large Repos**

- Git Large File Storage (LFS):

	```powershell
	git lfs install
	git lfs track "*.psd"
	git add .gitattributes
	git add file.psd
	git commit -m "Add large file"
	```

- Prune unreachable objects and garbage collect:

	`git gc --prune=now --aggressive`

- Split big repositories (monorepo → multi-repo) or use `git filter-repo` to rewrite history.

**GitHub CLI (`gh`)**

- Authenticate:

	`gh auth login`  # Interactive login

- Create a repo locally and push:

	`gh repo create <owner>/<repo> --public --source=. --push`

- Work with issues and PRs:

	```powershell
	gh issue create --title "Bug: X" --body "Steps to reproduce"
	gh pr list --state open
	gh pr view <number> --web   # open PR in browser
	```

- Release management:

	```powershell
	gh release create v1.2.3 ./build.zip --title "v1.2.3" --notes "Release notes"
	```

**GitHub Actions (Intro)**

- Add workflows in `.github/workflows/` to run CI/CD. Minimal example `ci.yml`:

	```yaml
	name: CI
	on: [push, pull_request]
	jobs:
		build:
			runs-on: ubuntu-latest
			steps:
				- uses: actions/checkout@v3
				- name: Set up Node
					uses: actions/setup-node@v4
					with:
						node-version: '18'
				- run: npm ci
				- run: npm test
	```

**Cheatsheet: Commands**

- Repository lifecycle:
	- `git init` : create repo
	- `git clone <url>` : clone remote
	- `git remote add origin <url>` : add remote

- Staging & commits:
	- `git add <file>`
	- `git commit -m "msg"`
	- `git commit --amend` : update last commit

- Branching & merging:
	- `git branch <name>`
	- `git switch <name>`
	- `git merge <branch>`
	- `git rebase <branch>`

- History & debugging:
	- `git log --oneline --graph --decorate --all`
	- `git bisect` / `git reflog` / `git blame <file>`

- Remote ops:
	- `git fetch` / `git pull` / `git push`
	- `git push origin --delete <branch>` : delete remote branch

- Undoing & cleaning:
	- `git restore <file>`
	- `git reset --hard <commit>`
	- `git revert <commit>`

- Advanced:
	- `git submodule` commands
	- `git stash` / `git stash pop`
	- `git filter-repo` (preferred over `filter-branch`)

**Common Examples / Recipes**

- Start fresh feature branch from latest main:

	```powershell
	git switch main
	git pull origin main
	git switch -c feature/x
	```

- Update your feature branch with main (merge):

	```powershell
	git switch feature/x
	git fetch origin
	git merge origin/main
	```

- Update your feature branch with main (rebase):

	```powershell
	git switch feature/x
	git fetch origin
	git rebase origin/main
	# resolve conflicts, then
	git push --force-with-lease
	```

- Stash work-in-progress, switch branch, reapply:

	```powershell
	git stash push -m "WIP: something"
	git switch other-branch
	git stash pop
	```

**Troubleshooting & Tips**

- Recover lost commits: use `git reflog` to find commit hashes.
- Avoid `git push --force` on shared branches; prefer `--force-with-lease`.
- Use `git status --porcelain` in scripts for stable parsing.
- Add helpful `.gitattributes` to normalize line endings, e.g., `* text=auto`.

**Security & Best Practices**

- Keep secrets out of the repo: use environment variables, GitHub Secrets, or secret management.
- Rotate compromised keys and remove secrets using `git filter-repo`.
- Protect important branches in GitHub settings (require PR reviews, CI checks).

**Learning Resources**
- Pro Git book: https://git-scm.com/book/en/v2
- GitHub Docs: https://docs.github.com/
- GitHub CLI docs: https://cli.github.com/manual/

---

If you'd like, I can:
- commit this `README.md` for you and suggest a commit message, or
- generate a small sample repo with example branches and files to practice commands, or
- produce a printable one-page cheatsheet PDF.
