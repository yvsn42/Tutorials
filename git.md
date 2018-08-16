# _Meet Your New Best Friend_: __Git__

![Git Logo](https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png)

## What is it?

Git is a Distributed Version Control System (_DVCS_).
In simpler terms, Git is a tool that you can use to track changes you make to a
bunch of files, and help you revert back to older versions of files in the event
of bugs that may arise from later modifications. It also keeps track of other 
details such as the authors and time of each modification. Git is used to 
efficiently track changes to small
as wells as large projects and is primarily used in software development
and open-source projects in any scale.

## Why do we care about Git as developers?

For many reasons (far too many to name really!). Git's ability to work on
different branches makes it really easy to not mess up the entire feature release.
If you have a bug to fix, you can just move it to another branch and work on it
on your own while not disturbing the software being developed by someone else.
Once you've fixed the bug, you can simply merge your branch with the master branch!

Another reason to use git is the ability to gain faster release cycles for your
piece of software. As you use git, you will start to notice that it facilitates
the [Agile Workflow](https://www.smartsheet.com/understanding-agile-software-development-lifecycle-and-process-workflow).

> The problem with Git jokes is that everyone has their own version.

## Bare vs Non-Bare Repositories
- A bare repository is a repository that you don't normally work in. It is
  conventionally used as a central repository for developers to push to and pull
  from. Think of a bare repository as a repository without a workspace.
- Non-bare repositories are the ones you can actually work in, have branches that
  track remote branches, and also push to and pull from changes.

## Some Common Terms
| Term | Definition|
|:------:|:---------|
|Repository(repo)|A "virtual place" where you project is stored and tracked by git. It also contains the information about the file versions, branches, commit logs, etc. <br>  It is the directory that contains the '.git/' directory.|
|Workspace/Worktree/Working directory|Where all the actual files of the repository are stored. You can modify the content and commit the changes as new commits to the repository.Using `git worktree`, you can have multiple worktrees for the same git repo|
|Objects|Essentially, a git repository is a tree-like structure, consisting of 4 objects: Blobs, Trees, Commits \& Tags|
|blob|**B**inary **L**arge **OB**ject. This is the file snapshot git uses to track chnages in a repo, and this is what is add to the Index on `git add/rm`|
|tree object|How subdirectories are stored in a git repo. They store a list of blobs, like how a directory stores a list of files|
|Index/Staging area|The staging area is the place to store changes in the working tree before the commit. The staging area contains the set of the snapshots of changes in the working tree (change or new files) relevant to create the next commit and stores their mode (file type, executable bit).|
|Commit|When you commit your changes into a repository this creates a new commit object in the Git repository. This commit object uniquely identifies a new revision of the content of the repository. This revision can be retrieved later. Each commit object contains the author and the committer, thus making it possible to identify who did the change. The author and committer might be different people. The author did the change and the committer applied the change to the Git repository.|
|Branches|A branch is a named pointer to a commit. If you are working in a certain branch, the creation of a new commit advances this pointer to the newly created commit. You can create a new branch from an existing one and change the code independently from other branches.|
|Checkout|Selecting a branch to work on|
|master|Conventionally, the name of the default/main branch of a repository|
|a head|a pointer/reference to a commit object|
|HEAD (also HEAD~1)|The pointer (in .git) to the last commit of the currently checked out branch.|
|HEAD~n|The pointer to the nth last commit of the currently checked out branch.|
|HEAD^n|The nth parent (commit) of the last commit of the currently checked out branch. <br> Remember that a commit can have multiple parents. [Here] is a good explanation of the difference between HEAD~ and HEAD^|
|Revision|Represents a version of the source code. Git implements revisions as commit objects (or shortcommits). These are identified by a SHA-1 secure hash. SHA-1 ids are 160 bits long and are represented in hexadecimal.|
|Tags|A tag points to a commit which uniquely identifies a version of the Git repository. With a tag, you can have a named point to which you can always revert to. You can revert to any point in a Git repository, but tags make it easier. The benefit of tags is to mark the repository for a specific reason e.g. with a release. Branches and tags are named pointers, the difference is that branches move when a new commit is created while tags always point to the same commit.|
|URL|The location of the repository on the server|

[Here]: https://stackoverflow.com/a/2222920

<!-- TODO: This part could moved into a Gist -->
## "How to ..." 

## Temporarily move back to a previous commit
- `git checkout <commit hash>` (Detaches head)
    - I'd recommend working on the changes on another branch
    - `git checkout -b old_state <commit hash>`
- To go back: `git checkout <branch>` (The branch you were working on)

### Make changes to an already committed file (but has not yet been pushed)
- Use git stash to store the changes you want to add.
- Use git rebase -i HEAD~n (Which shows the last n commits for you to edit)
- Mark the commit in question (a0865...) for edit by changing the word pick at the start of the line into edit. Don't delete the other lines as that would delete the commits. Note: ^
- Save the rebase file, and git will drop back to the shell and wait for you to fix that commit.
- Pop the stash by using git stash pop
- Add your file with git add.
- Amend the commit with git commit --amend.
- Do a git rebase --continue which will rewrite the rest of your commits against the new one.

## Dry Run
- Most git commands have a dry-run command
- `-n` or `--dry-run`
## Cheatsheet

### git init [_\<directory\>_]

- Makes a new git repository
- Creates a `.git/` directory inside the repository

### git add [_\<filename\>_]

- Stage files to be committed
- Shown in `git status` in green
- Options:
    - `. -A --all`: Add all modified, untracked, and removed files (tracked by git)
    - `-u --update`: Add all modified files
    - `--ignore-removal .`: Add all modified and untracked files
      (but not add removed files)

Here's a handy table to distinguish the options:

|Option|Modified files|New (Untracked) files|Removed files|
|:----:|:-------:|:------------:|:-----------:|
|-A (--all)|√|√|√|
| . |√|√|√|
|-u (--update)|√|||
| --ignore-removal .|√|√||

### git rm [_\<filename\>_]

- When you remove a file, you need to remove it from the remote repo as well.
    - A normal `rm` will only remove the file locally

### git mv [_\<source\>_] [_\<destination\>_]

- Just like with `git rm`, we also need a `git mv` for any renaming, or moving
  files in the git repo

### git commit

- 
- `-m` _\<message\>_ : Write the commit message on the command line
- `-a`: (Interactive mode)
- `--amend`: Change last commit message
    - You can also make changes to a file that has already been committed,
      then do `git add <file>` and then `git commit --amend` to change the
      commit file

### git remote add origin [_\<server URL\>_]

- If you are creating a git repository from the command line, link it your
  remote (GitHub/BitBucket) repo

### git pull [origin _\<branch name\>_]

- --rebase : Add local changes on top of pulled files

### git rebase
    - `--abort`
    - `--continue`
    - `--skip`

#### Difference between merge and rebase
<https://hackernoon.com/git-merge-vs-rebase-whats-the-diff-76413c117333>

### git push [origin _\<branch name\>_]

- `-u` set upstream
-  Try `git config --global push.default simple`
    - This way you can just type `git push` and it will only push the branch
          you are working on (provided that the upstream and local branch names
			  are the same)
- `-f --force` Force push
    - Could use this with `git rebase` to change commit history on remote
          [NOT RECOMMENDED]

### git clone _\<repository URL\>_ [_\<directory\>_]

- Checkout git repo
- Get a local copy of git repository

#### Differences between forking and cloning

[Here](https://stackoverflow.com/a/6286877)
is a Stack Overflow post that explains the difference

- Forking is in **GitHub**
    - You can fork a repo into your own [GitHub] account
    - Make changes
    - Ask for pull request (to contribute)
- Cloning is just having a local copy
    - You can only contribute if you are a collaborator

### git grep
- `grep` on all files tracked by git
    - If there are directories in repo, then does grep recursively
- Options:
    - `-n`: Print line number
    - `-l`: Print the filenames where pattern matches

### git stash [_pop/apply/drop_]

- Save all your local changes [onto a stack] and restore your branch to the
  state of the last pull
- Use `git stash list` to look at the stack of git-stashes
- Use `git stash pop` or `git stash apply` to restore the "stashed" work

#### Difference between `pop` and `apply`

- While both merge the last stashed changes to your local repository,
`pop` also drops the the topmost stash, and `apply` doesn't

- Simply put: `git stash pop` = `git stash apply` + `git stash drop`

### git ls-files
- List the files git is tracking

### git status

- Show the current status of the branch you are working on
- See untracked files and files added/removed

### git log

- View a list of commits starting from the most recent one

### git show
- Show git objects (Kind of obvious)        

### git blame

- Show the last revision and author who last modified the file

### git branch

- List all branches

### git checkout [_\<branch\_name\>_]

- Switch to branch
- `-b/-B`: Create a new branch and switch to that
- `-m`: Merge branch with current working branch.

### git reset

- Reset git branch to a previous state
    - Warning: You will lose any un-pushed changes if you use this
- `--soft HEAD^`: Un-staged last commit

### git config

- Set up your git config file
- [Here] is a

### git fetch

- Fetch updates from remote, but not merge them to local
- `--all`: fetch updates from all files in repo
    - Use this w/ `git reset --hard origin/<branch_name>`

### git cherry-pick

- Push a commit from another branch onto the current branch

### git worktree

- Work on more than one branch at once

## Better Explained
- [Git for Beginners: The Definitive Practical Guide](https://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide#320140)
- [Lars Vogel's Git Tutorial](http://www.vogella.com/tutorials/Git/article.html#introduction-into-version-control-systems)
- [Github's Git Cheatsheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
- [Getting Started with Git](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics)
- [Practical Introduction to Git](https://codeburst.io/git-good-part-a-e0d826286a2a)
