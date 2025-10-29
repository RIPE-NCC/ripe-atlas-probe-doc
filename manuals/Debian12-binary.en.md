# Debian Linux 12: Binary DEB-specific Installation Instructions

If you want to set up a new Virtual Machine using Debian 12 in order to host your probe:

* Set up a new installation of Debian 12 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Debian 12 installation guide](https://www.debian.org/releases/oldstable/installmanual).

* When installing Debian 12 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary DEB packages. These are currently available for Debian 12
(x86_64 and arm64). These have been verified to work on Debian 12 (bookworm) for amd64 and Raspberry Pi OS for arm64.

To add the repository to your system and install the package, follow these steps:

1. Download the DEB that sets up the repository for the software probe DEB:
    
    * amd64:
    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/debian/dists/bookworm/main/binary-amd64/ripe-atlas-repo_1.5-5_all.deb'
    ```
    * arm64:
    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/debian/dists/bookworm/main/binary-arm64/ripe-atlas-repo_1.5-5_all.deb'
    ```
    
2. Check the hash of the DEB:

    * amd64/arm64:
    ```
    sha256sum -b ripe-atlas-repo_1.5-5_all.deb
    ```
    The hash should be:

    * amd64:
    ```
    34b7afff1d31e12746e04a6760f3711a52c108f5c951e2dffa9fe699fc7777ca
    ```
    * arm64:
    ```
    6ce0e4cb36c3fa8e5515304f241104128d7dac1e6a0e3ebd15324f7e9b5076f7
    ```

3. Install the DEB (with root privileges):
    * amd64/arm64:
    ```
    dpkg -i ripe-atlas-repo_1.5-5_all.deb
    ```

5. Now you can install the package for the software probe itself (with root privileges):

    * amd64/arm64:
    ```
    apt-get update
    apt-get install ripe-atlas-probe
    ```

6. Answer `'y'` that is ok to install the DEB.

7. At the end of the installation process, follow the on-screen instructions to register and start
   up the probe.

    * The registration process is also described here for reasons of clarity. You need
    the public key part in order to [register the probe](https://atlas.ripe.net/apply/swprobe/). This process is
    necessary in order for the probe to function. The public key can be found in `/etc/ripe-atlas/probe_key.pub`.
