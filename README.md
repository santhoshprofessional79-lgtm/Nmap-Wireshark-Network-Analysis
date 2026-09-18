  Lab 1: Local Network Host Discovery using Nmap & Wireshark

 Objective
To analyze how Nmap identifies live hosts on a local subnet using the Address Resolution Protocol (ARP) instead of standard ICMP pings.

 Environment Setup
Attacker OS: Kali Linux
Target OS: Windows 11
Tools Used: Nmap, Wireshark

 The Attack (Execution)
Initiated a Ping Sweep scan targeting the local Windows machine:
nmap -sn 10.189.42.248 



 Key Observations
By analyzing the packet capture in Wireshark, I observed the following behavior:
1. Local Network Behavior: Because both the attacker and the target reside on the same local subnet, Nmap defaulted to using ARP for host discovery.
2. ARP Broadcast: The Kali Linux machine sent a broadcast message asking, "Who has <Target_IP>? Tell <Kali_IP>".
3. ARP Reply: The target Windows machine responded with its MAC address directly to the attacker, confirming the host is alive. 

Conclusion: Host discovery on a local network heavily relies on Layer 2 (MAC/ARP) communication rather than Layer 3 (IP/ICMP) communication.
