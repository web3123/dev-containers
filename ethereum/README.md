docker build --tag web3123/ethereum-dev:latest .

- 使用支持 MS vscode 开发的基础镜像构建 web3 镜像
docker build --tag ghcr.io/kimiazhu/dev-base:alpine-3.20-250114 -f Dockerfile .

- 推送/下载镜像使用
docker push ghcr.io/kimiazhu/dev-base:alpine-3.20-250114

- 执行:
podman run -d -p8888:22 ghcr.io/kimiazhu/dev-base:alpine-3.20-250114

- 加入ssh公钥：
ssh-copy-id -i id_rsa.pub -p8888 root@localhost

- VS-code配置：
windows为例，注意如果之前已经在known_hosts中存在别的容器用过这个 IP:Port 会出错，需要先删除。
```
Host localhost
  HostName localhost
  Port 8888
  User root
  ForwardAgent yes
  # IdentityFile C:/Users/kc/.ssh/id_rsa
```

