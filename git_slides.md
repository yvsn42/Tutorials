# Version Control

- Keep track of changes to files
    - Revert back to older versions if needed

- Merge the contributions of multiple developers

- Accountability - Who wrote the code?

# Before you start...
- Configure git with your name and e-mail address
```sh
git config --global user.name "Firstname Lastname"
git config --global user.email "name@ucdavis.edu"
```
# How to create a git repository?

- Create a new repository on GitHub (or GitLab, BitBucket, Gitl, etc.)
  - Name your repository and specify whether it should be public or private
- Make the directory in which you want to make a git repo

- Initialize a git repository on your local machine
```bash
mkdir <repo_name> && cd <repo_name>
git init # initialize the curren directory as a Git repository
```

- Connect your local git repo to the remote (GitHub)
```sh
git remote add origin https://github.com/<username>/<repo_name>.git
git push --set-upstream origin master
```

# An interlude: Some fundamental terms

- **Index**: A staging area where modifications are kept before being committed

- **HEAD**: A pointer to the last commit you've made

- **Commit**: An object that contains 3 things:
      - A set of files and the changes made to them at a given point in time
      - A reference to the parent (previous) commit(s)
      - A hash (SHA1) value (40 characters) to uniquely identify the commit

# How to push your code to Github
- Stage your file(s)s to the index
```sh
git add [file(s)]
```
- Commit your changes in the index with a message
```sh
git commit -m "Your message about the commit"
```

- **Alternatively**, you can combine the above two commands into one:
```sh
git commit -m "Your message about the commit" [file(s)]
```

- Push your changes to the remote repo (Github)
```sh
git push origin master # Push your commit(s) to the master branch on origin (Github)
```

# How to get the most recent code from the Github repo
```sh
git pull origin master # fetches the code and merges it into the current directory
```

- Running the following two commands should also do the same thing
```sh
git fetch origin master
git merge FETCH_HEAD
```

# How do you see what files have been changed or committed?
```sh
git status
```

- Shows a summary of the repo. This includes:
    - What branch you are on?
    - What files have been modified?
    - What files you are about to co

# File States
- **Untracked**: The file is not being tracked by git. It is in the git worktree but
  has not been staged
- **Tracked**: The file is tracked and committed, and there are no local changes
- **Staged**: The file has been changed, and has been put in the index by `git add`
- **Modified**: The file is tracked by git and has changes that haven't been staged.

# How to view changes to files
- Given that the files are tracked by git, you can run:
```sh
git diff 
```

# How to view the git history/previous commits
- To see the list of commits made:
```sh
git log # Most recent commit is at the top
git log --oneline # For a more condensed output
```

- To view changes made on a particular commit:
```sh
git show <commit_hash>
```

# How do I save my changes without committing them?
- You can temporarily save changes using:
```sh
git stash
```
- This makes it easy to move between branches or merge without having to commit
- The "stash" is a stack data structure (LIFO)

- To restore the most recently stashed changes:
```sh
git stash pop   # Note: The saved changes are popped of the stack after this
git stash apply # Same as the above, but the changes still remain in the stack
```

# How to create a new branch and switch to that branch
- Another feature of git is to split work into independent branches

- The main branch or the branch you initially start working on when you create the repo is `master`

- To create a new branch:
```sh
git branch [branch-name]  #create a new branch at the current commit
```

- List all local branches (and see which branch you are on)
```sh
git branch
```

- Switch to another branch
```sh
git checkout <branch_name>
```
- **Note:** You can only checkout to a branch if you've committed or stashed any changes
- Create a new branch and switch to it
```sh
git checkout -b <branch_name>
```

# Step 6: Merge your branch
- Say you want to merge `branch1` to `master`
- Make sure you are checked out to `branch1`
- Make sure the branch is clean (All changes are committed or stashed)
- Then run:
```
git merge master # merge the specified branch’s history into the current one
```

# How to deal with merge conflicts?
- When you pull code or merge branches, you'll often encounter merge conflicts
  - These occur when both branches have made changes to the same line of code in a file

- Run `git status` to see the conflicting files under `Unmerged Paths:`
- Run `git diff` to see what lines in the files conflict
- Open the files and keep the changes you want and discard the rest
- `git add` and `git commit` the files

# Download existing git repos 

```sh
git clone [url] #retrieve an entire repository from a hosted location via URL
```

# Other git commands
- Point each line of the file to the commit and the author that last changed that line
```sh
git blame
```
- delete the file(s) from project and stage the removal for commit
```sh
git rm [file(s)]
```
- Move files within the repo that git tracks
```sh
git mv [existing-path] [new-path]
```

- Need a reminder for git commands?
```sh
git help
```


