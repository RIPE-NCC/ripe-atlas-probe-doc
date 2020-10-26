# CentOS 7: Binary RPM-specific Installation Instructions

In case you want to set up a new Virtual Machine using CentOS 7 in order to host your probe:

* Set up a new installation of CentOS 7 (for example using [VirtualBox](https://www.virtualbox.org/) or [Parallels](https://www.parallels.com/)), please refer to the [CentOS installation guide](https://docs.centos.org/en-US/centos/install-guide/).

* When installing CentOS in a virtual machine, please configure the virtual network adapter in 'bridge mode' to allow IPv6 to work. Often the default is called 'shared' which only provides IPv4 NAT.

The RIPE NCC maintains binary RPM packages and is currently available for CentOS 7
(x86_64). To add the repository to your system and install the package,
follow these steps:

1. Download the RPM that sets up the repository for the software probe RPM:

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-2.el7.noarch.rpm'
    ```

2. Check the hash of the RPM:

    ```
    sha256sum ripe-atlas-repo-1-2.el7.noarch.rpm
    ```

    The hash should be:

    ```
    c02b6fb7004e86765257c93912403636f67ba59250f8f0904288f60eaad816c3
    ```

3. Install the RPM:

    ```
    yum install ripe-atlas-repo-1-2.el7.noarch.rpm
    ```

    Answer `'y'` to the question of whether that is ok.


4. Now you can install the package for the software probe itself:

    ```
    yum install atlasswprobe
    ```

5. Answer `'y'` to import the GPG key with fingerprint `afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5`

6. Answer `'y'` that is ok to install the RPM. You may may also need to accept a CentOS signing key.

7. Installing the probe software generates a new SSH key pair to be used to
   connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](https://atlas.ripe.net/apply/swprobe/).
   This can be found in `/var/atlas-probe/etc/probe_key.pub`.
