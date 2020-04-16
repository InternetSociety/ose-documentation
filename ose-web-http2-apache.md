# How to configure HTTP/2 on your apache web server

Hypertext Transfer Protocol Version 2 (HTTP2), defined in [RFC 7540](https://tools.ietf.org/html/rfc7540) improves website performance and enables a more efficient use of network resources. Unlike its predecessor, HTTP/1.1, HTTP/2 can handle heavy loads of resources such as images, fonts, scripts, and stylesheets which result in better load speeds.  It reduces latency by introducing header field compression and enables multiplexing, which allows the client and server to process multiple concurrent requests over the same connection.  

## HTTP/2 on Apache
 
During a default install on Debian, Apache is configured with mpm_prefork. This will not work with HTTP/2. You need to use either mpm_event or mpm_worker. For our example, we used mpm_event.
 
1. Stop apache
    ```
    apachectl stop
    ```
2. Install php7.3-fpm
    ```
    apt-get install php7.1-fpm # 
    ``` 
    Install the php-fpm from your PHP repository. This package name depends on the vendor.
3. Enable module for fast cgi
    ```
    a2enmod proxy_fcgi setenvif
    ```
4. Enable the php-fpm configuration
    ```
    a2enconf php7.3-fpm # Again, this depends on your PHP vendor.
    ```
5. Disable mod_php
    ```
    a2dismod php7.3 # 
    ```
    This disables mod_php.
6. Disable mpm_prefork
    ```
    a2dismod mpm_prefork # 
    ```
    This disables the prefork MPM. Only one MPM can run at a time.

7. Enable mpm_event
    ```
    a2enmod mpm_event # 
    ```
    Enable event MPM. You could also enable mpm_worker.
8. Enable the HTTP/2 module
    ```
    a2enmod http2
    ```
9. Restart Apache
    ```
    apachectl start
    ```
 
--------

Note: Developed on a server running Debian 10.2 and Apache 2.4.38.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation