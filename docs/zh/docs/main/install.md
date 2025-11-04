# 安装

## 它兼容什么系统？

自1.6.0起，Pixiv-MultiPlatform支持下列操作系统

- Windows
- Linux
- macOS
- Android
- IOS(部分支持)

::: danger

受限于我不会使用mac命令行的缘故，故IOS包无法加入CI发行版中。

如有人想要尝鲜的话，请自行下载编译安装。

:::

## 我该如何选择安装包？

1. 点击[下载页面](https://github.com/magic-cucumber/Pixiv-MultiPlatform/releases/latest)
2. Windows用户请跳转到[Windows安装](#windows安装)
3. Linux用户请跳转到[Linux安装](#Linux安装)
4. macOS用户请跳转到[macOS安装](#macOS安装)
5. Android用户请跳转到[安卓端安装](#安卓端安装)

## Windows安装

### 直接解压缩文件

1. 解压缩文件到你喜欢的位置中
2. 点击`Pixiv-MultiPlatform.exe`以启动

### 使用Windows Installer(.msi)安装

1. 下载`windows.msi`

2. 双击，选择合适的位置进行安装。

   :::warning

   默认情况下会安装到`C:\Program Files\Pixiv-MultiPlatform`，介意者可更换安装路径

   :::

## Linux安装

### 解压缩安装

使用`tar`相关命令解压归档文件到你喜欢的位置中

赋予可执行文件权限：`chmod +x ./Pixiv-MultiPlatform`

双击文件以启动。

### AUR(仅限ArchLinux)安装

目前已有对于`AUR`的[第三方软件包](https://aur.archlinux.org/packages?O=0&SeB=nd&K=pixiv-multiplatform&outdated=&SB=p&SO=d&PP=50&submit=Go)，您可以使用`yay -S`相关命令进行安装，对于此类功能则不再赘述

### 自动化安装脚本

鉴于有人不想手工制作desktop文件，您可以在下载的.tar.gz同级目录下创建一个sh脚本：

```bash
#!/bin/bash

# 检查sudo权限是否可用
if ! sudo -v &>/dev/null; then
    echo "Sudo权限不可用，脚本将停止执行。"
    exit 1
fi

# 检查tar.gz文件是否存在
if [ ! -f "linux.tar.gz" ]; then
    echo "未找到linux.tar.gz文件！"
    exit 1
fi

# 将linux.tar.gz解压到/opt/Pixiv-MultiPlatform
echo "正在将文件解压到/opt/Pixiv-MultiPlatform..."
sudo tar -xzvf linux.tar.gz -C /opt/

# 创建Pixiv-MultiPlatform.desktop文件
echo "正在创建桌面快捷方式..."
echo "[Desktop Entry]
Name=Pixiv-MultiPlatform
Comment=pixiv client on multiplatform
Exec=/opt/Pixiv-MultiPlatform/bin/Pixiv-MultiPlatform
Icon=/opt/Pixiv-MultiPlatform/lib/Pixiv-MultiPlatform.png
Terminal=false
Type=Application
Categories=Utility;" | sudo tee /usr/share/applications/Pixiv-MultiPlatform.desktop > /dev/null

# 给桌面文件赋予执行权限
echo "正在给桌面文件赋予执行权限..."
sudo chmod +x /usr/share/applications/Pixiv-MultiPlatform.desktop

# 运行Pixiv-MultiPlatform
echo "正在启动Pixiv-MultiPlatform..."
/opt/Pixiv-MultiPlatform/bin/Pixiv-MultiPlatform &
```

此脚本将：
1. 检查sudo权限
2. 将应用程序解压到 `/opt/Pixiv-MultiPlatform`
3. 创建桌面快捷方式以便于访问
4. 自动启动应用程序

## macOS安装

1. 下载`.dmg`文件
2. 双击文件
3. 拖动图标到`Applications`
4. 启动App

> ### macOS 上无法安装dmg文件的解决方案
> 
> 1. 打开
>    
>    ![image-20250130084342912](./install.assets/image-20250130084342912.png)
> 
> 2. 依次点击
>    
>    ![3](./install.assets/3.png)
> 
> 3. 输入密码后，即可继续安装。

## 安卓端安装

1. 下载`android.apk`文件到你喜欢的位置中

   ::: info

   默认的存储位置应该是`内置存储/Downloads中`
   :::

2. 打开你手机里的文件管理软件(若没有请下载诸如`MT管理器`等的第三方文件管理工具)，找到你下载的`android.apk`。

3. 单击进行安装，安装时请留意：`无视风险`等小字。

## iOS安装

1. 下载 `iOS.ipa` 到你的电脑中。

2. 使用签名工具进行签名。

   ::: warning

   本人已使用`爱思助手`成功安装并签名。

   若您使用 `巨魔商店`等其他方式进行签名，则需要确保**您手中有一台MacBook**来抓取APP的运行时闪退日志，**否则我将无能为力**

   :::

   ::: warning

   自`1.7.4`起，Pixiv-MultiPlatform对iOS的支持放宽到iOS16.4。

   其余**workflow**版本则需要iOS18+

   :::

3. 安装并打开应用。



## 卸载

安卓端请直接卸载，桌面端在删除文件夹后需要删除残留文件。

1. Windows的残留文件在`C:\Users\用户名\.config\pmf`中，直接拖进回收站即可。
2. Linux的残留文件在`~/.config/pmf`中，直接删除即可
3. macOS的残留文件在`~/.config\pmf`中，直接删除即可
