# How to configure HSTS on your web server with a CDN

HTTP Strict Transport Security (HSTS), defined in [RFC 6797](https://tools.ietf.org/html/rfc6797), requires web browsers to connect via HTTPS when visiting your website. This helps protect yourself and site visitors from man-in-the-middle (MitM) attacks.

**Note:** If you decide to disable HTTPS (TLS) while HSTS is enabled, visitors cannot access your site for the duration specified by the **max-age directive**. 
- The **max-age directive** states the maximum amount of time (in seconds) that responses remain in the browser cache. For instance, max-age=120 indicates that an asset can be reused for the next 120 seconds.
- In the case of HSTS, if the max-age directive is set to 6 months and you disable HTTPS 2 months after enabling HSTS, browsers that visited your site while HSTS was enabled cannot visit your site for another 4 months unless HTTPS is again enabled.

If you use a content delivery network (CDN) in front of your website, you will need to configure HSTS within the CDN.

## Enabling HSTS using Cloudflare:

1. Log in to the Cloudflare dashboard.
 
2. Click the appropriate Cloudflare account for the domain requiring HSTS.
 
3. Ensure the proper domain is selected.
 
4. Click on the Cloudflare SSL/TLS app.
 
5. Select the Edge Certificates tab.
 
6. Click Enable HSTS under the HTTP Strict Transport Security (HSTS) section.
 
7. A confirmation window appears. Review the warning content.
 
8. To proceed, click *I Understand*.
 
9. Click *Next*.

10. Configure HSTS settings appropriate for your domain.  We recommennd a HSTS max-age of at least six months (31536000 seconds). 

11. Save changes.


[Instructions for additional CDNs will be added in the future.]

--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, plase visit https://github.com/InternetSociety/ose-documentation
