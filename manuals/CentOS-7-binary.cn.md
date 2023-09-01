# CentOS 7: RPM 安装

使用新的虚拟机来寄存探针步骤：

* 全新安装 CentOS 7 （例如使用 [VirtualBox](https://www.virtualbox.org/) 或 [Parallels](https://www.parallels.com/) ），请阅读 [官方CentOS安装教程](https://docs.centos.org/en-US/centos/install-guide/) 。

* 为了让 IPv6 正常工作，请将虚拟机网卡设定成桥接模式。原因是在一般情况下，虚拟机网卡默认为共享模式，只提供了 IPv4 NAT。

RIPE NCC 为 CentOS 7 (x86_64) 提供了 RPM 包。您需要导入软件拓展源到系统，并且进行安装。

1. 下载探针 RPM 拓展源文件。

    ```
    curl -O 'https://ftp.ripe.net/ripe/atlas/software-probe/centos7/noarch/ripe-atlas-repo-1-3.el7.noarch.rpm'
    ```

2. 检查文件的哈希值

    ```
    sha256sum ripe-atlas-repo-1-3.el7.noarch.rpm
    ```

   此文件的哈希值应为：

    ```
    3cbaa92f4a1dc4c74a865a6c14c3cda0badb649ee18d561740a2ba229b3e1e63
    ```

3. 安装拓展源:

    ```
    yum install ripe-atlas-repo-1-3.el7.noarch.rpm
    ```

   输入 `'y'` 并回车以进行安装。


4. 安装探针软件包：

    ```
    yum install atlasswprobe
    ```

5. 输入 `'y'` 导入指纹为 `afbe 52eb 213a 90ef c72a 39dd 1b48 2af7 830d 38d5` 的 GPG 密钥。

6. 输入 `'y'` 安装软件。您可能还需要接受一个 CentOS 签名密钥。

7. 探针软件安装时，会生成一个新的 SSH 密钥，用于连接探针至 RIPE Atlas 基础设施。
   密钥位于 `/var/atlas-probe/etc/probe_key.pub`，请上传至 [注册探针](https://atlas.ripe.net/apply/swprobe/)。
