---
created: 2022-07-17T12:46:48.175Z
modified: 2022-07-17T12:48:40.308Z
---

```docker-compose.yml
version: '3'
services:
  db:
    image: mariadb
    container_name: nextcloud-mariadb
    networks:
      - nextcloud_network
    volumes:
      - db:/var/lib/mysql
      - /etc/localtime:/etc/localtime:ro
    environment:
      - MYSQL_ROOT_PASSWORD=1239876543456788765434
      - MYSQL_PASSWORD=098765432987654345678
      - MYSQL_DATABASE=nexdb
      - MYSQL_USER=nxd
    restart: unless-stopped
  app:
    image: linuxserver/nextcloud:latest
    container_name: nextcloud-app
    networks:
      - nextcloud_network
    depends_on:
      - db
    volumes:
      - nextcloud:/var/www/html
      - ./app/config:/var/www/html/config
      - ./app/custom_apps:/var/www/html/custom_apps
      - ./app/data:/var/www/html/data
      - ./app/themes:/var/www/html/themes
      - /etc/localtime:/etc/localtime:ro
    restart: unless-stopped
volumes:
  nextcloud:
  db:
networks:
  nextcloud_network:
```