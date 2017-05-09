> http://www.30abysses.com/TWY/2017/05/08/dns-notes.md
> by TW Yang <twy@30abysses.com> 2017-05-08 CC-BY-4.0

# CS: DNS

Notes about DNS (Domain Name System).


## Overview

* [Function][1]
* [Structure][2]
* [Operation][3]

[1]: https://en.wikipedia.org/wiki/Domain_Name_System#Function
[2]: https://en.wikipedia.org/wiki/Domain_Name_System#Structure
[3]: https://en.wikipedia.org/wiki/Domain_Name_System#Operation


### Authoritative vs. Recursive

* [Authoritative Name Server][4]
  * [Start of Authority Record (SOA)][10]
    * [What is a SOA record?][12]
  * [DNS Zone Files][11]
* [Recursive Name Server][5]
* [Authoritative DNS Servers vs. Recursive DNS Servers][9]

[4]: https://en.wikipedia.org/wiki/Domain_Name_System#Authoritative_name_server
[5]: https://en.wikipedia.org/wiki/Domain_Name_System#Recursive_and_caching_name_server
[9]: http://www.noip.com/blog/2013/11/22/authoritative-dns-vs-recursive-dns-work/
[10]: http://www.inetdaemon.com/tutorials/internet/dns/configuration/zone_files/resource_records/soa.shtml
[11]: http://www.inetdaemon.com/tutorials/internet/dns/configuration/zone_files/index.shtml
[12]: https://support.dnsimple.com/articles/soa-record/


### Anycast vs. Unicast

* [Anycast DNS - Part 1, Overview][7]
* [What is “anycast” and how is it helpful?][8]

[7]: http://ddiguru.com/blog/118-introduction-to-anycast-dns
[8]: https://serverfault.com/questions/14985/what-is-anycast-and-how-is-it-helpful


### DNS Record Types

* [List of DNS record types][6]

> The most common types of records stored in the DNS database are for
> Start of Authority (SOA), IP addresses (A and AAAA), SMTP mail
> exchangers (MX), name servers (NS), pointers for reverse DNS lookups
> (PTR), and domain name aliases (CNAME). Although not intended to be a
> general purpose database, DNS can store records for other types of
> data for either automatic lookups, such as DNSSEC records, or for
> human queries such as responsible person (RP) records.
>
> https://en.wikipedia.org/wiki/Domain_Name_System

[6]: https://en.wikipedia.org/wiki/List_of_DNS_record_types


## Online Tools

* [http://www.dnssy.com/][14]
* [https://mxtoolbox.com/NetworkTools.aspx][13]
* [http://dns.squish.net/][15]
* [https://asm.ca.com/en/dnstool.php][16]
* [http://www.traceroute.org/][17]

[13]: https://mxtoolbox.com/NetworkTools.aspx
[14]: http://www.dnssy.com/
[15]: http://dns.squish.net/
[16]: https://asm.ca.com/en/dnstool.php
[17]: http://www.traceroute.org/


## Local Tools

```
nslookup -querytype=SOA example.com

dig example.com any
```
