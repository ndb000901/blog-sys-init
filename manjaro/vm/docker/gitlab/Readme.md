# Gitlab 安装

## 文档

```shell
https://docs.gitlab.com/ee/install/docker/installation.html
```

## 安装

### 1、创建目录

```shell
mkdir -p config logs data
```

### 2、docker-compose.yml

```yml
version: '3.6'
services:
  gitlab:
    image: gitlab/gitlab-ee:17.1.7-ee.0
    container_name: gitlab
    restart: always
    hostname: 'gitlab.hello.work'
    networks:
      - base.svc.hello.com
    environment:
      GITLAB_OMNIBUS_CONFIG: |
        # Add any other gitlab.rb configuration here, each on its own line
        external_url 'https://gitlab.hello.work'
    ports:
      - '80:80'
      - '443:443'
      - '2222:22'
    volumes:
      - './config:/etc/gitlab'
      - './logs:/var/log/gitlab'
      - './data:/var/opt/gitlab'
      - './backup:/data/backup'
    shm_size: '256m'
networks:
  base.svc.hello.com:
    driver: bridge
    external:
      name: base.svc.hello.com
```

### 3、降低内存

[config/gitlab.rb](gitlab.rb)


## 备份

```shell
# https://docs.gitlab.com/ee/install/docker/backup_restore.html
docker exec -t <container name> gitlab-backup create

```

### 4、配置邮件

```shell
###! Docs: https://docs.gitlab.com/omnibus/settings/smtp.html
###! **Use smtp instead of sendmail/postfix.**
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "hello.work"
gitlab_rails['smtp_port'] = 11465
gitlab_rails['smtp_user_name'] = "gitlab.admin@hello.work"
gitlab_rails['smtp_password'] = "xxxxxxxxxxxx"
gitlab_rails['smtp_domain'] = "hello.work"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = false
gitlab_rails['smtp_tls'] = true
gitlab_rails['smtp_pool'] = false
gitlab_rails['smtp_openssl_verify_mode'] = 'none'
gitlab_rails['smtp_ca_path'] = "/etc/gitlab/ssl" # iredmail 配置 data/ssl
# gitlab_rails['smtp_ca_file'] = "/etc/ssl/certs/ca-certificates.crt"
```