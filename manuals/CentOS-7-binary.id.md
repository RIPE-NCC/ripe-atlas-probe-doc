# CentOS 7: Binary RPM-Cara Instalasi 

Berikut cara men-setup Virtual Machine dari awal menggunakan CentOS 7 yang akan digunakan untuk meng-host probe:

* Setup instalasi baru CentOS 7 (seperti contoh menggunakan [VirtualBox](https://www.virtualbox.org/) atau [Parallels](https://www.parallels.com/)), silahkan ikuti petunjuk sesuai dengan [Cara instalasi CentOS](https://docs.centos.org/en-US/centos/install-guide/).

* Saat instalasi CentOS dalam virtual machine, virtual network adapternya harus dikonfigurasi secara 'bridge mode' agar IPv6 bisa berfungsi. Stelan default biasanya dinamai 'shared' yang artinya hanya bisa untuk IPv4 NAT.

RIPE NCC mengelola paket binary RPM dan saat ini sudah bisa diakses untuk CentOS 7
(x86_64). Silahkan ikuti cara berikut untuk menambahkan repository ke sistem anda dan juga untuk menginstal paket tersebut: 


1. Download RPM untuk men-setup repository dari software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-2.el7.noarch.rpm'
    ```

2. Cek hash RPM dengan cara berikut:

    ```
    sha256sum ripe-atlas-repo-1-2.el7.noarch.rpm
    ```

    Hash yang benar adalah seperti ini:

    ```
    c02b6fb7004e86765257c93912403636f67ba59250f8f0904288f60eaad816c3
    ```

3. Install RPM-nya:

    ```
    yum install ripe-atlas-repo-1-2.el7.noarch.rpm
    ```

    Jawab `'y'` pada pertanyaan: is this ok y/N.


4. Sekarang, anda bisa melakukan instalasi paket dari software probe itu sendiri: 

    ```
    yum install atlasswprobe
    ```

5. Jawab `'y'` untuk mengimpor GPG key dengan fingerprint `afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5`

6. Jawab `'y'` bahwa sudah ok untuk menginstalasi RPM-nya. Ada kemungkinan anda juga harus menerima CentOS signing key.

7. Setelah menginstalasi software probe ini SSH key pair yang baru akan terbuat, ini bisa digunakan untuk menghubungkan probe ke infrastruktur RIPE Atlas. Public key ini akan digunakan untuk [mendaftarkan probe](/apply/swprobe/).
   Public key ini bisa anda temukan disini `/var/atlas-probe/etc/probe_key.pub`.
