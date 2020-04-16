# How to configure HTTP/2 on your web server with a CDN

Hypertext Transfer Protocol Version 2 (HTTP2), defined in [RFC 7540](https://tools.ietf.org/html/rfc7540) improves website performance and enables a more efficient use of network resources. Unlike its predecessor, HTTP/1.1, HTTP/2 can handle heavy loads of resources such as images, fonts, scripts, and stylesheets which result in better load speeds.  It reduces latency by introducing header field compression and enables Multiplexing, which allows the client and server to process multiple concurrent requests over the same connection.  

If you use a content delivery network (CDN) in front of your website, you will need to configure HTTP/2 within the CDN. We currently have instructions for the following CDNs:

## Enabling HTTP2 on Akamai
 
This should be enabled by default. But to confirm, you can do the following:
1. Login to your Akamai account
2. Go to the CDN/Properties section
3. Click on the property you want to verify
4. Under the Active Production Version, click on the hyperlink on the Version section
5. Under the Behaviors section, look for an HTTP/2 section. It should show HTTP/2 is Enabled. If it is, no further action is required.
6. If it has been disabled, re-enable and deploy the updated configuration
 
## Enabling HTTP2 on Cloudflare

HTTP/2 is enabled by default on all Cloudflare accounts
 
--------


This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation
