---
title: Basics
layout: default
nav_order: 2
---
# Basics of Git
{: .no_toc }
Learn how use Git! Read below for an introduction to the Git environment, or look at our pages for each action you need to know.

- TOC
{:toc}

---

## Introduction to Git
Git is a *version control system*, used to keep track of changes in your code or files over time. This is used for projects to allow developers to modify their files while maintaing a history of each change. If anything goes wrong, the work can be recovered by reverting to a previous version.

### How Does it Work?
Git works by letting you make changes in a local repository on your computer, and then save or share those changes by pushing them to a remote repository online.

> Understanding the difference between local and remote areas is key to using Git effectively.
>
> *Local* refers to everything on your own computer.
> *Remote* refers to a version of your repository that lives online, often on platforms like GitHub.

Git tracks changes to your files on your computer - this version of the project that is stored on your computer is your **local repository**. When you make a change, you create a **commit** to save a snapshot of your progress at that moment in time. These commits stay local until you push them to a **remote repository**. This is an online version of your project hosted on platforms like GitHub. From this remote repository you can back up your work, access it from other devices, and share it with others. You should always **pull** from the remote repository before pushing - this takes any new data or changes from the remote repository and updates your local repsitory accordingly. Pulling ensures that you are up to date on any changes before adding your code.

In general, Git follows a few basic steps that allow your project history to be saved:
1. Modify code in your local workspace. 
> This is in your working directory, which is different from your local repository. Git tracks the difference between these to determine what changes you've made.
2. Stage the changed files to allow Git to track them.
3. Commit to take a snapshot of the staged files and store these in your local Git repository.
4. Pull from your remote repository and handle any merge conflicts.
5. Push your local repository data to the remote repository.

### Terminology
While working with Git, there are some important terms to remember:
- Repository: A project folder that Git uses to track changes. This contains your files and the history of your changes.
    - Local repository: The version of your repository stored on your own computer.
    - Remote repository: A version of you repository stored on the internet (e.g. GitHub).
- Sections: Each Git Project is split into three main sections. These are different parts of the project.
    - Working directory: Where your project files live on your computer. These are the files that you see and edit.
    - Staging area (index): A holding area to prepare changes before commiting. This tells Git which files you want to the changes of.
    - .git directory (repository): A local, hidden folder where Git stores all of your commits and version history. This is what makes your folder a Git repository. When cloning, this is what is copied.
- States: The files in your project move through three different states.
    - Modified: The file has been changed but not staged. Git has not been told to track the changes for this file yet.
    - Staged: The changed file has been marked to go into your next commit in its current version.
    - Committed: The change has been saved in Git's history and is now part of the local repository.