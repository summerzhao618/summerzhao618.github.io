# Git: Check Current Branch & PR/Merge Workflow

## Checking the current branch

**See which branch you're on and status:**
```bash
git status
```
Shows "On branch &lt;name&gt;" and whether you're ahead/behind origin.

**List all local branches (current one has `*`):**
```bash
git branch
```

**List all branches including remotes:**
```bash
git branch -a
```

**Show only the current branch name:**
```bash
git branch --show-current
```

## Switch to an existing local branch
```bash
git checkout branch-name
```

```bash
git switch branch-name
```

---

## Process to create a Pull Request and merge into master (origin)

**1. Work on a feature branch (not master):**
```bash
git checkout -b your-branch-name
```
Or switch to an existing branch:
```bash
git checkout your-branch-name
```

**2. Make changes, then commit on that branch:**
```bash
git add .
git commit -m "Your commit message"
```

**3. Push the branch to origin:**
```bash
git push -u origin your-branch-name
```
(Use `-u` the first time to set upstream; after that you can use `git push`.)

**4. Create a Pull Request on GitHub:**
- In the browser: Go to your repo on GitHub → "Compare & pull request" (after the push), or **Pull requests** → **New pull request**.
- Set base branch to **master** (or `origin/master`) and compare branch to **your-branch-name**.
- Add title/description and create the PR.

**5. Merge the PR into master:**
- On GitHub: Open the PR → **Merge pull request** → confirm (and optionally delete the branch).
- Or merge locally then push:
  ```bash
  git checkout master
  git pull origin master
  git merge your-branch-name
  git push origin master
  ```

**Useful checks along the way:**
```bash
git status
git branch -a
git log --oneline -5
```
