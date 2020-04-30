# How to configure IPv6 on your Apache web server 

IPv6 is the latest version of the Internet Protocol (IP) addresses that every device needs to connect to the Internet. In order to make your web site available to the widest number of people at the fastest possible speed, your site needs to support both IPv4 and IPv6.

For your web site to respond over IPv6, your web server needs to be connected to a network with IPv6 connectivity. If you host your server on your own network, you may need to ask your IT team or Internet Service Provider (ISP) about receiving IPv6 connectivity. If you use a hosting provider, you may need to ask about getting an IPv6 address for your web server. If they are unable to provide an IPv6 address, you will need to either: 1) change to a different hosting provider; or 2) consider using a content delivery network (CDN) in front of your website.

--------

## Configuring IPv6 on Apache

Apache is configured by default to listen to all available IP addresses on your server, both IPv4 and IPv6. Once you confirm you have IPv6 connectivity on your web server, it should just start replying to HTTP requests over IPv6.

You can confirm this in your virtual host file. (This is often `httpd.conf` or `apache.conf`) You should see a line:

```
  <VirtualHost *:443>
```
 
Note that this configures your web server to respond to incoming HTTP requests on *any* IPv6 addresses on the server. If you have a web server with multiple IPv6 addresses and you want the web server to respond to only a single IPv6 address, you will need to change the line to something like this:

```
  <VirtualHost xxx.xxx.xxx.xxx:443 [xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx]:443>
```

--------

## Resources

* [IPv6 information](https://www.internetsociety.org/deploy360/ipv6/)
* [Making Content Available Over IPv6](https://www.internetsociety.org/resources/deploy360/2013/making-content-available-over-ipv6/)

--------

Note: Developed on a server running Debian 10.2 and Apache 2.4.38.
 
--------

This documentation is part of the Internet Society's [Open Standards Everywhere project](https://www.internetsociety.org/ose/).
To find the most recent version or to provide feedback, please visit https://github.com/InternetSociety/ose-documentation