---  
Title: argparse  
Category: default  
Author: Kevin Loughead  
Date: 2021-12-02  
Tags:   
---  

## nargs

Values
- `nargs=N` - consumes `N` args
- `nargs='?'` - consumes 1 arg if possible; otherwise, uses default value
- `nargs='*'` - gathers all args into a list 
- `nargs='+'` - gathers all args into a list and throws error if 0 args