--- How to Deploy Wordpress with Docker ---

if you deploy on your server create this Desktop folder on your server

>>> cd Desktop
>>> mkdir wpwebsite
>>> cd wpwebsite

create file docker-compose.yml --> 

>>> vi docker-compose.yml

paste this code below into the file docker-compese.yml don't forget save it.

version: "3"
services:
        mysql:
            image: mariadb
            ports:
                - "3260:3260"
            volumes:
                - mysql_data:/var/lib/mysql
            environment:
                MYSQL_ROOT_PASSWORD: example

        wordpress:
          image: wordpress
          ports:
              - "2000:80"
          volumes:
              - mywebsite_data:/var/www/html
              - ./wp-content/themes/:/var/www/html/wp-content/themes
              - ./wp-content/plugins/:/var/www/html/wp-content/plugins
          environment:
              WORDPRESS_DB_PASSWORD: example
          depends_on:
              - mysql
          links:
              - mysql
volumes:
        mysql_data:
        mywebsite_data:

login in your browser >>> http://localhost:2000 or http://yourserverhost:2000

it means your wordpress image on port 2000

login into wordpress CMS >>> http://localhost:2000/wp-login.php



