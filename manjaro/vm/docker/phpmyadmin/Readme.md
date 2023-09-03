# phpmyadmin 部署

## 详情

```
docker pull phpmyadmin:latest
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-phpmyadmin:
    image: phpmyadmin:latest
    container_name: phpmyadmin.coms.hello.com
    ports:
      - '8080:80'
    volumes:
      - ./data:/var/lib/mysql
      - ./log:/var/log/mysql
      - ./conf:/etc/mysql/conf.d
    environment:
      - UPLOAD_LIMIT=500M
      - PMA_HOST=mysql8.coms.hello.com
      - PMA_PORT=3306
      - MYSQL_ROOT_PASSWORD=root
      - PMA_ARBITRARY=1
      - PMA_USER=admin
      - PMA_PASSWORD=123456
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com
```