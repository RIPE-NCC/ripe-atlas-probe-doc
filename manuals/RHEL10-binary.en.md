# Enterprise Linux 10: Binary RPM-specific Installation Instructions

If you want to set up a new Virtual Machine using Oracle EL10 in order to host your probe:

* Set up a new installation of Oracle EL10 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Oracle EL10 installation guide](https://docs.oracle.com/en/operating-systems/oracle-linux/10/).

* When installing Oracle EL10 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary RPM packages. These are currently available for RHEL10
(x86_64). These have been verified to work on Rocky Linux 10.

To add the repository to your system and install the package, follow these steps:

1. Download the RPM that sets up the repository for the software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/el10/noarch/ripe-atlas-repo-1.5-5.el10.noarch.rpm'
    ```

2. Check the hash of the RPM:

    ```
    sha256sum -b ripe-atlas-repo-1.5-5.el10.noarch.rpm
    ```

    The hash should be:

    ```
    0f0c3dcb856287ceaa73e1b941951b4fad683fbb229d2c06c03df249c0ef0327
    ```

3. Install the RPM (with root privileges):

    ```
    rpm -Uvh ripe-atlas-repo-1.5-5.el10.noarch.rpm
    ```

    Answer `'y'` to the question of whether that is ok.


4. Now you can install the package for the software probe itself (with root privileges):

    ```
    dnf install ripe-atlas-probe
    ```

5. Answer `'y'` to import the GPG key with fingerprint `3AA1 535B DE7A 8322 11A4  7D46 D973 45B4 F6FC F4B8`.

6. Answer `'y'` that is ok to install the RPM. You may may also need to accept a signing key.

7. At the end of the installation process, follow the on-screen instructions to register and start up the probe.

    * The registration process is also described here for reasons of clarity. You need the public key part in order to
register the probe. This process is necessary in order for the probe to function. The public key can be found in 
`/etc/ripe-atlas/probe_key.pub`.
