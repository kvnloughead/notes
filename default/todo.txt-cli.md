---  
Title: todo.txt-cli  
Category: default  
Author: Kevin Loughead  
Date: 2023-01-25  
Tags:   
--- 

Installation

- Was necessary to use sudo on wsl2. 
- fails without explicitly specifying config dir

```bash
make 
sudo make install CONFIG_DIR=/home/kevin/.config INSTALL_DIR=/usr/bin BASH_COMPLETION=/usr/share/bash-completion/completions
make test
``` 
