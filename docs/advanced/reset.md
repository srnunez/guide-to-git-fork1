---
title: Reset
parent: Advanced
nav_order: 4
---
# Git Reset
{: .no_toc}
The `git reset` command is used to undo changes in your Git history. It can move your branch pointer, remove commits, and unstage or discard changes depending on how you use it.

- TOC
{:toc}

---

## What is Git Reset?
`git reset` works by changing where your current branch is pointing. You can use it to:

- Unstage files that were added with `git add`
- Remove one or more recent commits
- Discard changes in your working directory

{: .warning}
> The `reset` command is useful for fixing mistakes or cleaning up your Git history. However, it should be used carefully, especially when working with commits that have already been pushed. Improper use of this command can result in data loss.

### When to Use Reset

`git reset` is useful in the following cases:

- **Unstage files**: You ran `git add`, but now you want to remove the file from staging without deleting your changes.
- **Modify your commit history**: You committed too early or too often and want to rewrite recent commits.
- **Undo a commit**: You made a mistake and want to erase the commit as if it never happened (locally).

---

## Reset Command Options
Here are the most common ways to use `git reset`:

1. Unstage a file
    ```bash
    $ git reset <file>
    ```
    This removes the file from the staging area, but keeps your changes in the working directory.
2. Soft reset
    ```bash
    $ git reset --soft <commit>
    ```
    Undoes recent commits. Moves the branch pointer back by one commit but keeps all your changes staged.
3. Mixed reset
    ```bash
    $ git reset --mixed <commit>
    ```
    Undoes commits and unstage changes. Moves the branch pointer back and unstages the changes, but keeps them in your working directory.
4. Hard reset
    ```bash
    $ git reset --hard <commit>
    ```
    Discards commits and changes. This deletes the last commit and all changes in your working directory.

{: .warning}
> Hard resets cannot be undone easily. Use this command with extreme caution. Check out this site on [git reflog](https://github.blog/open-source/git/how-to-undo-almost-anything-with-git/#redo-after-undo-local) if for more information.

### Commit References
In each of the command options above, `<commit>` represents a commit reference. You can specify a specific commit SHA or branch name here.

Here are some common types of commit references:

- **`HEAD`**  
  Refers to your current position in the repository (usually the latest commit on your branch).

- **`HEAD~n`**  
  Refers to the commit *n* steps before the current one. For example, `HEAD~1` is one commit ago, `HEAD~3` is three commits ago.

- **`HEAD^`**  
  Refers to the parent of the current commit. Similar to `HEAD~1`, but used when dealing with merge commits. For example, `HEAD^2` refers to the second parent of a merge.

- **Commit SHA**  
  Every Git commit has a unique hash (SHA). This can be found in your repository's commit history or in your terminal using:
  ```bash
  $ git log
  ```
  Included in this output will be a line starting with `commit` - the text after that is the commit SHA. An example SHA might be `d94b5f7ec7c6d7602c78a5e9b8a5b8c94d093eda`.

- **Branch name**
    You can also use a branch name to reference the latest commit on that branch (e.g., `main` or `feature`).
