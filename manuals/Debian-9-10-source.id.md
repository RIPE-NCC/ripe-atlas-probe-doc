# Debian 9 & 10 - Source Installation

Sistem Debian Build cocok dan bisa dipakai untuk x86_64 (amd64), arm64, dan armhf. Perhatikan bahwa skrip instalasi dan juga startup mengasumsikan penggunaan `systemd`.

1. Untuk membuat dan menginstal paket software, harap ikuti Instruksi khusus Debian
    [INSTALL.rst] (https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. Menginstal software dari probe ini akan menghasilkan SSH key pair baru. Ini akan digunakan untuk menghubungkan probe ke infrastruktur RIPE Atlas. Anda harus mendaftarkan Public key tersebut untuk [mendaftarkan probe](/apply/swprobe/).

Public key ini dapat ditemukan di `/ var / atlas-probe / etc / probe_key.pub`.
