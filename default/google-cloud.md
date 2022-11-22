---
Title: google-cloud
Category: default
Author: Kevin Loughead
Date: 2021-12-15
Tags:
---

## Setup for E2-micro for fullstack MERN app

Temp server

- domain http://deleteme.students.nomoreparties.site
- IP 34.105.116.241

### 1. Create server

1. choose E2-micro, US-west1, Standard persistent disk <= 30GB
2. check buttons for HTTP and HTTPS
3. enable port 3000
4. add SSH pub key
5. connect once via GCP gui before trying from terminal

### 2. Prep server

1. install node

```bash
# replace version with the version you are using locally
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs
```

2. install MongoDB
   https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/

```bash
# install
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org

# run
sudo systemctl start mongod

# automatically start on system reboot
sudo systemctl enable mongod

# check status
sudo systemctl status mongod
```

3. install git

```bash
sudo apt update
sudo apt install git
```

4. clone project and set it up

```bash
git clone <repo-url>
cd project-dir
npm i && npm run start
```

5. check work
   Now you should be able to send a request like this

```bash
curl http://<ip>:3000
```

### 3. pm2 process manager

First, stop app if it is running

```bash
sudo npm install pm2 -g
cd ~/project-dir
pm2 start app.js
pm2 startup
# `pm2 startup` prints the next command you need to run to the terminal
# run that next command
pm2 save
```

Checkwork by sending a request to `curl http://<ip>:3000`

### 4. Register domain names

- Register domain names.
- wait a bit
- now you should be able to request like this `curl http://<domain>:3000`

### 5. HTTP with NGINX

#### a.

```bash
# install nginx
sudo apt-get update
sudo apt install -y nginx

# install and setup ufw
sudo apt install ufw
sudo ufw allow 'Nginx Full'
sudo ufw allow OpenSSH
sudo ufw enable

# start and enable nginx
sudo systemctl enable --now nginx

# at this point if you navigate in browser to domain you should see an nginx
# welcome screen
```

#### b.

- Open config file — `sudo nano /etc/nginx/sites-available/default`
- replace contents with the following (delete lines with Ctrl+K):

```bash
server {
  listen 80;

  server_name <domain>.students.nomoreparties.site www.<domain>.students.nomoreparties.site;

  location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }
}
```

- change both instances of `<domain>` to your domain
- check config syntax with `sudo nginx -t`
- restart nginx with `sudo systemctl reload nginx`

#### c. Check work

Now you should be able to send requests without specifying port: `curl://https://<domain>`

### 6. HTTPS with SSL and Certbot

https://certbot.eff.org/

Instructions for Ubuntu 20.04

- install snapd (if on Ubuntu 20.04, it's already installed)
- `sudo snap install core; sudo snap refresh core`
- `sudo apt-get remove certbot`
- `sudo snap install --classic certbot`
- `sudo ln -s /snap/bin/certbot /usr/bin/certbot`
- `sudo certbot --nginx`
- follow instructions
- restart nginx `sudo systemctl restart nginx`

Check work — now you should be able send requests via HTTPS `https://<domain>`

### 7. Frontend

#### Getting the code on the server

On server

- on server, run `cd ~`. You should now be in the same directory as your backend.
- create a new folder `frontend`. Name is arbitrary.

In local repo

- build project `npm run build`
- add key to ssh-agent `ssh-add ~/.ssh/id_ed25519`
- copy build folder to server, `scp -r -i <path/to/ssh/key> ./build/* <practicumuser>@<domainname>.students.nomoreparties.site:/home/<username>/frontend`

Now the contents of `build/` are in `~/frontend/` on the server.

- To make redeploying easier, add a deploy script to your frontend `package.json`. Just make the appropriate alterations:

```json
"deploy": "npm run build && scp -r ./build/* practicumuser@domainname.students.nomoreparties.site:/home/practicumuser/around-frontend"
```

#### Setting up NGINX

- open config file `sudo nano /etc/nginx/sites-available/default`
- here is what the current config should look like

```
server {
  server_name domainname.students.nomoreparties.site www.domainname.students.nomoreparties.site;

  location / {
    proxy_pass http://localhost:3000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }

  listen 443 ssl; # managed by Certbot
  ssl_certificate /etc/letsencrypt/live/domainname.students.nomoreparties.site/fullchain.pem; # managed by Certbot
  ssl_certificate_key /etc/letsencrypt/live/domainname.students.nomoreparties.site/privkey.pem; # managed by Certbot
  include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
  ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}

server {
  if ($host = www.domainname.students.nomoreparties.site) {
    return 301 https://$host$request_uri;
  } # managed by Certbot

  if ($host = domainname.students.nomoreparties.site) {
    return 301 https://$host$request_uri;
  } # managed by Certbot

  listen 80;

  server_name domainname.students.nomoreparties.site www.domainname.students.nomoreparties.site;
  return 404; # managed by Certbot
}
```

Changes to make:

1. Copy/paste the first server block, so that there are now three server blocks, and the first two are identical. Use Alt + 6 to copy and Ctrl + U to paste.

2. Change the `server_name` in the first server block like this:

```
server {
  server_name api.domainname.students.nomoreparties.site;
  # ...
}
```

This is the server block for our backend.

3. Change the second server block like this:

```
server {
  # leave server_name block alone
  server_name domainname.students.nomoreparties.site www.domainname.students.nomoreparties.site;

  # add in a root directive -- make sure it points to your build files
  # this tells nginx where to look for the frontend build
  root /home/username/frontend;

  # change location block to this. This tells nginx not to try to server index.html from subdirectories,
  # like /signup/index.html
  location / {
    try_files $uri $uri/ /index.html =404;
  }

  # ...
}
```

This server block serves our frontend.

After all this, the run

- `sudo nginx -t`
- `sudo systemctl restart nginx`

```

```
