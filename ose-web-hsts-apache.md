# How to configure HSTS on your apache web server

HTTP Strict Transport Security (HSTS), defined in [RFC 6797](https://tools.ietf.org/html/rfc6797), requires web browsers to connect via HTTPS when visiting your website. This helps protect your site visitors from man-in-the-middle (MitM) attacks.

**Note:** If you decide to disable HTTPS (TLS) while HSTS is enabled, visitors cannot access your site for the duration specified by the **max-age directive**. 
- The **max-age directive** states the maximum amount of time (in seconds) that responses remain in the browser cache. For instance, max-age=120 indicates that an asset can be reused for the next 120 seconds.
- In the case of HSTS, if the max-age directive is set to 6 months and you disable HTTPS 2 months after enabling HSTS, browsers that visited your site while HSTS was enabled cannot visit your site for another 4 months unless HTTPS is again enabled.

## HSTS on Apache:
 To enable HSTS (within a virtual host config):
 
1. make sure mod_headers and mod_rewrite are enabled. You check by going to 
    ```
    /etc/apache/mods-enabled 
    ```
    and look for: **rewrite.load**  and **headers.load**
 
2. If not loaded, run the following commands
    ```
    a2enmods rewrite
    a2enmods headers
    ```
    Then restart the apache server
 
3. Open your virtual host file to edit. (this might be `httpd.conf`, `apache.conf`, or a separate file for your virtual host)
 
4. If file has section for HTTP (port 80), add the following:
    ```
    RewriteEngine on
    RewriteCond %{SERVER_NAME} = <your hostname>
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
    ```
    For example, we used this for our server:
    ```
    RewriteEngine on
    RewriteCond %{SERVER_NAME} = ose-apache.internetsociety.org
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
 
5. Add the header statement in the (443) section. We recommend a HSTS max-age of at least six months (31536000 seconds). 
    ```
    Header Set Strict-Transport-Security "max-age=31536000"
    ```
6. Restart apache

--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation
