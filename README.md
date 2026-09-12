<div align="center">

<img src="assets/banner.png" width="100%" alt="GitVault Banner"/>

# 🔐 GitVault

### My Git & GitHub Practice Log

`Git` • `GitHub` • `Version Control` • `Collaboration`

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=for-the-badge)

*My own Git & GitHub practice log — exercises, questions, and answers in my own words.*

</div>

---

## 📑 Jump to a Section

[Exercises](#exercises) · [Git Basics](#git-basics) · [Branches](#branches) · [Merge](#merge) · [Rebase & Undo](#rebase--undo) · [References](#references) · [Git Diff](#git-diff) · [Git Internals](#git-internals)

---

## Exercises

| Name | Topic | Objective & Instructions | Solution |
|---|---|---|---|
| My First Commit | Commit | Init a repo, stage a file, make your first commit | *Link once done* |
| Time to Branch | Branch | Create a branch, switch to it, make a commit there | *Link once done* |
| Sync Two Branches | Branch | Bring `devel` up to date with `main` | *Link once done* |
| Force & Fix a Conflict | Merge | Create a conflict on purpose, then resolve it | *Link once done* |
| Undo a Bad Commit | Reset/Revert | Practice both `reset` and `revert`, note the difference | *Link once done* |

---

## Questions

### Git Basics

<details>
<summary>How do you know if a directory is a Git repository?</summary><br><b>

A directory is a Git repository if it contains a `.git` directory. The easiest way to check is:

```bash
git status
```

If Git recognizes the repository, it shows the current branch and working-tree status. You can also check directly with:

```bash
ls -la
```

and look for `.git`.

</b></details>

<details>
<summary>Explain: <code>git directory</code>, <code>working directory</code>, and <code>staging area</code></summary><br><b>

- **Working directory** → the files I am currently editing.
- **Staging area** → changes selected for the next commit using `git add`.
- **Git directory (`.git`)** → Git's internal database containing commits, branches, configuration, objects, and other repository metadata.

Simple flow:

```text
Working Directory → git add → Staging Area → git commit → Git Directory
```

</b></details>

<details>
<summary>What's the difference between <code>git pull</code> and <code>git fetch</code>?</summary><br><b>

`git fetch` downloads the latest remote information but does not merge it into my current branch.

`git pull` normally performs a fetch and then integrates the remote changes into my current branch.

```bash
git fetch origin
git pull origin main
```

</b></details>

<details>
<summary>How do you check if a file is tracked, and start tracking it if not?</summary><br><b>

Use:

```bash
git status
git ls-files
```

If the file is untracked, start tracking it with:

```bash
git add <file>
```

</b></details>

<details>
<summary>What is <code>.gitignore</code> used for?</summary><br><b>

`.gitignore` tells Git which files or directories should not be tracked. It is commonly used for generated files, dependencies, logs, build output, local configuration, and secrets.

Example:

```gitignore
.env
node_modules/
*.log
```

Important: `.gitignore` does not automatically stop tracking a file that is already tracked.

</b></details>

<details>
<summary>How do you see what's changed before committing?</summary><br><b>

```bash
git diff
```

This shows changes in the working directory that are not yet staged.

To see staged changes:

```bash
git diff --staged
```

</b></details>

<details>
<summary>What does <code>git status</code> actually tell you?</summary><br><b>

`git status` shows the state of my working tree and staging area. It can tell me:

- which branch I am on
- which files are untracked
- which files are modified
- which changes are staged
- whether my branch is ahead of or behind its remote-tracking branch
- what Git suggests I do next

</b></details>

<details>
<summary>You created new files. How do you make Git track them?</summary><br><b>

```bash
git add <files>
```

Or to stage all changes in the current directory:

```bash
git add .
```

Then commit them:

```bash
git commit -m "Add new files"
```

</b></details>

---

### Branches

<details>
<summary>What branching strategies have you heard of?</summary><br><b>

Common Git branching strategies include:

- **Git Flow** → uses long-lived branches such as `main` and `develop`, plus feature/release/hotfix branches.
- **GitHub Flow** → simpler workflow based around short-lived branches and pull requests into `main`.
- **Trunk-based development** → developers integrate small changes frequently into a main/trunk branch, usually using short-lived branches or direct commits.

For modern CI/CD teams, GitHub Flow and trunk-based development are commonly used because they encourage small, frequent integrations.

</b></details>

<details>
<summary>True or False: a branch is basically a pointer to the head of a line of commits.</summary><br><b>

**True.** A Git branch is essentially a movable pointer/reference to a commit. When a new commit is made on that branch, the branch pointer moves forward to the new commit.

</b></details>

<details>
<summary>You have <code>main</code> and <code>devel</code>. How do you make sure <code>devel</code> is up to date with <code>main</code>?</summary><br><b>

One simple merge-based approach is:

```bash
git switch main
git pull origin main
git switch devel
git merge main
```

If there are conflicts, resolve them and complete the merge. This makes `devel` contain the latest commits from `main`.

</b></details>

<details>
<summary>What happens behind the scenes when you run <code>git branch &lt;name&gt;</code>?</summary><br><b>

Git creates a new branch reference pointing to the current commit. It does **not** create a second copy of the project files.

For example, if `HEAD` is currently at commit `abc123`, then:

```bash
git branch feature
```

creates `feature` pointing to `abc123`.

</b></details>

<details>
<summary>How does Git know which commit to point a new branch at?</summary><br><b>

By default, a new branch points to the commit currently referenced by `HEAD`.

For example, if `HEAD` points to `main`, Git creates the new branch at the same commit where `main` currently points.

</b></details>

<details>
<summary>What does "unstaged" mean?</summary><br><b>

**Unstaged** means a change exists in the working directory but has not been added to the staging area yet.

You can see these changes with:

```bash
git diff
```

Stage them with:

```bash
git add <file>
```

</b></details>

<details>
<summary>True or False: <code>git checkout some_branch</code> updates <code>.git/HEAD</code> to point at that branch.</summary><br><b>

**True**, when `some_branch` is a local branch. Git moves `HEAD` so that it refers to that branch, and the working tree is updated to match the branch's commit.

Modern Git usually recommends:

```bash
git switch some_branch
```

for switching branches.

</b></details>

---

### Merge

<details>
<summary>You have <code>main</code> and <code>devel</code>. How do you merge <code>devel</code> into <code>main</code>?</summary><br><b>

```bash
git switch main
git pull origin main
git merge devel
git push origin main
```

If a conflict occurs, resolve it before pushing.

</b></details>

<details>
<summary>How do you resolve a merge conflict, step by step?</summary><br><b>

1. Start the merge:

```bash
git merge devel
```

2. Git reports the conflicted files.

3. Open each conflicted file and look for markers such as:

```text
<<<<<<< HEAD
current branch changes
=======
other branch changes
>>>>>>> devel
```

4. Decide which content to keep, or combine both changes.

5. Remove the conflict markers.

6. Stage the resolved file:

```bash
git add <file>
```

7. Finish the merge:

```bash
git commit
```

8. Check the result:

```bash
git status
git log --oneline --graph
```

If I want to cancel the merge instead:

```bash
git merge --abort
```

</b></details>

<details>
<summary>What merge strategies have you come across?</summary><br><b>

Git can use different merge strategies/options depending on the situation. Common concepts include:

- **Fast-forward** → moves the branch pointer forward when no divergent commit exists.
- **Three-way merge** → combines changes from two branches using their common ancestor; this can create a merge commit.
- **ours strategy** → records a merge while keeping the current branch's tree as the result.
- **Recursive** was historically the default strategy for many two-head merges; modern Git uses the `ort` strategy by default for ordinary two-head merges.

</b></details>

<details>
<summary>What is the difference between <code>git reset</code> and <code>git revert</code>?</summary><br><b>

`git reset` moves the current branch pointer to another commit. Depending on the option, it can also change the staging area and working tree. It can rewrite local history.

`git revert` creates a **new commit** that reverses the changes introduced by an earlier commit. It is safer for commits that have already been shared with others.

```bash
git reset --hard HEAD~1
git revert <commit>
```

</b></details>

---

### Rebase & Undo

<details>
<summary>When would you use <code>git rebase</code> instead of merge?</summary><br><b>

I would use rebase when I want to replay my branch commits on top of the latest base branch and keep a cleaner, more linear history.

Example:

```bash
git switch devel
git fetch origin
git rebase origin/main
```

I should avoid rebasing commits that other people are already depending on unless the team explicitly agrees, because rebase rewrites commit history.

</b></details>

<details>
<summary>How do you revert a single file back to a previous commit?</summary><br><b>

A modern Git command is:

```bash
git restore --source=HEAD~1 -- /path/to/file
```

This restores the file in the working tree. If I want the restored version staged as well:

```bash
git restore --source=HEAD~1 --staged --worktree -- /path/to/file
```

The older equivalent often seen in tutorials is:

```bash
git checkout HEAD~1 -- /path/to/file
```

</b></details>

<details>
<summary>How do you squash your last two commits into one?</summary><br><b>

Use interactive rebase:

```bash
git rebase -i HEAD~2
```

In the editor, keep the first commit as `pick` and change the second from `pick` to `squash` (or `fixup`). Then save and follow Git's instructions to finish the rebase.

</b></details>

<details>
<summary>What is the <code>.git</code> directory, and what's inside it?</summary><br><b>

The `.git` directory is Git's internal repository database. It contains information such as:

- `HEAD` → tells Git what `HEAD` currently refers to
- `refs/` → branch and tag references
- `objects/` → Git's stored objects such as commits, trees, and blobs
- `index` → staging area's data
- `config` → repository-specific Git configuration
- `logs/` → reference update history, when reflogs are enabled

It is the part that turns an ordinary directory into a Git repository.

</b></details>

<details>
<summary>How do you remove a remote branch?</summary><br><b>

The modern syntax is:

```bash
git push origin --delete <branch_name>
```

Older syntax also works:

```bash
git push origin :<branch_name>
```

</b></details>

<details>
<summary>How do you discard local file changes before committing?</summary><br><b>

For a tracked file, a modern command is:

```bash
git restore <file_name>
```

To discard all unstaged changes in tracked files:

```bash
git restore .
```

The older command commonly seen is:

```bash
git checkout -- <file_name>
```

Be careful: these commands discard uncommitted working-tree changes.

</b></details>

<details>
<summary>How do you discard your last local commit?</summary><br><b>

If I want to remove the commit but keep its changes staged:

```bash
git reset --soft HEAD~1
```

If I want to remove the commit and keep the changes unstaged:

```bash
git reset HEAD~1
```

If I want to remove the commit **and** discard its changes:

```bash
git reset --hard HEAD~1
```

`--hard` is destructive, so I should use it carefully.

</b></details>

<details>
<summary>True or False: to remove a file from Git but keep it on disk, you use <code>git rm</code>.</summary><br><b>

**False.** `git rm` normally removes the file from both Git's index and the working tree.

To stop tracking the file while keeping it on disk, use:

```bash
git rm --cached <file>
```

</b></details>

---

## References

<details>
<summary>How do you list the current Git references in a repository?</summary><br><b>

A simple command is:

```bash
git show-ref
```

It lists references such as local branches and tags along with the commit IDs they point to.

For a more compact branch/tag view, I can also use:

```bash
git branch -a
git tag
```

</b></details>

---

## Git Diff

<details>
<summary>What does <code>git diff</code> actually compare?</summary><br><b>

Plain `git diff` compares the **working tree** with the **staging area** (index). It shows changes that are not staged yet.

Other useful comparisons include:

```bash
git diff --staged
git diff HEAD
git diff main..devel
```

</b></details>

<details>
<summary>Which Git commands rely on the diff mechanism internally?</summary><br><b>

Several Git commands use Git's diff machinery or expose diff-like comparisons, including:

- `git diff`
- `git show`
- `git log -p`
- `git format-patch`
- `git range-diff`
- `git whatchanged` (legacy)

Commands such as `git status` also determine file changes, but its purpose is broader than simply displaying a diff.

</b></details>

---

## Git Internals

<details>
<summary>Describe how <code>git status</code> works internally.</summary><br><b>

At a high level, Git compares information from three places:

1. **HEAD / current commit**
2. **Index / staging area**
3. **Working tree**

It uses these comparisons to determine:

- staged changes → index differs from `HEAD`
- unstaged changes → working tree differs from index
- untracked files → files in the working tree that are not represented in the index

Git can also use cached index information and filesystem metadata to avoid unnecessarily reading every file from scratch.

</b></details>

<details>
<summary>Why is <code>git status</code> fairly fast even on large repos?</summary><br><b>

Git stores repository information efficiently and uses the index to track file metadata and staged content. It can use filesystem metadata, cached information, and optimizations such as the untracked cache and file-system monitor when available.

So Git does not need to reconstruct the entire repository history every time I run `git status`.

</b></details>

---

<div align="center">

# Hit the Star! ⭐

***If this repo is helping you learn Git too, please hit the star. Thanks!***

#### Maintained by Pallavi

</div>
