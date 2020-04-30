# How to install an NGINX web server as part of a LEMP stack 

The LEMP software stack is a group of software that can be used to serve dynamic web pages and web applications. The acronym that stands for Linux operating system, with an NGINX web server, Maria DB and PHP. (The "E" in "LEMP" comes from pronouncing NGINX as "engine-X".)

This page demonstrates how to install a LEMP stack on an Debian 10.3 OS. 

## How to create LEMP stack on system
1. Update Software Packages
    Before we install the LEMP stack, it’s a good idea to update repository and software packages. Run the following command on your Debian 10 OS.
    ```
    sudo apt update
    ```
    
	```
	sudo apt upgrade
    ```
2. Install NGINX Web Server on Debian 10
    
    NGINX is a high performance web server and very popular these days. It also can be used as a reverse proxy and caching server. Enter the following command to install NGINX Web server.
    ```
	sudo apt install nginx
	```

    ```
	systemctl status nginx
    ```

3. Install MariaDB Database Server on Debian 10

- MariaDB is a drop-in replacement for MySQL. Enter the following command to install it on Debian 10.
	```
	sudo apt install mariadb-server mariadb-client
	```
- Now run the post installation security script.
    ```
	sudo mysql_secure_installation
    ```
    
- When it asks you to enter MariaDB root password, press **Enter** key as the root password isn’t set yet. 
    Then enter **y** to set the root password for MariaDB server.

- Next, press **Enter** to answer all remaining questions. This will remove anonymous user, disable remote root login and remove test database. This step is a basic requirement for MariaDB database security. 
    **Note**:  the letter Y is capitalized, which means it’s the default answer. You can press Enter.


4. Install PHP7.3 on Debian 10.3

    At the the time of this writing, PHP7.3 is the latest stable version of PHP and has minor performance improvement over previous versions.
- Enter the following command to install PHP7.3 and some common PHP extensions from Debian 10 repository.
    ```
	apt install php7.3 php7.3-fpm php7.3-mysql php-common php7.3-cli php7.3-common php7.3-json php7.3-opcache php7.3-readline
    ```
5.  Create a NGINX Server Block
    A NGINX server block is like a virtual host in Apache. We will not use the default server block because it’s inadequate to run PHP code and if we modify it, it becomes a mess.
- Remove the default symlink in sites-enabled directory by running the following command (it’s still          available as /etc/nginx/sites-available/default):
    ```
	rm /etc/nginx/sites-enabled/default
    ```
- Then create a brand new server block file under /etc/nginx/conf.d/ directory with a command line text editor, such as Nano.
    ```
	nano /etc/nginx/conf.d/default.conf
    ```
- Paste the following text into the file. The following snippet will make Nginx listen on IPv4 port 80 and IPv6 port 80 with a catch-all server name:
    ```
    server {
        listen 80;
        listen [::]:80;
        server_name _;
        root /usr/share/nginx/html/;
        index index.php index.html index.htm index.nginx-debian.html;

    location / {
        try_files $uri $uri/ /index.php;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/run/php/php7.3-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
        include snippets/fastcgi-php.conf;
    }

    # A long browser cache lifetime can speed up repeat visits to your page
    location ~* \.(jpg|jpeg|gif|png|webp|svg|woff|woff2|ttf|css|js|ico|xml)$ {
       access_log        off;
       log_not_found     off;
       expires           360d;
    }

  # disable access to hidden files
  location ~ /\.ht {
      access_log off;
      log_not_found off;
      deny all;
      }
    }

- Save and close the file. 
    To save a file in Nano text editor, press Ctrl+O, then press Enter to confirm. To exit, press Ctrl+X.
- Test Nginx configurations.

    ```
    nginx -t
    systemctl reload nginx
    ```

6. Test PHP
To test PHP scripts with Nginx server, we need to create a info.php file in the Web root directory:
    ```
	nano /usr/share/nginx/html/info.php
    ```


- Paste the following PHP code into the file.
    ```php
    <?php phpinfo(); ?>
    ```


- Create DNS entry (IPv4 and IPv6)

    -   Start with self-signed cert:
    ```
	openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt
    ```


- Add Certbot from Let's Encrypt
	- Create certificate
    ```
    apt-get install certbot python-certbot-apache
	certbot --apache
    ```

--------

Note: Developed on a server running Debian 10.2 and NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation



