---  
Title: netstat  
Category: default  
Author: Kevin Loughead  
Date: 2023-01-22  
Tags:   
---

- on Ubuntu, install `net-tools`. The `netstat` command comes with it

```bash
# to check if a service is running
sudo netstat -ltnp | grep service-name
```
