---
Title: wsl-backup
Category: default
Author: Kevin Loughead
Date: 2022-01-18
Tags:
---


Script
```
rsync --archive --verbose --delete /home/<username>/ /mnt/c/Users/<username>/wsl2-backup/
```
1. Works like a charm. Accidentally copied first to my wsl
user dir and it was _fast_. Never seen node_modules fly so
fast.
2. Copy to windows file system worked to, but much slower
	a. made me think, I need to try to ignore node_modules
	b. wound up ignoring node_modules, .npm, .pyenv, tutor, practicum projects
	c. should delete backup to do it fresh and see what else should be ignored
3. also need, might be better to keep multiple backups
	a. try using --backup, --backup-dir flag, --suffix
	b. reference man page
4. also, not sure about that --delete flag, what does that do?

Task Scheduling
1. Started with this article https://stephenreescarter.net/automatic-backups-for-wsl2/#:~:text=Automating%20WSL2%20Backups&text=Using%20the%20Task%20Scheduler%2C%20we,the%20Windows%20Administrative%20Tools%20folder.&text=With%20the%20Task%20Scheduler%2C%20we,backup%20up%20to%20a%20schedule.
2. when tying to create task, realized that there was no config for
windows 11 options. Googling did not immediately provide a reason for
this, so I found another article that shows how to create task on
windows 11
3. click Create Basic Task instead of Create Task
4. follow wizard, more reasonable time
5. TODO
