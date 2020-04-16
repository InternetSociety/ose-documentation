# How to configure HSTS on your web server with NGINX

HTTP Strict Transport Security (HSTS), defined in [RFC 6797](https://tools.ietf.org/html/rfc6797), requires web browsers to connect via HTTPS when visiting your website. This helps protect your site visitors from man-in-the-middle (MitM) attacks.

**Note:** If you decide to disable HTTPS (TLS) while HSTS is enabled, visitors cannot access your site for the duration specified by the **max-age directive**. 
- The **max-age directive** states the maximum amount of time (in seconds) that responses remain in the browser cache. For instance, max-age=120 indicates that an asset can be reused for the next 120 seconds.
- In the case of HSTS, if the max-age directive is set to 6 months and you disable HTTPS 2 months after enabling HSTS, browsers that visited your site while HSTS was enabled cannot visit your site for another 4 months unless HTTPS is again enabled.

## HSTS on NGINX:

1. In a server block, we added the following to redirect to HTTPS.  If you are using Let's Encrypt, when the certificate was created you could choose to redirect which will create the same config:
    ```
    if ($host = ose-nginx.internetsociety.org) {
        return 301 https://$host$request_uri;
    } 
    ```
 
2. Now you can add the header either in the main config, or use an externally called config file. If you add the header in your main config file, this is the line to add. You can adjust the max-age directive, but it is recommended to not go below 31536000 (which is 6 months)
    ```
  	add_header Strict-Transport-Security "max-age=31536000";
    ```
    On our server we created an `ssl-params.conf` file where we store server settings.  This is what ours looks like:
    ```
  	ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_dhparam /etc/ssl/certs/dhparam.pem;
    ssl_ciphers    ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDH$ssl_ecdh_curve secp384r1; # Requires nginx >= 1.1.0
    ssl_session_timeout  10m;
    ssl_session_cache shared:SSL:10m;
    ssl_session_tickets off; # Requires nginx >= 1.5.9
    ssl_stapling on; # Requires nginx >= 1.3.7
    ssl_stapling_verify on; # Requires nginx => 1.3.7
    resolver 8.8.8.8 8.8.4.4 valid=300s;
    resolver_timeout 5s;
    add_header X-Frame-Options DENY;
    add_header X-Content-Type-Options nosniff;
    add_header X-XSS-Protection "1; mode=block";
    add_header Referrer-Policy no-referrer;
    add_header Strict-Transport-Security "max-age=31536000";
    ```
3. Once the changes are done, restart NGINX server

--------

Note: Developed on a server running Debian 10.2 and NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation
