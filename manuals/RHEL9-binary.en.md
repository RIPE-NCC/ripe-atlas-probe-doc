# Enterprise Linux 9: Binary RPM-specific Installation Instructions

If you want to set up a new Virtual Machine using Oracle EL9 in order to host your probe:

* Set up a new installation of Oracle EL9 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [Oracle EL9 installation guide](https://docs.oracle.com/en/operating-systems/oracle-linux/9/).

* When installing Oracle EL9 in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary RPM packages. These are currently available for RHEL9
(x86_64). These have been verified to work on Oracle Linux Server 9.4 and Rocky Linux 9.2. 

To add the repository to your system and install the package, follow these steps:

1. Download the RPM that sets up the repository for the software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/el9/noarch/ripe-atlas-repo-1.5-2.el9.noarch.rpm'
    ```

2. Check the hash of the RPM:

    ```
    sha256sum -b ripe-atlas-repo-1.5-2.el9.noarch.rpm
    ```

    The hash should be:

    ```
    5c66f29b3c02b7289f25290d9d374fd7ea611447f4733ead7b9b51513791c324
    ```

3. Install the RPM (with root privileges):

    ```
    rpm -Uvh ripe-atlas-repo-1.5-2.el9.noarch.rpm
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
