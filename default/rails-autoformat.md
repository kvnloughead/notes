---  
Title: rails-autoformat  
Category: default  
Author: Kevin Loughead  
Date: 2022-05-22  
Tags:   
---  

Ruby files themselves are autoformatted once you install rufo extension on vscode. 

Formatting `erb` files need more work. Here's something that worked for me, 
although I'm not crazy about all the default settings. 

1. Follow this [post](https://aleksandar.xyz/blog/formatting-ruby-and-erb-in-vscode/): 

   - install Ruby VSCode extension, rufo and ERB Formatter/Beautify
   - add this to VSCode settings

         ```json
         "files.associations": {
             "*.erb": "erb"
           },
           "[erb]": {
             "editor.formatOnSave": true,
             "editor.defaultFormatter": "aliariff.vscode-erb-beautify",
           },
         ```
2. But then I was getting errors about htmlbeautifier, so I installed that
gem with `gem install htmlbeautifier`.