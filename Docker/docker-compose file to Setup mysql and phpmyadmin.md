
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
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql
    networks:
      - mynetwork

  phpmyadmin-service:
    image: phpmyadmin/phpmyadmin:latest
    container_name: pma_container
    restart: always
    depends_on:
      - mysql-service
    environment:
      PMA_HOST: mysql-service
    ports:
      - "8080:80"
    networks:
      - mynetwork

volumes:
  mysql_data:

networks:
  mynetwork:
    external: true
    
    
    
    
    
    docker network create mynetwork 
run this before apply dockercompsoe
```