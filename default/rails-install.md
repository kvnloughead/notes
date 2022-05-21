---
Title: rails-install
Category: default
Author: Kevin Loughead
Date: 2022-05-16
Tags:
---

## Ruby on Rails installation

[source](https://gorails.com/setup/ubuntu/18.04)

```bash
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

```bash
sudo apt-get update
sudo apt-get install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev nodejs yarn
```

```bash
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL
```

```bash
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL
```

### Install Gems

After this, you still need to run install a ruby version and gems. Example:

```bash
rbenv install 3.1.2
rbenv global 3.1.2
gem install rails -v 7.0.2.4
gem install bundler
rbenv rehash # must run this command after installing gems
```

### Install webpacker

```bash
# Necessary to run the devserver
rails webpacker:install
```
