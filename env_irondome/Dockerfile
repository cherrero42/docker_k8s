FROM ubuntu:22.04   

RUN set -x -e && apt-get update && \
    apt-get install openssh-server -y && apt-get install vim sudo python3 pip libmagic1 -y

COPY sshd_config /etc/ssh/sshd_config
COPY ssh.sh /ssh.sh
COPY requirements.txt /tmp/

RUN set -x -e && pip3 install --requirement /tmp/requirements.txt && \
    chmod +x /ssh.sh && \
    echo "root:xxxx" | chpasswd

RUN useradd -m probe && \
    echo "probe:123xxx" | chpasswd && \
    groupadd sshusers && \
    usermod -aG sshusers probe && \
    usermod -aG sudo probe

EXPOSE 4141

RUN adduser --no-create-home --disabled-password --gecos "" user
USER user

CMD ["sh", "/ssh.sh"]
