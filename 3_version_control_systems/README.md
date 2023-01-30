# Summary

1. [What is Version Control?](#what-is-version-control)
    1.1. [The importance of source code management tools](#11-the-importance-of-source-code-management-tools)
2. [Source code management best practices](#2-source-code-management-best-practices)
3. [What is Git](#3-what-is-git)
4. [Configure Git ](#4-configure-git)  
    4.1. [Set your global name](#41-set-your-global-name)  
    4.2. [Set your global email](#42-set-your-global-email)  
    4.3. [Set your global.username](#43-set-your-globalusername)  
5. [Repositories](#5-repositories)  
    5.1. [Create a Repository](#51-create-a-repository)  
6. [Commits](#6-commits)  
    6.1. [Check Status + Add and Commit Changes](#61-check-status--add-and-commit-changes)  
    6.2. [List the differences ](#62-list-the-differences)
7. [Remote Control](#7-remote-control)  
    7.1. [Connect your Local to your Remote](#71-connect-your-local-to-your-remote)  
    7.2. [Push Work to your Remote](#72-push-work-to-your-remote)
8. [Forks and Clones](#8-forks-and-clones)  
    8.1. [Fork the Patchwork Repository](#81-fork-the-patchwork-repository)  
    8.2. [Clone Your Fork Locally](#82-clone-your-fork-locally)  
    8.3. [Connect to the Original Repository](#83-connect-to-the-original-repository)
9. [Branches](#9-branches)  
    9.1. [Create a branch](#91-create-a-branch)  
    9.2. [Push a branch](#92-push-a-branch)  
    9.3. [Rename a branch you're currently on](#93-rename-a-branch-youre-currently-on)
10. [Pulling from a Remote](#10-pulling-from-a-remote)
11. [Merge](#11-merge)
12. [Deleting Branch](#12-deleting-branch)

---
![](/3_version_control_systems/version_control_systems.png)

---

## 1. What is Version Control?

[🔗 What is version control?](https://www.atlassian.com/git/tutorials/what-is-version-control)

Version control, also known as source control, is the practice of tracking and managing changes to software code. 

One of the most popular VCS tools in use today is called **Git**. Git is a Distributed VCS, a category known as DVCS, more on that later. Like many of the most popular VCS systems available today, Git is free and open source.

You should expect from version control:
- A complete long-term change history of every file.
- Branching and merging.
- Traceability.

## 1.1. The importance of source code management tools

SCM brought version control safeguards to prevent loss of work due to conflict overwriting. These safeguards work by tracking changes from each individual developer and identifying areas of conflict and preventing overwrites. SCM will then communicate these points of conflict back to the developers so that they can safely review and address.

## 2. Source code management best practices

- Commit often;
- Ensure you're working from latest version;
- Make detailed notes;
- Review changes before committing;
- Use Branches;,
- Agree on a Workflow;

## 3. What is Git

By far, the most widely used modern version control system in the world today is Git. Git is a mature, actively maintained open source project originally developed in 2005 by Linus Torvalds, the famous creator of the Linux operating system kernel. Git has been designed with performance, security and flexibility in mind.
 

## 4. Configure Git 

You can verify that Git is really there by typing:

```bash
git --version 
```
This will return the version of Git on your computer and look something like this:
```bash
git version 2.34.1 
```

### 4.1. Set your global name

```bash
git config --global user.name "Your Name"
```

### 4.2. Set your global email
```bash
git config --global user.email "youremail@example.com"
```

### 4.3. Set your global.username
```bash
git config --global user.username "Your Username"
```

## 5. Repositories

A repository is a collection of related items. In our case, when writing software, it is a collection of files related to a software project. 

### 5.1. Create a Repository

First, make a new folder:
```bash
mkdir hello-world && cd hello-world
```

Initialize (start tracking) the folder you are now in
```bash
git init
```
If you want to be double-sure that it's a Git repository:
```bash
git status
```

## 6. Commits

Commits are core to using Git. They are the moments in which you save and describe the work you've done. They are the ticks in the timeline of your project's history.

### 6.1. Check Status + Add and Commit Changes

First, check the status:
```bash
git status
```
Then add the file you just created so that it becomes a part of the changes you will commit (aka save) with Git:
```bash
git add README.md
```
You can add all with:
```bash
git add .
```
Finally, commit those changes to the repository's history with a short (m) message describing the updates.
```bash
git commit -m "Created README.md"
```

### 6.2. List the differences 

```bash
git diff
```
## 7. Remote Control

### 7.1 Connect your Local to your Remote

To add a remote named 'origin' to your repository:
```bash
git remote add origin <URLFROMGITHUB>
```

You can change the url repository using:
```bash
git remote set-url origin <URLFROMGITHUB>
```

### 7.2 Push Work to your Remote
```bash
git push origin master
```

## 8. Forks and Clones

When you fork a repository, you're creating a copy of it on your GitHub account. 
To get a forked repository from your GitHub account onto your computer you clone it.

### 8.1. Fork the Patchwork Repository

Go to github project page and click the 'Fork' button at the top right.

### 8.2. Clone Your Fork Locally
```bash
git clone <URLFROMGITHUB>
```

### 8.3. Connect to the Original Repository
```bash
git remote add upstream <URLFROMGITHUB>
``` 

To be sure you have the correct remotes set up, type ```git remote -v``` to list out the addresses you have stored. 

## 9. Branches

Git repositories use branches to isolate work when needed.

### 9.1. Create a branch

When you create a branch, Git copies everything from the current branch you're on and places it in the branch you've requested be made.

To list all branches:
```bash
git branch
```
To create a branch:
```bash
git branch <BRANCHNAME>
```
To go into that branch and work on it you checkout a branch. Go on your new branch:
```bash
git checkout <BRANCHNAME>
```
You can create a branch with ```-b``` in ```checkout``` command:
```bash
git checkout -b <BRANCHNAME>
```

### 9.2. Push a branch
```bash
git push origin <BRANCHNAME>
```

### 9.3. Rename a branch you're currently on
```bash
git branch -m <NEWBRANCHNAME>
```

## 10. Pulling from a Remote

If you're working on something with someone else you need to stay up to date with the latest changes. So you'll want to pull in any changes that may have been pushed to the central GitHub repository.
```bash
git pull <REMOTENAME> <BRANCHNAME>
```

## 11. Merge

First, move into the branch you want to merge into:
```bash
git checkout <BRANCHNAME>
```
Now tell Git what branch you want to merge in:
```bash
git merge <BRANCHNAME>
```

### 12.  Deleting Branch

Tidy up by deleting your feature branch. Now that it has been merged you don't really need it around.
```bash
git branch -d <BRANCHNAME>
```
You can also delete the branch from your remote on GitHub:
```bash
git push <REMOTENAME> --delete <BRANCHNAME>
```


