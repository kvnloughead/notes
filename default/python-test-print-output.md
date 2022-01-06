---  
Title: python-test-print-output  
Category: default  
Author: Kevin Loughead  
Date: 2022-01-02  
Tags:   
---  

To test functions that print, rather than `return`, try this

```python
# Run this test with `python3 -m tests.test_show`
import io
import sys

from foo import foo

def test_foo():
    capturedOutput = io.StringIO()                 # Create StringIO object
    sys.stdout = capturedOutput                    # and redirect stdout.
    foo()                                          # Call function.
    sys.stdout = sys.__stdout__                    # Reset redirect.
    print('Captured', capturedOutput.getvalue())   # Now works as before.

test_foo()
```