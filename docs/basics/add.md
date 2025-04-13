---
title: Add
parent: Basics
nav_order: 4
---
# Git Add
Once files have been modified in your workspace, you'll need to add these revisions to your [staging area](https://sophia-nunez.github.io/guide-to-git/docs/basics/#terminology). This prepares the files for the version control.

## How to Add Files
When using the `git add` command, you can either add files individually, or all at once. To add one file, do the following in your terminal:

```terminal
$ git add [filename]
```

To add all files in the project, use:

```terminal
$ git add .
```

After using this command, you shouldn't see any additional output in the terminal. If you would like to check the status of your repository and changes, use [`git status`](https://sophia-nunez.github.io/guide-to-git/docs/basics/status/)

{: .note }
>Using `git add` will add the specified files to the staging area as they are in that moment in time. Further revisions would need to be added again.