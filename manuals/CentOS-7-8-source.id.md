# CentOS 7 and 8 - Source Installation

Versi CentOS cocok dan bisa diakses untuk  x86_64 (amd64). Perhatikan bahwa skrip untuk penginstalan dan juga startup mengasumsikan penggunaan `systemd`.

1. Untuk membuat dan menginstalasi paket softwarenya, silahkan ikuti petunjuk cara instalasi  CentOS seperti tertera di dokumen berikut [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst).

2. Setelah menginstalasi software untuk probe ini akan menghasilkan SSH key pair yang baru, ini akan digunakan untuk menghubungkan probe ke infrastruktur RIPE Atlas. Public key ini akan digunakan untuk [mendaftarkan probe](/apply/swprobe/).
Public key ini bisa anda temukan disini 
`/var/atlas-probe/etc/probe_key.pub`
