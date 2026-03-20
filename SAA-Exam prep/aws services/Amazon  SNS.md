It is a Pub/sub(publish/subscribe)


Buying service --> SNS Topic --> Email Notification
					    --> fraud Service
						--> Shipping Service
						--> SQS


- The events producer only sends message to the SNS Topic.
