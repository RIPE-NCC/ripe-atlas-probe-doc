# CentOS 8: Binary RPM-Istruzioni di installazione specifiche

Nel caso in cui desideri configurare una nuova macchina virtuale utilizzando CentOS per ospitare la tua probe:

* Configurare una nuova installazione di CentOS 8 (ad esempio utilizzando [VirtualBox](https://www.virtualbox.org/) o [Parallels](https://www.parallels.com/)), fare riferimento alla [Guida all'installazione di CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Quando si installa CentOS in una macchina virtuale, configurare la scheda di rete virtuale in `bridge mode` per consentire il funzionamento di IPv6. Spesso il valore predefinito è chiamato `shared` e fornisce solo NAT IPv4.

RIPE NCC mantiene i pacchetti RPM binari ed è attualmente disponibile per CentOS 8 (x86_64). Per aggiungere il repository al tuo sistema e installare il pacchetto,
segui questi passi:

1. Scaricare l'RPM che configura il repository per l'RPM della probe software:

 ```
 curl -O "https://ftp.ripe.net/ripe/atlas/software-probe/centos8/noarch/ripe-atlas-repo-1-2.el8.noarch.rpm"
 ```

2. Controlla l'hash dell'RPM:

 ```
 sha256sum ripe-atlas-repo-1-2.el8.noarch.rpm
 ```

 L'hash dovrebbe essere:

 ```
 cfb433f54395f5d2ac0d29e806f19f1b854d33f02c256087586e50e49003929c
 ```

3. Installa l'RPM:

 ```
 yum install ripe-atlas-repo-1-2.el8.noarch.rpm
 ```

 Rispondi `'y'` alla domanda per confermare l'installazione.


4. Ora puoi installare il pacchetto per la probe software stessa:

 ```
 yum install atlasswprobe
 ```

5. Rispondere `'y'` per importare la chiave GPG con impronta digitale `AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Rispondere `'y'` per installare l'RPM. Potrebbe anche essere necessario accettare un CentOS signing key.

7. L'installazione del software della probe genera un nuovo paio di chiavi SSH da utilizzare per
 collegare la probe all'infrastruttura di RIPE Atlas. Devi registrare
 la parte della public key (chiave pubblica) per [registrare la probe](/apply/swprobe/).
La public key può essere trovata in `/var/atlas-probe/etc/probe_key.pub`.
