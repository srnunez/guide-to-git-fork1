---
title: Push
parent: Basics
nav_order: 6
---
# Git Push
{: .no_toc}
Once you've commited changes, you need to push to send these to your remote repository. The commits will then appear on the page for your repository, such as GitHub.

- TOC
{:toc}

---

## Commit History on GitHub
To view the commit history on GitHub, you can click the clock icon on the right side of the header for the repository files:

![Image of the Guide to Git repository page with the Commit History icon circled in red](/guide-to-git/assets/images/Push-commit-history.png)

This will bring you to a page of all commits to the repo, with the commit message displayed:

![Image of the Guide to Git commit history](/guide-to-git/assets/images/Push-commit-history-page.png)

Clicking on any of these commits will show you a list of the files changed in that commit and what edits were made. From here, you can also view all files in the repository at that point in the version history!

---

## How to Push
To push your local commits to the remote repository, use the `git push` command. 

{: .warning}
> You should always [pull](https://sophia-nunez.github.io/guide-to-git/docs/basics/pull/html) before pushing your changes. This ensures that you can handle any areas where changes made to the code locally conflict with updates made to the remote repository since your last pull.
>
>For more information on these conflicts, check out our page on [Merge Conflicts](https://sophia-nunez.github.io/guide-to-git/docs/intermediate/)!

To use `git push`, run the following command in your terminal:

```terminal
$ git push
```
When starting out, you will likely be working in something called the main branch. Due to this, the command above can be used. If you'd like more information on branching and how this may change the `git push` command, check out our page on [Branches](https://sophia-nunez.github.io/guide-to-git/docs/advanced/branches.html).

Pushing will give you output confirming the push, as given below:

```terminal
$ git push
Enumerating objects: 20, done.
Counting objects: 100% (20/20), done.
Delta compression using up to 16 threads
Compressing objects: 100% (11/11), done.
Writing objects: 100% (12/12), 134.60 KiB | 6.73 MiB/s, done.
Total 12 (delta 4), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (4/4), completed with 4 local objects.  
To https://github.com/sophia-nunez/guide-to-git.git
   9bc8202..bba9521  main -> main
```
As noted above, pulling before you push is important. If you recieve an error message after pushing, check out our Troubleshooting and Merge Conflict pages.

Once you get the output indicating the push was a success, your commits should now appear on the page for your repository on GitHub!

---