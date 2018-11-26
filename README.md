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
Install Mongo 4.0.6 ????
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list

sudo apt-get update

sudo apt-get install -y mongodb-org=4.0.6 mongodb-org-server=4.0.6 mongodb-org-shell=4.0.6 mongodb-org-mongos=4.0.6 mongodb-org-tools=4.0.6

#OPTIONAL 3.4.10
sudo apt-get install -y mongodb-org=3.4.10 mongodb-org-server=3.4.10 mongodb-org-shell=3.4.10 mongodb-org-mongos=3.4.10 mongodb-org-tools=3.4.10

# prevent auto upgrade
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
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
scp ../build/disp2.tar.gz ovz:/home/meteor/
```
### Server
Unpack bundle archive
```
cd /home/meteor/
tar xvf disp2.tar.gz
cd bundle/
```
```
(cd programs/server && npm install)
export MONGO_URL='mongodb://localhost/dispatcher'
export ROOT_URL='http://url-here.com'
export MAIL_URL='smtp://user:password@mailhost:port/'
node main.js
```
