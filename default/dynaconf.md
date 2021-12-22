---  
Title: dynaconf  
Category: default  
Author: Kevin Loughead  
Date: 2021-12-06  
Tags:   
---  

1. Do this inside project `dynaconf init -f <markup-lang>`
2. Add settings to the `settings.<markup-lang>` file that is generated
3. Access settings like this

```python
from config import settings

print(settings["key"])
```