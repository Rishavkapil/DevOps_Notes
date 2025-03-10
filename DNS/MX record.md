#### 5. MX(Mail Exchange) record 

Directs mail to email server. 

The MX record indicates how email messages should be routed in accordance with the Simple mail Transfer Protocol (SMTP).

![[Pasted image 20250307175647.png]]

The 'Priority' number before the domains before these MX records indicates preference, the lower 'priority' value is prefered . This server will always try mailhost 1 because it has lower priority value. 




#### What is the process of querying MX record 

MTA (Message Transfer agent ) software is responsible for querying record. When a user sends an email, the MTA agent sends the DNS query to the DNS resolver to identify the mail server for the email recipients. The MTA establishes the SMTP connection with those mail servers. starting with prioritized domains. 

