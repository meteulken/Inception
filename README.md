# Inception
42 Ecole inception project

### Kurulum

```bash
apt-get update && apt-get install make docker.io docker-compose
```
#### Dizin Oluşturma
```bash
mkdir -p srcs/requirements/{wordpress,mariadb,nginx}/{tools,conf}
```
srcs dizini içerisine env adında gizli bir dosya oluşturalım.
```bash
touch .env
```
env'nin içine aşağıdaki kodları yazsın
```bash
WP_URL=test.42.fr
WP_TITLE=wordpress

WP_ADMIN_LOGIN=superuser
WP_ADMIN_PASSWORD=superuser
WP_ADMIN_EMAIL=superuser@42.fr

WP_USER_LOGIN=test
WP_USER_PASSWORD=12345
WP_USER_EMAIL=test@42.fr
```
wordpress/ dizini içerisine Dockerfile adında bir dosya oluşturalım.
```bash
FROM debian:buster

RUN apt-get update && apt-get -y install php7.3 php-mysqli php-fpm wget sendmail

EXPOSE 9000

COPY ./conf/www.conf /etc/php/7.3/fpm/pool.d
COPY ./tools /var/www/

RUN chmod +x /var/www/wordpress_start.sh

ENTRYPOINT [ "/var/www/wordpress_start.sh" ]

CMD ["/usr/sbin/php-fpm7.3", "--nodaemonize"]
```
/wordpress/conf/ dizinine gidip www.conf adında dosya oluşturalım ve aşağıdaki komutları yazalım.
```bash
[www]
user = www-data
group = www-data
listen = wordpress:9000
pm = dynamic
pm.start_servers = 6
pm.max_children = 25
pm.min_spare_servers = 2
pm.max_spare_servers = 10
```
Şimdi tools/ dizinine gidip wordpress_start.sh adında dosya oluşturup aşağıdaki bash kodunu yazalım.
```bash
#!/bin/bash

	sed -i "s/listen = \/run\/php\/php7.3-fpm.sock/listen = 9000/" "/etc/php/7.3/fpm/pool.d/www.conf";
	chown -R www-data:www-data /var/www/*;
	chown -R 755 /var/www/*;
	mkdir -p /run/php/;
	touch /run/php/php7.3-fpm.pid;

if [ ! -f /var/www/html/wp-config.php ]; then
	echo "Wordpress: setting up..."
	mkdir -p /var/www/html
	wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar;
	chmod +x wp-cli.phar; 
	mv wp-cli.phar /usr/local/bin/wp;
	cd /var/www/html;
	wp core download --allow-root;
	mv /var/www/wp-config.php /var/www/html/
	echo "Wordpress: creating users..."
	wp core install --allow-root --url=${WP_URL} --title=${WP_TITLE} --admin_user=${WP_ADMIN_LOGIN} --admin_password=${WP_ADMIN_PASSWORD} --admin_email=${WP_ADMIN_EMAIL}
	wp user create --allow-root ${WP_USER_LOGIN} ${WP_USER_EMAIL} --user_pass=${WP_USER_PASSWORD};
	echo "Wordpress: set up!"
fi

exec "$@"
```
### MariaDB
mariadb/ dizinine girip Dockerfile dosyasını oluşturalım.
```bash
FROM debian:buster

RUN apt-get update && apt-get install -y mariadb-server

EXPOSE 3306

COPY ./conf/50-server.cnf /etc/mysql/mariadb.conf.d/
COPY ./tools /var/www/

RUN service mysql start && mysql < /var/www/initial_db.sql && rm -f /var/www/initial_db.sql;

CMD ["mysqld"]
```
