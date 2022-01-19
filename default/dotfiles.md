---
Title: dotfiles
Category: default
Author: Kevin Loughead
Date: 2021-12-12
Tags:
---

## immediate
- [] write install script
		- should install micro, watson, pyenv
		- should ask "do you have VSCode and Terminal installed"
			- if yes, should call set_all_configs
			- if no, should say "VSCode and Terminal config files were
			  not installed. Go install them and then run `set_windows_configs`"

## Long term

- [] figure out better way to iterate through files (see .bash_profile)
- [] move practicum projects to `~/practicum/projects`
- [] refactor functions in window.sh
- [] figure out why can't open $terminalconfig etc. with vscode
  - works fine with micro, nano
  - code wants to open it with it's windows file path

1. Making $HOME a git repo (avoids symlinks) - https://drewdevault.com/2019/12/30/dotfiles.html
2. How to set up on new machine

```
cd ~
git init
git remote add origin https://github.com/kvnloughead/dotfiles
git fetch
git checkout -f main
```

