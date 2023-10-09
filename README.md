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
/Internet Data Mining:
https://www.netcraft.com

/DSN Recon:
```
dnsrecon hackersploit.org
```
OR can use: https://dnsdumpster.com 

/Addons:
- Built with
- Wappalyzer

/WAF (Web Application Firewall):
```
wafw00f hackersploit.org
```
/Subdomain Enumeration:
```
sublist3r -d hackersploit.org -e google, yahoo
```
/Exploit-DB:
https://www.exploit-db.com/

/Email Harvesting With theHarvester:
```
theHarvester -d hackersploit.org -b google,linkedin
```
/Leaked Password Databases
https://haveibeenpwned.com/

## Active Information Gathering:
