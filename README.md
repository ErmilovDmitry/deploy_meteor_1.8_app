# How to deploy Meteor 1.8 App

## 1. Manually

Deploy from local Meteor 1.8 to remote server with Debian/Ubuntu OS
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
