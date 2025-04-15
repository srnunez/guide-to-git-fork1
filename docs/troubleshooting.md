---
title: Troubleshooting
layout: default
nav_order: 4
---
# Troubleshooting
{: .no_toc}
You may run into some issues when using Git, especially as you first start out. Check this page for solutions to certain problems.

- TOC  
{:toc}

---

## Deleting or Overwriting Files Accidentally
Sometimes you may accidentally delete or overwrite files while working on projects. This instruction is to help you with different cases you may face.

Before doing anything you can use the command `git status` to check:
- Files that have been modified
- Files that have been delete
- Files staged for commit

For example:
```bash
git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### Case 1: Modified or deleted file but not staged
If you made any changes to files but did not stage them, like the example below:

```bash
echo “.json” >> .gitignore
git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .gitignore

no changes added to commit (use "git add" and/or "git commit -a")
```

You can use `git restore <file>`  as shown below to discard the changes:

```bash
git restore .gitignore
git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### Case 2: Modified or deleted file and staged
If you made any changes to files and already staged them, like the example below:

```bash
rm .gitignore
git add .gitignore
git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    .gitignore

```

You can use `git restore --staged <file>` to discard the stage. If you only modified the file, this command is enough.

If you deleted the file, you need another `git restore <file>` to recover the deleted file:

```bash
git restore --staged .gitignore
git status
git restore .gitignore
git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    .gitignore

no changes added to commit (use "git add" and/or "git commit -a")
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

```

### Case 3: Modified or deleted file and committed
If you have made changes to the files and already committed the changes, like the example below:

```bash
echo ".java" >> .gitignore
git add .gitignore
git commit -m "Bad change"
git status
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
[main 1b64be4] Bad change
 1 file changed, 1 insertion(+)
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

You can use the command `git reset --hard HEAD~1`, which will undo the last commit and discard the changes:

```bash
git reset --hard HEAD~1
git status
HEAD is now at fb8fe62 Add .gitignore to ignore sensitive files
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

The last commit and changes have been discarded as shown above.

### Case 4: Modified or deleted file and pushed
If you have made changes to the files and already pushed the changes, like the example below:

```bash
echo ".java" >> .gitignore
git add .gitignore
git commit -m "Bad change"
git push origin main
git status
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it
[main d250a24] Bad change
 1 file changed, 1 insertion(+)
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 249 bytes | 124.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Eric-L111/testRepo.git
   fb8fe62..d250a24  main -> main
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

You would need the command `git log` to check the commit hash of the previous commit:

```bash
git log
commit d250a24135028a8881a19fb185dc43adba9c10b8 (HEAD -> main, origin/main)
Author: author email-address
Date:   Sun Apr 12 22:47:37 2025 -0400

    Bad change

commit fb8fe62a2fd7431c12a48e554fc670cd13cbeeda
Author: author email-address
Date:   Sun Apr 12 21:30:35 2025 -0400

    Add .gitignore to ignore sensitive files
```

Then you can use the command `git revert -n <commit-hash>` to undo the change made by that commit without rewriting commit history.

{: .note}
> This will avoid you going into the Vim editor. 

Then, you need to commit the change with a message using `git commit -m “any message you want”`:

```bash
git revert -n ab6bd5ac639867ce9dfe2b4c769b9249b6073b43 && git commit -m "Revert bad change"
[main fce4275] Revert bad change
 1 file changed, 1 deletion(-)
```
{: .note}
> Remember to run `git push origin <branch-name>` to update the change to your repository!

Commands:

```bash
git push origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 249 bytes | 124.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Eric-L111/testRepo.git
   ab6bd5a..fce4275  main -> main
```

Result:

![Image of GitHub commit history before and after the revert](/guide-to-git/assets/images/revert-change.png)
