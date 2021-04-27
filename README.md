# SQLi
# SQL Injection tutorial step by step 
First of all, to download DVWA you need to have Kali Linux operating system.<br/>To download linux on your desktop, you need to have eather a Vertual Box or Parallels if you have the new M1 chip Macbook like me. 
* Download Vertual Box <br/>
https://www.virtualbox.org/wiki/Downloads

* Download Parallels.<br/> 
https://www.parallels.com/products/desktop/trial/?gclid=Cj0KCQjwyZmEBhCpARIsALIzmnKRiVtGVxbcPy2oUcUQ58Ts3SmxnEfYqW1H-fKMv9-GKH9QgTC_hXwaAk9pEALw_wcB

After downloading vertual box or parallels, you can download Kali Linux operating system. 
* Download Kali Linux<br/>  https://www.kali.org/downloads/<br/>

# downloading DVWA
After downloading Kali Linux, now you can download DVWA on Kali Linux. 
* Download DVWA<br/> https://dvwa.co.uk, <br/> https://github.com/digininja/DVWA.git

Now you need to go to your terminal to download it in your operating system: <br/>
* You have to switch your privileges to root. 
* Sudo su, then enter your password <br/>
<br/>
Folow these steps in your terminal: <br/>
root@kali:~# cd /var/www/html/ <br/>
root@kali:~/var/www/html/# git clone https://github.com/digininja/DVWA.git <br/>
root@kali:~/var/www/html/# chmod -R 777 DVWA/ <br/>
root@kali:~/var/www/html/# cd DVWA/config/<br/>
root@kali:~/var/www/html/config# cp config.inc.php.dist config.inc.php<br/>
root@kali:~/var/www/html/config# nano config.inc.php<br/>
* Now you need to change the user and password to any username and password you want lests assume it is user, pass. save the file by contorl+O and the exit control+X<br/>
root@kali:~/var/www/html/config# cd~<br/>
root@kali:~# service mysql start <br/>
root@kali:~# mysql -u root -p <br/>
click enter when it askes you for a password. <br/>
MariaDB [ (none) ]> create user 'user'@'127.0.0.1' identified by 'pass'; <br/>
MariaDB [ (none) ]> grant all privileges on dvwa.* to 'user'@'127.0.0.1' identified by 'pass'; <br/>
MariaDB [ (none) ]> exit <br/>
root@kali:~# service apache2 start <br/>
root@kali:~# cd /etc/php/7.3/apache2/ <br/>
root@kali:~/etc/php/7.3/apache2# gedit php.ini <br/>
* The changes you to bame is allow_url_fopen = on & allow_url_include = on you have to set both of them to on. <br/>
root@kali:~/etc/php/7.3/apache2# service apache2 start <br/>

* Now go to your web aplication and write 127.0.0.1/DVWA/ in your url. <br/>
scroll down and press Creat / Reset Database button <br/> 
you will be redirected to the login page, the deful username and password is : <br/>
* Username: admin 
* Password: Password 
<br/> 
once you get the page open, you will find alot of Vulnerablilites and one of them is SQL injection. <br/> 
# Download Burp Suite <br/> 
https://portswigger.net/burp/communitydownload <br/> 
Go to your teminal 
root@kali:~# cd Downloads/ <br/> 
root@kali:~/Downloads# chmod u*x burbsuite_comunity_linux_v2020_7.sh <br/> 

root@kali:~# ./ burbsuite_comunity_linux_v2020_7.sh <br/> 

Now you will have burb suite up and running <br/> 

You have to read and study for SQL injection, and I really recommend portswigger: <br/> 
https://portswigger.net/web-security/sql-injection

Thank you 
