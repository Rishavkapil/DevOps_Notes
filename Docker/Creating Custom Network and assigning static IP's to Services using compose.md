

```sh
version: '3.8'

  

services:

mysql-service:

image: mysql:latest

container_name: mysql_container

restart: always

environment:

MYSQL_ROOT_PASSWORD: admin@123

MYSQL_DATABASE: mydb

# Remove MYSQL_USER and MYSQL_PASSWORD for root login only

ports:

- "3306:3406"

volumes:

- mysql_data:/var/lib/mysql

- $PWD/my.cnf:/etc/my.cnf

networks:

my-custom-network:

ipv4_address: 192.168.0.9

  
  
  
  

phpmyadmin-service:

image: phpmyadmin/phpmyadmin:latest

container_name: pma_container

restart: always

depends_on:

- mysql-service

environment:

PMA_HOST: mysql-service

PMA_PORT: 3406

#PMA_USER: root # Add this if you want to login as root by default in phpMyAdmin

#PMA_PASSWORD: admin@123

ports:

- "8080:80"

networks:

my-custom-network:

ipv4_address: 192.168.0.10

  

volumes:

mysql_data:

  

networks:

my-custom-network:

driver: bridge

ipam:

config:

- subnet: 192.168.0.0/16

gateway: 192.168.0.1
```