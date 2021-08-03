CentOS 7 e 8 - Instalação de código fonte

A versão CentOS suporta x86_64 (amd64). Tenha em conta que os scripts de instalação e inicialização pressupõem o uso de `systemd`.

1. Para criar e instalar o pacote de software, siga as instruções específicas do CentOS referidas no arquivo
    [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. A instalação do software da probe gera um novo par de chaves SSH que vai ser utilizado na ligação da probe à infraestrutura RIPE Atlas. É necessário registar a chave pública para poder [registar a probe](https://atlas.ripe.net/apply/swprobe/).
A chave pública encontra-se em `/var/atlas-probe/etc/probe_key.pub`.
