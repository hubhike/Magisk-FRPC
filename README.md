# Magisk-FRPC-hubhike修改版，不要Sync Fork！！！

A Magisk module for running FRPC on Android devices.

If your terminal device uses WEB service or other services need remote access, then this module will be your good choice.

---

在 Android 设备上运行 FRPC 的一个 Magisk 模块。

若您的终端设备使用了 WEB 服务或其他服务需要远程访问，那么该模块将是您的不错的选择。

## Usage
![](https://raw.githubusercontent.com/hubhike/Magisk-FRPC/main/help/97105821.png)

After the module is installed, please browse and edit the frpc.ini configuration file in the Android/frpc directory. Then restart the device, after the device is running, it will run the FRPC daemon on your device.

---

模块安装完成后，请到 Android/frpc 目录下浏览并编辑 frpc.ini 配置文件文件。然后重启设备，设备运行后，会在你的设备上运行 FRPC 守护程序。

## About

### Features

- The module supports `arm`, `arm64`, `amd64`, `x86` architecture. Automatically judge and apply the equipment instruction structure during installation.
- Use the crond command in the Busybox program carried by the module to establish the timing task detection status.
- After the FRPC configuration file is modified, it will automatically detect and reload the configuration file.
- Magisk module page automatically displays module status information.
- Check the integrity of the file to prevent the module from being damaged. (thanks to the inspiration provided by the Riru module).
- It can be turned on or off in the Magisk module to control the start and end of the FRPC program.
- The power of the device is less than 20% and the FRPC program is automatically terminated when it is not being charged. Please keep the device full of power!
- Creating a `screen` file in the module directory means that the screen is detected, otherwise it will not be detected.

---

- 模块支持`arm`、`arm64`、`amd64`、`x86`架构。安装时自动判断设备指令架构并应用。
- 使用模块携带的 Busybox 程序中 crond 命令建立定时任务检测状态。
- FRPC 配置文件修改后会自动检测并重载配置文件。
- Magisk 模块页面自动显示模块状态信息。
- 检验文件完整性，防止模块被破坏。（感谢 Riru 模块提供的灵感）。
- 可在 Magisk 模块中开启或关闭来控制 FRPC 程序启动与结束。
- 设备电量低于 20% 且未在充电自动终止 FRPC 程序，请保持设备电量充足！
- 在模块目录创建 `screen` 文件则表示息屏检测，反之不检测。

## How to build？


The traditional direct zip package construction method is not feasible, so I wrote a build script, you can refer to the article: https://www.isisy.com/1276.html

---

正常情况直接下载 release 处的 zip 包在 Magisk 中安装即可，若您的 Magisk 版本高于 24.0，后续更新直接在 Magisk 中即可。

为保证模块不被破坏，模块安装时校验模块内部相关文件 sha256 信息，传统的直接打 ZIP 包方式已不可行。下面自己写了个脚本用于对项目源码 ZIP 包的构建，给其它二次构建着方便自主构建食用。

为此写了一份构建脚本，可参考文章：https://www.isisy.com/1276.html

将如下代码保存至脚本文件中，脚本文件放置于与模块文件夹的同目录下，**勿放置在模块文件夹目录下。**
目录结构：ls
build.sh Magisk-FRPC（模块文件夹）
然后根据帮助信息构建 zip 包即可。

构建ZIP脚本代码如下：
https://raw.github.com/hubhike/Magisk-FRPC/main/help/build_zip.sh

### ｄｅｂｉａｎ环境中构建步骤：

> 0、说明
> 安装 dos2unix（报错，系统中没有就安装）
> Ubuntu/Debian：
> apt-get install dos2unix

> 转换脚本格式
> dos2unix ./build_zip.sh
>
> 安装ZIP（报错，系统中没有就安装）
> apt-get install zip

1、建立个临时目录，进入临时目录

cd /tmp/

２、下载构建脚本

wget https://raw.github.com/hubhike/Magisk-FRPC/main/help/build_zip.sh

给脚本权限：chmod +x ./build_zip.sh

３、拉取项目

git clone --depth=1 https://github.com/hubhike/Magisk-FRPC

４、运行构建命令

./build.sh -G Magisk-FRPC

５、说明：build_zip.sh和 Magisk-FRPC 在同一目录，build_zip.sh不在目录Magisk-FRPC。

效果图：

![](https://raw.githubusercontent.com/hubhike/Magisk-FRPC/main/help/2405645629.png)

## Uninstall && Clear

The module only releases the files required for additional work in the Android/frpc directory of the device (excluding other path settings for customizing frpc logs). If the `uninstall.sh` script is not executed when the module is uninstalled, please manually clear the files in the Android/frpc directory.

---

模块仅在设备 Android/frpc 目录释放额外工作需要的文件（不含 frpc 日志自定义其它路径设置），若模块卸载时未执行 `uninstall.sh` 脚本，请手动清除 Android/frpc 目录内文件。

> FRPC 程序的日志路径设置请勿设置到根目录中去，除非您有需要自定义日志路径，否则请保持默认日志设置或关闭日志生成。

## Thanks

- https://github.com/topjohnwu/Magisk
- https://github.com/osm0sis/android-busybox-ndk
- https://github.com/fatedier/frp
- https://github.com/RikkaApps/Riru
- 其它模块的参考
