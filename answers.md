# Git Mini Exo — Answers

## Part 1: Setup & Config

**Verify the git version:**
```bash
git --version
```

**Configure your Git username and email:**
```bash
git config --global user.name "yourusername"
git config --global user.email "youremail@example.com"
```

---

## Part 2: Create Your First Repository

**Create a folder called `my-first-repo`:**
```bash
mkdir my-first-repo
```

**Navigate into that folder:**
```bash
cd my-first-repo
```

**Initialize a Git repository:**
```bash
git init
```

**Create a file called `readme.txt`:**
```bash
touch readme.txt
```

---

## Part 3: Your First Commit

**1. What command shows you the current state of your repository?**
`git status` — it shows which files have been modified, which are staged, and which are untracked.

**2. What command stages `readme.txt` for commit?**
`git add readme.txt` — this moves the file to the staging area, meaning it is ready to be included in the next commit.

**3. What command commits with the message "Add readme file"?**
`git commit -m "Add readme file"` — this saves a snapshot of the staged changes with a descriptive message.

**4. What command shows your commit history?**
`git log` — it displays all previous commits with their hash, author, date, and message.

---

## Part 4: Make Changes

**1. Edit `readme.txt` and add a new line of text:**
```bash
echo "This is my first Git repository." > readme.txt
echo "This line was added later for Part 4" >> readme.txt
```

**2. What does `git status` show now?**
It shows `readme.txt` under "Changes not staged for commit" with the label "modified". This means Git knows the file exists and has tracked it before, but the new changes have not been staged yet.

**3. Stage and commit your changes with an appropriate message:**
```bash
git add readme.txt
git commit -m "Update readme with new line"
```

**4. How many commits do you have now?**
Two. The first one was "Add readme file" and the second one is "Update readme with new line".

---

## Part 5: Exploration

**`git diff`:**
This command shows the exact differences between the current state of your files and the last staged or committed version. Added lines appear in green with a `+`, and removed lines appear in red with a `-`.

**`git log --oneline`:**
This command displays the commit history in a compact format, with each commit on a single line showing its abbreviated hash and commit message. It is useful for getting a quick overview of the project history.

---

## Part 6: Working with Branches

**1. What command lists all branches in your repository?**
`git branch` — the current branch is marked with an asterisk `*`.

**2. What command creates a new branch called `feature-script`?**
`git branch feature-script` — this creates the branch but does not switch to it.

**3. What command switches to the `feature-script` branch?**
`git checkout feature-script`

**4. What single command creates and switches to a new branch called `dev`?**
`git checkout -b dev` — the `-b` flag tells Git to create the branch and switch to it at the same time.

**5. Switch back to the `feature-script` branch:**
`git checkout feature-script`

**6. Verify you are on the correct branch:**
`git branch` — the asterisk `*` should be next to `feature-script`.

---

## Part 7: Create a Bash Script on a Branch

**Script content (`install.sh`):**
```bash
#!/bin/bash
echo "Starting installation..."
sudo apt update
sudo apt install -y curl
echo "Installation complete!"
```

**Make the script executable:**
```bash
chmod +x install.sh
```

**Stage and commit:**
```bash
git add install.sh
git commit -m "Add install script"
```

---

## Part 8: Merge Branches

**1. Switch back to the `main` branch:**
`git checkout main`

**2. Is `install.sh` present? Why or why not?**
No. The file was created and committed on the `feature-script` branch, so it does not exist on `main` until you merge.

**3. What command merges `feature-script` into `main`?**
`git merge feature-script` — this brings all commits from `feature-script` into `main`.

**4. What changed after the merge?**
`install.sh` now appears alongside `readme.txt`. The merge brought over the file from the feature branch.

**5. What do you observe in the commit history?**
All commits from both branches are now visible in the log. The history shows the full timeline of changes across branches.

**6. What command deletes the `feature-script` branch after merging?**
`git branch -d feature-script` — the `-d` flag deletes the branch safely, only if it has already been merged.

---

## Part 9: Push to GitHub

**What command links your local repo to GitHub?**
```bash
git remote add origin https://github.com/yourusername/my-first-repo.git
```
This tells Git where the remote repository is located.

**What command pushes your commits to GitHub?**
```bash
git branch -M main
git push -u origin main
```
The `-u` flag sets the upstream so future pushes can be done with just `git push`.

---

## Part 10: Delete and Clone

**Navigate out of the project folder:**
```bash
cd ..
```

**Delete the local repository folder:**
```bash
rm -rf my-first-repo
```

**Clone your repository from GitHub:**
```bash
git clone https://github.com/yourusername/my-first-repo.git
```

**Verify your files are there:**
```bash
cd my-first-repo
ls
```

---

## Reflection Questions

**1. Why is version control useful?**
It lets you track every change made to your code over time, revert to previous versions if something breaks, and collaborate with others without overwriting each other's work.

**2. What is the difference between staging and committing?**
Staging selects which changes you want to include in the next commit. Committing actually saves those staged changes as a permanent snapshot in the project history.

**3. When should you make a commit?**
Whenever you complete a small, logical unit of work. For example, after adding a new feature, fixing a bug, or updating documentation. Each commit should represent one clear change.

**4. What is the difference between `git init` and `git clone`?**
`git init` creates a brand new empty repository from scratch. `git clone` copies an existing remote repository to your local machine, including all its files and commit history.

**5. Why should you write good commit messages?**
So that you and others can understand what was changed and why, without having to read through the actual code changes. Good messages make it easier to navigate the project history.

**6. What is the purpose of using branches?**
Branches let you work on new features or experiments in isolation, without affecting the stable main codebase. Once the work is done and tested, you can merge it back into main.

**7. When would you create a new branch instead of working on main?**
Whenever you are working on a new feature, a bug fix, or anything experimental. Working on a separate branch keeps the main branch clean and stable while you develop and test your changes.
