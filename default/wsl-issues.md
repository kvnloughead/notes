---  
Title: wsl-issues  
Category: default  
Author: Kevin Loughead  
Date: 2022-03-25  
Tags:   
---  

## Nasty recurring issues with WSL interactions with Windows programs

First thing to try:

1. `sudo apt update && sudo apt upgrade`
2. `wsl --shutdown`
3. restart wsl

One thing that seemed to resolve the issue at one point in time is

1. `DISM /online /enable-feature /featurename:VirtualMachinePlatform /norestart`
2. Reboot
3. `DISM /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart`
4. Reboot

But the issue came back.
