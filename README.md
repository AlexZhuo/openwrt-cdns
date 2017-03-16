CDNS for OpenWrt
===
forked from https://github.com/ghostry/openwrt-gmod/tree/master/package/cdns  ,本repo用于编译[该固件][O]所需依赖包

简介
---

本软件包是 [CDNS][1] 在OpenWrt上的移植，用于快速获得无污染DNS，可与[luci-app-cdns][2]配合使用。在OpenWrt CC 15.05 , CC 15.05.1 , PandoraBox 16.10 SDK, LEDE 17.01.0编译通过

特性
---

1、UDP协议请求DNS，可使用53端口，使用国外DNS服务器可有效避免污染

2、速度快于非53端口的TCP DNS

3、CDNS自身不带缓存，推荐作为dnsmasq的上游DNS使用

获取最新代码
---
可以修改Makefile中PKG_SOURCE_VERSION为你需要编译的commit id

编译
---

 - 从 OpenWrt 的 [SDK][S] 编译

   ```bash
   # 以 ar71xx 平台为例
   tar xjf OpenWrt-SDK-ar71xx-for-linux-x86_64-gcc-4.8-linaro_uClibc-0.9.33.2.tar.bz2
   cd OpenWrt-SDK-ar71xx-*
   # 获取 cdns Makefile
   git clone https://github.com/AlexZhuo/openwrt-cdns.git package/cdns
   # 选择要编译的包 Utilities -> DNS -> cdns
   make menuconfig
   # 开始编译
   # 如果使用PandoraBox SDK请先编译cdns-pandorabox再编译cdns，最终用于安装的ipk应为cdns
   make package/cdns/compile V=99
   ```

[O]: http://www.right.com.cn/forum/thread-198649-1-1.html
[1]: https://github.com/semigodking/cdns
[2]: https://github.com/AlexZhuo/luci-app-cdns
[S]: https://wiki.openwrt.org/doc/howto/obtain.firmware.sdk
