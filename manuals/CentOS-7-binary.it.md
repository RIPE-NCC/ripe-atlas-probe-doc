# CentOS 7: Istruzioni di installazione Binary RPM-specific 


Nel caso in cui desideri configurare una nuova macchina virtuale utilizzando CentOS 7 per ospitare la tua probe:

* Configurare una nuova installazione di CentOS 7 (ad esempio utilizzando [VirtualBox](https://www.virtualbox.org/) o [Parallels](https://www.parallels.com/)), fai riferimento alla [Guida all'installazione di CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Quando si installa CentOS in una macchina virtuale, configurare la scheda di rete virtuale in `bridge mode` per consentire il funzionamento di IPv6. Spesso il valore predefinito è chiamato `shared` e fornisce solo NAT IPv4.

RIPE NCC mantiene i pacchetti binari RPM e sono attualmente disponibile per CentOS 7 (x86_64). Per aggiungere il repository al tuo sistema e installare il pacchetto, segui questi passaggi:

1. Scaricare l'RPM che configura il repository per l'RPM della probe software:

 ```
 curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-3.el7.noarch.rpm'
 ```

2. Controlla l'hash dell'RPM:

 ```
 sha256sum ripe-atlas-repo-1-3.el7.noarch.rpm
 ```

 L'hash dovrebbe essere:

 ```
 3cbaa92f4a1dc4c74a865a6c14c3cda0badb649ee18d561740a2ba229b3e1e63
 ```

3. Installa l'RPM:

 ```
 yum install ripe-atlas-repo-1-3.el7.noarch.rpm
 ```

 Rispondi `'y'` alla domanda per confermare l'installazione.


4. Ora puoi installare il pacchetto per la probe software:

 ```
 yum install atlasswprobe
 ```

5. Rispondi `'y'` per importare il GPG key con impronta digitale `afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5`

6. Rispondere `'y'` per installare l'RPM. Potrebbe anche essere necessario accettare un CentOS signing key.

7. L'installazione del software della probe genera una nuova coppia di chiavi SSH da utilizzare per
 collegare la probe all'infrastruttura di RIPE Atlas. Devi registrare
 la parte public key (chiave pubblica) per [registrare la probe](/apply/swprobe/).
La public key può essere trovata in `/var/atlas-probe/etc/probe_key.pub`.
