FROM almalinux:9

RUN dnf install -y \
        curl \
        wget \
        telnet \
        iputils \
        bind-utils \
        net-tools \
        iproute \
        procps-ng \
        traceroute \
        nmap-ncat \
        openssl \
    && dnf clean all

CMD ["sleep", "10000"]