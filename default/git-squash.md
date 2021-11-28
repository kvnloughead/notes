---  
Title: git-squash  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-23  
Tags:   
---  

```bash
# squash last three commits
git reset --soft HEAD~3
git commit

# start commit message with concatenation of existing messages
git reset --soft HEAD~3 
git commit --edit -m"$(git log --format=%B --reverse HEAD..HEAD@{1})"
```

