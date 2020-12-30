# Zugzwang Project

Zugzwang Project is a content management system for websites (short: `zzproject`).

## Installation

You can install zzproject on a local development server (e. g. your computer). 

You need to install a webserver, a database and PHP. I’d recommend to use a package manager. I am using HomeBrew <https://brew.sh/> on macOS. This is a possible list of packages you should install:

    brew install httpd curl exiftool ffmpeg ghostscript ufraw imagemagick mysql mkcert php

It is recommended to set up the server on a local domain ending `.local`, e. g. for a server at `www.example.org` you need to create a DNS entry `www.example.org.local` in your `/etc/hosts`-file

    127.0.0.1 www.example.org.local # localhost IPv4
    ::1 www.example.org.local # localhost IPv6

It is recommended to set up this development server with an SSL certificate. You can use `mkcert` for that.

    mkcert www.example.org.local
    
The supported webserver is `apache`. This is an example for a webserver configuration file for a virtual host:

	<VirtualHost *:80>
		 DocumentRoot /Users/Gustaf/Sites/example.org/www
		 ServerName www.example.org.local
	   <Directory "/Users/Gustaf/Sites">
		   Require all granted
	   </Directory>
	</VirtualHost>

	<VirtualHost *:443>
		DocumentRoot "/Users/Gustaf/Sites/example.org/www"
		ServerName www.example.org.local
		SSLEngine on
		SSLCertificateFile "/Users/Gustaf/Sites/_system/certs/www.example.org.local.pem"
		SSLCertificateKeyFile "/Users/Gustaf/Sites/_system/certs/www.example.org.local-key.pem"
	   <Directory "/Users/Gustaf/Sites">
		   Require all granted
	   </Directory>
	</VirtualHost>

If you got your local webserver up and running, install the CMS files. You can download them from GitHub at <https://github.com/koenige/zzproject>.

@todo to be continued

## Libraries

@todo

## Modules

There is a separate Module.md readme file.

## Contact

Gustaf Mossakowski <gustaf@koenige.org> or <https://www.koenige.org>
Zugzwang Project: <https://www.zugzwang.org>
