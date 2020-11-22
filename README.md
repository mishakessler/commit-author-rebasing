# Commit Rebasing

Occasionally, when working between GitHub and GitHub Enterprise Servers, you might notice that your commit history isn't crediting you with your own commits. Most likely, this happened because either you haven't set up your computer's global git env file, and commits are being made to the working tree without your author information, or 2) you're using two different emails between your Git and GitHub accounts.

To make sure your profile is accurately reflecting your commit history, look at your repositories' commit histories. If you notice your commits are not linking to your GitHub profile, this will help you out.

> Please note, as Adam DeHaven states: This action is destructive to your repository's history. If you're collaborating on a repository with others, it's considered bad practice to rewrite published history... Running this script will rewrite history for all repository collaborators. After completing these steps, any person with forks or clones must fetch the rewritten history and rebase any local changes into the rewritten history.

If you are not the only person on your repository, you will need to alert your teammates to the changes made the working tree's history, or all kinds of issues will arise.

With that out of the way, I've managed to get the bulk of the work down to two terminal commands, so take a look below for an easy solution!

## Getting Started

First, in your terminal, set up a temporary directory that will allow you to clone the necessary repositories; `cd` into the temporary directory.

```sh
mkdir temp && cd temp
```

## Setting Up

In the directory, run clone the [Change Git Author Script by Adam DeHaven](https://www.adamdehaven.com/blog/update-commit-history-author-information-for-git-repository/); `cd` into the cloned repository.

```sh
git clone https://github.com/adamdehaven/change-git-author && cd change-git-author
```

Once inside the cloned directory, you need to grant the script file the necessary privileges.

```sh
chmod +x changeauthor.sh
```

Let's go back up a level to parent `temp` directory.

```sh
cd ..
```
