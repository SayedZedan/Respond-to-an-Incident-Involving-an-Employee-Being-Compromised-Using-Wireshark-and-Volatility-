# Respond-to-an-Incident-Involving-an-Employee-Being-Compromised-Using-Wireshark-and-Volatility-

In this project, I investigated a potential security breach after a customer expressed concerns about a practice virtual machine (VM) they had downloaded from a compromised capture the flag website. I focused on identifying vulnerabilities exploited by threat actors, particularly through Cross-Site Scripting (XSS) attacks, which directed traffic to malicious IP addresses.

My key actions included:

1. **Vulnerability Assessment:** I evaluated the web applications on the VM for known vulnerabilities.
2. **Traffic Analysis:** I monitored network traffic to identify suspicious IP addresses.
3. **Impact Evaluation:** I assessed the potential risks to the customer's infrastructure.
   ----------------------------------------------------------------------------------------------------
   
   ## 1. **Identifying the IP Address of the Malicious Website:**

In my analysis, I considered the IP address of the virtual machine hosting the malicious website to be **192.168.248.217**. Given the client's hints that the victim was “practicing” with a local VM, I assumed the victim was using an internal IP address to maintain isolation. 

With this assumption in mind, I applied a filter in Wireshark, setting the source IP address to **192.168.248.100** and allowing the destination to be any IP address within that range. 

I quickly observed connections to **192.168.248.2** and **192.168.248.217**. It became clear that there was web browsing activity directed toward the **217** address. Upon further investigation, I found that a vulnerable practice server was being accessed. I noted this in packet number **30197**.
![Screenshot (545)](https://github.com/user-attachments/assets/20a46387-9856-4a52-a61d-0de61fa47de7)

_________________________________________________________________________________________________________________________________________

## 2. **Identifying the Attackers' IP Address:**

I deduced that the eventual attacker's IP address is **192.168.248.200**. This conclusion stemmed from observing that immediately after connecting to what appeared to be the practice web server, there was a direct connection to port **8080** on **192.168.248.200**. This was quickly followed by another connection to port **4444** on the same IP address.

To further validate my findings, I filtered the traffic for both **192.168.248.100** (the victim's IP) and **192.168.248.200**. This filter revealed the same behavior, showcasing all connections between the two IP addressees 
![Screenshot (547)](https://github.com/user-attachments/assets/10b7cff3-7e5b-49df-89c6-b0c5bef3bc53)
--------------------------------------------------------------------------------------------------------



