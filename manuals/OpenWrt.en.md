# RIPE Atlas software probe on OpenWrt

OpenWrt packages the RIPE Atlas software probe as `ripe-atlas-probe`
(and `ripe-atlas-anchor` for anchors). It replaces the older
`atlas-sw-probe` package.

> [!NOTE]
> The package is a community contribution, not officially supported by
> the RIPE NCC. Please report problems at
> https://github.com/openwrt/packages/issues and mention the package
> maintainer.

## Install

On OpenWrt with apk (snapshots and newer releases):

    apk update
    apk add ripe-atlas-probe

On OpenWrt with opkg:

    opkg update
    opkg install ripe-atlas-probe

On Turris OS, enable the RIPE Atlas package list in reForis.

The service is enabled and started right away. On its first start it
creates the probe's SSH key in `/etc/ripe-atlas/probe_key` and
`/etc/ripe-atlas/probe_key.pub`.

## Register the probe

1. Print the public key:

       /etc/init.d/ripe-atlas get_key

2. Log in with your RIPE NCC Access account, open
   https://atlas.ripe.net/register/swprobe and paste the key there.
3. Once the RIPE NCC accepts the key, the probe registers by itself.
   This can take a while. You do not need to restart it.
4. Check that it registered:

       /etc/init.d/ripe-atlas probeid

   It prints `Probe ID is <ID>`, and `get_key` now says
   `Registered as probe <ID>`. The probe page is
   `https://atlas.ripe.net/probes/<ID>/`.

The registration is kept in RAM. After a reboot, `probeid` fails and
`get_key` asks to register again until the probe has re-registered,
which usually takes a few minutes. The key stays the same, so there is
nothing to do.

## Backup

The key is the probe's identity. A sysupgrade keeps
`/etc/ripe-atlas/probe_key` and `probe_key.pub`, but keep a copy
elsewhere too. With a new key the probe has to be registered again.

## Configuration settings

The settings are in `/etc/config/ripe-atlas`:

| Option | Default | Meaning |
|---|---|---|
| `enabled` | `1` | Run the probe |
| `mode` | `prod` | Leave at `prod`. `test` and `dev` are for RIPE NCC testing |
| `log_stderr` | `0` | Send the probe's error output to the system log |
| `log_stdout` | `0` | Send the probe's normal output to the system log |
| `rxtx_report` | `0` | Report the interface traffic counters to the RIPE NCC |

After a change:

    uci commit ripe-atlas
    /etc/init.d/ripe-atlas restart
