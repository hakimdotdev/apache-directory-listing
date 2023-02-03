
# Configuring Apache for Directory Listing with .htaccess Authentication

## Prerequisites

-   Apache web server installed and running (*this guide is assuming a ubuntu/debian setup*).

## Configuration of the Server

 1. Open `/etc/apache/sites-enabled/000-default.conf`in a text editor.
 3.  Locate the section for the desired directory where you want to enable directory listing or set one up like this (Assuming the document root and directory for the listing is at `/srv/data`:
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /srv/data
        <Directory /srv/data>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
 4. Change the Document Root within the configuration file, if needed.

 5.  You may need to activate the rewrite module with the following command `sudo a2enmod rewrite`
 
 6. Restart Apache `systemctl restart apache2`

 7. You also may want to add some theme, [Abba](https://github.com/jmlemetayer/abba) has some really fancy options. Otherwise you can provide an own styling `.htaccess` like this:
 

    

 - [ ] TO-DO: Include custom .htaccess

