## Write ups VULN
1. ip address : 107.180.47.12

# error server 
once user are connected, the server always redirect on account/login but the user are so connected, so the session id of any user change
everytime, all only

<b>Warning</b>:  session_start(): open(/opt/alt/php72/var/lib/php/session/sess_a150685c822e9f5be519db002b1cf296, O_RDWR) failed: Disk quota exceeded (122) in <b>/home/achtel9/public_html/ibous.com/home/index.php</b> on line <b>10</b><br />
<br />
<b>Warning</b>:  session_start(): Failed to read session data: files (path: /opt/alt/php72/var/lib/php/session) in <b>/home/achtel9/public_html/ibous.com/home/index.php</b> on line <b>10</b><br />

# waf scan
[-] No WAF detected by the generic detection

# nmap scan 
21/tcp   open  ftp        Pure-FTPd
22/tcp   open  ssh        OpenSSH 5.3 (protocol 2.0)
25/tcp   open  smtp?
80/tcp   open  http       Apache httpd
110/tcp  open  pop3       Dovecot pop3d
143/tcp  open  imap       Dovecot imapd
443/tcp  open  ssl/http   Apache httpd
465/tcp  open  ssl/smtp   Exim smtpd 4.93
587/tcp  open  smtp       Exim smtpd 4.93
993/tcp  open  ssl/imaps?
995/tcp  open  ssl/pop3s?
3306/tcp open  mysql      MySQL 5.6.49-cll-lve

# remark

strip_tags, filter php
htmlentities also
control JS for input
SQLMAP doesn't work
form no-response with invalid varible 
Burpsuite inspecting 
# Webmaster
webmaster@ibous.achtel9.ibous.com

# dirb
+ http://www.ibous.com/.htaccess (CODE:403|SIZE:318)                                                                                                                 
+ http://www.ibous.com/.htpasswd (CODE:403|SIZE:318)                                                                                                                 
==> DIRECTORY: http://www.ibous.com/account/                                                                                                                         
+ http://www.ibous.com/activate (CODE:302|SIZE:0)                                                                                                                    
+ http://www.ibous.com/admin.php (CODE:302|SIZE:325)                                                                                                                 
==> DIRECTORY: http://www.ibous.com/agent/                                                                                                                           
==> DIRECTORY: http://www.ibous.com/api/                                                                                                                             
==> DIRECTORY: http://www.ibous.com/app/                                                                                                                             
==> DIRECTORY: http://www.ibous.com/business/                                                                                                                        
+ http://www.ibous.com/Business (CODE:302|SIZE:0)                                                                                                                    
==> DIRECTORY: http://www.ibous.com/cgi-sys/                                                                                                                         
+ http://www.ibous.com/common (CODE:200|SIZE:0)                                                                                                                      
+ http://www.ibous.com/controlpanel (CODE:200|SIZE:33899)                                                                                                            
+ http://www.ibous.com/cpanel (CODE:200|SIZE:33899)                                                                                                                  
==> DIRECTORY: http://www.ibous.com/css/                                                                                                                             
+ http://www.ibous.com/data (CODE:200|SIZE:2)                                                                                                                        
==> DIRECTORY: http://www.ibous.com/developers/                                                                                                                      
+ http://www.ibous.com/en (CODE:302|SIZE:0)                                                                                                                          
+ http://www.ibous.com/es (CODE:302|SIZE:0)                                                                                                                          
==> DIRECTORY: http://www.ibous.com/fonts/                                                                                                                           
+ http://www.ibous.com/fr (CODE:302|SIZE:0)                                                                                                                          
==> DIRECTORY: http://www.ibous.com/functions/                                                                                                                       
==> DIRECTORY: http://www.ibous.com/help/                                                                                                                            
==> DIRECTORY: http://www.ibous.com/home/                                                                                                                            
+ http://www.ibous.com/ht (CODE:302|SIZE:0)                                                                                                                          
==> DIRECTORY: http://www.ibous.com/images/                                                                                                                          
==> DIRECTORY: http://www.ibous.com/inc/                                                                                                                             
+ http://www.ibous.com/index (CODE:302|SIZE:0)                                                                                                                       
+ http://www.ibous.com/index.php (CODE:302|SIZE:325)                                                                                                                 
+ http://www.ibous.com/info.php (CODE:302|SIZE:324)                                                                                                                  
==> DIRECTORY: http://www.ibous.com/js/                                                                                                                              
==> DIRECTORY: http://www.ibous.com/languages/                                                                                                                       
+ http://www.ibous.com/login (CODE:200|SIZE:6236)                                                                                                                    
+ http://www.ibous.com/Login (CODE:200|SIZE:6236)                                                                                                                    
==> DIRECTORY: http://www.ibous.com/mailman/                                                                                                                         
==> DIRECTORY: http://www.ibous.com/notification/                                                                                                                    
+ http://www.ibous.com/php.ini (CODE:403|SIZE:318)                                                                                                                   
+ http://www.ibous.com/phpinfo.php (CODE:302|SIZE:327)                                                                                                               
==> DIRECTORY: http://www.ibous.com/pipermail/                                                                                                                       
==> DIRECTORY: http://www.ibous.com/product/                                                                                                                         
+ http://www.ibous.com/robots.txt (CODE:200|SIZE:238)                                                                                                                
+ http://www.ibous.com/signup (CODE:200|SIZE:51397)                                                                                                                  
+ http://www.ibous.com/sitemap.xml (CODE:200|SIZE:2502) 
 
*PANEL ADMIN :* https://www.ibous.com/cpanel-admin/login
# vulnerable
1. 21/tcp   open  ftp        Pure-FTPd
|_clamav-exec: ERROR: Script execution failed (use -d to debug)
| ftp-libopie: 
|   VULNERABLE:
|   OPIE off-by-one stack overflow
|     State: LIKELY VULNERABLE
|     IDs:  BID:40403  CVE:CVE-2010-1938
|     Risk factor: High  CVSSv2: 9.3 (HIGH) (AV:N/AC:M/Au:N/C:C/I:C/A:C)
|       An off-by-one error in OPIE library 2.4.1-test1 and earlier, allows remote
|       attackers to cause a denial of service or possibly execute arbitrary code
|       via a long username.

2. 80/tcp   open  http       Apache httpd
|_http-vuln-cve2014-3704

3. 143 & 110/tcp  open  pop3       Dovecot pop3d
| ssl-dh-params: 
|   VULNERABLE:
|   Diffie-Hellman Key Exchange Insufficient Group Strength
|     State: VULNERABLE
|       Transport Layer Security (TLS) services that use Diffie-Hellman groups
|       of insufficient strength, especially those using one of a few commonly
|       shared groups, may be susceptible to passive eavesdropping attacks.

4. 3306/tcp open  mysql      MySQL 5.6.49-cll-lve
|_mysql-vuln-cve2012-2122
