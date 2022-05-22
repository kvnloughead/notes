---  
Title: rails-routes  
Category: default  
Author: Kevin Loughead  
Date: 2022-05-21  
Tags:   
---  

[Routing guide](https://guides.rubyonrails.org/routing.html)

```rb
# define a route in config/routes.rb
Rails.application.routes.draw do
  root 'controller#action'
end

# controller corresponds to controller_controller.rb
# action is the name of a function defined in controller_-_controller.rb
```

```rb
# corresponding controller_controller.rb
class ApplicationController < ActionController::Base
  def action
    render html: "hello, world!"
  end
end
```

