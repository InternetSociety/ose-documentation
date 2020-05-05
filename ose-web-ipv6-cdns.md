# How to configure IPv6 on your web server with a CDN

IPv6 is the latest version of the Internet Protocol (IP) addresses that every device needs to connect to the Internet. In order to make your web site available to the widest number of people at the fastest possible speed, your site needs to support both IPv4 and IPv6.

Content delivery networks (CDNs) provide one mechanism to easily add IPv6 support to your website. Many CDNs do not require that your original web server (called an 'origin server' in CDN terminology) supports IPv6. It can only work over IPv4.

Many CDNs support IPv6 by default. There is no further action you need to do once you have set up your account with the CDN. We are currently aware that the following CDNs enable IPv6 by default:

* Akamai
* Amazon CloudFront
* BelugaCDN
* Cloudflare
* Fastly
* Limelight
* OVH

--------

## Configuring a CNAME record

Some CDNs require that they host your DNS records directly. Other CDNs allow you to set a `CNAME` record in DNS pointing over to the CDN. For example, for ose-apache-cdn.internetsociety.org the record is as follows:
 
```
ose-apache-cdn.internetsociety.org  CNAME  ose-apache-cdn.internetsociety.org.cdn.cloudflare.net
```

When you initially add this `CNAME` record at your DNS provider, we recommend setting your TTL (Time-to-live) for the CNAME record to 5 minutes (or as low as possible) to make sure the setup is correct. Once you are comfortable that the settings are correct, you can raise the TTL to what you are using for a standard for your organization.

--------

## Resources

* [IPv6 information](https://www.internetsociety.org/deploy360/ipv6/)
* [Making Content Available Over IPv6](https://www.internetsociety.org/resources/deploy360/2013/making-content-available-over-ipv6/)
* [Video: How How To IPv6-Enable ANY Website Using A Content Delivery Network (CDN)](https://www.internetsociety.org/blog/2012/05/video-how-to-ipv6-enable-any-website-using-a-cdn/)
--------


This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation