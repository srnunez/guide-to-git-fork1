---
title: Merge Conflicts
parent: Intermediate
nav_order: 4
---
# Merge Conflicts  
{: .no_toc}
Merge conflicts happen when Git can't automatically combine changes from two sources. This page explains when and why conflicts happen and how to resolve or avoid them.

- TOC  
{:toc}

---

## What Is a Merge Conflict?
A **merge conflict** occurs when Git tries to merge two [branches](https://sophia-nunez.github.io/guide-to-git/docs/advanced/branches.html) and encounters changes to the same parts of the same file that it can’t automatically reconcile. For example:

- Two people edited the same line in a file.
- One person edited a file that someone else deleted.
- Two commits added the same file with different content.

When this happens, Git pauses the merge and asks you to resolve the conflicts manually.

---

## Conflicts *Before* Merging
If a merge fails prior to actually attempting the merge, this is most likely due to a conflict with local, uncommitted changes. Sometimes you’ll get a message when pulling from a remote branch:

```bash
$ git merge feature
error: Your local changes to the following files would be overwritten by merge:
        prac.txt
Please commit your changes or stash them before you merge.
Aborting
Updating faf1752..354d25e
```
This means Git sees uncommitted changes in your working directory that conflict with what you’re pulling in.

### How to Fix
**Method 1: Keep local changes with git commit**
[Commit](https://sophia-nunez.github.io/guide-to-git/docs/basics/commit.html) unstaged changes first, as described previously in the instructions:

```bash
$ git add .
$ git commit -m "commit message here"
```

This may lead to conflicts during the merge. Resolving these conflicts is detailed in the [Conflicts During Merge](https://sophia-nunez.github.io/guide-to-git/docs/intermediate/merge.html) section.

**Method 2: Discard local changes with git restore**
`git restore <filename>` or discard all local changes with `git restore`. You can also overwrite local changes with a hard reset:

``bash
$ git reset --hard
$ git pull
```

{: .warning}
> Remember, always use hard resets with extreme caution to avoid losing data!

**Method 3: Store local changes for later with `git stash`**
Use `git stash` to save changes, `git stash pop` to reapply the local changes:

```bash
$ git stash
$ git pull
$ git stash pop
```

Popping the stash may cause merge conflicts, which can be resolved in the same process described in the [Conflicts During Merge](https://sophia-nunez.github.io/guide-to-git/docs/intermediate/merge.html) section.

## Conflicts During Merge
If you’re merging one branch into another and there are conflicting changes, Git will pause the process and mark the files that need your attention. This may happen if multiple developers have edited the same lines of code (or deleted a file another developer wants to push changes to), as Git will not be able to determine which changes to keep.

An example of the output you may see in this scenario:

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master)
$ git merge feature
Auto-merging prac.txt
CONFLICT (content): Merge conflict in prac.txt
Automatic merge failed; fix conflicts and then commit the result.
```

The git status command will show conflicts under “Unmerged paths”:
```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master|MERGING)
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   prac.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

### How to Fix
**Method 1: Accept local changes**
For an individual file:

```bash
git checkout --ours [file_name]
```

For all conflicts:

```bash
git merge --strategy-option ours
```

**Method 2: Accept remote changes**
For an individual file:

```bash
git checkout --theirs [file_name]
```

For all conflicts:

```bash
git merge --strategy-option theirs
```

**Method 3: Resolve changes**
Resolve the conflict by editing the conflicted line to the desired change. This can be done in an IDE, or through the command line with commands such as nano or echo. If you are using an IDE the conflict may be altered in a similar format to the conflict displayed below.

To resolve the conflict, open the conflicted files. You should see markers similar to the following:

```bash
<<<<<<< HEAD
Branch being merged into
=======
Branch merging
>>>>>>> feature
```

If this is the case, edit the file to resolve the conflict and delete any markers in the editor. Stage the resolved change with `git add` and commit the resolved change with `git commit` to complete the merge.

### Example:
The original prac.txt in this example read as follows:

    practicing
    merge
    conflicts

This was changed to the following:

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (feature)
$ cat prac.txt
practicing
changed line
conflicts
```

I committed the above change in the feature branch.

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master|MERGING)
$ cat prac.txt
practicing
diff change
conflicts
```
I committed the above change in the master branch.

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master)
$ git merge feature
Auto-merging prac.txt
CONFLICT (content): Merge conflict in prac.txt
Automatic merge failed; fix conflicts and then commit the result.
```
I tried to merge master and feature, but git was unable to determine which change was correct.

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master|MERGING)
$ nano prac.txt
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master)
$ cat prac.txt
practicing
change
conflicts
```

I resolved the conflict by using nano to edit the conflicting line to “change”.

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master|MERGING)
$ git add prac.txt
```
I used git add to stage the resolved change.

```bash
camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master|MERGING)
$ git commit
[master d07b0ee] Merge branch 'feature'

camde@CMK-NCSU-Laptop MINGW64 ~/merge-practice (master)
$ cat prac.txt
practicing
change
conflicts
```

I used git commit to commit my resolved change, allowing the branch to merge properly. The master branch now contains “change” as the second line (while feature still contains “changed line” as its second line).

## Avoiding Merge Conflicts
Smart development processes can help reduce the chance of merge conflicts.

**Method 1: Staying up to date and keep others up to date**
Pulling often helps prevent developers from working with outdated code that has already been edited by a collaborator. Pushing your work in a timely manner also helps others stay up to date.

**Method 2: Use of feature branches**
Making a separate branch for an individual task, and then merging that branch when the feature is complete, prevents the branch from moving too far off from the main/master branch. Long running branches are likely to cause conflicts when they are finally merged. For more information on branching and how to do this, check out our page on [Branches](https://sophia-nunez.github.io/guide-to-git/docs/advanced/branches.html).

**Method 3: Smart file usage and code organization**
If multiple developers have to work from the same file, it is likely merge conflicts will occur. Breaking down very large files into component files can improve overall readability, while reducing the chance of a merge conflict by allowing developers to work out of separate files.
Following this methodology for code can also be beneficial. Even if a file can’t/shouldn’t be broken into multiple files, organized code makes it easier for developers to not interfere with each other.

**Method 4: Smart teamwork**
Dividing tasks so that multiple developers are not editing the same files/code can help prevent merge conflicts. However, this may not be possible in every scenario. If it is necessary for multiple developers to work on the same pieces of code, communicating with each other and pulling/pushing when necessary will reduce the likelihood of a merge conflict.
