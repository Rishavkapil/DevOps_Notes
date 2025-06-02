AWS cloudfront is a content delivery Network(CDN) service provided by aws that accelerates the delivery of static, dynamic and streaming web content to end users with low latency and high transfer rates . 

It is a web service  that speeds up distribution of your static and dynamic web content , to the users. 

Cloud Front delivers your content through a world wide network of data centers called **edge locations.** 


When a user request content that you're serving with cloudfront , the request is routed to the edge location with the lowest latency (time delay ) , so that content is delivered with best possible performance. 

If the content is already in the edge location with the lowest latency. The cloudfront delivers it immediately . 

If the content is not in that edge location , cloud front retrieves it from the origin that you have defined - such as amazon s3 bucket , a media packet channel or HTTP server that you have identified as the source .


#### Cloud front origin access Control


Cloudfront oac is a feature introduced by amazon cloudfront to secure Amazon S3 origins by allowing access to only designated cloudfront distributions . 


Cloudfront provides two ways to send authenticated requests to amazon S3 origin : origin access control and origin access identity. 
OAC helps you secure your origins such as amazon s3. 

OAC supports HTTP and HTTPS request using the POST method in AWS regions requiring AWS signature version 4 and integrates with server side Encryption with KMS(SSE-KMS)


	