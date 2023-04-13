---
Title: ssh
Category: default
Author: Kevin Loughead
Date: 2022-03-06
Tags:
---

```bash
# Generate new key
ssh-keygen -t ed25519 -C "kvnloughead@gmail.com"

# start the ssh-agent in the background
eval "$(ssh-agent -s)"

# add key to ssh-agent
ssh-add ~/.ssh/id_ed25519
```

## opening PC to SSH (linux)

https://linuxhint.com/enable-ssh-linux-mint/

```
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl status ssh

# if firewall is enabled
sudo ufw allow ssh
sudo ufw enable
sudo ufw reload
```

## ssh into another PC on local network

First, make sure you have an SSH key on the computer, that the agent is on and the key is added. Then you can copy the key to the other machine:

```ssh
ssh-copy-id username@ip-address
```

On Linux Mint, the best way to get your ip address is to go to the network settings and select the IPv4 address.
