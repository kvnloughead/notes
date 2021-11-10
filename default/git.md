---  
Title: git  
Category: default  
Author: Kevin Loughead  
Date: 2021-10-13  
Tags:   
---  

## Branches
```bash
# rename local branch
git branch -m <oldname> <newname>

# to delete a branch locally and on github
git branch -D <localBranchName>
git push origin --delete <remoteBranchName>

# to change remote repo
git remote set-url <repo-name> <new-repo>
```

## New Repos
```bash
# To set up new remote repo from command line
gh create-repo project-name
git remote add origin $GH/project-name.git
git push -u origin main
```

## Undo Commits
```bash
# To undo a commit and redo
git commit -m "Something terribly misguided" # (0: Your Accident)
git reset HEAD~                              # (1)
(edit files as necessary)                    # (2)
git add .                                    # (3)
git commit -c ORIG_HEAD                      # (4)
```

Explanation - [source](https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git)
1. This command is responsible for the undo. It will undo your last commit while leaving your working tree (the state of your files on disk) untouched. You'll need to add them again before you can commit them again).
2. Make corrections to working tree files.
3. git add anything that you want to include in your new commit.
4. Commit the changes, reusing the old commit message. reset copied the old head to .git/ORIG_HEAD; commit with -c ORIG_HEAD will open an editor, which initially contains the log message from the old commit and allows you to edit it. If you do not need to edit the message, you could use the -C option.