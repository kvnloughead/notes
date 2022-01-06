---  
Title: python-relative-imports
Category: default  
Author: Kevin Loughead  
Date: 2022-01-02  
Tags:   
---  

## Python relative imports suck
Had a lot of trouble running a simple test file in `tests/test_something.py` that imports something from the parent directory. Here is one thing I found that works. Set up the file like this:

```python
from show import show

def test_show():
    # do stuff

test_show()
```

and run the program from the parent directory with `python3 -m tests.test_show`. You may also need `__init__.py` files in parent and `tests` directories.

I
