FROM mcr.microsoft.com/devcontainers/base:0-alpine-3.20

LABEL org.opencontainers.image.description "An alpine based images with c/c++ support"

# environment variables
ENV LANG C.UTF-8
ENV TERM=xterm

WORKDIR /root

# alpine packages
RUN apk update && \
    apk upgrade

RUN apk --no-cache --virtual build-dependencies add \
    g++ \
    gcc \
    git \
    libc-dev \
    libffi-dev \
    make \
    openssl-dev \
    zlib-dev \
    openssh \
    tzdata

RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && sed -i "s/#PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config \
    && sed -i "s/#AllowAgentForwarding yes/AllowAgentForwarding yes/g" /etc/ssh/sshd_config \
    && sed -i "s/AllowTcpForwarding no/AllowTcpForwarding yes/g" /etc/ssh/sshd_config \
    && ssh-keygen -t dsa -P "" -f /etc/ssh/ssh_host_dsa_key \
    && ssh-keygen -t rsa -P "" -f /etc/ssh/ssh_host_rsa_key \ 
    && ssh-keygen -t ecdsa -P "" -f /etc/ssh/ssh_host_ecdsa_key \
    && ssh-keygen -t ed25519 -P "" -f /etc/ssh/ssh_host_ed25519_key \
    && echo "root:abc@123456" | chpasswd

RUN rm -rf /var/cache/apk/*

RUN chsh -s /bin/zsh

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
