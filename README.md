# Host N8N On Your Local Machine

## Windows
1. Download and install [NodeJS](https://nodejs.org)
2. Open Command Prompt
3. Paste the following command:
```
npm install n8n
```
4. Once it's done installing, paste this command:
```
n8n
```
if this doesn't work, try with this one.
```
n8n start
```
or if it still doesn't work, try this:
```
npx n8n
```
5. N8N will be hosted on localhost:5678


## Linux
1. Run the following commands:
```
sudo apt update
sudo apt upgrade -y
curl -sL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt install nodejs -y
sudo apt install mariadb-server mariadb-client -y
sudo su
mysql_secure_installation
```
2. Press Enter to login as root
3. Type N and press Enter to not switch to unix socket authentication
4. Type Y and press Enter to set a root password, type the password twice to confirm
5. Type Y and press Enter to remove anonymous users
6. Type Y and press Enter to disallow root login remotely
7. Type Y and press Enter to remove the test database
8. Type Y and press Enter to reload privilege tables
9. Run the following command:
```
mysql -u root -p
```
10. Authenticate with the root password set earlier
11. Run the following commands:
```
CREATE DATABASE n8n;
GRANT ALL ON n8n.* to 'n8n_rw'@'localhost' IDENTIFIED BY 'n8n_N8N!';
FLUSH PRIVILEGES;
EXIT;
exit
```
12. Then, continue with the following commands:
```
export DB_TYPE="mysqldb"
export DB_MYSQLDB_DATABASE="n8n"
export DB_MYSQLDB_HOST="localhost"
export DB_MYSQLDB_USER="n8n_rw"
export DB_MYSQLDB_PASSWORD="n8n_N8N!"
export GENERIC_TIMEZONE="America/New_York"
sudo npm install n8n --location=global
sudo npm audit fix
n8n
```
13. N8N will be hosted on localhost:5678

## MacOS
1. Run the following commands to install homebrew package manager:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. After it finished installing, run these:
```
brew install node@16
brew unlink node
brew link --overwrite node@16
brew install mariadb
mysql.server start
brew services start mariadb
sudo mysql -uroot
```
3. Then, run these:
```
CREATE DATABASE n8n;
GRANT ALL ON n8n.* to 'n8n_rw'@'localhost' IDENTIFIED BY 'n8n_N8N!';
FLUSH PRIVILEGES;
EXIT;
```
4. Continue with the following commands:
```
export DB_TYPE="mysqldb"
export DB_MYSQLDB_DATABASE="n8n"
export DB_MYSQLDB_HOST="localhost"
export DB_MYSQLDB_USER="n8n_rw"
export DB_MYSQLDB_PASSWORD='n8n_N8N!'
export GENERIC_TIMEZONE="America/New_York"
sudo npm install n8n --location=global
sudo n8n start
```
5. N8N will be hosted on localhost:5678
