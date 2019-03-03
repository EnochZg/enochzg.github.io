---
layout: post
title: Ubuntu系统快捷方式创建小技巧
date: 2018-07-21
categories: 工具技巧
tags: [ubuntu, shortcut, 快捷方式, deepin, 工具, gnome]
---

* content
{:toc}

> 最近把笔记本系统换成了deepin，除了深度商店的应用外，很多软件都没有快捷方式。之前都是通过手动编写`.desktop`文件，很繁琐，今天无意中发现了一个小工具，可以通过图形化创建快捷方式，与大家分享一下。

### 安装`gnome-panel`

```bash
sudo apt-get install --no-install-recommends gnome-panel
```

### 使用

- 创建快捷方式文件
```bash
gnome-desktop-item-edit --create-new ~/Desktop
```

- 按图中要求选中可执行文件以及图标

![deepinscreenshot_select-area_20180721163756.png](https://wx2.sinaimg.cn/mw690/0070pygtgy1fthnls4z1rj30c1065jrf.jpg)

![deepinscreenshot_select-area_20180721164248.png](https://wx3.sinaimg.cn/mw690/0070pygtgy1fthnltifg1j30c0062q32.jpg)

大功告成，到桌面看一看吧！

![deepinscreenshot_select-area_20180721165629.png](https://wx4.sinaimg.cn/mw690/0070pygtgy1fthnnj1nl3j302o02edfu.jpg)

### 延伸

我们打开刚才在桌面创建的快捷方式，可以看到如下代码：
```bash
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0     #版本号
Type=Application    #应用类型
Terminal=false  #是否为终端
Exec=/home/enoch/Software/PhpStorm-181.5281.35/bin/phpstorm.sh     #所执行的脚本
Name=phpstorm   #快捷方式名称
Icon=/home/enoch/Software/PhpStorm-181.5281.35/bin/phpstorm.png    #图标的绝对路径

```
我们只需要编写`.desktop`文件即可完成快捷方式的创建，而这款小工具只是简化了我们的操作。
