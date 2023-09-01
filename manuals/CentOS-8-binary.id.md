# CentOS 8: Binary RPM - Cara Instalasi 

Berikut cara men-setup virtual machine yang baru untuk meng-host RIPE Atlas software anda:

* Buat instalasi CentOS 8 yang baru (misalnya menggunakan [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), silahkan ikuti petunjuk disini [Cara instalasi CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Ketika anda menginstalasi CentOS di virtual machine,  virtual network adapter-nya harus dikonfigurasikan menjadi 'bridge mode' agar IPv6 bisa berfungsi. Setting default(setting yang automatis dipakai) biasanya 'shared' yang berarti hanya bisa untuk NAT IPv4.

RIPE NCC mengelola paket binary RPM dan saat ini sudah bisa diakses untuk CentOS 7
(x86_64). Silahkan ikuti cara berikut untuk menambahkan repository ke sistem anda dan juga untuk menginstal paket tersebut:


1. Unduh(download) RPM untuk men-setup repository dari software probe RPM:

   ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos8/noarch/ripe-atlas-repo-1-3.el8.noarch.rpm'
    ```

2. Cek hash dari RPM tersebut:

    ```
    sha256sum ripe-atlas-repo-1-3.el8.noarch.rpm
    ```

    Hash -nya harus sama dengan:

    ```
    e1e7800666f6978eb2e78dfabcd8aa0fa0ca45d9e97cc861a5e93300a2e46a00
    ```

3. Sekarang instalasi RPM-nya:

    ```
    yum install ripe-atlas-repo-1-3.el8.noarch.rpm
    ```

    Jawab `'Y'` jika benar.


4. Sekarang, anda bisa melakukan instalasi paket dari software probe itu sendiri:

    ```
    yum install atlasswprobe
    ```

5. Jawab `'Y'` untuk mengimpor GPG key dengan menggunakan fingerprint `AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Jawab  `'Y'` bahwa sudah OK untuk menginstalasi RPM-nya. Ada kemungkinan anda juga harus menerima CentOS signing key.

7.Setelah menginstalasi software probe ini, SSH key pair yang baru akan terbuat, ini bisa digunakan untuk menghubungkan probe ke infrastruktur RIPE Atlas. Public key ini akan digunakan untuk [mendaftarkan probe](/apply/swprobe/).
Public key ini bisa anda temukan disini `/var/atlas-probe/etc/probe_key.pub`
