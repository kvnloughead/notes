---  
Title: bash-parameters  
Category: cheatsheets  
Author: Kevin Loughead  
Date: 2021-08-07  
Tags: bash  
---  

```bash
$0            #	the first positional parameter, equivalent to argv[0] in C, see the first argument
$FUNCNAME     #	the function name (attention: inside a function, $0 is still the $0 of the shell, not the function name)
$1            # … $9	the argument list elements from 1 to 9
${10} … ${N}	# the argument list elements beyond 9 (note the parameter expansion syntax!)
$*            #	all positional parameters except $0, see mass usage
$@            #	all positional parameters except $0, see mass usage
$#            #	the number of arguments, not counting $0

# source https://wiki.bash-hackers.org/scripting/posparams
```