# How to disable TLS 1.0 and 1.1 on your web server with NGINX
Transport Layer Security (TLS), defined in [RFC 8446](https://tools.ietf.org/html/rfc8446) provides communication security. Websites and client/server applications use TLS to secure communications between their servers and web browsers in a way that is designed to prevent eavesdropping, tampering, or message forgery. When you connect to a web address that starts with "https://", you are connecting using TLS. Note that some people still refer to TLS using an older name, Secure Sockets Layer (SSL).

TLS is currently at version 1.3. Web servers can support multiple versions, but version 1.0 (from 1999) and 1.1 (from 2006) are known to be at risk of not being secure enough. To protect your website from possible attacks against these older TLS versions, IT security guidelines recommend disabling TLS 1.0 and 1.1 on your web server and only support TLS versions 1.2 and 1.3.

## Disable TLS 1.0/1.1 on NGINX:
To disable, we will set the `ssl_protocols` directive to only allow TLS1.2 and TLS1.3

1. Edit `ssl-parms.conf`
    **Note**: we have our SSL directives setup in a file called ssl-parms.conf. You configuration may differ, so be sure you are editing where your SSL configuration is being read from.

2. Find the ssl_protocols directive and set to the following:
    ```
    ssl_protocols  TLSv1.2 TLSv1.3;
    ``` 
3. Restart NGINX

--------

## Resources

* [IT Security Guidelines for Transport Layer Security (TLS)](https://english.ncsc.nl/publications/publications/2019/juni/01/it-security-guidelines-for-transport-layer-security-tls) - from the Dutch National Cyber Security Centre (NCSC)
* [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446)

--------

Note: Developed on a server running Debian 10.2 and NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation