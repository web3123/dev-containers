FROM qmkfm/qmk_cli:latest

LABEL org.opencontainers.image.description "An qmk dev container"

# environment variables
ENV LANG C.UTF-8
ENV TERM=xterm

WORKDIR /root

RUN apt-get update

RUN apt-get update && apt-get install -y openssh-server tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && mkdir /var/run/sshd \
    && echo 'root:abc@123456' | chpasswd \
    #&& sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
    && sed -i 's/#PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config \
    && sed -i 's/#AllowAgentForwarding yes/AllowAgentForwarding yes/g' /etc/ssh/sshd_config \
    && sed -i 's/AllowTcpForwarding no/AllowTcpForwarding yes/g' /etc/ssh/sshd_config
#    && sed -i 's/UsePAM yes/UsePAM no/' /etc/ssh/sshd_config

RUN ssh-keygen -A
#RUN ssh-keygen -t dsa -P "" -f /etc/ssh/ssh_host_dsa_key \
  #  && ssh-keygen -t rsa -P "" -f /etc/ssh/ssh_host_rsa_key \ 
 #   && ssh-keygen -t ecdsa -P "" -f /etc/ssh/ssh_host_ecdsa_key \
  #  && ssh-keygen -t ed25519 -P "" -f /etc/ssh/ssh_host_ed25519_key

#RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
#    && sed -i "s/#PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config \
#    && sed -i "s/#AllowAgentForwarding yes/AllowAgentForwarding yes/g" /etc/ssh/sshd_config \
#    && sed -i "s/AllowTcpForwarding no/AllowTcpForwarding yes/g" /etc/ssh/sshd_config \
#    && ssh-keygen -t dsa -P "" -f /etc/ssh/ssh_host_dsa_key \
#    && ssh-keygen -t rsa -P "" -f /etc/ssh/ssh_host_rsa_key \ 
#    && ssh-keygen -t ecdsa -P "" -f /etc/ssh/ssh_host_ecdsa_key \
#    && ssh-keygen -t ed25519 -P "" -f /etc/ssh/ssh_host_ed25519_key \
#    && echo "root:abc@123456" | chpasswd

#RUN rm -rf /var/cache/apk/*

#RUN chsh -s /bin/zsh

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
