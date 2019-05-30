FROM debian:stable-slim
WORKDIR /home/project

ADD "https://github.com/cdr/code-server/releases/download/1.1119-vsc1.33.1/code-server1.1119-vsc1.33.1-linux-x64.tar.gz" ./archive.tar.gz
RUN tar -xvzf archive.tar.gz --strip-components=1 --wildcards "*/code-server" && mv "code-server" /usr/local/bin && rm archive.tar.gz && apt-get update && apt-get install -y openssl net-tools python3 python3-pip

RUN groupadd user
RUN useradd -m -g user -p user -s /bin/bash user

EXPOSE 8443
USER user
ENTRYPOINT ["/usr/local/bin/code-server", "--no-auth", "--allow-http"]
