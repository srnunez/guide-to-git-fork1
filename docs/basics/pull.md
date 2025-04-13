---
title: Pull
parent: Basics
nav_order: 5
---
# Git Pull
{: .no_toc }
Pulling updates your local repository with any new commits on the remote repository. This allows you to see any changes made on another computer, by someone else in the repository, or in the case that the files on your computer become inaccessible.

- TOC
{:toc}

---

## How it Works
The `git pull` command combines fetching and merging - topics covered in our Advanced section. Essentially, it takes new commits from the remote repository and brings them to your computer by combining the local and new versions together. 

You should always pull before starting to make changes and before pushing in order to reduce any conflicting edits.

## Before Pulling
If you've made changes to any code since you last pulled, you want to make sure to preserve your current revisions before pulling. This will prevent any overwriting or other issues.

To do this, there are two options:

1. **Commit Before Pulling**
This is the typical recommendation for saving your changes before pulling. Use `git commit` to take a snapshot of your files and prevent loss of data.

In your terminal, this would use following commands:

```terminal
$ git add .
$ git commit -m "message here"
$ git pull
```

2. **Stash Before Pulling**
Another option is to stash your changes temporarily. This will not create a commit, so this is typically used when you've modified files but are not ready to include them in the version history. 

Stashing will allow you to save your changes and pull without conflicts, overwriting any edits. Using `git stash pop`, you then add your modifications back on afterwards.

In your terminal, this would use following commands:

```terminal
$ git stash
$ git pull
$ git stash pop
```

## How to Pull
To pull, run the following in your terminal:

```terminal
$ git pull
```

Similar to `git push`, this command may change if you are using branches. Please check our page on [Branches](https://sophia-nunez.github.io/guide-to-git/docs/advanced/branches/) for more information.

If no commits have been added to the remote repository since your last push, you may see the following output:

```terminal
$ git pull
Already up to date.
```

Otherwise, you will see output similar to the following:

```terminal
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)  
Unpacking objects: 100% (3/3), 957 bytes | 35.00 KiB/s, done.
From https://github.com/sophia-nunez/guide-to-git
   7914dab..2d41162  main       -> origin/main
Updating 7914dab..2d41162
Fast-forward
 _config.yml | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

## Merge Conflicts
When pulling, you may get a message about a merge. This is the step where the changes from the remote repository are combined with your local one. In most cases, this is done automatically - you may see a message such as this in your terminal:

``` vim
Merge branch 'main' of https://github.com/sophia-nunez/guide-to-git
# Please enter a commit message to explain why this merge is necessary,# especially if it merges an updated upstream into a topic branch.     
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
~                                                                      ~                                                                      ~                                                                      ~                                                                      ~                                                                      .git/MERGE_MSG [unix] (16:08 13/04/2025)                        1,1 All
"~/git/guide-to-git-1/.git/MERGE_MSG" [unix] 6L, 294B
```
This is indicating that a merge was done automatically and prompting you to write a merge message for the commit history. The editor this file opens in is the default for your computer, which is usually VI. To finish the merge, write a message and quit by doing the following:
1. `i` to enter Insert mode and write your message.
2. `esc` to enter command mode.
3. `:wq` to save and exit, or `:q` to exit without saving.

With the automatic merge completed, your terminal should contain output similar to the following:

```terminal
$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)  
Unpacking objects: 100% (3/3), 957 bytes | 35.00 KiB/s, done.
From https://github.com/sophia-nunez/guide-to-git
   7914dab..2d41162  main       -> origin/main
Merge made by the 'ort' strategy.
 _config.yml | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

{: .warning}
> In the case that changes between the versions conlict, such as edits made to the same line in a file, you may have to handle the merge conflict yourself. This topic is covered in more depth on our [Merge Conflicts](https://sophia-nunez.github.io/guide-to-git/docs/intermediate/MergeConflicts/) page!