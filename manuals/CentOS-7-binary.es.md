# CentOS 7: Instrucciones de instalación específicas para RPM binario

En caso de que desee configurar una nueva máquina virtual usando CentOS 7 para alojar su probe:

* Configure una nueva instalación de CentOS 7 (por ejemplo, usando [VirtualBox](https://www.virtualbox.org/) o [Parallels](https://www.parallels.com/)), consulte la [Guía de instalación de CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Al instalar CentOS en una máquina virtual, configure el adaptador de red virtual en ‘bridge mode' para permitir que funcione IPv6. A menudo, el valor predeterminado se establece como “shared", que solo proporciona NAT IPv4.

RIPE NCC mantiene paquetes RPM binarios y actualmente está disponible para CentOS 7 (x86_64). Para agregar el repositorio a su sistema e instalar el paquete, siga estos pasos:

1. Descargue el RPM que configura el repositorio para el RPM del probe de software:

 ```
 curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-3.el7.noarch.rpm'
 ```

2. Verifique el hash del RPM:

 ```
 sha256sum ripe-atlas-repo-1-3.el7.noarch.rpm
 ```

 El hash debe ser:

 ```
 3cbaa92f4a1dc4c74a865a6c14c3cda0badb649ee18d561740a2ba229b3e1e63
 ```

3. Instale el RPM:

 ```
 yum install ripe-atlas-repo-1-3.el7.noarch.rpm
 ```

 Responda `'y'` a la pregunta de si eso está bien.


4. Ahora puede instalar el paquete para el propio probe de software:

 ```
 yum install atlasswprobe
 ```

5. Responda `'y'` para importar la llave GPG con la huella digital `afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5`

6. Responda `'y'` que está bien para instalar el RPM. Es posible que también deba aceptar un CentOS signing key.

7. La instalación del software del probe genera un nuevo par de claves SSH (SSH key pair) que se utilizará para
 conectar el probe a la infraestructura de RIPE Atlas. Debe registrar la clave pública (public key) para [registrar el probe](https://atlas.ripe.net/apply/swprobe/).
 Esta se puede encontrar en `/var/atlas-probe/etc/probe_key.pub`.
