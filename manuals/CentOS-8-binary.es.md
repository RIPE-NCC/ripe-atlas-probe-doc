# CentOS 8: Instrucciones de instalación específicas para RPM binario

En caso de que desee configurar una nueva máquina virtual usando CentOS 8 para alojar su probe:

* Configurar una nueva instalación de CentOS 8 (por ejemplo, usando [VirtualBox](https://www.virtualbox.org/) o [Parallels](https://www.parallels.com/)), consulte la [Guía de instalación de CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Al instalar CentOS en una máquina virtual, configure el adaptador de red virtual en ‘bridge mode' para permitir que funcione IPv6. A menudo, el valor predeterminado se establece como 'shared', que solo proporciona NAT IPv4.

RIPE NCC mantiene paquetes RPM binarios y actualmente está disponible para CentOS 8 (x86_64). Para agregar el repositorio a su sistema e instalar el paquete,
sigue estos pasos:

1. Descargue el RPM que configura el repositorio para el RPM del probe de software:

   ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos8/noarch/ripe-atlas-repo-1-2.el8.noarch.rpm'
   ```

2. Verifique el hash del RPM:

    ```
    sha256sum ripe-atlas-repo-1-2.el8.noarch.rpm
    ```

    El hash debe ser:

    ```
    cfb433f54395f5d2ac0d29e806f19f1b854d33f02c256087586e50e49003929c
    ```

3. Instale el RPM:

   ```
    yum install ripe-atlas-repo-1-2.el8.noarch.rpm
   ```

    Responda `'y'` a la pregunta de si eso está bien.


4. Ahora puede instalar el paquete para la propia probe de software:

   ```
    yum install atlasswprobe
   ```

5. Responda `'y'` para importar la GPG key con huella digital` AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Responda `'y'` que está bien instalar el RPM. También es posible que deba aceptar un CentOS signing key.

7. La instalación del software de la probe genera un nuevo par de claves SSH (SSH key pair) que se utilizará para
   conectar el probe a la infraestructura de RIPE Atlas. Debe registrar
   la clave pública (public key) para [registrar el probe](/apply/swprobe/).
   Esta se puede encontrar en `/var/atlas-probe/etc/probe_key.pub`.
