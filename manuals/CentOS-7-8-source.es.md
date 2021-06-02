# CentOS 7 y 8 - Instalación de Código Fuente

La versión de CentOS es compatible con x86_64 (amd64). Tenga en cuenta que los scripts de instalación e inicio asumen el uso de `systemd`.

1. Para crear e instalar el paquete de software, siga las
 Instrucciones específicas para CentOS incluidas en el archivo
 [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. La instalación del software del probe genera un nuevo par de claves SSH (SSH key pair) que se utilizará para conectar el probe a la infraestructura de RIPE Atlas. Debe registrar la clave pública (public key) para [registrar el probe](https://atlas.ripe.net/apply/swprobe/).
Esta se puede encontrar en `/var/atlas-probe/etc/probe_key.pub`.
