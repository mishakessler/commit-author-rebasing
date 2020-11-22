# Commit Rebasing

Occasionally, when working between GitHub and GitHub Enterprise Servers, you might notice that your commit history isn't crediting your own commits to you. Most likely, this happens when either 1) you haven't set up your computer's global git env file, or 2) you're using two different emails between your accounts.

To make sure your profile is accurately reflecting your commit history, look at your repositories' commit histories. If you notice your commits are not linking to your GitHub profile, this will help you out.

> 

I've managed to get it down to two terminal commands, so take a look below for an easy solution!

## Getting Started

First, in your terminal, set up a temporary directory that will allow you to clone the necessary repositories; `cd` into the temporary directory.

```shell
mkdir temp && cd temp
```

In the directory, run clone the [Change Git Author Script by Adam DeHaven](https://www.adamdehaven.com/blog/update-commit-history-author-information-for-git-repository/); `cd` into the cloned repository.

```shell
git clone https://github.com/adamdehaven/change-git-author
```
