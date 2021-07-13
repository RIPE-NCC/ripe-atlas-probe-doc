# Debian 9 e 10 - Instalação de código fonte


O sistema Debian Build inclui suporte para x86_64 (amd64), arm64 e armhf. Tenha em conta que os scripts de instalação e inicialização assumem o uso de `systemd`.

1. Para criar e instalar o pacote de software, siga as instruções específicas do Debian disponíveis no ficheiro
    [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. A instalação do software da sonda gera um novo par de chaves SSH que vai ser utilizado na ligação da sonda à infraestrutura RIPE Atlas. É necessário registar a chave publica para poder [registar a sonda](/apply/swprobe/).
    Esta encontra-se em `/var/atlas-probe/etc/probe_key.pub`.
