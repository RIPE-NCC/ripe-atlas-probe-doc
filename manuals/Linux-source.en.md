# Linux - Source Installation

The source installation has been tested only on RHEL8, RHEL9, Debian 11 and Debian 12 on the x86_64
platform. Note that the installation and startup scripts assume the use of `systemd`.

1. In order to create and install the software package, please follow the instructions as laid
   out in the [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst)
   file.

2. Starting the RIPE Atlas software probe for the first time generates a new SSH key pair
   to be used to connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](https://atlas.ripe.net/apply/swprobe/).
   This can be found in `/etc/ripe-atlas/probe_key.pub`.
