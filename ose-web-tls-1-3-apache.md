# How to configure TLS 1.3 on your web server with Apache

Transport Layer Security (TLS), defined in [RFC 8446](https://tools.ietf.org/html/rfc8446) provides communication security. Websites and client/server applications use TLS to secure communications between their servers and web browsers in a way that is designed to prevent eavesdropping, tampering, or message forgery. When you connect to a web address that starts with "https://", you are connecting using TLS. Note that some people still refer to TLS using an older name, Secure Sockets Layer (SSL).

TLS is currently at version 1.3. Web servers can support multiple versions, but version 1.0 (from 1999) and 1.1 (from 2006) are known to be at risk of not being secure enough. To protect your website from possible attacks against these older TLS versions, IT security guidelines recommend disabling TLS 1.0 and 1.1 on your web server and only support TLS versions 1.2 and 1.3.

## Configure TLS 1.3 on Apache:

1. Go to the directory where you installed Let's Encrypt, typically `/etc/letsencrypt`

2. Edit `options-ssl-apache.conf`

3. Find the `SSLProtocol` line and set it to the following (if it is not already set):
    ```
    SSLProtocol all -SSLv2 -SSLv3 -TLSv1 -TLSv1.1
    ``` 
    
4. Save the file.

5. Restart Apache

Note that this change will enable TLS 1.3, continue support for TLS 1.2, and remove support for TLS 1.0 and TLS 1.1.

--------

## Resources

* [IT Security Guidelines for Transport Layer Security (TLS)](https://english.ncsc.nl/publications/publications/2019/juni/01/it-security-guidelines-for-transport-layer-security-tls) - from the Dutch National Cyber Security Centre (NCSC)
* [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446)

--------

Note: Developed on a server running Debian 10.2 and Apache 2.4.38.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation