# 1、kibana-8.5.0 单节点部署

## 详情

```
docker pull kibana:8.5.0
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-kibana8:
    image: kibana:8.5.0
    container_name: kibana8.coms.hello.com
    ports:
      - '5602:5601'
    environment:
      - ELASTICSEARCH_HOSTS=http://192.168.43.43:9201
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com
```


# 2、kibana-7.17.6 单节点部署

## 详情

```
docker pull kibana:7.17.6
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-kibana7:
    image: kibana:7.17.6
    container_name: kibana7.coms.hello.com
    ports:
      - '5601:5601'
    environment:
      - ELASTICSEARCH_HOSTS=http://192.168.43.43:9200
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com

```


# 3、kibana-7.16.2 单节点部署

## 详情

```
docker pull kibana:7.16.2
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-kibana7-16-2:
    image: kibana:7.16.2
    container_name: kibana7-16-2.coms.hello.com
    ports:
      - '5603:5601'
    environment:
      - ELASTICSEARCH_HOSTS=http://192.168.43.43:9202
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com
```
