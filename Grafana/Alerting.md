

Alerting is a feature that allows you to define conditions based on prometheus expression language expressions and send notifications about firing alerts to an external service. 

Prometheus Alerting is powered by alert manager. Prometheus forwards its alerts to Alert manager for handling any silencing , aggregation,  or sending of notifications across your platforms or event management system of choice . 


We can also run alert manager either inside or outside of our cluster. 


#### Alerting Concepts

There are three alerting concepts to familiarize yourself with when using Alertmanager to configure alerts : 

*  **Grouping :**  You can group alerts into categories (eg. node alerts , pod alerts)
			***Node alerts and pod alerts*** in alert manager are used to monitor the health and performance of nodes and pods in a Kubernetes cluster. 
* **Inhibition :**  They are used to suppress notifications for certain alerts if other specific alerts are already **firing** . 
			**Firing alerts** refers to the alerts that are currently active and meet the conditions set for them to trigger. 
* **Silencing :**  You can mute alerts based on labels or regular expressions .


### Rule file component 

A rule file uses the following basic template : 

		groups:  
		-name:  
		-rules: 
		- alert:
		- expr:  
		- for: 
		- labels:   
		- annotations:


* **Groups :** A collection of rules that run sequentially at a regular interval.
* **Name :** Name of the group 
* **rules :** rules in the group 
* **Alert :** A valid name label 
* **Expr :** The condition required for the alert to trigger. 
* **For :** The minimum duration for an alert's expression to be true(active) before updating              to a firing status 
* **Labels :** Any additional labels attached to the alerts. 
* **Annotations :** Annotations are like sticky notes attached to something . In this case , they help useful information, like a short description. 


### Recording Intervals 

Recording Interval is a setting that defines how long a threshold must be met before an alert enters a firing state. 




## Alert States

There are three main alert states to know : 

*  **Inactive :**  The alert rule condition is not met, meaning everything is normal and no alert 
			is triggered . 
*  **Pending :** The alert is met but has not reached the required duration. If the condition 
			stays true for the defined period , it moves to the firing state. 
	* **Firing :** The alert condition has been met for the required duration, and the alert is now active. 