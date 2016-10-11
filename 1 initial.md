# Initial server setup

## Before
Before this, the server is up to date with all the latest versions.

## Setup (execute everything as root)

Add a user
  1. adduser demian

Add this user to the sudo group
  1. gpasswd -a demian sudo

Do not permit root login, and change default port number of SSH
  1. nano /etc/ssh/sshd_config
  2. PermitRootLogin no
  3. port 47222
  4. service ssh restart

  It's recommenced to check if you can login with 'demian', before you shutdown this SSH session;

## Firewall (exit root, and login as demian)

First let's setup some defaults:
  1. sudo ufw default deny incoming
  2. sudo ufw default allow outgoing

Then add some rules
  1. sudo ufw allow 47222/tcp
  2. sudo ufw allow 80/tcp
  3. sudo ufw allow 443/tcp

Enable this new settings
  1. sudo ufw enable
  2. sudo ufw status verbose
