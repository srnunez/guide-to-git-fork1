---
title: Commit
parent: Basics
nav_order: 4
---
# Git Commit
{: .no_toc }
Commiting records the snapshots of you files in the staging area, putting them in the version history for the repository. You should do this whenever you want to record the current state of your project - starting off, commit more often than you think you should!

- TOC
{:toc}

---

## Commit Messages
When commiting your revisions, you should add a message to describe what changes were made since the last commit. This will show up in the commit history on your repository, and lets you and others keep track of when certain changes may have been made.

Commit messages don't have a specific formatting they have to follow. However, it's typically a good idea to include certain keywords depending on the types of changes made. A good starter rule is to include these in brackets at the beginning of your message, followed by a brief sentence or two providing more detail.

Some of these keywords may include:
- Skeleton: When making the skeleton for your project, such as adding empty class files and method headers.
- Implementation: When adding functionality to your program, such as implementing methods.
- Test: When writing or modifying tests for your program, such as adding unit tests for a class.
- STP: When writing or modifying a System Test Plan for your project.
- Debug: When making changes on an implemented file to fix an error, failing test, or other bug.
- Javadoc: When adding or updating Javadoc in your files.

Examples of a commit message you may see include:
- "[Implementation] Added functionality for the RecipeBook class."
- "[Test] Improved unit test coverage for the Coffee class."
- "[Debug] Updated addRecipe() method to fix incorrect id assignment."

The level of detail you add may vary between projects. In some cases, multiple keywords may be needed in the same commit. When getting started, try to commit often enough to not need more than two or three in one commit.

---

## How to Commit
The `git commit` command allows you to commit your **staged** revisions. It is important to use [`git add`](https://sophia-nunez.github.io/guide-to-git/docs/basics/add.html) on any files you want to commit *before* using the commit command, as unstaged files will not be inlucded.

To commit, use the following command in your terminal:

```terminal
$ git commit -m "commit message inside quotations here"
```
An example of what this may look like (using a commit from our own repo!) would be:

```terminal
$ git commit -m "Favicon replaced with favicon-2"
[main 9bc8202] Favicon replaced with favicon-2
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 assets/images/gtg-favicon-2.png
```

{: .note }
> At this point, our changes are still confined to the local repository. In order to update the remote repository, make sure to [push](https://sophia-nunez.github.io/guide-to-git/docs/basics/push.html) your commits!