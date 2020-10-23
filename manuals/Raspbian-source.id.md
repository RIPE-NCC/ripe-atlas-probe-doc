### Raspbian - Source Installation

Sistem Debian Build cocok untuk x86_64 (amd64), arm64, dan armhf. Perhatikan bahwa skrip instalasi dan juga skrip startup mengasumsikan penggunaan `systemd`.

1. Untuk membuat dan menginstal paket software, harap ikuti instruksi khusus Debian yang tertera disini
    [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. Menginstal software dari probe ini akan menghasilkan SSH key pair baru yang akan digunakan untuk menghubungkan probe ke infrastruktur RIPE Atlas. Anda perlu mendaftarkan bagian public key tersebut untuk [mendaftarkan probe](https://atlas.ripe.net/apply/swprobe/).
Public key ini dapat ditemukan di `/ var / atlas-probe / etc / probe_key.pub`.
