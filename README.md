# LAMP and LEMP
# 1. Install packages
## Update ubuntu server
```
sudo apt update && apt upgrade -y
```

## Install Essentials (apache2, php,...)
```
sudo apt install apache2 nginx libapache2-mod-php mysql-server php php-mysql php-fpm php-mbstring php-xml php-zip php-bcmath php-curl
```
---
# 2. LAMP
# a. Wordpress
## Create wordpress directory
```
sudo mkdir -p /srv/www
```

## Change owner to www-data
```
sudo chown www-data: /srv/www
```

## Download latest wordpress and extract to /srv/www
```
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
```

## Create Virtual Host for wordpress
```
sudo vi /etc/apache2/sites-available/wordpress.training.vn.conf

# Create Virtual Host
<VirtualHost *:8080>
    ServerName wordpress
    ServerAlias wordpress.training.vn
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```
## Change ports.conf port
```
vi /etc/apache2/ports.conf
Listen 8080 # Wordpress port
Listen 80   # Laravel port
```
## Edit wp-config file, add 2 lines
```
sudo -u www-data mv -v /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
sudo -u www-data cp -v /srv/www/wordpress/wp-config.php /srv/www/wordpress/wp-config.bk

define('WPSITEURL','http://localhost:8080/');
define('WPHOME','http://localhost:8080/');
```
## Enable wordpress site
```
sudo a2ensite wordpress.training.vn
```

## Enable URL rewrite with command bellow
```
sudo a2enmod rewrite
```

## Disable the default "It Works" page
```
sudo a2dissite 000-default
```
## Reload apache2
```
sudo service apache2 reload
```
## Create wordpress database
```
sudo mysql -u root
CREATE DATABASE wordpress;
CREATE USER wordpress@localhost IDENTIFIED BY 'password';
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;
FLUSH PRIVILEGES;
quit;
```
## Edit wp-config.php (database connect)
```
sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/password_here/password/' /srv/www/wordpress/wp-config.php
```

## Change unique phrase https://api.wordpress.org/secret-key/1.1/salt/
```
sudo -u www-data vi /srv/www/wordpress/wp-config.php

define( 'AUTH_KEY',         'put your unique phrase here' );
define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
define( 'NONCE_KEY',        'put your unique phrase here' );
define( 'AUTH_SALT',        'put your unique phrase here' );
define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
define( 'NONCE_SALT',       'put your unique phrase here' );
```
## Reload apache2
```
sudo systemctl reload apache2
```
---

# b. Laravel
## Start php-fpm service
```
systemctl start nginx mysql php7.4-fpm 
systemctl enable nginx mysql php7.4-fpm 
```
## Create Database
```
mysql 
CREATE DATABASE laravel;
CREATE USER 'laravel_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL ON laravel.* TO 'laravel_user'@'%';
FLUSH PRIVILEGES;
exit;
```
## Install Laravel
```
curl -sS https://getcomposer.org/installer | php
sudo mv -v composer.phar /usr/local/bin/composer
sudo chmod +x /usr/local/bin/composer

cd /var/www/html
sudo composer create-project --prefer-dist laravel/laravel laravel

Output shoud be: 
> @php artisan vendor:publish --tag=laravel-assets --ansi --force

   INFO  No publishable resources for tag [laravel-assets].  

No security vulnerability advisories found.
> @php artisan key:generate --ansi

   INFO  Application key set successfully.  
```
## Set permissions and ownership
```
sudo chown -R www-data: /var/www/html/laravel
sudo chmod -R 775 /var/www/html/laravel

cd laravel
sudo -u www-data php artisan key:generate
```
## Edit the environment variable file.
```
sudo -u www-data nano /var/www/html/laravel/.env

# Define your Laravel database settings as shown below.

LOG_CHANNEL=stack

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laravel_user
DB_PASSWORD=password
```

## Configure Virtual host for Laravel
```
sudo vi /etc/apache2/sites-available/laravel.training.vn.conf

<VirtualHost *:80>
    ServerName laravel
    ServerAlias laravel.training.vn
    DocumentRoot /var/www/html/laravel/public

    <Directory /var/www/html/laravel>
            AllowOverride All
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

a2ensite laravel.training.vn.conf
```
## Edit apache config file
```
# Edit /etc/apache2/ports.conf
Listen 8080 # Wordpress port
Listen 80   # Laravel port
```
## Add new line to /etc/apache2/apache2.conf
```
<Directory /var/www/html/laravel/public>
        DirectoryIndex index.php
</Directory>

systemctl reload apache2
```
# c. Access Webserver
## Wordpress
http://\<webserver-ip>\:8080
![image](https://github.com/GitGudAuth/training-02-07-2024/assets/117452333/fbfb2b81-ffb0-4655-973e-45b846447790)
## Laravel
http://\<web-server-ip>\:80
![image](https://github.com/GitGudAuth/training-02-07-2024/assets/117452333/c3d4b619-3c9b-495c-a836-b70c4571cd48)

# 3. LEMP
## Start php-fpm service
```
systemctl start nginx mysql php7.4-fpm 
systemctl enable nginx mysql php7.4-fpm 
```

## Create Virtual Host for Laravel and Wordpress
```
sudo vi /etc/nginx/sites-available/laravel.training.vn.conf
# laravel.training.vn.conf
server {
    listen 80;
    server_name laravel.training.vn;
    root /var/www/html/laravel/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Content-Type-Options "nosniff";

    index index.html index.htm index.php;

    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;   # Check version php-fpm
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}

sudo vi /etc/nginx/sites-available/wordpress.training.vn.conf
# wordpress.training.vn.conf
server {
            listen 8080;
            root /srv/www/wordpress;
            index index.php index.html;
            server_name wordpress.training.vn;

	    access_log /var/log/nginx/wordpress.access.log;
    	    error_log /var/log/nginx/wordpress.error.log;

            location / {
                         try_files $uri $uri/ =404;
            }

            location ~ \.php$ {
                         include snippets/fastcgi-php.conf;
                         fastcgi_pass unix:/run/php/php7.4-fpm.sock;
            }
            
            location ~ /\.ht {
                         deny all;
            }

            location = /favicon.ico {
                         log_not_found off;
                         access_log off;
            }

            location = /robots.txt {
                         allow all;
                         log_not_found off;
                         access_log off;
           }
       
            location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
                         expires max;
                         log_not_found off;
           }
}

# Create symlink from sites-available to sites-enabled
ln -s /etc/nginx/sites-available/{wordpress.training.vn.conf,laravel.training.vn.conf} /etc/nginx/sites-enabled/
```
## Edit Nginx configuration file
```
# Edit /etc/nginx/nginx.conf
sudo vi /etc/nginx/nginx.conf
server_names_hash_bucket_size 64;

# Delete /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-{available,enabled}/default

```
## Verify syntax error and reload nginx
```
sudo service nginx configtest
sudo service nginx reload
```

# Access Webserver
## Wordpress
http://\<webserver-ip\>:8080
![image](https://github.com/GitGudAuth/training-02-07-2024/assets/117452333/d4480148-3788-4956-be36-f6ac742b04c8)
## Laravel
http://\<webserver-ip\>:80
![image](https://github.com/GitGudAuth/training-02-07-2024/assets/117452333/1bbc201b-bfa8-4730-a2c5-d380f5b8fdc8)
