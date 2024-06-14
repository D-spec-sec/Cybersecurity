smbclient \\\\10.10.10.131\\ADMIN$ -U Administrator  - connect to box using admin 

smbclient -N \\\\{TARGET_IP}\\{share}

smbclient -N -L \\\\{TARGET_IP}\\   - list shares without logging in 
