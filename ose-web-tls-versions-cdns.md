# How to disable TLS 1.0 and 1.1 on your web server with a CDN

Transport Layer Security (TLS), defined in [RFC 8446](https://tools.ietf.org/html/rfc8446) provides communication security. Websites and client/server applications use TLS to secure communications between their servers and web browsers in a way that is designed to prevent eavesdropping, tampering, or message forgery. When you connect to a web address that starts with "https://", you are connecting using TLS.  Note that some people still refer to TLS using an older name, Secure Sockets Layer (SSL).

TLS is currently at version 1.3. Web servers can support multiple versions, but version 1.0 (from 1999) and 1.1 (from 2006) are known to be at risk of not being secure enough. To protect your website from possible attacks against these older TLS versions, IT security guidelines recommend disabling TLS 1.0 and 1.1 on your web server.

If you use a content delivery network (CDN) in front of your website, you will need to configure TLS versions within the CDN.

## TLS 1.3 on Cloudflare:
1. Login to your Cloudflare account
2. Click on SSL/TLS icon
3. Click on Edge Certificates
4. Scroll to Minimum TLS Version section
5. Select TLS 1.2 (this will automatically set the TLS version to 1.2 or higher.)


## TLS 1.3 on Akamai:
1. Login to your Akamai account
2. Go to the CDN/Certificates section
3. Under Actions, select View and Edit Deployment Settings
4. Click Edit on the Advanced Network Configuration section
5. Selection Disable specific TLS versions and Check TLS 1.0 and TLS 1.1
6. Click Submit and wait until deployment of the configuration is complete

--------

## Resources

* [IT Security Guidelines for Transport Layer Security (TLS)](https://english.ncsc.nl/publications/publications/2019/juni/01/it-security-guidelines-for-transport-layer-security-tls) - from the Dutch National Cyber Security Centre (NCSC)
* [RFC 8446 - The Transport Layer Security (TLS) Protocol Version 1.3](https://tools.ietf.org/html/rfc8446)

--------


This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation