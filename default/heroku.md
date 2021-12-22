---
Title: heroku
Category: default
Author: Kevin Loughead
Date: 2021-10-25
Tags:
---

## Deploy an app to heroku

```bash
# creates a new remote called heroku with random name
heroku create

# creates project with given name (if available)
heroku create project-name

# rename app
heroku apps:rename new-name --app old-name
# after renaming app, change remote
git remote rm heroku
heroku git:remote -a todo-name-blog

# deploy
git push heroku main
```

## Other Commands
```bash

# run heroku app locally
heroku local web

# run heroku app locally with nodemon
nodemon --exec 'heroku local'
```

## Links
1. set up MongoDB https://www.mongodb.com/developer/how-to/use-atlas-on-heroku/
