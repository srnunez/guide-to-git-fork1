---
title: Additional Commands
parent: Intermediate
nav_order: 3
---

# Additional Git Commands  
{: .no_toc}
Once you're comfortable with the basics like `clone`, `add`, `commit`, and `push`, there are a few other commands that can help you manage and understand your repository more.

- TOC  
{:toc}

---

## `git status`

This is one of the most useful Git commands, especially when you're not sure what you've done recently.

To run this command, use:
```bash
$ git status
```
This will tell you what branch you're on, which files have been changed, which files are staged or unstaged, and if there are untracked files. Use this to keep track of your workflow and avoid mistakes.

An example of output you may see from `git status` would be:
```bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)        
  (use "git restore <file>..." to discard changes in working directory)
        modified:   docs/basics/clone.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)       
        docs/advanced/ssh.md

no changes added to commit (use "git add" and/or "git commit -a") 
```
## `git remote`
This command shows the remote repositories that your local project is connected to. Run it using the following:

```bash
$ git remote -v
```

Your output will typically look something like this:

```bash
origin  https://github.com:yourname/your-repo.git (fetch)
origin  https://github.com:yourname/your-repo.git (push)
```

---

## `git log`
This shows a history of all commits in your current branch. Type the following:

```bash
$ git log
```
The log view will appear. To quit, press `q`. The default command with show commit hashes (SHAs), authors, dates, and commit messages for the commits. 

For the simplified version, use:

```bash
$ git log --oneline
```
This may give output similar to the following:

```bash
1a23bc4 Commit message 1
9z87yx6 Commit message 2
```

---

## `git diff`
This shows the differences between your working files and what’s staged or committed. Run using:

```bash
$ git diff
```
Use it to review your changes before committing. If you’ve already staged changes, use:

```bash
$ git diff --staged
```

---

## More commands
Git has many more commands, and each of these (incuding the ones in this guide) have many additional arguments that can be added on for a more fine-tuned execution. 

This guide will not cover all of these in detail - we recommend checking out the [official documentation](https://git-scm.com/doc) for specific cases!

(: .note)
The documentation for Git assumes prior knowledge and may be confusing for beginners. Don't worry if this material is difficult to understand at first!