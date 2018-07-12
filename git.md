# GIT Tutorial

## What is it?
Git is a Distributed Version Control System (DVCS).
In simpler terms, Git is a tool that you can use to track changes you make to a
bunch of files, and also keep track of other details such as who and when made a
certain change to a file.

When we say Git is distributed, we mean that every person working on a specific
project

## Cheatsheet
### `git init` _[<directory\>]_
- Makes a new git repository
- Creates a `.git/` directory inside the repository

### `git add` _[<filename\>]_
- stage files to be committed
- Shown in `git status` in green

### `git rm` _[\<filename>]_
- remove files from the git repository
- The standard `rm` will only remove the file locally

### `git commit`
- __[-m <message>]__ : Write the commit message on the command line
- _[-a]_ (Interactive mode)
- --amend: Change the last commit message

### `git remote add origin` _<server URL>_
- If you are creating a git repository from the command line, link it your
  remote (GitHub/BitBucket) repo

### `git pull`
- --rebase : Add local changes on top of pulled files

### `git push` _[origin]_ _[<branch name>]_
- `-u` set upstream
-  Try `git config --global push.default simple`
    - This way you can just type `git push` and it will only push the branch
          you are working on (provided that the upstream and local branch names
			  are the same)
- `-f --force` Force push
    - Could use this with `git rebase` to change commit history on remote
          [NOT RECOMMENDED]

### `git clone` _<repository URL>_ _[<directory>]_
- Checkout git repo
- Get a local copy of git repository

#### Differences between forking and cloning
[Here](https://stackoverflow.com/questions/6286571/are-git-forks-actually-git-clones)
is a Stack Overflow post that explains the difference


- Forking is in **GitHub**
    - You can fork a repo into your own [GitHub] account
    - Make changes
    - Ask for pull request (to contribute)
- Cloning is just having a local copy
    - You can only contribute if you are a collaborator

### `git stash` _[pop]_ _[apply]_
- Save all your local changes [onto a stack] and restore your branch to the
  state of the last pull
- Use `git stash pop` to restore the "stashed" work

### `git status`
- Show the current status of the branch you are working on
- See untracked files and files added/removed

### `git log`
- View a log of commits`

### `git blame`
- Show the last revision and author who last modified the file

### `git branch`
- List all branches

### `git checkout` _[\<branch_name>]_
- Switch to branch
- `-b/-B`: Create a new branch and switch to that
- `-m`: Merge branch with current working branch.

### `git reset`
- Reset git branch to a previous state
    - Warning: You will lose any un-pushed changes if you use this
- `--soft HEAD^`: Un-staged last commit

### `git config`
- Set up your git config file

## `git fetch`
- Fetch updates from remote, but not merge them to local
- `--all`: fetch updates from all files in repo
    - Use this w/ `git reset --hard origin/<branch_name>`

### `git rebase`

### `git cherry-pick`
- Push a commit from another branch onto the current branch

### `git worktree`
- manage multiple working trees

## Other Great Git Resources/References

* [Github's Git Cheatsheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
* [Getting Started with Git](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
* [Practical Introduction to Git](https://codeburst.io/git-good-part-a-e0d826286a2a)
