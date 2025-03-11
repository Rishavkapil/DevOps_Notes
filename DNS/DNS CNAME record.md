

#### What is DNS CNAME record


A "Canonical Domain" (CNAME) points from alias domain to canonical domain

When a domain or subdomain is in alias for another domain  , All CNAME records must point to a domain , not to a IP address. 


Imagine  a Scavenger hunt where each clue points to a another clue , and the final clue points to a treasure. 


#### Can a CNAME record points to another CNAME record 



Pointing a CNAME record to another CNAME record is inefficient because it requires multiple DNS lookups before the domain name can be loaded -- which slows down the user experience . 



NO other DNS records can have same name as any given CNAME record . 
