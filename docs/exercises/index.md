---
title: Exercises
layout: default
nav_order: 5
---

Here are some exercises to apply what you've learned from the guide!

## Exercise 1: Configure Git

Configure your username and email, then display this info.

<details markdown="block">
<summary>💡 Show Solution</summary>

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list
```
</details>

## Exercise 2: Clone repo

Clone one of your repos and enter the directory so you can edit its contents locally

<details markdown="block">
<summary>💡 Show Solution</summary>

1. Find the link to your repo (e.g. https://github.com/sophia-nunez/guide-to-git.git)
2. Enter the following commands
```bash
git clone https://github.com/sophia-nunez/guide-to-git.git
cd your-repo
```
</details>

## Exercise 3: Push Changes
Create a file called `hello.txt`, stage it, and push it to your repo

<details markdown="block">
<summary>💡 Show Solution</summary>
1. Create the `hello.txt` file in your directory
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
You should see something like this
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

## Exercise 5: Fork a repo and create a PR (requires a partner)
Create a repo. Have a partner fork your repo and submit a PR.

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


