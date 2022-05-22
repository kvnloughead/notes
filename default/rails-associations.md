---  
Title: rails-associations  
Category: default  
Author: Kevin Loughead  
Date: 2022-05-22  
Tags:   
---  

## Examples

A `user` can be associated with many `posts`. 
- Note the difference in plurality. 
- This will expose a property `posts` for each user containing an array of the user's posts

```rb
# app/models/user.rb
class User < ApplicationRecord
  has_many :posts
end
```

```rb
# app/models/post.rb
class User < ApplicationRecord
  belongs_to :user
end
```