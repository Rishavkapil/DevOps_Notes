
1. You need to create a telegram channel and then you need to create a bot for that
2. From there you need to copy Bot_token and chat id
3. to get chat id to need to hit : 
			https://api.telegram.org/bot{dein_bot_api_token}/getUpdates
4. Then you need to create a alertrules for the server
5. for that create a new file in /etc/promethes and it will be alert.rules.yml
6. then add the following content to that file : 

			groups :
			  - name : server_is_down
			    rules :
			    - alert : ServerDown
				    expr : up == 0
				    for : 1m
				    annotations :
			        summary : "Server Down Alert"
				    description : "Instance {{ $labels.instance }} is down for more that 1 minute."
			      labels :
			       severity : 'critical'
                                                                                                                                                                                           


7. Then if you also need to create the alertmanager.yml file (if you are using prometheus to send alerts)
8. And in that file you need to add the following content in that file : 

				route:
			  receiver: 'telegram'
				receivers:
				  - name: 'telegram'
			    telegram_configs:
			      - bot_token : 7643043590:AAHW0CFBSHR_S5NpRv260A8JzEXHoJt5xX4
			        chat_id :-1002554813188
		        message : "{{range.Alerts}} Alert : {{.Annotations.summary}}\n Description: {{.Annotations.description}}\n Severity: {{.Labels.severity}}\n"

## and if you are sending alerts from grafana


You need to Create a Alert rules in Grafana

![[Pasted image 20250326132600.png]]




![[Pasted image 20250326132618.png]]



then you need to configure contact point for sending notifications like here i have used telegram for that 
![[Pasted image 20250326132703.png]]


	then just click **save rule and exit** . 