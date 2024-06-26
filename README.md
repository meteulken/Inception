# Inception
42 Ecole inception project
- Dockeri arka planda çalıştırmazsan işi bitince kapanır
- Docker it = input terminal
- Docker inspect = docker config bilgisi verir
- Sanal makine tam bir işletim sistemi barındırır ve fiziksel makineyi sanallaştırırsınız.
- Container ise içinde işletim sistemi bulunmaz uygulamayı sanallaştırırsınız.
- image okunabilir bir şablondur, container ise bu şablonda oluşturulmuş çalışan bir kopyadır.
- RUN komutu ile çalıştırılan komutların çıktıları Docker Image'e yazılır.
- docker ps -a = eski containerleri gösterir
- docker image history komutu, bir Docker imajının katmanlarını ve her katmanın oluşturulma geçmişini gösterir. 

1. **Docker ve Docker Compose Nasıl Çalışır?**
   - Docker, konteynerleştirme teknolojisi kullanarak yazılım uygulamalarını hızlı ve kolay bir şekilde paketleme, dağıtma ve çalıştırma imkanı sunar. Docker, uygulamaları bağımsız ve hafif konteynerlere yerleştirerek, bu konteynerlerin farklı ortamlarda tutarlı bir şekilde çalışmasını sağlar.
   - Docker Compose ise, Docker konteynerlerini tanımlamak ve yönetmek için kullanılan bir araçtır. Docker Compose, YAML dosyaları kullanarak birden fazla Docker konteynerini tek bir dosyada tanımlamanıza olanak tanır. Bu dosya, bir uygulamanın farklı bileşenlerini (örneğin, veritabanı, web sunucusu) ve bunların yapılandırmalarını içerir. Docker Compose, bu konteynerleri başlatma, durdurma ve yönetme işlemlerini kolaylaştırır.

2. **Docker Compose ile Kullanılan Bir Docker Görüntüsü ile Docker Compose Olmadan Kullanılan Bir Docker Görüntüsü Arasındaki Fark**
   - Docker Compose kullanarak bir Docker görüntüsü kullanırken, uygulamanın farklı bileşenlerini tek bir YAML dosyasında tanımlayabilirsiniz. Bu dosya, uygulamanın altyapısını ve bileşenlerinin nasıl çalıştırılacağını açıkça belirtir. Docker Compose, bu bileşenleri başlatma, durdurma ve yönetme işlemlerini otomatikleştirir.
   - Docker Compose olmadan bir Docker görüntüsü kullanırken, her bir bileşeni manuel olarak Docker komutlarıyla başlatmanız gerekir. Bu, daha karmaşık ve hata yapmaya daha yatkın olabilir. Docker Compose kullanmadan, bileşenler arasındaki bağımlılıkları ve yapılandırmaları yönetmek daha zor olabilir.

3. **Sanal Makinelere Kıyasla Docker'ın Avantajları**
   - Docker, sanal makinelerden daha hafif ve daha hızlıdır. Docker konteynerleri, işletim sistemi çekirdeğiyle paylaşılan bir ortamda çalışırken, sanal makineler tam bir işletim sistemi üzerinde çalışır. Bu nedenle, Docker konteynerleri daha az kaynak tüketir ve daha hızlı başlatılır.
   - Docker, taşınabilirlik sağlar. Docker konteynerleri, herhangi bir platformda ve herhangi bir ortamda tutarlı bir şekilde çalışabilir. Bu, uygulamaların bulut ortamlarında, yerel sunucularda veya geliştirme makinelerinde sorunsuz bir şekilde çalışmasını sağlar.
   - Docker, izolasyon sağlar. Docker konteynerleri, uygulamaları birbirinden izole edilmiş ortamlarda çalıştırır. Bu, bir uygulamanın diğer uygulamalardan etkilenmemesini ve güvenlik risklerinin azaltılmasını sağlar.
   - Docker, hızlı dağıtım sağlar. Docker konteynerleri, uygulamaları hızlı bir şekilde paketleme ve dağıtma imkanı sunar. Bu, geliştirme sürecini hızlandırır ve uygulamaların daha hızlı bir şekilde kullanıma sunulmasını sağlar.

## Docker Image Nedir?

Docker image (Docker imajı), bir Docker container'ın çalışması için gerekli olan dosyaları, araçları ve diğer tüm bileşenleri içeren, salt-okunur (read-only) bir pakettir. Bir Docker image, bir veya daha fazla katman (layer) tarafından oluşturulur ve Dockerfile veya diğer imaj oluşturma yöntemleri kullanılarak tanımlanır.

Docker image'ler, uygulamaları, hizmetleri ve bileşenleri taşımak, dağıtmak ve çalıştırmak için kullanılır. Her image, çalıştırılmak üzere bir veya daha fazla Docker container oluşturmak için kullanılabilir. Docker image'ler, Docker Hub gibi uzak depolama alanlarında paylaşılabilir veya yerel olarak saklanabilir.

### Temel Özellikler

- **Salt-Okunur (Read-Only):** Docker image'ler, salt-okunur bir yapıya sahiptir, yani içeriği oluşturulduktan sonra değiştirilemez. Bu, image'lerin güvenilir ve tutarlı olmasını sağlar.

- **Katmanlar (Layers):** Docker image'ler, birbiri üzerine eklenen katmanlar (layers) tarafından oluşturulur. Her bir katman, Dockerfile'daki bir komutun sonucunu temsil eder ve image'in dosya yapısını tanımlar. Bu, image'lerin hafif ve etkili olmasını sağlar.

- **Dagıtım ve Paylaşım:** Docker image'ler, Docker Hub gibi uzak depolama alanlarında paylaşılabilir ve dağıtılabilir. Bu sayede, farklı sistemler arasında uygulamaların ve hizmetlerin taşınması ve paylaşılması kolaylaşır.

- **Versiyonlama ve Yönetim:** Docker image'ler, versiyon kontrolüne tabi tutulabilir ve yönetilebilir. Her bir versiyon, image'in farklı bir durumunu temsil eder ve değişikliklerin takip edilmesini sağlar.

Docker image'ler, Docker container'ların oluşturulması için temel yapı taşlarıdır ve Docker'ın hızlı, etkili ve güvenilir bir şekilde konteyner tabanlı uygulamaların dağıtımını ve yönetimini sağlamasını sağlar.

## Docker Container Nedir?

Docker'da bir container, Docker imajından oluşturulmuş ve çalışan bir işlem ortamını temsil eder. Her bir container, kendi dosya sistemine, ağa ve process'lere sahiptir ve Docker Engine tarafından izole edilmiştir.

Docker container'ları, bir uygulamanın tüm bağımlılıklarını içeren ve bağımsız olarak çalışabilen hafif, taşınabilir birimlerdir. Bir Docker imajı, bir container'ın başlatılması için temel alınan şablondur. Bir imaj, bir işletim sistemi ve bu işletim sisteminde çalışacak uygulamaları içeren bir dosya sistemini tanımlar. Bir container, bu imajı kullanarak çalıştırılabilir ve çalışma zamanı ortamını oluşturur.

Docker container'ları, yazılım geliştirme, dağıtım ve yönetim süreçlerini hızlandırmak için kullanılır. Her container, kendi izole çalışma ortamına sahip olduğu için, uygulamaları farklı ortamlarda (geliştirme, test, üretim) çalıştırmak ve taşımak daha kolaydır. Ayrıca, container'lar hızlı bir şekilde başlatılıp durdurulabilir ve yüksek ölçeklenebilirlik sağlar. Bu nedenle, Docker container'ları modern yazılım geliştirme ve dağıtım süreçlerinde sıkça kullanılır.

 ---

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
WP_URL=mulken.42.fr
WP_TITLE=wordpress

WP_ADMIN_LOGIN=superuser
WP_ADMIN_PASSWORD=superuser
WP_ADMIN_EMAIL=superuser@42.fr

WP_USER_LOGIN=test
WP_USER_PASSWORD=12345
WP_USER_EMAIL=test@42.fr
```

### Wordpress

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
conf/ dizinine gidip 50-server.cnf adında dosya oluşturalım.
```
[server]
[mysqld]
user                    = mysql
pid-file                = /run/mysqld/mysqld.pid
socket                  = /run/mysqld/mysqld.sock
port                    = 3306
basedir                 = /usr
datadir                 = /var/lib/mysql
tmpdir                  = /tmp
lc-messages-dir         = /usr/share/mysql
query_cache_size        = 16M
log_error = /var/log/mysql/error.log
expire_logs_days        = 10
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci
[embedded]
[mariadb]
[mariadb-10.3]
```
Bu dosya, MariaDB’nin temel yapılandırma ayarlarını içeriyor.
tools/ dizinine gidip initial_db.sql adında dosya oluşturalım.
```bash
CREATE DATABASE IF NOT EXISTS wordpress;
CREATE USER IF NOT EXISTS 'test'@'%' IDENTIFIED BY '12345';
GRANT ALL PRIVILEGES ON wordpress.* TO 'test'@'%';
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED BY 'root12345';
```
### Nginx
nginx/ dizinine gidip Dockerfile dosyasını oluşturalım.
```bash
FROM debian:buster

RUN apt-get update && apt-get install -y nginx openssl

EXPOSE 443

COPY ./conf/nginx.conf/ /etc/nginx/sites-enabled/default
COPY ./tools/nginx_start.sh /var/www

RUN chmod +x /var/www/nginx_start.sh

ENTRYPOINT ["var/www/nginx_start.sh"]

CMD ["nginx", "-g", "daemon off;"]
```
conf/ dizinine gidip nginx.conf dosyasını oluşturalım.
```bash
server {
    listen 443 ssl;
    listen [::]:443 ssl;

    server_name test.42.fr;

    ssl_certificate /etc/ssl/certs/nginx.crt;
    ssl_certificate_key /etc/ssl/private/nginx.key;
    ssl_protocols TLSv1.3;

    index index.php;

    root /var/www/html;

    location / {
        try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass wordpress:9000;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param PATH_INFO $fastcgi_path_info;
    }
}
```
tools/ dizinine nginx_start.sh adında dosya oluşturalım.
```bash
#!/bin/bash

if [ ! -f /etc/ssl/certs/nginx.crt ]; then
echo "Nginx: setting up ssl ...";
openssl req -x509 -nodes -days 365 -newkey rsa:4096 -keyout /etc/ssl/private/nginx.key -out /etc/ssl/certs/nginx.crt -subj "/C=TR/ST=KOCAELI/L=GEBZE/O=42Kocaeli/CN=mulken.42.fr";
echo "Nginx: ssl is set up!";
fi

exec "$@"
```
### Docker Compose Yapılandırması
srcs/ dizinine gidip docker-compose.yml adında dosya açalım.

```bash
version: "3.5"

networks:
  app-network:
    name: app-network
    driver: bridge

volumes:
  wp:
    driver: local
    name: wp
    driver_opts:
      type: none
      o: bind
      device: /$HOME/data/wordpress
  db:
    driver: local
    name: db
    driver_opts:
      type: none
      o: bind
      device: /$HOME/data/mariadb

services:
  mariadb:
    container_name: mariadb
    build: ./requirements/mariadb
    env_file:
      - .env
    volumes:
      - db:/var/lib/mysql
    networks:
      - app-network
    restart: unless-stopped

  wordpress:
    container_name: wordpress
    build: ./requirements/wordpress
    env_file:
      - .env
    depends_on:
      - mariadb
    volumes:
      - wp:/var/www/html
    networks:
      - app-network
    restart: unless-stopped

  nginx:
    container_name: nginx
    build: ./requirements/nginx
    ports:
      - "443:443"
    depends_on:
      - wordpress
    volumes:
      - wp:/var/www/html
    networks:
      - app-network
    restart: unless-stopped
```
### Makefile
Projenin ana dizinine(srcs’den önce) gidip bir Makefile dosyası oluşturalım.

```bash
# -f: --file
# -q: --quiet
# -a: --all
# $$: escape $ for shell
all:
	@mkdir -p $(HOME)/data/wordpress
	@mkdir -p $(HOME)/data/mariadb
	@docker-compose -f ./srcs/docker-compose.yml up

down:
	@docker-compose -f ./srcs/docker-compose.yml down

re:
	@docker-compose -f srcs/docker-compose.yml up --build

clean:
	@docker stop $$(docker ps -qa);\
	docker rm $$(docker ps -qa);\
	docker rmi -f $$(docker images -qa);\
	docker volume rm $$(docker volume ls -q);\
	docker network rm $$(docker network ls -q);\
	rm -rf $(HOME)/data/wordpress
	rm -rf $(HOME)/data/mariadb

.PHONY: all re down clean
```
x.42.fr adresine bağlanabilmek için hosts dosyasını düzenlememiz gerekiyor. Bunun için etc/ dizini içerisindeki hosts dosyasını açın.
```bash
127.0.0.1 localhost
127.0.0.1 test.42.fr
127.0.1.1 debian

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
