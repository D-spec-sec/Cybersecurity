# CheatSheet: 

![image](https://github.com/D-spec-sec/Cybersecurity/assets/172300374/fcf4cae7-34ad-4ffc-a804-2ed6ed17870e)
![image](https://github.com/D-spec-sec/Cybersecurity/assets/172300374/cfedc9ab-9b21-4a22-b89d-f0a76114c5a8)
![image](https://github.com/D-spec-sec/Cybersecurity/assets/172300374/54ff733d-eb6d-4db4-b7b1-2999edc324e7)


sudo nmap -sV -sC xxx.xxx.xxx.xxx

This does default sript scan and version detection


sudo nmap -sV -sC -p- xxx.xxx.xxx.xxx

This adds the port flag wich will scan all 65535 ports

adding the --min-rate 5000 (or whatever number) will specify the mininum number of packets Nmap should send per second, scans faster the higher the number goes

Determine if firewall is statefull or stateless

-sA (TCP ACK scan) .This scan is different than the others discussed so far in that it never determines open (or even open|filtered) ports. It is used to map out firewall rulesets, determining whether they are stateful or not and which ports are filtered  

Arp Ping Scan - discover assets 

# nmap -sP -PR 192.168.1.1/24 

ICMP Timestamp ping  : nmap -PP find system time on target machine 
