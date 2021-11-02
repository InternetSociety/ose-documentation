# The Internet Society's Open Standards Everywhere Project

This repository contains documentation for the Internet Society's 2020 [Open Standards Everywhere](https://www.internetsociety.org/ose/) project with the goal of helping people create more secure web servers using the latest open standards.

## Documentation

The following documents were created as part of the project. The documentation has been developed and verified on our reference servers running Debian 10.2 and either Apache 2.4.38 or NGINX 1.14.2. We use certbot 0.31.0 for Let's Encrypt certificates.

### Introduction
* **[How to install an Apache web server as part of a LAMP stack](ose-web-lamp-stack.md)**
* **[How to install a NGINX web server as part of a LEMP stack](ose-web-lemp-stack.md)**

### IPv6
* **[How to configure IPv6 on your apache web server](ose-web-ipv6-apache.md)**
* **[How to configure IPv6 on your NGINX web server](ose-web-ipv6-nginx.md)**
* **[How to configure IPv6 on your web server with a CDN](ose-web-ipv6-cdns.md)**

### DNSSEC
* **[How to configure DNSSEC for your apache or NGINX web server](ose-web-dnssec-apache-nginx.md)**

### TLS 1.3 using Let's Encrypt
* **[How to configure TLS 1.3 on your apache web server](ose-web-tls-1-3-apache.md)**
* **[How to configure TLS 1.3 on your NGINX web server](ose-web-tls-1-3-nginx.md)**

### TLS - How to disable TLS 1.0 and 1.1

* **[How to disable TLS 1.0 and 1.1 on your apache web server](ose-web-tls-versions-apache.md)**
* **[How to disable TLS 1.0 and 1.1 on your NGINX web server](ose-web-tls-versions-nginx.md)**
* **[How to disable TLS 1.0 and 1.1 on your web server with a CDN](ose-web-tls-versions-cdns.md)**

### TLS - HSTS
* **[How to configure HSTS on your apache web server](ose-web-hsts-apache.md)**
* **[How to configure HSTS on your NGINX web server](ose-web-hsts-nginx.md)**
* **[How to configure HSTS on your web server with a CDN](ose-web-hsts-cdns.md)**

### TLS - Cipher Order
* **[How to configure TLS cipher order on your apache web server](ose-web-tls-cipher-order-apache.md)**
* **[How to configure TLS cipher order on your NGINX web server](ose-web-tls-cipher-order-nginx.md)**

### TLS - HTTP security headers
* **[How to configure HTTP security headers on your apache web server](ose-web-http-security-headers-apache.md)**
* **[How to configure HTTP security headers on your NGINX web server](ose-web-http-security-headers-nginx.md)**

### HTTP/2
* **[How to configure HTTP/2 on your apache web server](ose-web-http2-apache.md)**
* **[How to configure HTTP/2 on your NGINX web server](ose-web-http2-nginx.md)**
* **[How to configure HTTP/2 on your web server with a CDN](ose-web-http2-cdns.md)**

## Servers

For the 2020 Open Standards Everywhere (OSE) project, we built four reference servers so that you could use them for tests to see what "good" looks like:
* https://ose-apache.internetsociety.org/
* https://ose-apache-cdn.internetsociety.org/
* https://ose-nginx.internetsociety.org/
* https://ose-nginx-cdn.internetsociety.org/

All of these servers are being configured to achieve 100% on [the Internet.nl website test suite](https://internet.nl/) 
and to pass the [http2.pro](https://http2.pro/) HTTP/2 test.

Two of the servers are set up as "regular" web servers running in virtual machines. Two of the servers are set up behind a [content delivery network (CDN)](https://en.wikipedia.org/wiki/Content_delivery_network).

## Providing feedback

If you find any errors in the documentation, or have additional suggestions, [please open a new issue here on GitHub](https://github.com/InternetSociety/ose-documentation/issues) so that we can respond. If you do not use GitHub and do not wish to create a free GitHub account, you can [email project lead Dan York](mailto:york@isoc.org).

## Questions?

If you have questions about this project, please contact project lead Dan York, either here on Github (@danyork) or at [york@isoc.org](mailto:york@isoc.org)

