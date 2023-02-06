---  
Title: node  
Category: default  
Author: Kevin Loughead  
Date: 2023-01-02  
Tags:   
--- 

```javascript
// to get return value from shell commands
const { execSync } = require('child_process');
const res = execSync(`commands`).toString();
``
