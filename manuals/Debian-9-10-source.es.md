# Debian 9 y 10 - Instalación de Código Fuente
El sistema Debian Build incluye soporte para x86_64 (amd64), arm64 y armhf. Tenga en cuenta que los scripts de instalación e inicio asumen el uso de `systemd`.

1. Para crear e instalar el paquete de software, siga las instrucciones específicas para Debian incluidas en el archivo
    [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. La instalación del software del probe genera un nuevo par de claves SSH (SSH key pair) que se utilizará para conectar el probe a la infraestructura de RIPE Atlas. Debe registrar la clave pública (public key) para [registrar el probe](/apply/swprobe/).
Esta se puede encontrar en `/var/atlas-probe/etc/probe_key.pub`.
