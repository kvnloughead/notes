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

## opening PC to SSH
- [open port 22](https://linuxconfig.org/how-to-open-ssh-port-22-on-ubuntu-20-04-focal-fossa-linux)
- [to enable password auth](https://serverpilot.io/docs/how-to-enable-ssh-password-authentication/)
- [enable ssh service on 22.04](https://ubuntuhandbook.org/index.php/2022/04/enable-ssh-ubuntu-22-04/)

   In practice, I needed to run

   ```bash
   sudo apt install ssh
   sudo systemctl enable ssh
   ```

   Running the second command with `sshd` failed.

## ssh into another PC on local network

I haven't succeeded so far in using ssh-copy-id, but it works to pass the public key via email and add it to `~/.ssh/authorized_keys` on the other machine. Then log in using

```bash
# ip not needed if they share ip addressed
ssh username@computer-name
```

However, this only works when the lid is not closed. Solution:

```bash
sudo vim /etc/systemd/login.conf
```

Then uncomment `#HandleLidSwitch=suspend` and change it to `ignore`  

