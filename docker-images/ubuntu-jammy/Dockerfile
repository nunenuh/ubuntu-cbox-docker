FROM ubuntu:jammy

RUN apt-get update && \
    apt-get install build-essential libssl-dev wget nano curl file git ruby-full locales --no-install-recommends -y

RUN apt-get update && \
    apt-get install snapd nmap net-tools -y

RUN apt-get update && \
    apt-get install golang-go -y

RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN useradd -m -s /bin/bash cbox && \
    echo 'cbox ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

USER cbox
RUN sudo snap install cmake --classic

RUN wget https://github.com/nats-io/natscli/releases/download/v0.0.34/nats-0.0.34-amd64.deb -O  /home/cbox/nats-0.0.34-amd64.deb

USER root
RUN chmod 777 /home/cbox/nats-0.0.34-amd64.deb

USER cbox
RUN dpkg -i /home/cbox/nats-0.0.34-amd64.deb


# USER cbox
# RUN wget https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh -O /home/cbox/install.sh

# USER root
# RUN chmod 777 /home/cbox/install.sh

# USER cbox
# RUN /bin/bash /home/cbox/install.sh

# USER root
# ENV PATH="/home/cbox/.linuxbrew/bin:${PATH}"