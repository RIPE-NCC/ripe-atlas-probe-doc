# CentOS 8: Instruções de instalação específicas para pacote RPM binário

Caso queira configurar uma nova máquina virtual usando CentOS para hospedar sua sonda:

* Configure uma nova instalação do CentOS 8 (por exemplo, usando [VirtualBox](https://www.virtualbox.org/) ou [Parallels](https://www.parallels.com/)), consulte o [Guia de instalação do CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Ao instalar o CentOS em uma máquina virtual, configure o adaptador de rede virtual no `bridge mode` para permitir que o IPv6 funcione. Frequentemente, o padrão é chamado de `shared`, que fornece apenas NAT IPv4.

O RIPE NCC mantém pacotes RPM binários e está atualmente disponível para CentOS 8 (x86_64). Para adicionar o repositório ao seu sistema e instalar o pacote, siga os passos seguintes:

1. Faça download do RPM que configura o repositório para o RPM da sonda de software:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos8/noarch/ripe-atlas-repo-1-3.el8.noarch.rpm'
    ```

2. Verifique o hash do RPM:

    ```
    sha256sum ripe-atlas-repo-1-3.el8.noarch.rpm
    ```

    O hash deve ser:

    ```
    e1e7800666f6978eb2e78dfabcd8aa0fa0ca45d9e97cc861a5e93300a2e46a00
    ```

3. Instale o RPM:

    ```
    yum install ripe-atlas-repo-1-3.el8.noarch.rpm

    ```

    Responda `'y'` à pergunta se está tudo bem.


4. Agora pode instalar o pacote para a própria sonda de software:

    ```
    yum install atlasswprobe
    ```

5. Responda `'y'` para importar a GPG key com impressão digital `AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Responda `'y'` que está ok para instalar o RPM. Pode também precisar de aceitar uma CentOS signing key.

7. A instalação do software da sonda gera um novo par de chaves SSH que vai ser usado para ligar a sonda à infraestrutura RIPE Atlas. É necessário registar a parte pública da chave para [registrar a sonda](https://atlas.ripe.net/apply/swprobe/).
   Esta encontra-se em `/var/atlas-probe/etc/probe_key.pub`.
