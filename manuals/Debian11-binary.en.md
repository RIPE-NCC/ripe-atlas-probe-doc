# Debian Linux 11: Binary DEB-specific Installation Instructions

If you want to set up a new Virtual Machine using Debian 11 in order to host your probe:

* Set up a new installation of Debian 11 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Debian 11 installation guide](https://www.debian.org/releases/bullseye/installmanual).

* When installing Debian 11 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary DEB packages. These are currently available for Debian 11
(x86_64). These have been verified to work on Debian 11 (bullseye).

To add the repository to your system and install the package, follow these steps:

1. Download the DEB that sets up the repository for the software probe DEB:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/debian/dists/bullseye/main/binary-amd64/ripe-atlas-repo_1.5-2_all.deb'
    ```

2. Check the hash of the DEB:

    ```
    sha256sum -b ripe-atlas-repo_1.5-2_all.deb
    ```

    The hash should be:

    ```
    519aa81ced15a13cae784396a7ece83d2866d42c4fdc8a29c78ef3cefaa8e03c
    ```

3. Install the DEB (with root privileges):

    ```
    dpkg -i ripe-atlas-repo_1.5-2_all.deb
    ```

4. Now you can install the package for the software probe itself (with root privileges):

    ```
    apt-get update
    apt-get install ripe-atlas-probe
    ```

5. Answer `'y'` that is ok to install the DEB.

6. Now you can configure the RIPE Atlas software probe to be started at system boot time
   using (with root privileges):
    ```
    systemctl enable ripe-atlas.service
    ```
7. To start the RIPE Atlas software probe, execute (with root privileges):
    ```
    systemctl start ripe-atlas.service
    ```
8. Starting the RIPE Atlas software probe for the first time generates a new SSH key pair to be used to
   connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](https://atlas.ripe.net/apply/swprobe/).
   This can be found in `/etc/ripe-atlas/probe_key.pub`.
