# Debian Linux 11: Binary DEB-specific Installation Instructions

If you want to set up a new Virtual Machine using Debian 11 in order to host your probe:

* Set up a new installation of Debian 11 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Debian 11 installation guide](https://wiki.debian.org/DebianEdu/Documentation/Bullseye/Installation).

* When installing Debian 11 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary DEB packages. These are currently available for Debian 11
(x86_64). These have been verified to work on Debian 11 (bullseye).

To add the repository to your system and install the package, follow these steps:

1. Download the DEB that sets up the repository for the software probe DEB:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/debian/dists/bullseye/main/binary-amd64/ripe-atlas-repo_1.5-5_all.deb'
    ```

2. Check the hash of the DEB:

    ```
    sha256sum -b ripe-atlas-repo_1.5-5_all.deb
    ```

    The hash should be:

    ```
    8105140585dc4e1bf5b893832f1d4b6e7c2671b55b578bb792c305996df266a2
    ```

3. Install the DEB (with root privileges):

    ```
    dpkg -i ripe-atlas-repo_1.5-5_all.deb
    ```

4. Now you can install the package for the software probe itself (with root privileges):

    ```
    apt-get update
    apt-get install ripe-atlas-probe
    ```

5. Answer `'y'` that is ok to install the DEB.

6. At the end of the installation process, follow the on-screen instructions to register and start
   up the probe.
    * The registration process is also described here for reasons of clarity. You need
    the public key part in order to [register the probe](https://atlas.ripe.net/apply/swprobe/). This process is
    necessary in order for the probe to function. The public key can be found in `/etc/ripe-atlas/probe_key.pub`.
