---  
Title: python-unittest  
Category: default  
Author: Kevin Loughead  
Date: 2022-01-04  
Tags:   
---  

## Test suite syntax

```python
class TestShow(unittest.TestCase):
    
    @classmethod
    def setUpClass(cls):
        """Runs before the tests."""
        cls.something = '...'
  
  @classmethod
    def tearUpClass(cls):
        """Runs after the tests."""
        pass

    def test_something(self):
        """A test case."""
        print(self.something) # '...'
```