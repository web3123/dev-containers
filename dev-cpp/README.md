c/c++ 用的开发镜像；

`podman build --tag ghcr.io/kimiazhu/dev-base-cpp:alpine-3.20-250412 -f Dockerfile .`

push:
`pm push ghcr.io/kimiazhu/dev-base-cpp:alpine-3.20-250412`

first time running:
`podman run -d --user root --cap-add=NET_RAW -v ~/Development:/root/Development -p8889:22 ghcr.io/kimiazhu/dev-base-cpp:alpine-3.20-250412`
