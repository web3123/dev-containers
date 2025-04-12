QMK/vial keyboard firmware用的开发镜像；

`podman build --tag ghcr.io/kimiazhu/dev-qmk:250412 -f Dockerfile .`

push:
`pm push ghcr.io/kimiazhu/dev-qmk:250412`

first time running:
`pm run -d --user root --cap-add=NET_RAW -v ~/Development:/root/Development -p8890:22  ghcr.io/kimiazhu/dev-qmk:250412`
