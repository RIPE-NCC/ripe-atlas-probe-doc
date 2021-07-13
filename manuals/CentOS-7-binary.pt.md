# CentOS 7: Instruções de instalação específicas de RPM binárias

Caso queira configurar uma nova máquina virtual usando CentOS 7 para hospedar sua probe:

* Configure uma nova instalação do CentOS 7 (por exemplo, usando [VirtualBox](https://www.virtualbox.org/) ou [Parallels](https://www.parallels.com/)), consulte o [Guia de instalação do CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Ao instalar o CentOS numa máquina virtual, configure o adaptador de rede virtual em `bridge mode` para permitir que o IPv6 funcione. Frequentemente, a configuração original é chamada de `shared`, que fornece apenas NAT IPv4.

O RIPE NCC mantem pacotes RPM binários e está atualmente disponível para CentOS 7 (x86_64). Para adicionar o repositório ao seu sistema e instalar o pacote, siga estes passos:

1. Faça download do RPM que configura o repositório para o RPM do probe de software:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-2.el7.noarch.rpm'
    ```

2. Verifique o hash do RPM:

    ```
    sha256sum ripe-atlas-repo-1-2.el7.noarch.rpm
    ```

    O hash deve ser:

    ```
    c02b6fb7004e86765257c93912403636f67ba59250f8f0904288f60eaad816c3
    ```

3. Instale o RPM:

    ```
    yum install maduro-atlas-repo-1-2.el7.noarch.rpm
    ```

    Responda `'y'` à pergunta.


4. Agora pode instalar o pacote para a probe de software:

    ```
    yum install atlasswprobe
    ```

5. Responda `'y'` para importar o GPG key com impressão digital` afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5`

6. Responda `'y'` que está de acordo em instalar o RPM. Também pode ser necessário aceitar uma CentOS signing key.

7. A instalação do software da probe gera um novo SSH key que vai ser utilizado na ligação da probe à infraestrutura RIPE Atlas. É necessário registar a chave pública para poder [registar a probe](https://atlas.ripe.net/apply/swprobe/).
   Esta encontra-se em `/var/atlas-probe/etc/probe_key.pub`.
