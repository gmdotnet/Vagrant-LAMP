# Vagrant Box LAMP Stack

This is a DEV LAMP debian based box. Use it for a basic development.

## Requirements

- virtualbox 5.x
- vagrant >1.8.4
- (in case of error of shared folder mount errors) vagrant vagrant-vbguest plugin (install with the command `vagrant plugin install vagrant-vbguest`)

## How to use

1) download https://github.com/gmdotnet/Vagrant-LAMP/archive/master.zip

2) unzip on your favorite work folder

3) change Vagrantfile - section config.vm.synced_folder to sync your project folder

4) run 'vagrant up'

5) make your configuration on vagrant machine entering by run 'vagrant ssh'

6) have fun!

## OS and base box

- debian/jessie64  8.5.1
- private network ip: 192.168.250.10

## Software Installed

- apache2  2.4.10
- [composer](https://getcomposer.org/)  1.2.0
- curl
- git
- [git-up](https://github.com/aanand/git-up/) (plugin for git)
- htop
- jpegoptim 1.4.1
- mailutils
- [mailhog](https://github.com/mailhog/MailHog)  0.2.0
- mc-dbg (midnight commander)
- mysql-server 5.5
- mysqltuner 1.6.0
- optipng 0.7.5
- phpmyadmin 4.6.3 - all languages (accessible via *http://phpmyadmin.vagrant* on your file host with the same ip of vagrant machine)
- postfix
- [sass](http://sass-lang.com/)  3.4.22
- tig
- xdebug

- Magento Utils:
    - [modman](https://github.com/colinmollenhour/modman) 1.12
    - [n98-magerun](https://github.com/netz98/n98-magerun)  1.97.22

- PHP
    - php5  5.6
    - php5-cli
    - php5-curl
    - php5-dev
    - php5-gd
    - php5-intl
    - php5-mcrypt
    - php5-mysql
    - php-pear

- [Node.js](https://nodejs.org/en/) 4.4.7
    - [npm](https://www.npmjs.com/)  2.15.8
    - [bower](https://bower.io/)  1.7.9
    - [LESS](http://lesscss.org/)  2.7.1
    - [CSS Lint](http://csslint.net/)  1.0.2
    - [grunt-cli](http://gruntjs.com/)  1.2.0
    - [grunt](http://gruntjs.com/)  1.0.1

### MySQL server

- created an user called 'local' with root privilegies
- root password is 'vagrant'

### Apache server

- daemon user is 'vagrant'
- root folder is '/var/www'
- mod_rewrite and mod_vhost_alias enabled
- IMPORTANT: you need to add `EnableSendfile Off` on your website configuration under <Directory "..."> </Directory> ( here all info  https://www.vagrantup.com/docs/synced-folders/virtualbox.html )

### PHP Xdebug

- auto-activated in PHP cli and PHP "web"
- IDEKEY = "VAGRANT"
- uncomment `xdebug.remote_host` in `php.ini` to enable your IDE for remote xdebug

### SMTP and EMAIL with postfix and MailHog

- postfix is configured as satellite system with 127.0.0.1:1025
- mailhog do not start automatically. Just open a shell and type `mailhog`
    - web interface is set on `<vagrant ip>:8025`
- all emails are not sent outside the machine
- to test:
    - start mailhog
    - send a test email with `echo "this is a test email | mail -s "subject test email" fake@fake.mail`
    - check on your browser `<vagrant ip>:8025` the email sent
- you can use mailhog as SMTP server, just configure your application to send email at 127.0.0.1 with port 1025

### Vagrant Provision script

- the script makes a backup of all databases into /home/backup/database/ folder

### Other info

- root password is 'vagrant' but you can simply run 'sudo su' from vagrant user
- if you can't find a configuration in this file before, it means is used the default value
