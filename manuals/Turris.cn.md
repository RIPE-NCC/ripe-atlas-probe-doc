# Turris 路由器

本文翻译自 [Atlas Probes - Turris Document](https://docs.turris.cz/basics/apps/atlas/) 。

## 安装

请前往 _reForis_ 菜单 _Package Management → Packages_
，选择 _RIPE Atlas SW Probe_。

安装完成后，使用 SSH 连接至路由器，启动 `atlas` 服务。

使用以下指令启动服务：
```
/etc/init.d/atlas enable
/etc/init.d/atlas start
```

探针使用 SSH 隧道连接至 Atlas 服务器。SSH 密钥在探针服务第一次启动时生成。

运行 `get_key` 指令获取 SSH 公钥。请上传至 [注册探针](https://atlas.ripe.net/apply/swprobe/) 。

```
/etc/init.d/atlas get_key
```

服务需要数秒时间生成密钥。

## 配置文件

配置文件位于 `/etc/config/atlas`。此文件包含一个布尔选项 `rxtxrpt`，是否同意在探针测量中发送网卡流量数据。

## 探针 ID 和测量结果

探针注册完成后，您会收到一封标题为 __Your new RIPE Atlas software probe is created__ 的邮件。在邮件内您可以找到探针 ID 和管理连接。

您也可以使用以下指令获取探针 ID ： 

```
/etc/init.d/atlas probeid
```

测量结果可以通过以下连接查看（请替换 __<ID>__ 为您的探针 ID ）：

```
https://atlas.ripe.net/measurements/<ID>/
```
