

DNS record types are the records that provide information about the hostname or domain. These records include current IP address for the domain. 

Also , DNS records are stored in  text files (Zone files)  on the authoritative DNS server. 


### DNS record types

1. A record
2. AAAA record
3. CNAME record
4. Nameserver(NS ) record
5. Mail exchange record (MX ) record



#### 1. A record
 " A " in A record stands for address. 
 An A record shows the IP address for the specific hostname or domain . 

The main use of A record is for IP address Lookup . 

#### AAAA record

AAAA record , just like A record point to the IP address for a domain. 

But it points to IPV6 addresses. 


#### CNAME record

CNAME ( Canonical name) - is a DNS record that points  a domain name to another domain . 

A practical example for the use of CNAME record is running multiple subdomains for different purposes on the same server. 

It's also possible to point a CNAME To another CNAME. 

#### 4. NS record

A Nameserver (NS) record specifies the authoritative DNS server for a domain. 

In other words , A NS record helps point to internet applications like web browsers can find the IP address of the domain name. 