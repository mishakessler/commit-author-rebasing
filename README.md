# Commit Rebasing

Occasionally, when working between GitHub and GitHub Enterprise Servers, you might notice that your commit history isn't crediting you with your own commits. Most likely, this happened because either you haven't set up your computer's global git env file, and commits are being made to the working tree with an email address like `misha@mishas-macbook-pro.local`, or you're using different email addresses between your Git and GitHub accounts.

> Please note, as Adam DeHaven states: This action is destructive to your repository's history. If you're collaborating on a repository with others, it's considered bad practice to rewrite published history... Running this script will rewrite history for all repository collaborators. After completing these steps, any person with forks or clones must fetch the rewritten history and rebase any local changes into the rewritten history.

If you are not the only person on your repository, you will need to alert your teammates to the changes made the working tree's history, or all kinds of issues will arise.

With that out of the way, I've managed to get the bulk of the work down to two terminal commands, so take a look below for an easy solution!

## Getting Started

First, in your terminal, set up a temporary directory that will allow you to clone the necessary repositories; `cd` into the temporary directory.

```sh
mkdir temp && cd temp
```

## Setting Up

In the directory, clone the [Change Git Author Script by Adam DeHaven](https://www.adamdehaven.com/blog/update-commit-history-author-information-for-git-repository/); `cd` into the cloned repository.

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

## Determining Which Repos to Clone

With our script ready to go, let's return to GitHub and find the repository that needs to be updated.

Once in the repository, check out the commit history. If you see multiple commits that aren't linked, you'll want to update that repository.

![commit history screen cap]()

First, you'll want to clone the repository down into the same `temp` directory as the cloned script; `cd` into the repository.

```sh
git clone <repository link> && cd <cloned repository name>
```

## Finding The Authorship Information

In order to use this script, we'll first have to know the author information on the old commits. If you're not sure, run a `git log` so you can browse the commits and see the commit author email.

![commit log author info]()

From this example, we can see that two of my commits are under two different emails. I need my commit author information to have my gmail address. Let's get to running that script.

## Running Our Rebase Script

Now that we have the old email, we're able to run the full script; from inside the git repository, run the following command, replacing all content inside a `< >` with your information:

```sh
../change-git-author/changeauthor.sh --old-email <misha.kessler@generalassemb.ly> --new-email <misha.kessler@gmail.com> --new-name "<Misha Kessler>" --remote <origin>
```

Let's break down what's happening:

1. We're telling our terminal to access the script at the location provided in the first argument: `../change-git-author/changeauthor.sh`
1. Next, we're giving the script the email that needs to be replaced, which we found by running `git log`. In my case, it's my General Assembly email, but for you, it may be something like `misha@mishas-macbook-pro.local`.
1. Next, we provide the email we need to change the commit to reflect. This should be your personal GitHub email.
1. Next, we need to provide the `--new-name` flag, even if we're not changing the name on our commits. Just put your name in. 
1. Finally, we give the destination name of our remote repository– most likely just your `origin`. This allows us to directly update our remote with our new commit history.

Once you run this command, your terminal will prompt you twice to confirm 1) the origin's URL, and 2) you understand that you're affecting the git history.

![script confirmation 1]()

![script confirmation 2]()

Finally, it will automatically run a push to your remote, automatically updating the rebased history.

## Voila

That's all! Your commits will now be reflected on your Contribution Graph. 
