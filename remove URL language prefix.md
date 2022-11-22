Add the follwoing to the `.htaccess` file of the website from which you remove the URL prefixes.

```
RewriteCond %{HTTP_HOST} ^benaharoni\.com$ [OR]
RewriteCond %{HTTP_HOST} ^www\.benaharoni\.com$
RewriteRule ^he\/?(.*)$ "https\:\/\/benaharoni\.com\/$1" [R=301,L]
```
