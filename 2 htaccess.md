##the Advantage in htaccess
1. we can define to wich directory we can accessed
1. we make redirect
1. we can make one ip to access web
1. we can make except one ip every one to access
1. ...

### First
for use redirect you  must write
```
RewriteEngine On
```
this is help us to do a reidrect

###second
```
RewriteEngine On
RewriteBase /
```
this help us to chose redirect to which path and if we write / this is guide us to our base website

###Third
```
RewriteEngine On
RewriteCond  %{REQUEST_FILENAME} !-d
RewriteCond  %{REQUEST_FILENAME} !-f
```
line two it means if directory with request name don't exist. example:
```
https://www.w3schools.com/directory
```
line three it means if flie with request name don't exist. example:
```
https://www.w3schools.com/file.php
```

###Fourth
```
RewriteEngine On
RewriteCond  %{REQUEST_FILENAME} !-d
RewriteCond  %{REQUEST_FILENAME} !-f
RewriteRule ^(.+)$ mvc/404.php [QSA,L]
```
it means redirect to 404.php

##learn more

```
RewriteEngine On
RewriteCond  %{REQUEST_FILENAME} !/public/* [NC]
RewriteCond  %{REQUEST_FILENAME} /(application|view|system)/.+ [NC]
RewriteRule ^ - [R=403,L]
```
`[nc]`:
it means case insensitive

`L` :
this means this code is last code to run

`RewriteCond  %{REQUEST_FILENAME} !/public/* [NC]` :
it means free to access public

`RewriteCond  %{REQUEST_FILENAME} /(application|view|system)/.+ [NC]` : 
it means you can't access to application , view , system

`RewriteRule ^ - [R=403,L]` :
it means it return a 403 error

=========================

```
DirectoryIndex file.php //
```
when you write address web the first load file is index.php with this code you can change the file you want to load first !

=========================

```
Options All -indexes
Options indexes
```

`Options All -indexes` :
when you uploaded your web in file zip to your host sometime your forgot to delet your source zip file and someone can access to your zip file and your web source be stolen this code your zip source can't be identified

`Options indexes` :
sometime when you didn't manage web file Properly your user can see all of your directoryand file for prevent this happen we add this code

=========================

```
deny from 1.1.2.3
allow from all
```
with this you can prevent this ip to see your web and access everyone to see your web or

```
allow from 1.1.2.3
deny from all
```

=========================

```html
<files wp-config.php>
oreder allow,deny
deny from all
</files>
```
with this code you say everyone never can access to wp-config.php

=========================

```
AddType application/octet-stream .pdf
AddType application/octet-stream .zip
AddType application/octet-stream .mov
```
with this your user when click pdf file your pdf file don't open and it just can be downloaded incloud your zip , mov

=========================

```
php_value upload_max_filesize 20M
```
with this you can make a condition to your max upload file size

=========================

```
php_value memory_limit 128M
```

=========================

##http and https 
```
RewriteEngine On
RewriteCond  %{HTTPS} off
RewriteRule ^(.+)$ https://%{HTTP_HOST}%{REQUEST_URL} [L,R=301]
```
with this code whent user write http://your web it redirect to https://your web

=========================

##www
```
RewriteEngine On
RewriteCond  %{HTTP_HOST} !^www.example.com [NC]
RewriteRule ^(.+)$ https://www.example.com/$1 [L,R=301]
```
with this code whent user write http://your web it redirect to https://your web

=========================

```
ErrorDocument 401 /error_page/401.html
ErrorDocument 404 /error_page/404.html
ErrorDocument 500 /error_page/500.html
```
when you your web had this error your user ridirect to file.html