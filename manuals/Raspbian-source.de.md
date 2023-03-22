# Raspbian - Installation via Quellcode

## Präambel
Beachten Sie, dass die Installations- und Startskripte die Verwendung von „systemd“ voraussetzen.  
Evtl. werden root-Rechte benötigt, gegebenenfalls die Befehle mit ```sudo``` ausführen.  


## Anweisungen

**1. Notwendige Pakete installieren:**  
```
apt update && sudo apt install git tar fakeroot libssl-dev libcap2-bin autoconf automake libtool build-essential
```

**2. GitHub-Repository klonen:**  
```
git clone --recursive https://github.com/RIPE-NCC/ripe-atlas-software-probe.git
```

**3. Kompilieren des Installationspakets:**  
```
./ripe-atlas-software-probe/build-config/debian/bin/make-deb
```

**4. Installationspaket installieren:**  
```
dpkg -i atlasswprobe-??????.deb
```

**5. Öffentlichen Schlüssel anzeigen:**  
```
cat /var/atlas-probe/etc/probe_key.pub
```
Dieser SSH-Schlüssel wird verwendet, um die Probe mit der Atlas RIPE-Infrastruktur zu verbinden.  

**6. Neue Sonde registrieren:**  
Rufen Sie die folgende Adresse auf, um Ihre neue Probe zu registrieren: [https://atlas.ripe.net/apply/swprobe/](https://atlas.ripe.net/apply/swprobe/)  
Sie benötigen den in Schritt 5 gezeigten Schlüssel.
