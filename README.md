<div align="center">

<img src="assets/banner.png" width="100%" alt="GitVault Banner"/>

# 🔐 GitVault

### My Git & GitHub Learning Vault

`Git` • `GitHub` • `Version Control` • `Collaboration`

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Status](https://img.shields.io/badge/Status-Learning-7C3AED?style=for-the-badge)

</div>

---

## 🧭 Navigation

- [🎯 About GitVault](#-about-gitvault)
- [📚 What I'm Learning](#-what-im-learning)
- [🧠 Git & GitHub Notes](#-git--github-notes)
- [🛠️ Practice](#️-practice)
- [💡 Key Takeaways](#-key-takeaways)
- [🚀 What's Next](#-whats-next)

---

## 🎯 About GitVault

**GitVault** is my hands-on learning repository for understanding Git and GitHub from the fundamentals to real-world version-control practices.

This repository is not just a collection of commands. It documents my learning, practice, mistakes, fixes, and the Git workflows I build along the way.

> **Learn → Practice → Break → Fix → Commit → Repeat**

---

## 📚 What I'm Learning

| Topic | Focus |
|---|---|
| 🧩 Git Basics | repositories, commits, branches, status, log |
| 🌿 Branching | branch creation, switching, merging |
| 🔄 Remote Workflows | push, pull, fetch, clone |
| 🤝 GitHub | repositories, README, collaboration |
| 🔐 SSH | secure GitHub authentication |
| 🧹 Undo & Recovery | restore, reset, revert |
| 🔀 Collaboration | pull requests, reviews, conflicts |
| ⚙️ GitHub Actions | automation and CI basics |

---

## 🧠 Git & GitHub Notes

### 1. What is Git?

Git is a **distributed version control system** used to track changes in files and source code.

It helps developers:

- track changes
- work with branches
- collaborate with others
- return to previous versions
- maintain a history of project changes

### 2. What is GitHub?

GitHub is a cloud-based platform for hosting Git repositories and collaborating on software projects.

Git and GitHub are **not the same thing**:

- **Git** → version control tool
- **GitHub** → platform for hosting and collaboration

### 3. Git vs GitHub

| Git | GitHub |
|---|---|
| Local version-control tool | Cloud collaboration platform |
| Runs on your computer | Runs on the web |
| Tracks file changes | Hosts Git repositories |
| Works offline | Usually requires internet for remote operations |
| Created for version control | Adds collaboration features |

---

## 🛠️ Practice

### Basic Git Commands

```bash
git init
git status
git add .
git commit -m "message"
git log
git branch
git switch main
git merge <branch-name>
git remote -v
git push origin main
git pull origin main
git fetch origin
```

### What I understand

**`git init`** creates a new Git repository in the current directory.

**`git status`** shows the current state of the working tree, including modified, staged, and untracked files.

**`git add`** moves changes into the staging area.

**`git commit`** records staged changes in Git history.

**`git push`** sends local commits to a remote repository.

**`git pull`** gets remote changes and integrates them into the current branch.

**`git fetch`** downloads information from a remote repository without automatically merging those changes into the current branch.

---

## 🌿 Git Workflow

```text
Working Directory
       │
       ▼
   git add
       │
       ▼
Staging Area
       │
       ▼
 git commit
       │
       ▼
 Local Repository
       │
       ▼
  git push
       │
       ▼
 Remote Repository
```

---

## 💡 Key Takeaways

- Git tracks changes; GitHub hosts and enables collaboration around Git repositories.
- A commit should represent a meaningful change.
- Branches allow work to be isolated from the main development line.
- `git fetch` and `git pull` are different: fetch downloads remote information, while pull also integrates changes.
- Good commit messages make project history easier to understand.
- Git becomes easier when commands are practiced rather than memorized.

---

## 🚀 What's Next

This repository will grow as I continue my Git and DevOps learning journey.

Planned practice areas include:

- [ ] Branching & merging
- [ ] Merge conflicts
- [ ] Git reset / restore / revert
- [ ] Git stash
- [ ] Git tags
- [ ] SSH authentication
- [ ] Pull requests
- [ ] GitHub Actions
- [ ] Real-world Git workflow

---

<div align="center">

### 🔐 GitVault
**Building strong Git fundamentals, one commit at a time.**

</div>
