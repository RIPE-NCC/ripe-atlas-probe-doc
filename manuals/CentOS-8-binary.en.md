# CentOS 8: Binary RPM-specific Installation Instructions

In case you want to set up a new Virtual Machine using CentOS in order to host your probe:

* Set up a new installation of CentOS 8 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [CentOS installation guide](https://docs.centos.org/en-US/centos/install-guide/).

* When installing CentOS in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary RPM packages and is currently available for CentOS 8
(x86_64). To add the repository to your system and install the package,
follow these steps:

1. Download the RPM that sets up the repository for the software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos8/noarch/ripe-atlas-repo-1-3.el8.noarch.rpm'
    ```

2. Check the hash of the RPM:

    ```
    sha256sum ripe-atlas-repo-1-3.el8.noarch.rpm
    ```

    The hash should be:

    ```
    e1e7800666f6978eb2e78dfabcd8aa0fa0ca45d9e97cc861a5e93300a2e46a00
    ```

3. Install the RPM:

    ```
    yum install ripe-atlas-repo-1-3.el8.noarch.rpm
    ```

    Answer `'y'` to the question of whether that is ok.


4. Now you can install the package for the software probe itself:

    ```
    yum install atlasswprobe
    ```

5. Answer `'y'` to import the GPG key with fingerprint `AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Answer `'y'` that is ok to install the RPM. You may may also need to accept a CentOS signing key.

7. Installing the probe software generates a new SSH key pair to be used to
   connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](https://atlas.ripe.net/apply/swprobe/).
   This can be found in `/var/atlas-probe/etc/probe_key.pub`.
