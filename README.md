# How to deploy Meteor 1.8 App

## 1. Manually

Deploy from local Meteor 1.8 to remote server with (Debian 9)/Ubuntu 16 OS
### On remote server

Install nvm
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```
```
source ~/.zshrc
```
Install Node 8.11.4
```
nvm install 8.11.4

# check installed
nvm ls

# Check available
nvm ls-remote
```

or alternative, without NVM
```
# Using Ubuntu
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -sL https://deb.nodesource.com/setup_8.x | bash -
apt-get install -y nodejs
```
Install npm (if needed)
```
npm install npm@latest -g
```
Install Mongo
```
apt-get install mongodb-server
```
Install forever to launch scripts forever :)
```
npm install -g forever
```
### Local machine (MacOS)
Build bundle
```
meteor build ./../build  --architecture=os.linux.x86_64
```
Copy to remote (SSH with keys)
```
scp ../build/archive.tar.gz server_name:/path/to/meteor/folder/
```
### Server
Unpack bundle archive
```
cd /path/to/meteor/folder/
tar xvf archive.tar.gz
cd bundle/
```
Install dependencies & set variables & RUN
```
(cd programs/server && npm install)
export PORT=80
export MONGO_URL='mongodb://localhost/data_base_name_as_local'
export ROOT_URL='http://url-here.com'
export MAIL_URL='smtp://user:password@mailhost:port/'
export BIND_IP=192.168.0.2

forever start /home/meteor/bundle/main.js
```
## Automatic deploy using scripts
To be continued ...
## Automatic with Meteor-Up (with Docker and seamless deploy)
To be continued ...
