---  
Title: gnome  
Category: default  
Author: Kevin Loughead  
Date: 2023-01-19  
Tags:   
---  

Some extensions are problematic to install on firefox, so install an extension manager: `sudo apt install gnome-shell-extension-manager`. 

# extensions

1. gnome-tweaks - various small tweaks
2. switcher - simple app switcher (https://github.com/daniellandau/switcher)

    ```
    # I was unable to use it without explicitly setting the command
    dconf write /org/gnome/shell/extensions/switcher/show-switcher "['<Super>tab']"
    ```

