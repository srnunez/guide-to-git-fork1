---
title: Privacy
parent: Intermediate
nav_order: 4
---
# Privacy
{: .no_toc}
When using Git, you may be handling sensitive information. Below are some areas to keep an eye on when making repositories or using sensitive data.

- TOC  
{:toc}

---

## Repository Privacy
By default, GitHub will allow you to create a public repository. Make sure to change it to private if you don’t want others to access your repository. 

When making a repository, this can be done using the selection circled below:

![Image of the repository creation screen, with the selection for privacy settings boxed in red](/guide-to-git/assets/images/repo-privacy-creation.png)

The privacy setting of a repository will be displayed in text next to the repository name. To change this setting after creating the repo, go into the **Settings** tab in the repository menu:

![Image of the repository Settings selection from the repository menu](/guide-to-git/assets/images/repo-settings.png)

From here, go to the **Danger Zone** section and find **Change repository visibility**:

![Image of the Danger Zone section in the repository settings where the visibility can be changed](/guide-to-git/assets/images/change-visbility.png)

Click the **Change visibility** button circled above and select the desired option from the dropdown menu. There will be two pop-ups asking you to confirm the change. After confirming, your repository settings will update.

## Repository Authorization
In the **Collaborators** section of the repository settings, you can add users:

![Image of menu to add collaborators to a repository](/guide-to-git/assets/images/add-users.png)

While adding collaborators, make sure you enter the correct information, otherwise, it will lead to unauthorized access. 

## Leaking Sensitive Data
While pushing sensitive data like passwords, API keys, SSH private keys, etc. GitHub won’t stop you, so it’s your responsibility to keep that information private.

To solve this problem, you need to create a [.gitignore](https://sophia-nunez.github.io/guide-to-git/docs/intermediate/git-files.html#gitignore) file in your repository to prevent pushing the sensitive data.

By using a repository, you can create a file named `.gitignore` with the path or filename of the sensitive files.

Example:

![Image of a .gitignore file](/guide-to-git/assets/images/gitignore.png)

To make this file using bash, enter the following commands:
1. Use the command touch .gitignore to create a .gitignore file.
    ```bash
    touch .gitignore
    ```
2. Use the command echo “path or file name” >> .gitignore to add files you want to ignore while pushing commits.
    ```bash
    echo “*.log” >> .gitignore
    ```
3. Use the command git add .gitignore to stage the .gitignore file for pushing.
    ```bash
    git add .gitignore
    ```
4. Use the command `git commit -m “commit message”` to commit the .gitignore file.
    ```bash
    git commit -m “Add .gitignore to ignore sensitive files”
    ```
5. Use the command git push -u origin main to push the commit to your repository. The -u flag sets the upstream reference, which means you can use git push and git pull without specifying the remote and branch name each time (origin main).
    ```bash
    # -u flag sets the upstream reference
    git push -u origin main
    ```

