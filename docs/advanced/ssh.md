---
title: SSH Key Setup
parent: Advanced
nav_order: 5
---

# Setting Up SSH Keys for GitHub
{: .no_toc}
Using SSH to connect to GitHub allows you to securely push and pull without typing your username and password every time. This page will walk you through creating and using an SSH key for Git.

- TOC
{:toc}

---

## What Is an SSH Key?
An **SSH key** is a pair of secure cryptographic keys used to identify you when connecting to remote servers like GitHub. When set up, it allows Git to authenticate with GitHub without needing your username and password.

---
## Set Up Your SSH Key
### Step 1: Check for Existing SSH Keys
First, open your terminal and check if you already have an SSH key using the following command:

```bash
$ ls -al ~/.ssh
```

Look for files named `id_ed25519` or `id_rsa` and their `.pub` versions. These are keys that are supported for GitHub. If you already have a key you’d like to use, you can skip to Step 3.

### Step 2: Generate a New SSH Key
If you don’t have a key or want to create a new one, run this command with the following output:
```bash
$ ssh-keygen -t ed25519 -C "your-email@domain.edu"
> Generating public/private ALGORITHM key pair.
> Enter file in which to save the key (/c/Users/YOU/.ssh/id_ALGORITHM):[Press enter]
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]

```
Use your GitHub email address. When prompted to choose a file location, press Enter to use the default. You can set a passphrase or leave it blank - note that setting a passphrase may require it to be used any time you use the SSH key to clone, add, etc.

### Add the SSH Key to the ssh-agent
This step varies depending on your operating system. Click the appropriate link below for more information:

- [Mac](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=mac#adding-your-ssh-key-to-the-ssh-agent)
- [Linux](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux#adding-your-ssh-key-to-the-ssh-agent)
- [Windows](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)