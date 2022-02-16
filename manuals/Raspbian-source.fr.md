# Raspbian - Installation depuis les sources

## Preambule
Notez que les scripts d'installation et de démarrage supposent l'utilisation de `systemd`.


## Instructions

**1. Installer les paquets necessaires:**  
```
apt update && sudo apt install git tar fakeroot libssl-dev libcap2-bin autoconf automake libtool build-essential
```

**2. Cloner le dépot github:**  
```
git clone --recursive https://github.com/RIPE-NCC/ripe-atlas-software-probe.git
```

**3. Compiler le paquet d'installation:**  
```
./ripe-atlas-software-probe/build-config/debian/bin/make-deb
```

**4. Installer le paquet:**  
```
dpkg -i atlasswprobe-??????.deb
```

**5. Afficher la clef publique:**  
```
cat /var/atlas-probe/etc/probe_key.pub
```
Cette clé SSH est utilisé pour connecter la sonde à l'infrastructure Atlas RIPE.  

**6. Enregistrer la nouvelle sonde:**  
Rendez vous à l'adresse suivante pour enregistrer votre nouvelle sonde: [https://atlas.ripe.net/apply/swprobe/](https://atlas.ripe.net/apply/swprobe/)  
Vous aurez besoin de la clef affichée dans l'étape 5.
