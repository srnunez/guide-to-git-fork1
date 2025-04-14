---
title: Git-Specific Files
parent: Intermediate
nav_order: 3
---
# Git-Specific Files
{: .no_toc}
Some files are commonly found in Git repositories and serve important purposes for organizing, documenting, or managing how Git tracks files. While not required, it's important to understand what they are used for. This page covers the most common ones you’ll encounter.

- TOC  
{:toc}

---

## `.gitignore`

The `.gitignore` file tells Git which files or folders to ignore — meaning they won’t be tracked, committed, or pushed.

This is useful for:
- Temporary files (e.g., `.DS_Store`, `*.log`, `*.tmp`)
- Build folders (e.g., `node_modules/`, `dist/`)
- Files with sensitive info or environment settings

**Example contents of `.gitignore`:**

```gitignore
*.log
node_modules/
.env
__pycache__/
```

Once a file is already being tracked by Git, adding it to .gitignore won’t remove it. Instead, you’ll need to untrack it using:

```bash
$ git rm --cached [filename]
```
---

## `README.md`
The `README.md` file is used to describe your project. It's written in Markdown and usually appears at the top of your repository on GitHub.

A README often includes:

- Project name and description
- How to install or run it
- Examples or usage instructions
- License or contributor info

GitHub automatically renders Markdown, so headers, lists, and links are displayed nicely.

Example README.md format:

```markdown
# Guide to Git
This is a simple guide to Git for beginners. This README has lots of important information.

## Website
Access our guide's website at this [link](https://sophia-nunez.github.io/guide-to-git/)!
```

---

## `.git` Directory
Every Git repository has a hidden folder called `.git`. This is where Git stores all version history, branch info, and configuration - this may sound familiar to a discussion from our Basics page.

{: .warning}
> You should not modify or delete anything inside `.git`. This folder is what makes your directory a Git repository.

If this folder is missing or deleted, Git commands will stop working. You can reinitialize it with:

```bash
$ git init
```