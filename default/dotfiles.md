---
Title: dotfiles
Category: default
Author: Kevin Loughead
Date: 2021-12-12
Tags:
---

## Second attempt -- Bare Repo Dotfiles

Resources

- great explanation of bare repo dotfiles https://stegosaurusdormant.com/bare-git-repo/#fnref:no-home-git-repo
- example of bare repo dotfiles https://github.com/kalkayan/dotfiles

### Inital setup

1. Create a new bare Git repo in `~/.dotfiles` to store the history for your dotfiles.

```bash
git init --bare $HOME/.dotfiles
```

2. Create alias for running git commands for the dotfiles repo

```bash
alias dotgit='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'

# --git-dir tells git where history is
# --work-tree tells git where working tree is
# add this to .bashrc
```

3. Ignore untracked files

I am torn between this and `echo "*" >> .gitignore`.

```bash
dotgit config status.showUntrackedFiles no

# helpfully, this prompts with "(use -u to show untracked files)" when you run `git commit`
# but less helpfully, the `-u` flag shows everything in .dotfiles bare repo...
```

4. Setup remote repo

```bash
dotgit remote add origin remote-url
```

###

Workflow

```bash
dotgit add some-file
dotgit commit -m "message"
dotgit push origin main
```

### Setup a new machine

1. Clone repo as non-bare repository

```bash
git clone \
   --separate-git-dir=$HOME/.dotfiles \
   remote-url \
   dotfiles-tmp

# --separate-git-dir means history should go in $HOME/.dotfiles
# snapshot will go in dotfiles-tmp
```

2. Copy snapshot to where each file should go

```bash
rsync --recursive --verbose --exclude '.git' dotfiles-tmp/ $HOME/

# I'm not sure why `cp` isn't being used. And not sure why `.git` needs to be
# excluded. I would have expected `.git` to only reside inside `.dotfiles`.
```

3. `rm -rf dotfiles-tmp`

## First attempt -- Repo in $HOME with `.gitignore` of `*`

1. Article - https://drewdevault.com/2019/12/30/dotfiles.html
2. How to set up on new machine

```bash
cd ~
git init
git remote add origin repo-url
git fetch
git checkout -f main
```

3. Problems
   a. Everything under $HOME is already in a git repo.So running a command for repo X in some non-git directory inside of $HOME will actually run the command in your dotfiles repo. Not good.
   b. Impossible to use override global settings in a nested repo? If not impossible, at least annoyingly difficult. Learned this when trying to push from a separate account from inside a nested repo.
   c. README in $HOME
