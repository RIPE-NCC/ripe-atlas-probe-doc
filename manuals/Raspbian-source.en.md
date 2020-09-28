### Raspbian - Source Installation

The Debian Build system includes support for x86_64 (amd64), arm64 and armhf. Note that the installation and startup scripts assume the use of `systemd`.

1. In order to create and install the software package, please follow the
   Debian specific instructions laid out in the
   [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst)
   file.

2. Installing the probe software generates a new SSH key pair to be used to
   connect the probe to the RIPE Atlas infrastructure. You need to register
   the public key part to in order to [register the probe](/apply/swprobe/).
   This can be found in `/var/atlas-probe/etc/probe_key.pub`.
