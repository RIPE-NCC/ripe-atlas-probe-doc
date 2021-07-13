# Sondas RIPE Atlas

RIPE Atlas é uma rede global de sondas que mede a conectividade e acessibilidade pela Internet em tempo real. As sondas são instaladas e mantidas principalmente por voluntários. Se hospedar a sonda, receberá créditos (veja mais sobre [o sistema de créditos](https://atlas.ripe.net/docs/credits/)) que podem ser usados posteriormente para executar suas próprias medições na rede RIPE Atlas.

Este documento descreve as etapas que deve seguir para ligar o seu router como uma sonda à rede RIPE Atlas.

## Instalação

Para instalar a sonda, vá para o menu *reForis*  *Gerenciamento de pacotes* → *Pacotes* e selecione *RIPE Atlas SW Probe*.

Depois disso, deve-se ligar ao seu router via SSH e iniciar o serviço `atlas`.

Active e execute o daemon com estes comandos:

```
/etc/init.d/atlas enable
/etc/init.d/atlas start
```
A sonda comunica com os servidores Atlas por meio de um túnel SSH. A chave SSH é gerada após a primeira execução do daemon da sonda.

Após iniciar o daemon, execute o comando `get_key` para obter a chave pública SSH gerada. Você precisará dessa chave para registrar sua sonda em sua conta no site RIPE.


`/etc/init.d/atlas get_key`

Demora alguns segundos para gerar a chave.

## Registo da Sonda

Para registrar sua sonda, deve ter uma conta no [site do RIPE NCC](https://access.ripe.net/registration).

Assim que estiver ligado à sua conta no [site RIPE Atlas] (https://access.ripe.net/registration), preencha o formulário neste [link](https://atlas.ripe.net/apply/swprobe/). No campo do formulário *Chave Pública*, copie a chave obtida pelo comando `get_key`.

Consulte [RIPE Atlas Service Terms and Conditions](https://www-static.ripe.net/static/rnd-ui/atlas/media/legal/RIPEAtlasServiceTermsandConditionsV2.0.pdf), se concordar com isso, verifique e clique no botão *Submit your application*.

## Configuração

A configuração está localizada em `/etc/config/atlas`. Ele contém apenas uma opção booleana `rxtxrpt` que define se queremos enviar estatísticas de tráfego da interface como resultado da medição da sonda.

## ID da Sonda e Medição

Após o registo da sonda, deve receber um e-mail com o assunto <b> Your new RIPE Atlas software probe is created</b>, onde pode encontrar seu ID de sonda e link para gerir sua sonda.

Pode também usar este comando para obter o ID da sonda:

```
/etc/init.d/atlas probeid
```
A medição de sua sonda pode ser acedida através da web (where is your probe ID).

```
https://atlas.ripe.net/measurements/<ID>/
```
