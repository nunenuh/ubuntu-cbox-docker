FROM ubuntu:bionic

RUN apt-get update && \
    apt-get install build-essential wget nano curl file git ruby-full locales --no-install-recommends -y && \
    rm -rf /var/lib/apt/lists/*

RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN useradd -m -s /bin/bash linuxbrew && \
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

USER linuxbrew
RUN wget https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh -O /home/linuxbrew/install.sh

USER root
RUN chmod 777 /home/linuxbrew/install.sh

USER linuxbrew
RUN /bin/bash /home/linuxbrew/install.sh

USER root
ENV PATH="/home/linuxbrew/.linuxbrew/bin:${PATH}"
