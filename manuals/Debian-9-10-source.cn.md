# Debian 9 和 10 - 源码安装

Debian 源码安装支持 x86_64 (amd64), arm64 和 armhf 架构。请注意，安装和启动脚本使用`systemd`

1. 请阅读教程 [INSTALL.rst](https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst) 中 Debian 的内容，安装所需软件包。


2. 探针软件安装时，会生成一个新的 SSH 密钥，用于连接探针至 RIPE Atlas 基础设施。
   密钥位于 `/var/atlas-probe/etc/probe_key.pub`，请上传至 [注册探针](https://atlas.ripe.net/apply/swprobe/)。