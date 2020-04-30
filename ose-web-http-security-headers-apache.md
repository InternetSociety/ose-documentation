# How to configure HTTP security headers on your Apache web server

The addition of these HTTP headers will help secure the web server from several common attacks. This document shows simple configurations. You may need to adjust these for your specific site. We recommended that you do add these security headers one at a time and test them in a non-production environment to ensure there are no negative impacts to your site.

## SSL Stapling:

SSL Stapling needs to be added outside of the secure Virtual Host block (right before the `<IfModule mod_ssl.c>` statement). The statement is as follows:

 ```
    SSLStaplingCache shmcb:/tmp/stapling_cache(128000)
 ```
                
## Other Security Headers

These headers should be added in the Virtual Host section dealing with 443 (or the port that you are using for secure connections).  If you have already configured your Apache server for HSTS, then all other required steps have been done to allow for the inclusion of these headers. 

```
   Header always append X-Frame-Options DENY
   Header set X-XSS-Protection "1; mode=block"
   Header set X-Content-Type-Options nosniff
   Header set Referrer-Policy "no-referrer"
```

When you are done, you will need to restart Apache.

--------

## Resources

* *(To be added - list of relevant RFCs and/or tutorials.)*

--------

Note: Developed on a server running Debian 10.2 and Apache 2.4.38.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation
