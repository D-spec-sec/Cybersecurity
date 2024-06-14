gobuster dir -u xxx.xxx.xxx.xxx -w /usr/share/wordlists/dirb/common.txt 
This will scan a target host using the wordlist (-w) from the specified directory
Adding a -x will define a specific file type.   (-x php, html)

Sub Domain enumeration - gobuster vhost -w /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -u  
To get this directory use - sudo apt install seclists

URL: gobuster dir --url http:whatever.com --wordlist /usr/share/wordlists/dirbuster/directory-list-2.3.txt
