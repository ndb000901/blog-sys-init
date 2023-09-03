# 1、elasticsearch-8.5.0 单节点部署

## 详情

```
docker pull elasticsearch:8.5.0
```

## docker-compose.yml

```
version: '3.9'
services:
  coms-es8:
    image: elasticsearch:8.5.0
    container_name: es8.coms.hello.com
    ports:
      - '9201:9200'
      - '9301:9300'
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
      - xpack.security.http.ssl.enabled=false
    networks:
      - coms.hello.com
    volumes:
      - ./config/jvm.options:/usr/share/elasticsearch/config/jvm.options:rw
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com
```

# 2、elasticsearch-7.17.6 单节点部署

## 详情

```
docker pull elasticsearch:7.17.6
```

## docker-compose.yml

```
version: '3.9'
services:
  coms-es7:
    image: elasticsearch:7.17.6
    container_name: es7.coms.hello.com
    ports:
      - '9200:9200'
      - '9300:9300'
    environment:
      - discovery.type=single-node
    networks:
      - coms.hello.com
    volumes:
      - ./config/jvm.options:/usr/share/elasticsearch/config/jvm.options:rw
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com
```

# 3、elasticsearch-7.16.2 单节点部署

## 详情

```
docker pull elasticsearch:7.16.2
```

## docker-compose.yml

```
version: '3.9'
services:
  coms-es7-16-2:
    image: elasticsearch:7.16.2
    container_name: es7-16-2.coms.hello.com
    ports:
      - '9202:9200'
      - '9302:9300'
    environment:
      - discovery.type=single-node
    networks:
      - coms.hello.com
    volumes:
      - ./config/jvm.options:/usr/share/elasticsearch/config/jvm.options:rw
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com

```
