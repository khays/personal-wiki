---
layout: post
title: Setting up webdav on apache with SSL
tags: apache webdav yum keys https ssl
---

This one was a bit of a doozie, but I found that the information on [this centos site](http://wiki.centos.org/HowTos/Https) to be indispendcible in making it happen.

## 1. Setup SSL

This is what I did to get it to work, you will have to follow a few command to complet this string.

    1041  yum install mod_ssl openssl
    1042  vim /etc/httpd/conf/httpd.conf
    1043  service httpd start
    1044  service httpd restart
    1045  openssl genrsa -out ca.key 1024
    1046  openssl req -new -key ca.key -out ca.csr
    1047  ll
    1048  openssl x509 -req -days 3655 -in ca.csr -signkey ca.key -out ca.crt
    1049  ll
    1050  mkdir ~/certs
    1051  cp ca* ~/certs/.
    1052  mv ca.crt /etc/pki/tls/certs/ca.crt
    1053  mv ca.key /etc/pki/tls/private/ca.key
    1054  mv ca.csr /etc/pki/tls/private/ca.csr
    1056  restorecon -RvF /etc/pki
    1057  vim +/SSLCertificateFile /etc/httpd/conf.d/ssl.conf
    1058  service httpd restart

In line 1057, make sure that you say the location of your SSL Files

    SSLCertificateFile /etc/pki/tls/certs/ca.crt

Restart apache and you should be good to go.

## 2. Setup webDav

This was pretty easy, as it was already partly setup for me. In `/etc/httpd/conf/httpd.conf` add these lines

    NameVirtualHost *:443

    <VirtualHost *:443>
        SSLEngine on
        SSLCertificateFile /etc/pki/tls/certs/ca.crt
        SSLCertificateKeyFile /etc/pki/tls/private/ca.key
        ServerAdmin user@domain.com
        DocumentRoot /var/www/html
        ServerName servername
        ErrorLog logs/error_log
        CustomLog logs/access_log common

        Alias /webdav /var/www/directory
            <Location /webdav>
               DAV On
               AuthType Basic
               AuthName "webdav"
               AuthUserFile /etc/httpd/conf/htpasswd
               Require valid-user
           </Location>
    </VirtualHost>

Restart apache.

## 3. Connect

I did this so that I could connect to my VPS, from anywhere.
