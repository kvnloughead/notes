---  
Title: rails-validation  
Category: default  
Author: Kevin Loughead  
Date: 2022-05-22  
Tags:   
---  

Validate data in `models/model-name.rb`. 

## Examples 

```rb
class ModelName < ApplicationRecord
  # restrict character length of content field to 140
  validates :content, length: { maximum: 140 },
                      # must be present
                      presence: true
end
```