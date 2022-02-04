---  
Title: cln  
Category: default  
Author: Kevin Loughead  
Date: 2021-11-28  
Tags:   
---  

- fix rename
- [] check for existing notes with same name in different categories
    - when attempting to delete
    - when attempting to edit
- [] have default EDITOR read from system defaults
- [] testing
- [] --exclude-metadata flag for `grep` and/or `find`
- [] search by metadata (via grep and/or find)
- [] add -y flag to accept in yes/no scenarios
- [] prompt to create new notes / tags
- [x] rename notes
- [] add readme for .notes and .dev-notes on initial setup
- [x] config file
  - [x] editor, author, dev
  - notes directory
- [] try getting this set up on another machine
- [] auto-complete
- [] metadata - last updated
- [] tags
- [] improve metadata 
- [] enable different filetypes (consider metadata)
  - [] maybe refactor note into class
- [] improve `opendir`
  - currently if `nano` is default editor it fails silently, opening a file instead
  - possible solution - add IDE option to override EDITOR in the case of opendir
  - probably similar issues with other command line editors
- [] make `cln foo` do the same as `cln edit foo`

## better github integration
- when first push is attempted, if remote is not setup, prompt through creation via gh.new script
