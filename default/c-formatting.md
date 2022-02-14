---  
Title: c-formatting  
Category: default  
Author: Kevin Loughead  
Date: 2022-02-10  
Tags:   
---  

The clang-format vscode extension doesn't play nicely with VScode but it doesn't seem necessary either. 
- Just use the C/C++ extension and format with `.clang-format` file in project (YAML)
- Or apply rules in VScode settings.json
  - Example
  ```json
  "C_Cpp.clang_format_format": "{ BasedOnStyle: Google, IndentWidth: 4, ColumnLimit: 0}",
  ```
- Format styles https://clang.llvm.org/docs/ClangFormatStyleOptions.html