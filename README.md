#  LAMP with Docker Compose

  
LAMP stack environment built using Docker Compose. It consists of the following:

* PHP 7.3.x
* Apache 2.4.x
* MySQL 5.7.x

##  Installation
 
* Clone this repository on your local computer
* configure .env as needed 
* Run the `docker-compose up -d`.

```shell
git clone https://github.com/jonathansanchez/lamp.git
cd lamp/
cp vars.env .env
// modify vars.env as needed
docker-compose up -d
// visit localhost:8080
```

Your LAMP stack is now ready!! You can access it via `http://localhost:8080`.

##  Configuration and Usage

### General Information 
This Docker Stack is build for local development and not for production usage.

### Configuration
This package comes with default configuration options. You can modify them by creating `.env` file in your root directory.
To make it easy, just copy the content from `vars.env` file and update the environment variable values as per your need.

### Configuration Variables
There are following configuration variables available, you can customize them by overwriting in your own `.env` file.

---
PHP
---
_**PHP_INI**_
Define your custom `php.ini` modification to meet your requirments. 

---
Apache 
---

_**DOCUMENT_ROOT**_

It is a document root for Apache server. The default value for this is `./www`. All your sites will go here and will be synced automatically.

_**VHOSTS_DIR**_

This is for virtual hosts. The default value for this is `./config/vhosts`. You can place your virtual hosts conf files here.

> Make sure you add an entry to your system's `hosts` file for each virtual host.

_**APACHE_LOG_DIR**_

This will be used to store Apache logs. The default value for this is `./logs/apache2`.

---
Database
---

_**MYSQL_DATA_DIR**_

This is MySQL data directory. The default value for this is `./data/mysql`. All your MySQL data files will be stored here.

_**MYSQL_LOG_DIR**_

This will be used to store Apache logs. The default value for this is `./logs/mysql`.

## Web Server

Apache is configured to run on port 80. So, you can access it via `http://localhost:8080`.

#### Apache Modules

By default following modules are enabled.

* rewrite
* headers

> If you want to enable more modules, just update `./bin/webserver/Dockerfile`. You can also generate a PR and we will merge if seems good for general purpose.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

#### Connect via SSH

You can connect to web server using `docker-compose exec` command to perform various operation on it. Use below command to login to container via ssh.

```shell
docker-compose exec webserver bash
```

## PHP

#### Extensions

By default following extensions are installed. 
May different for PHP versions < 7.3.x

* mysqli
* pdo_sqlite
* pdo_mysql
* mbstring
* zip
* intl
* mcrypt
* curl
* json
* iconv
* xml
* xmlrpc
* gd

> If you want to install more extension, just update `./bin/webserver/Dockerfile`.
> You have to rebuild the docker image by running `docker-compose build` and restart the docker containers.

## Credits

https://github.com/sprintcube/docker-compose-lamp