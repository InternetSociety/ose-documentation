# How to configure DNSSEC for your web server using either Apache or NGINX

“DNS Security Extensions,” commonly known as DNSSEC, provide a way to be sure you are getting accurate information from DNS.  For example, before you connect to a website, your browser has to retrieve the IP address of the site using DNS. However, it is possible for an attacker to intercept your DNS queries and provide false information. This could cause your browser to connect to a fake website where you could potentially provide personal information (for example, what you think is a bank website). DNSSEC provides a level of additional security where the web browser (or other application) can check to make sure the DNS information is correct and was not modified.

The steps involved include:

1. The DNS servers that host your domain must "sign" the domain. These DNS servers might be ones that you operate directly. They might be at a DNS hosting provider. They might be at your domain name registrar.

2. Information from the DNS server about the signatures (a "DS record") must be given to your domain name registrar.

3. The domain name registrar will send that DS record to the "registry" for the top-level domain for your domain (ex. .COM, .ORG, .NL, .MX)

Once this has been completed, your domain will be signed.

--------

## Resources

* [DNSSEC resources from Deploy360 Programme](https://www.internetsociety.org/deploy360/dnssec/)
* [DNSSEC Basics](https://www.internetsociety.org/deploy360/dnssec/basics/)

--------

Note: Developed on servers running Debian 10.2 and Apache 2.4.38 or NGINX 1.14.2.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation