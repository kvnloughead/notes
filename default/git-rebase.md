---  
Title: git-rebase  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-13  
Tags:   
---  

## To squash previous <x> commits
1. run `git rebase -i HEAD~<x>`
2. modify the list of commits. Example

```
# change this
pick hash-1 message-1
pick hash-2 message-2

# to this
pick hash-1 message-1
squash hash-2 message-2
```

Squashes the second commit into the first. Then you can change the commit message.

## To add stuff to an older commit
See [here](https://stackoverflow.com/questions/2719579/how-to-add-a-changed-file-to-an-older-not-last-commit-in-git)

```bash
git add <my fixed files>
git commit --fixup=OLDCOMMIT
git rebase --interactive --autosquash OLDCOMMIT^
```

See the explanation in the link. Sadly it is not as simple as it seems. 
