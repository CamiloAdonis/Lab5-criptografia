FROM ubuntu:20.10

RUN sed -i 's|archive.ubuntu.com|old-releases.ubuntu.com|g; s|security.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y openssh-client iproute2 nano

CMD ["bash"]
