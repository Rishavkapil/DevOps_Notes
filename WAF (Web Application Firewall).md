

A WAF or web application firewall helps protect web applications by filtering and monitoring HTTP traffic between a web application and the internet .

It typically protects web applications from attacks such as `cross-site fogery, cross-site scripting , sql injections` and others. 

* **cross-site fogery attack** : A cross-site request fogery attack is a type of confused deputy cyber attack that tricks users into accidentally using their credentials to invoke a state changing activity, such as transforming funds from their account , changing their email address etc. 
* **cross-site scripting :** Cross site Scripting is an exploit where an attacker attaches code onto a legitimate website that will execute when the victim loads the website. That malicious code can be inserted in several ways. Most popularity , it is either added to the end of the url or posted directly onto the page. 

By deploying a waf in front of a web appication, a shield is placed between the web application and the internet. While a proxy server protects a clients machine identity by using an intermediary, a waf is type of reverse-proxy , protecting the server from exposure by having clients pass through the waf before reaching the server. 

A waf operates on set of rules often called policies. These polices aim to protect against vulnerabilities in the application by filtering out malicious traffic 



### What is the difference between Blocklist and allowlist WAF's 

A WAF that operates based on a blocklist protect against know attacks. 

A WAF that operates based on allowlist only admits traffic that have been pre-approved. 



### What are network based , Host-based , and cloud-based WAFs ?

* **Network-Based WAF :**  This is generally hardware based. Since they are installed locally they minimize latency, buy they are expensive since they require local hardware setup. 

* **Host-based WAF :** maybe fully integrated into an application software


* **Cloud-based WAF :** offers an affordable option that is very easy to implement; they usually offers a turnkey installation that is as simple as change in DNS to redirect traffic. 
