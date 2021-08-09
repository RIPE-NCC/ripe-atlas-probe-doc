CentOS 7 and 8 - Installazione da codice sorgente

La versione CentOS supporta x86_64 (amd64). Nota che gli script di installazione e avvio presuppongono l'uso di `systemd`.

1. Per creare e installare il pacchetto software, seguire le
 istruzioni specifiche per CentOS contenute nel file
 [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst)
 

2. L'installazione del software della probe genera un nuovo paio di chiavi SSH da utilizzare per collegare la probe all'infrastruttura di RIPE Atlas. 
Devi registrare la parte public key (chiave pubblica) per [registrare la probe](/apply/swprobe/).
La public key può essere trovata in
`/var/atlas-probe/etc/probe_key.pub`.
