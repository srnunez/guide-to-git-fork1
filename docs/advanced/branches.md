---
title: Branches
parent: Advanced
nav_order: 1
---

# Git Branches
{: .no_toc}
Branches let you work on different versions of a project without affecting the main code. This is useful for experimenting, fixing bugs, or building new features safely.

- TOC
{:toc}

---

## Introduction
When you’re working on a project, you often want to make changes or try new ideas without affecting the current working version. Git lets you do this by using **branches**. A branch is like a separate workspace where you can try out changes. Later, you can bring those changes back into the main project by **merging** or **rebasing**.

By default, Git starts with one branch, usually called `main`. This is what most beginners or small projects use. When you create a new branch, it copies the current state of the project and lets you build from there.

---

### Terminology

Here are some key terms related to branching:
- **Branch**: A separate line of development in your Git repository.
- **Main**: The default primary branch in most Git projects.
- **Feature branch**: A branch created to work on a specific feature or change.
- **checkout**: The command used to switch between branches.
- **Merge**: Combines the changes from one branch into another.
- **Rebase**: Moves commits from one branch onto the end of another, creating a linear history.

---

### When to use Branches
Branches are useful anytime you want to make changes without affecting the main code:

- Add a new feature: Create a feature branch while developing.
- Fix a bug: Make a debug branch so you can test without breaking other code.
- Experiment: Try something new without worrying about damaging the current project.

---

## How to Branch
### Creating Branches
When you create a new branch, Git creates a pointer to the current commit. Any new commits you make on that branch stay separate from the `main` branch. You can switch between branches at any time using `git checkout` or the newer `git switch` command.

Here’s how to create and switch to a new branch:

```bash
git checkout -b [branchname]
```
This creates a new branch called feature-branch and switches you to it.

You can see all branches in your repository with:
```bash
git branch
```

You can also check all branches on the GitHub repository page. This can be found in the dropdown pictured below:

![Image of dropdown on GitHub that shows all branches of the repository](/guide-to-git/assets/images/branch-list.png)

### Combining Branches
Once you've completed making changes and are done with the branch, you can either merge it back into main or rebase your changes. For more information on the rebasing and how it differs from merging, check out our [Rebase page](https://sophia-nunez.github.io/guide-to-git/docs/advanced/rebase.html). 

To merge, using the following command: 

```bash
git checkout main
git merge [branchname]
```

To rebase your changes, use:
```bash
git checkout main
git rebase [branchname]
```

Following either of these commands, push your updated branch using:

```bash
git push origin [branchname]
```

{: .note}
> Depending on how project structure or management, you may need to submit a **pull request** rather than directly merging or rebasing. Check out our page on [Pull Requests](https://sophia-nunez.github.io/guide-to-git/docs/advanced/pull-request.html) for more information!

--- 