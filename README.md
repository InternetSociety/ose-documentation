# The Internet Society's Open Standards Everywhere Project

This repository contains documentation for the Internet Society's [Open Standards Everywhere](https://www.internetsociety.org/ose/) project.

## Servers

For the Open Standards Everywhere (OSE) project, we are building four reference servers:
* https://ose-apache.internetsociety.org/
* https://ose-apache-cdn.internetsociety.org/  (not yet available at this address)
* https://ose-nginx.internetsociety.org/
* https://ose-nginx-cdn.internetsociety.org/ (not yet available at this address)

All of these servers have been configured to achieve 100% on [the Internet.nl website test suite](https://internet.nl/) 
and are in the process of being configured to pass the [http2.pro](https://http2.pro/) HTTP/2 test.

## Current plan for documentation

The following documents will be created as part of the project. Note that they will all be written in English and then translated into French and Spanish.

We are not planning to create all of these documents entirely from scratch. We will also reference many of the other existing
excellent tutorials on these topics, including some the Internet Society created earlier as part of our Deploy360 Programme.

The technical documentation listed below is currently planned. As the project is just getting underway, **this list may change**.
Once documents are created in this repository, they will be linked from this page. We are planning to get the documentation
work underway in the later part of February 2020.

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
[Note: need to include notes about how to turn off older versions of TLS]

### TLS - HSTS
* How to configure HSTS on your apache web server
* How to configure HSTS on your nginx web server
* How to configure HSTS on your apache or nginx web server with a CDN

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

## Questions?
If you have questions about this project, please contact project lead Dan York, either here on Github (@danyork) or at [york@isoc.org](mailto:york@isoc.org)

