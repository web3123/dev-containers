docker build --tag web3123/ethereum-dev:latest .

- 使用支持 MS vscode 开发的基础镜像构建 web3 镜像
docker build --tag kimiazhu/dev-base:alpine-3.20 -f Dockerfile.dev .

- 推送/下载镜像使用
docker push ghcr.io/kimiazhu/dev-base:alpine-3.21
