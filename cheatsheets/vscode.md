---  
Title: vscode  
Category: cheatsheets  
Author: Kevin Loughead  
Date: 2021-08-07  
Tags: shortcuts,editor  
---  

Notes from Phoenix about useful keyboard shortcuts. Look up shortcut with `ctrl + shift + p`.

Copy line up/down
Move line up/down — works on multiple lines if you select a range covering multiple lines
Toggle line comment
Add selection to next find match (for multicursor editing), and its companion, Select All Matches for the equivalent of holding the first shortcut down until all of them are selected
Add cursor below (more multicursor editing)
Show Explorer / Show Run and Debug — The first also selects the current file in the file viewer, so you can delete or rename it with the keyboard, and can be used again to go back to the editor afterward
Delete Line (I think I had to bind this myself, to cmd-backspace)
Format Document (though if I'm using autoformat, I'll usually have it format-on-save instead)
Go to bracket — jumps to the matching bracket  ([](){}) for the one your cursor is on now
Join Lines — takes this and the next line and combines them into one line
Go to Definition — jumps to wherever the variable or function under the cursor is defined. This one is a huge timesaver
View: Open previous/next editor — go left/right one tab
Find — in current file
Search: Find in Files — search all files
Go to file...
Cut — when on a single line, cuts the entire line and will paste it as a whole line if you paste it somewhere else, even if the cursor isn't at the start of the line when you paste
macos ones that apply to all text editing:
cmd-left/right — go to beginning or end of line
option-left/right — go left/right one word at a time
(and add shift to any cursor moving action to select from current position to the new position.)
^ these are also particularly useful when doing multi-cursor editing on lines that have variable length, to re-align the cursors by word boundaries
ctrl-t swaps the previous and next characters — good for fixing typos from typing too fast. This is actually from emacs, but works in all macos text fields as well