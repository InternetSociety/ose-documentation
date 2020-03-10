# How to configure TLS cipher order on your Apache web server
Transport Layer Security (TLS), defined in [RFC 8446](https://tools.ietf.org/html/rfc8446) provides communication security. Websites and client/server applications use TLS to secure communications between their servers and web browsers in a way that is designed to prevent eavesdropping, tampering, or message forgery. When you connect to a web address that starts with "https://", you are connecting using TLS. Note that some people still refer to TLS using an older name, Secure Sockets Layer (SSL).

TLS supports the use of multiple cryptographic ciphers for encryption and digital signatures. A best practice today is to configure your web server to prefer the most secure ciphers over other ciphers. When a web browser connects to your web server, the server will indicate that it wants to use the most secure ciphers first.


## TLS cipher order on Apache:

To set the cipher order so that they are in the correct order for the TLS1.2 and TLS1.3 protocols:

1. Edit ssl.conf (should have already been enabled when setting up server for SSL connections)
 
2. Find the SSLCipherSuite direction and set to the following:
    ```
    SSSLCipherSuite      
    ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305::ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384
    ```
3. Restart Apache

--------

## Resources

* [IT Security Guidelines for Transport Layer Security (TLS)](https://english.ncsc.nl/publications/publications/2019/juni/01/it-security-guidelines-for-transport-layer-security-tls) - from the Dutch National Cyber Security Centre (NCSC)
* [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446)

--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation