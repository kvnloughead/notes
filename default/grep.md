---  
Title: grep  
Category: default  
Author: Kevin Loughead  
Date: 2021-09-15  
Tags:   
---  

```bash
# find pattern in file
grep <pattern> <filename>

# find pattern in all subdirectories
grep -r <pattern> .


# exclude node_modules
grep -r --exclude-dir=node_modules <pattern> .

# exclude multiple directories
grep -r --exclude-dir={node_modules,.git} <pattern> .

# pipe man page into grep
man curl | grep -- <pattern>
```
