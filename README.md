# linux-commands

list of common linux command i use when i setup Ubuntu server

## permissions
![image](https://user-images.githubusercontent.com/86796762/235347441-75e56147-ece8-4de2-bf19-8fa47117bcf1.png)

## user

### create 
```shell
adduser username
```
```shell
passwd username
```
```shell
deluser --remove-home username
```

### add to group 
```shell
getent group
```
```shell
usermod -a -G group1,group2 username
```
add user to all default groups (kvm servers):
```shell
usermod -a -G root,daemon,bin,sys,adm,tty,disk,lp,mail,news,uucp,man,proxy,kmem,dialout,fax,voice,cdrom,floppy,tape,sudo,audio,dip,www-data,backup,operator,list,irc,src,gnats,shadow,utmp,video,sasl,plugdev,staff,games,users,nogroup,systemd-journal,systemd-network,systemd-resolve,systemd-timesync,crontab,messagebus,input,kvm,render,syslog,tss,uuidd,tcpdump,ssh,landscape,admin,netdev,lxd,systemd-coredump username
```

## DNS
dns are in the following path:
```shell
/etc/resolv.conf
```
or in :
```shell
/etc/netplan
```
## docker

```shell
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```
```shell
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg```
```shell
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```shell
sudo apt-get update
```
```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## php
```shell
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt upgrade
sudo apt update
```
```shell
sudo apt install php php-cli php-common
```
```shell
sudo apt install openssl php8.1-curl php8.1-mbstring php8.1-mysql php8.1-xml php8.1-zip php8.1-mysqlnd php8.1-opcache php8.1-pdo php8.1-calendar php8.1-ctype php8.1-exif php8.1-ffi php8.1-fileinfo php8.1-ftp php8.1-gd php8.1-gettext php8.1-iconv php8.1-mysqli php8.1-phar php8.1-posix php8.1-readline php8.1-shmop php8.1-sockets php8.1-sysvmsg php8.1-sysvsem php8.1-sysvshm php8.1-tokenizer
```
## composer
```shell
cd ~
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
```
```shell
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
## laravel sail
```shell
alias sail='[ -f sail ] && bash sail || bash vendor/bin/sail'
```
```shell
sail up -d
```

## webserver
start apache
```shell
sudo service apache2 start
```
stop nginx
```shell
sudo systemctl stop nginx
```
disable nginx from startup
```shell
sudo systemctl disable nginx
```
laravel config
```text
<VirtualHost *:80>
   ServerName thedomain.com
   ServerAdmin webmaster@thedomain.com
   DocumentRoot /var/www/html/example/public

   <Directory /var/www/html/example>
       AllowOverride All
   </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
enable rewrite module in apache
```shell
sudo a2enmod rewrite
```

## mysql
install mysql
```shell
sudo apt-get install mysql-server
```
enter mysql server for the first time
```shell
sudo mysql
```
change default password mysql (sql command)
```shell
ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';
```
mysql create database
```shell
CREATE DATABASE db_name;
```

mysql create user
```shell
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```
```shell
GRANT ALL PRIVILEGES ON database_name.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```

php my admin
```shell
sudo apt install phpmyadmin php-mbstring php-zip php-gd php-json php-curl
```

## VPN server
### Orginal x-ui installation
default port is 54321
```shell
sudo bash < <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```
### English version x-ui installation
```shell
sudo bash < <(curl -Ls https://raw.githubusercontent.com/hossinasaadi/x-ui/master/install.sh)
```
