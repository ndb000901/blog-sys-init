## portainer配置

## 详情

```
docker pull portainer/portainer-ce:latest
```

## docker-compose.yml

```yml
version: '3.9'
services:
  coms-portainer:
    image: portainer/portainer-ce:latest
    container_name: portainer.coms.hello.com
    restart: always
    ports:
      - '9000:9000'
      - '8000:8000'
    volumes:
      - ./data:/data
      - /var/run/docker.sock:/var/run/docker.sock
    networks:
      - coms.hello.com
networks:
  coms.hello.com:
    driver: bridge
    external:
      name: coms.hello.com

```