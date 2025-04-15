---
title: Exercises
layout: default
nav_order: 5
---
Here are some exercises to apply what you've learned from the guide! You can work in any repository you'd like - we recommed following the exercises in order within the same repository.

- TOC
{:toc}

---

## Exercise 0: Configure Git
Configure your username and email, then display this info.

<details markdown="block">
<summary>💡 Show Solution</summary>

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list
```
</details>

## Exercise 1: Make your repository
Create a new Git repository to track your work on GitHub. Do this exercise from the GitHub page (we're NOT working from the terminal quite yet!).

<details markdown="block">
<summary>💡 Show Instructions</summary>
1. On GitHub, create a repository named `practice`.
2. Add a file named `exercise1.txt`.
3. Commit the changes.
</details>

<details markdown="block">
<summary>💡 Show Solution</summary>

1. On GitHub, click **New Repository**
2. Name it something, such as `practice`
3. To add a file, click **Add file** --> **Create new file**
4. Name this something, such as `exercise1.txt` and put text
5. Click **Commit new file**

</details>


## Exercise 2: Clone repo
Clone your practice repo and enter the workspace so you can edit its contents locally.

<details markdown="block">
<summary>💡 Show Solution</summary>
1. Find the link to your repo on GitHub (e.g. https://github.com/sophia-nunez/guide-to-git.git)
2. Enter the following commands
```bash
git clone https://github.com/sophia-nunez/guide-to-git.git
cd [repo-name]
```
</details>

## Exercise 3: Push Changes
Use your terminal for this exercise to practice the basic commands of Git!

<details markdown="block">
<summary> Show Instructions</summary>
1. Create a file called `hello.txt`.
2. Stage the changes.
3. Push to your repository.
</details>

<details markdown="block">
<summary>💡 Show Solution</summary>
1. Create the `hello.txt` file in your directory. This can be done using your editor or:
    ```bash
    echo "exercise 3!" > hello.txt
    ```
2. Run `git add hello.txt`
3. Run `git commit -m “Added hello.txt”
</details>

## Exercise 4: Merge Conflicts (solo)
Create a repo for yourself. Add a file called conflict.txt, and then get a merge conflict to occur by utilizing branching. Bonus points for solving the conflict!

<details markdown="block">

<summary>💡 Show Solution</summary>
 Edit the same line in conflict.txt in two seperate branches. Commit the changes in each branch, and then try to merge them. 
 
```bash
git add conflict.txt
git commit -m "conflicting edit"
```
You should see something like this when you try to merge the two branches
```bash
$ git merge <branchName>
Auto-merging conflict.txt
CONFLICT (content): Merge conflict in conflict.txt
Automatic merge failed; fix conflicts and then commit the result.
```
To fix the conflict, you can either edit conflict.txt in your IDE or in the command line. This process is demonstrated in detail in the example section of Merge Conflicts, which can be accessed through the Interrmediate tab in the sidebar.

</details>

## Exercise 4: Merge Conflicts (partner)
Create a repo for you and your partner. Add a file called conflict.txt, and then get a merge conflict to occur. Bonus points for solving the conflict!

<details markdown="block">

<summary>💡 Show Solution</summary>
 Have you and a partner both clone the same repo and edit the same line in conflict.txt. Ask your partner to push their changes. Now, you try to push your changes via
 
```bash
git add conflict.txt
git commit -m "conflicting edit"
```
You should see something like this:
```bash
Auto-merging conflict.txt
CONFLICT (content): Merge conflict in conflict.txt
Automatic merge failed; fix conflicts and then commit the result.
```
To fix the conflict, you can either edit conflict.txt in your IDE, or try the following commands
```bash
# accepting their changes
git merge --strategy-option theirs
```
Or 
```bash
# keeping our changes
Git merge –strategy-option ours
```
</details>

## Exercise 5: Create a branch for a repo and create a PR
Create a repo, or go to your `practice` one, and practice using branches.

<details markdown="block">
<summary> Show Instructions</summary>
1. Create a branch called `exercise-5`.
2. Add a file called **branch-practice.txt**.
3. Commit and push your changes.
4. Submit a pull request to merge `exercise-5` into main.
</details>

This exercise can be done on GitHub or from the command line. We recommend trying both options - just make two separate files!

<details markdown="block">
<summary>💡 Show Solution</summary>
1. Option 1: GitHub
    1. On the `practice` repository page on GitHub, click **Branch: main** and create a new branch by typing `exercise-5` into the menu.
    2. Click **Add file -> Create new file** and name it `branch-practice.txt`.
    3. In the file contents section, type any text you'd like.
    5. Click **Commit changes**
    6. GitHub should display an option to **Compare & pull request**. Click this and submit the pull request.
    8. Click **Merge pull request** and **Confirm merge**.
2. Option 2: Command Line
    1. Go to your workspace for the repository using `cd [path]`.
    2. Create and switch to the new branch using `git checkout -b exercise-5`.
    3. Create the file in you editor or using the following commands:
        ```bash
        $ echo "Any text you want here" > branch-practice.txt
        $ git add branch-practice.txt
        $ git commit -m "Add branch-practice.txt on exercise-5"
        ```
    5. Push the new branch using `git push -u origin exercise-5`.
    6. Go to GitHub, where you should see a prompt to open a pull request. Click **Compare & pull request**, then **Merge**.
</details>

## Exercise 6: Fork a repo and create a PR (requires a partner)
Create a repo. Have a partner fork your repo and submit a PR.

<details markdown="block">
<summary> Show Instructions</summary>
1. Fork the repository
2. Clone this fork
3. Edit a file in the repository
5. Commit and push these changes
6. Submit a pull request and check GitHub
</details>

<details markdown="block">
<summary>💡 Show Solution</summary>

1. Have your partner fork your repo on Github
2. Have your partner clone their forked repo using `git clone <their repo url>`.
3. Your partner then must create a new branch using `git checkout -b update(or any name)`
4. Have your partner edit a file in their local repo, for example hello.txt
5. Have your partner commit these changes via 
```bash
git add hello.txt
git commit -m "Changed hello.txt"
git push origin update
```
6. Have your partner go on Github and submit a PR
7. You should see their Pull Request when you enter your repo on GitHub!
</details>