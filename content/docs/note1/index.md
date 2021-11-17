---
title: "Tasks Sept 2021"
date: 2019-02-11T19:27:37+10:00
weight: 2
summary: Commands of the 1st round.
---

**Install php-curl**

```Bash
$ sudo add-apt-repository ppa:ondrej/php
$ sudo apt update
$ sudo apt-get update
$ sudo apt-get install php6-curl
$ sudo service apache2 restart
```

get php.ini file location

amelearning.com.conf@ --> /etc/apache2/sites-available/amelearning.com.conf

**Install php 7**

```
$ sudo apt install -y php7.4 php7.4-cli libapache2-mod-php7.4
```

**Remove old php versions**

```Bash
$ sudo apt-get purge 'php5.6*'
$ sudo apt-get purge 'php7.0*'
$ sudo apt-get purge 'php7.1*'
$ sudo apt-get purge 'php7.2*'
$ sudo apt-get purge 'php7.3\*'
$ sudo apt-get autoremove
```

**Upgrade ubuntu 16.04 to 18.04**

```Bash
$ sudo apt-get update
$ sudo apt-get upgrade -y
$ sudo apt-get dist-upgrade -y
$ sudo apt-get autoremove
$ sudo apt-get install update-manager-core
$ sudo vim /etc/update-manager/release-upgrades
# Prompt option should be set to lts
$ sudo do-release-upgrade
```

**Install php stock**

```Bash
$ sudo apt install -y php7.4-mysql php7.4-dom php7.4-simplexml php7.4-ssh2 php7.4-xml php7.4-xmlreader
$ sudo apt install -y php7.4-curl php7.4-exif php7.4-ftp php7.4-gd php7.4-iconv php7.4-imagick
$ sudo apt install -y php7.4-json php7.4-mbstring php7.4-posix php7.4-sockets php7.4-tokenizer
```

**Link to executable (application/x-executable)**

```html
<form
  action="https://ameengage2019.dealopia.com/learninglibrary/GetPin.php"
  method="get"
>
  Name: <input type="text" name="name" /><br />
  E-mail: <input type="text" name="email" /><br />
  <input type="submit" />
</form>
```

**Moodle Server**
**php.ini file**

```Bash
$ sudo vim /etc/php/7.1/apache/php.ini
# Change 'display_errors' to 'On' --default:'Off'
# Change 'error_log' to '/var/log/php/error.log' --default: commented
```

**Restart apache2**

```Bash
$ sudo service apache2 start
# or
$ sudo systemctl restart apache2
```

**Create Log file for PHP**

```
$ sudo mkdir /var/log/php
$ sudo chown root:www-data /var/log/php
$ sudo chmod 2750 php
$ sudo touch /var/log/php/error.log
$ sudo chmod 0664 /var/log/php/error.log
```

**How to enable debug mode in Moodle**

```php
# Edit the config.php file and placing the following code at the beginning:
@error_reporting (E_ALL | E_STRICT);
@ini_set ('display_errors','1');
$ CFG-> debug = (E_ALL | E_STRICT);
$ CFG-> debugdisplay = 1;
```

**Check php extension**

```
$ php -i | grep -i openssl
```

**CodeIgniter4**

```
$ composer require twbs/bootstrap enyo/dropzone datatables.net-dt
```

**Deploy node app apache/ubuntu**

Step 1: Install Node.js

```console
$ curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
$ sudo apt install -y nodejs
$ node -v
$ npm -v
$ sudo apt install build-essential
```

Step 2: Install Process Manager

```Bash
$ sudo npm install pm2 -g
$ pm2 start path_tonode_app/app.js
$ sudo pm2 startup systemd
# or
$ sudo pm2 startup upstart
```

Step 3: Configure Apache

```
$ sudo a2enmod proxy proxy_http
```

**app.js**

```JavaScript
const http = require("http");
const hostname = "localhost";
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader("Content-Type", "text/plain");
  res.end("Welcome to Node.js!\n");
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

#### Deploy adonisjs

1. Buil for production

```
$ node ace build --production
```

2. install dependencies

```console
$ cd build
$ npm ci --production
```

3. Start server

```
$ node server.js
```

**Apache Proxy Reverse Configuration**

```ApacheConf
<Location /resources>
Order allow,deny
Allow from all

    RewriteEngine On
    RewriteCond %{HTTP:Upgrade} =websocket [NC]
    RewriteRule /var/www/(.*)           ws://127.0.01:3333/$1 [P,L]
    RewriteCond %{HTTP:Upgrade} !=websocket [NC]
    RewriteRule /var/www/(.*)           http://127.0.0.1:3333/$1 [P,L]

    ProxyPassReverse http://127.0.0.1:3333

</Location>
```

**AMEDocs Node**

```Bash
ROOT_URL = https://ameengage2019.dealopia.com/resources/ node main.js
email = admin@amedocs.com
password = !SJ[Edc7abGgLYtr
```

**Conect with ssh**

```console
$ ssh -i path/to/key user@IP_ADDRESS
```

examples

```Bash
$ ssh -i ~/.ssh/id_rsa_ibipul w8hj48kvvds3@166.62.75.227
$ ssh -p 22 -i ~/.ssh/central-canada-key1.pem ubuntu@52.60.233.18
$ scp -v -P 22 -i ~/.ssh/central-canada-key1.pem amedocs_build.tar.bz2 ubuntu@52.60.233.18:/ebs/amedocs/
```

**Error with argon2**

```
$ sudo npm install -g node-pre-gyp
$ node-pre-gyp rebuild -C ./node_modules/argon2
```
