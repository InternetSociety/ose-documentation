# How to install an Apache web server as part of a LAMP stack 

The "LAMP software stack" is a group of software that can be used to serve dynamic web pages and web applications. The acronym stands for Linux operating system, with an Apache web server, Maria DB and PHP.

This document demonstrates how to install a LAMP stack on an Debian 10.3 OS. 


## How to create a LAMP stack 
For this example we are using DigitalOcean as our hosting provider and creating a LAMP system based on Debian Linux 10.3. Here are the basic things you need to select when building the system:

   - Create droplet
   - Select Debian 10.3 as distribution 
   - Select size
   - Select IPv6
   - Backup to be selected AFTER fully setup server. In our example we chose no additional storage or backup.

**Note:** if you are logged in as a non-admin user, you will need to use the sudo command. If you are logged in as root, you **do not need** the sudo command as you already have admin privileges.

1. **Update Software Packages:** Before we install the LAMP stack, it’s a good idea to update repository and software packages. Run the following command on your Debian 10 OS.
    ```
    sudo apt update
	sudo apt upgrade
    ```	
2. **Install Apache Web Server on Debian 10**: Enter the following command to install Apache Web server. The apache2-utils package will install some useful utilities, such as the Apache HTTP server benchmarking tool ab and the user authentication management tool htpasswd.
    ```
	sudo apt install apache2 apache2-utils
    ```
3.  **Install MariaDB Database Server on Debian 10:** MariaDB is a drop-in replacement for MySQL. 
- Enter the following command to install it on Debian 10.
	```
	sudo apt install mariadb-server mariadb-client
	```

- After it’s installed, MariaDB server should be automatically started. Use systemctl to check its status.
	```
	systemctl status mariadb
    ```
    
    If you see 'active (running)'.
    To exit this press 'q'

- Now run the post installation security script.
    ```
	sudo mysql_secure_installation
    ```

    When it asks you to enter MariaDB root password, press **Enter** key as the root password isn’t set yet. Then enter **y** to set the root password for MariaDB server.

- Next, you can just press Enter to answer all remaining questions. This will remove anonymous user, disable remote root login and remove test database. This step is a basic requirement for MariaDB database security.
**Note:** the letter Y is capitalized, which means it’s the default answer.


4. **Install PHP7.3 on Debian 10** At the the time of this writing, PHP7.3 is the latest stable version of PHP and has minor performance improvement over previous versions. Enter the following command to install PHP7.3 from Debian 10 repository:
    ```
	sudo apt install php7.3 libapache2-mod-php7.3 php7.3-mysql php-common php7.3-cli php7.3-common php7.3-json php7.3-opcache php7.3-readline
    ```

- Enable the Apache php7.3 module 
    ```
	sudo a2enmod php7.3
    ```
- Then, restart Apache Web server.
    ```
	sudo systemctl restart apache2
    ```

--------

Note: Developed on a server running Debian 10.2 and Apache 2.4.38.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation