# The Internet Society's Open Standards Everywhere Project

This repository contains documentation for the Internet Society's [Open Standards Everywhere](https://www.internetsociety.org/ose/) project.

## Servers

For the Open Standards Everywhere (OSE) project, we are building four reference servers:
* https://ose-apache.internetsociety.org/
* https://ose-apache-cdn.internetsociety.org/
* https://ose-nginx.internetsociety.org/
* https://ose-nginx-cdn.internetsociety.org/

All of these servers are being configured to achieve 100% on [the Internet.nl website test suite](https://internet.nl/) 
and to pass the [http2.pro](https://http2.pro/) HTTP/2 test.

12 Feb 2020 Update - The two non-CDN sites are at 100% in the tests. The two CDN sites are at 97% while we are getting
some changes made to the TLS configuration (dropping support for TLS 1.0/1.1) in the CDN.  All four servers support HTTP/2.

## Current plan for documentation

The following documents will be created as part of the project. Note that they will all be written in English and then translated into French and Spanish.

We are not planning to create all of these documents entirely from scratch. We will also reference many of the other existing
excellent tutorials on these topics, including some the Internet Society created earlier as part of our Deploy360 Programme.

The technical documentation listed below is currently planned. As the project is just getting underway, **this list may change**.

As each piece of documentation is added to the repository, a link will be added to the list below. Documents without a link have not been created yet.

### Introduction
* How a generic apache, nginx, or basic LAMP-stack is missing security pieces

### IPv6
* How to configure IPv6 on your apache or nginx web server
* How to configure IPv6 on your apache or nginx web server with a CDN

### DNSSEC
* How to configure DNSSEC for your apache or nginx web server
* How to configure DNSSEC for your apache or nginx web server with a CDN

### TLS 1.3 using Let's Encrypt
* How to configure TLS 1.3 on your apache or nginx web server
* How to configure TLS 1.3 on your apache or nginx web server with a CDN

### TLS - How to disable TLS 1.0 and 1.1

* How to disable TLS 1.0 and 1.1 on your apache web server
* How to disable TLS 1.0 and 1.1 on your nginx web server
* **[How to disable TLS 1.0 and 1.1 on your web server with a CDN](ose-web-tls-versions-cdns.md)**

### TLS - HSTS
* **[How to configure HSTS on your apache web server](ose-web-hsts-apache.md)**
* **[How to configure HSTS on your nginx web server](ose-web-hsts-nginx.md)**
* **[How to configure HSTS on your web server with a CDN](ose-web-hsts-cdns.md)**

### TLS - Cipher Order
* How to configure TLS cipher order on your apache web server
* How to configure TLS cipher order on your nginx web server
* How to configure TLS cipher order on your apache or nginx web server with a CDN

### TLS - HTTP security headers
* How to configure HTTP security headers on your apache web server
* How to configure HTTP security headers on your nginx web server
* How to configure HTTP security headers on your apache or nginx web server with a CDN

### HTTP/2
* How to configure HTTP/2 on your apache web server
* How to configure HTTP/2 on your nginx web server
* How to configure HTTP/2 on your apace or nginx web server with a CDN

## Providing feedback

If you find any errors in the documentation, or have additional suggestions, [please open a new issue here on GitHub](https://github.com/InternetSociety/ose-documentation/issues) so that we can respond. If you do not use GitHub and do not wish to create a free GitHub account, you can [email project lead Dan York](mailto:york@isoc.org).

## Questions?

If you have questions about this project, please contact project lead Dan York, either here on Github (@danyork) or at [york@isoc.org](mailto:york@isoc.org)

