# mysql-8.0.30单节点部署

## 详情

```
docker pull mysql:8.0.30
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-mysql8:
    image: mysql:8.0.30
    container_name: mysql8.coms.hello.com
    ports:
      - '3306:3306'
    volumes:
      - ./data:/var/lib/mysql
      - ./log:/var/log/mysql
      - ./conf:/etc/mysql/conf.d
    environment:
      - MYSQL_ROOT_PASSWORD=root
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com

```