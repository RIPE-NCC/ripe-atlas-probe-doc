# Enterprise Linux 8: Binary RPM-specific Installation Instructions

If you want to set up a new Virtual Machine using Oracle EL8 in order to host your probe:

* Set up a new installation of Oracle EL8 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Oracle EL8 installation guide](https://docs.oracle.com/en/operating-systems/oracle-linux/8/).

* When installing Oracle EL8 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary RPM packages. These are currently available for RHEL8
(x86_64). These have been verified to work on Oracle Linux Server 8.10.

To add the repository to your system and install the package, follow these steps:

1. Download the RPM that sets up the repository for the software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/el8/noarch/ripe-atlas-repo-1-4.el8.noarch.rpm'
    ```

2. Check the hash of the RPM:

    ```
    sha256sum -b ripe-atlas-repo-1-4.el8.noarch.rpm
    ```

    The hash should be:

    ```
    b9023adebda4cdc6072ee532946a13e3894348a112761b3194c00a97070047c9
    ```

3. Install the RPM (with root privileges):

    ```
    rpm -Uvh ripe-atlas-repo-1-4.el8.noarch.rpm
    ```

    Answer `'y'` to the question of whether that is ok.


4. Now you can install the package for the software probe itself (with root privileges):

    ```
    dnf install ripe-atlas-probe
    ```

5. Answer `'y'` to import the GPG key with fingerprint `AFBE 52EB 213A 90EF C72A 39DD 1B48 2AF7 830D 38D5`

6. Answer `'y'` that is ok to install the RPM. You may may also need to accept a signing key.

7. Now you can configure the RIPE Atlas software probe to be started at system boot time
   using (with root privileges):
    ```
    systemctl enable ripe-atlas.service
    ```
8. To start the RIPE Atlas software probe, execute (with root privileges):
    ```
    systemctl start ripe-atlas.service
    ```
9. Starting the RIPE Atlas software probe for the first time generates a new SSH key pair to be used to
   connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](https://atlas.ripe.net/apply/swprobe/).
   This can be found in `/etc/ripe-atlas/probe_key.pub`.

10. For users of the 5080 release software probe or earlier (atlasswprobe), the process is identical.
    During installation of the 5090 or later release, ripe-atlas-probe will automatically uninstall
    atlasswprobe and migrate the configuration files and keys. After successful migration the
    /var/atlas-probe, /home/atlas directories and the atlasmsm & atlas users may be removed.
