---
Title: cron
Category: default
Author: Kevin Loughead
Date: 2022-03-15
Tags:
---

## Commands

```sh
crontab -l # show crontab file for current user
crontab -e # edit jobs for current user
```

## Cron job format

```
# |-------------- min (0 - 59)
# | |--------------- hour (0 - 23)
# | | |---------------- day of month (1 - 31)
# | | | |----------------- month (1 - 12)
# | | | | |------------------ day of week (0 - 6)
# | | | | |              [Sunday to Saturday; names also work; 7 is also Sunday]
# | | | | |
# * * * * *  command to exeute
```

## WSL Automatic Setup

By default cron jobs won't run automatically. Steps to solve:

1. Open `sudoers` file with `sudo visudo`
2. Enter this at the bottom to disable passwords for starting cron service
   `%sudo ALL=NOPASSWD: /usr/sbin/service cron start`
3. Go to Windows task scheduler
4. Set up basic task to run when computer starts

- Program/script should be set to `C:\Windows\System32\wsl.exe`
- Add arguments: `sudo /usr/sbin/service cron start`

5. Click "open properties" checkbox before finishing

- In properties popup, check "Run whether user is logged in or not"

- [How to make them run automatically on WSL](https://www.howtogeek.com/746532/how-to-launch-cron-automatically-in-wsl-on-windows-10-and-11/)

## Links

- [How to](https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/)
- [Syntax for various time intervals](https://ostechnix.com/a-beginners-guide-to-cron-jobs/)
