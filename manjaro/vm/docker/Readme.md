# docker 配置

## 1、代理配置

```bash
# 创建目录
sudo mkdir -p /etc/systemd/system/docker.service.d

# 切换路径
cd /etc/systemd/system/docker.service.d

# 创建配置
vim http-proxy.conf

[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80"
Environment="HTTPS_PROXY=https://proxy.example.com:443"
Environment="NO_PROXY=your-registry.com,10.10.10.10,*.example.com"

# 重启dcokerd
sudo systemctl daemon-reload
sudo systemctl restart docker

# 检查
sudo systemctl show --property=Environment docker
docker info
```