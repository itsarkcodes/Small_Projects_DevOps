## 1 Keep system updated
- ```sudo apt-get update```

## 2 Disable Server Details like Os and apache version
![image](https://github.com/itsarkcodes/assignment/assets/87442305/07358005-5d1c-4aa6-b023-55e015ac35e6)

Disabling server signature and tokens helps minimize information disclosure.
```vi /etc/apache2/apache2.conf```
Add 
```
ServerTokens Prod
ServerSignature Off
```
![image](https://github.com/itsarkcodes/assignment/assets/87442305/500cb797-67bb-4183-aca0-05f5a7b398d6)

After Adding 
![image](https://github.com/itsarkcodes/assignment/assets/87442305/961ddea7-d09d-4779-8ee7-7cdab8136586)

## 2 Limit Request Size
```vi /etc/apache2/apache2.conf```
```
<Directory "/var/www/website.com/wp_content/uploads">
LimitRequestBody 10485760
</Directory>
```

## 3 Firewall configuration
```
sudo ufw allow ssh 
sudo ufw allow http
sudo ufw allow https
sudo ufw enable
sudo ufw status verbose
```
![image](https://github.com/itsarkcodes/assignment/assets/87442305/1b20e6a4-f22d-44e4-b5b1-028a1139dc8f)

## 4 Strong Passwords and Backups
Enforce Strong Password Policies:
- Configure strong passwords for server login and applications.
Set Up Regular Backups:
- Ensure regular backups of server data.

## 5. Log Monitoring
```
tail -f /var/log/apache2/access.log
tail -f /var/log/apache2/error.log
```

## 6. Secure Apache using SSL Certificate 
Securiing Apache with Let's Encrypt SSL Certificate

## 7. Enable HTTP Strict Transport Security (HSTS) for Apache
HTTP Strict Transport Security (HSTS) is a policy mechanism that protects websites from man-in-the-middle attacks & cookie hijacking. 
```
sudo a2enmod headers
```
Now Reload Apache 
Access domain's vritual host config
```
sudo vim /etc/apache2/sites-available/mydomain.conf
```
```
<VirtualHost *:443>
        # .....
        # ....
        Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"
</VirtualHost>
```
Now restart apache
```
systemctl restart apache2
```
The max-age parameter instructs web browsers to only access your site using HTTPS for the next one year (31536000 = 1 year)

## 8. Disable Unnecessary Module
```
sudo a2dismod <module_name>
```
