---  
Title: dynaconf  
Category: default  
Author: Kevin Loughead  
Date: 2021-12-06  
Tags:   
---  

## Startup
1. Do this inside project `dynaconf init -f <markup-lang>`
2. Add settings to the `settings.<markup-lang>` file that is generated
3. Access settings like this

```python
from config import settings

print(settings["key"])
```

## Loading settings from files outside of pwd
For some cases it is as easy as adding absolute paths to the settings files to the `settings_files` option of the `Dynaconf` class. 

But it is trickier to manage with the home directory. Here is a sample `__init__.py` file that should resolve this:

```py
# source https://www.nicholasnadeau.com/post/2020/5/tip-of-the-day-user-based-python-configurations-with-dynaconf/
from pathlib import Path

from dynaconf import LazySettings  # type: ignore

ENVVAR_PREFIX_FOR_DYNACONF = "MYPACKAGE"
ENV_SWITCHER_FOR_DYNACONF = f"{ENVVAR_PREFIX_FOR_DYNACONF}_ENV"
ENVVAR_FOR_DYNACONF = f"{ENVVAR_PREFIX_FOR_DYNACONF}_SETTINGS"
DYNACONF_SETTINGS_FILE = Path.home() / ".mypackage.toml"
settings = LazySettings(
    ENV_SWITCHER_FOR_DYNACONF=ENV_SWITCHER_FOR_DYNACONF,
    ENVVAR_FOR_DYNACONF=ENVVAR_FOR_DYNACONF,
    ENVVAR_PREFIX_FOR_DYNACONF=ENVVAR_PREFIX_FOR_DYNACONF,
    SETTINGS_FILE_FOR_DYNACONF=DYNACONF_SETTINGS_FILE,
)
```


- You should be able to use `.env` to override values, but I haven't figured out how to do it yet