---
title: Ubuntu 18.04 下安装搜狗输入法的临时解决方法
date: 2018-07-11 15:00:59
tags: [ubuntu]
---

由于系统版本、软件升级，依赖无法正确安装，导致搜狗拼音无法使用，搜集的解决方案如下。

```bash
sudo apt install libfcitx-qt0
mkdir unpack # 创建临时目录
dpkg-deb -R sogoupinyin_2.2.0.0102_amd64.deb unpack/ # 解包
```

编辑 unpack/DEBIAN/control 把 Depends: 那一行里面的

```bash
fcitx-libs-qt (>= 4.2.7)
```

替换成:

```bash
libfcitx-qt0 (>= 1:4.2.9.6-1)
```

```bash
dpkg-deb -b unpack/ fixed.deb # 重新封包
sudo dpkg -i fixed.deb
sudo apt install --fix-broken # 解决依赖关系
```

然后重启一下, 切换输入法到中文就 OK 了.
