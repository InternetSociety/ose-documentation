# How to configure HTTP security headers on your NGINX web server

The addition of these HTTP headers will help secure the web server from several common attacks. This document shows simple configurations. You may need to adjust these for your specific site. We recommended that you do add these security headers one at a time and test them in a non-production environment to ensure there are no negative impacts to your site.

## Using a separate SSL parameters file


With NGINX, you can add HTTP security headers directly into the standard `nginx.conf` file. Or you can create a separate configuration file with the SSL parameters. The benefit of doing this in a separate file is that you can use the same file and include it in multiple web configurations or exclude it from sites that need different configurations.

Our reference servers use a separate configuration file called `ssl-params.conf`. The contents are below, with the new headers in bold:

<pre><code>
ssl_protocols TLSv1.2 TLSv1.3;
ssl_prefer_server_ciphers on;
ssl_dhparam /etc/ssl/certs/dhparam.pem;
ssl_ciphers    ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-$
 
 
ssl_ecdh_curve secp384r1; # Requires nginx >= 1.1.0
ssl_session_timeout  10m;
ssl_session_cache shared:SSL:10m;
ssl_session_tickets off; # Requires nginx >= 1.5.9
<strong>ssl_stapling on; # Requires nginx >= 1.3.7</strong>
<strong>ssl_stapling_verify on; # Requires nginx => 1.3.7</strong>
resolver 8.8.8.8 8.8.4.4 valid=300s;
resolver_timeout 5s;
<strong>add_header X-Frame-Options DENY;</strong>
<strong>add_header X-Content-Type-Options nosniff;</strong>
<strong>add_header X-XSS-Protection "1; mode=block";</strong>
<strong>add_header Referrer-Policy no-referrer;</strong>
add_header Strict-Transport-Security "max-age=31536000";
<strong>add_header Content-Security-Policy "default-src 'none'; img-src 'self'; style-s$</strong>
</code></pre>

## Including the separate file

In our `nginx.conf` file, we then include this `ssl-params.conf` file that we put in a `snippets` subdirectory:

<pre><code>
server {
    listen 443 ssl;
    listen [::]:443 ssl;
    <strong>include snippets/ssl-params.conf;</strong>
 
    server_name example.com www.example.com;
 
    root /var/www/example.com/html;
    index index.html index.htm index.nginx-debian.html;
}
</code></pre>

When you are done, you will need to restart NGINX.

--------

## Resources

* *(To be added - list of relevant RFCs and/or tutorials.)*
1. https://tools.ietf.org/html/rfc2660 - RFC2660: The Secure Hypertext Transfer Protocol RFC
2. https://developers.cloudflare.com/ssl/ssl-tls/cipher-suites/ - Cloudflare's list of supported Cipher Suites
3. https://wiki.mozilla.org/Security/Server_Side_TLS - Server Side TLS by Mozilla
4. https://github.com/cloudflare/sslconfig - ChaCha20/Poly1305 patch by Cloudflare

--------

Note: Developed on a server running Debian 10.2 and NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation
