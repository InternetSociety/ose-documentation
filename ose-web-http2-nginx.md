# How to configure HTTP/2 on your NGINX web server

Hypertext Transfer Protocol Version 2 (HTTP2), defined in [RFC 7540](https://tools.ietf.org/html/rfc7540) improves website performance and enables a more efficient use of network resources. Unlike its predecessor, HTTP/1.1, HTTP/2 can handle heavy loads of resources such as images, fonts, scripts, and stylesheets which result in better load speeds.  It reduces latency by introducing header field compression and enables multiplexing, which allows the client and server to process multiple concurrent requests over the same connection.  

## HTTP2 on NGINX
1. Open your configuration file (we will use `default.conf` as an example)
2. Edit the listen direction by adding http2. It should look like the following assuming you are using both IPv4 and IPv6.
    ```    
    listen 443 http2 ssl;
    listen [::]:443 http2 ssl;
    ```   
3. Save file and restart NGINX

--------

## Resources

* [RFC 7540 - Hypertext Transfer Protocol Version 2 (HTTP/2)](https://tools.ietf.org/html/rfc7540)
* [HTTP/2 site - IETF HTTP Working Group](https://http2.github.io/)
* [Introduction to HTTP/2 - Google](https://developers.google.com/web/fundamentals/performance/http2)

-------

Note: Developed on a server running Debian 10.2 and NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation