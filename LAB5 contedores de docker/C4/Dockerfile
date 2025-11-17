FROM ubuntu:22.10

# Fix repos archivados de Ubuntu
RUN sed -i 's|archive.ubuntu.com|old-releases.ubuntu.com|g; s|security.ubuntu.com|old-releases.ubuntu.com|g' /etc/apt/sources.list

# Instalar SSH cliente y servidor
RUN apt-get update && apt-get install -y openssh-client openssh-server iproute2 nano sudo

# Crear carpeta necesaria para sshd (sin error si existe)
RUN mkdir -p /run/sshd

# Crear usuario "prueba" con contraseña "prueba"
RUN useradd -m prueba && echo "prueba:prueba" | chpasswd

# Habilitar autenticación por contraseña
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# ⚠️ AGREGAR ESTA LÍNEA - Generar claves SSH del servidor ⚠️
RUN ssh-keygen -A

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]