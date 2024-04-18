---
{"dg-publish":true,"aliases":[null],"tags":[null],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/258563812","title":"玩转 Windows 自带的 Linux 子系统 （图文指南）","summary":null,"Created-Date":"2023-08-09 08:36:14","Modified-Date":"2024-04-18 11:52:10","permalink":"/Z01_InBox/SimpRead/玩转 Windows 自带的 Linux 子系统 （图文指南）/","dgPassFrontmatter":true}
---

涉及到计算机科学离不开 Linux 系统，当然，也离不开 Windows。但是，二者从操作到核心的不同，貌似让鱼和熊掌不可兼得。

但是！微软已经拿出了一款让鱼和熊掌兼得的方案 WSL （Windows Subsystem for Linux），也就是 Windows 系统中自带 Linux 子系统。

![](https://pic1.zhimg.com/v2-be69ef6a7ee44bd2080fa63f6c8e1540_r.jpg)

这比其他方案的优势在于：

* 不会产生传统虚拟机或双启动设置开销
* 实现 Windows 系统与 Linux 系统磁盘资源的共享
* 相对其他 Bash，更接近原生 Linux 系统
* 网络设置等配置与 Windows 系统保持一致，减少维护
* 等等

下面我们从几个方面来安装并使用：

* 命令行界面安装
* 图形化界面安装
* 其他技巧

### Z.1.1. 一、命令行界面安装

1、`win`+`S`，搜索 PowerShell，右键管理员身份运行

![](https://pic3.zhimg.com/v2-6777d0bd93ce201442bc4edcccd99896_r.jpg)

2、输入命令，启用 `适用于 Linux 的 Windows 子系统` 功能

`dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

![](https://pic2.zhimg.com/v2-7a5330125f566e10c9f030b629ba4009_r.jpg)

这一步完成启用 “适用于 Linux 的 Windows 子系统” 可选功能

3、选择中意的 Linux 分发版：

网址：[https://aka.ms/wslstore](https://link.zhihu.com/?target=https%3A//aka.ms/wslstore)

![](https://pic1.zhimg.com/v2-d370743027c361dd10faf4252a3ed490_r.jpg)

4、这里以 Ubuntu 18 为例来进行下一步安装

[https://www.microsoft.com/zh-cn/p/ubuntu-1804-lts/9n9tngvndl3q?rtc=1#activetab=pivot:overviewtab](https://link.zhihu.com/?target=https%3A//www.microsoft.com/zh-cn/p/ubuntu-1804-lts/9n9tngvndl3q%3Frtc%3D1%23activetab%3Dpivot%3Aoverviewtab)

![](https://pic2.zhimg.com/v2-beb07737e612c7fd2febc4ea68070ea1_r.jpg)

5、自动安装中...

![](https://pic4.zhimg.com/v2-9ef57c0900026a8d6ef102c3d20c4d23_r.jpg)

6、按 `win`，打开 Ubuntu

![](https://pic3.zhimg.com/v2-5bb2b2c65c24d8a5f65ec827a5966556_b.jpg)

7、设置好用户和密码

![](https://pic4.zhimg.com/v2-8f75debcdf7f752d1cf752cff6b2b3c7_r.jpg)

8、设置初始 root 密码

`sudo passwd`

9、配置软件源，加速国内访问速度

备份配置文件

`cp /etc/apt/sources.list /etc/apt/sources_bk.list`

修改配置文件

```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse

```

参考：[https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/](https://link.zhihu.com/?target=https%3A//mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)  

### Z.1.2. 二、安装图形化界面

### Z.1.3. 在 Ubuntu 端的配置

1、安装 xorg

`sudo apt-get install xorg`

xorg 是 xfce 桌面需要的一个基础依赖，开机时提供登陆界面

![](https://pic1.zhimg.com/v2-d544732994a212b30e0547eb4167bc50_r.jpg)

2、安装 xfce4

`sudo apt-get install xfce4`

![](https://pic1.zhimg.com/v2-78e4f5d0f42ecb18b8a4f3087410a610_r.jpg)

3、安装并配置 xrdp

Xrdp 通过远程桌面的方式来访问另外一台主机

`sudo apt-get install xrdp`

4、设置使用 3390 端口

`sudo sed -i 's/port=3389/port=3390/g' /etc/xrdp/xrdp.ini`

5、向 xsession 中写入 xfce4-session

`sudo echo xfce4-session >~/.xsession`

6、重启 xrdp 服务

`sudo service xrdp restart`

### Z.1.4. 在 Windows 端配置

1、`win`+`S`，搜索 `远程桌面`

![](https://pic1.zhimg.com/v2-c5ffbc80f758233f89d455b5cb0f87fc_b.jpg)

2、配置连接信息

![](https://pic2.zhimg.com/v2-92ea5c2403aa70f072ea05a413bd21d9_r.jpg)

3、运行连接，过程会有防火墙，同样允许就行

![](https://pic1.zhimg.com/v2-c6d8017c4b8eb1604973402b20536e6c_r.jpg)

4、连接到 Ubuntu

![](https://pic2.zhimg.com/v2-a6a556429a0e05df4cc5eac52de24071_r.jpg)

5、登录到 Ubuntu

![](https://pic3.zhimg.com/v2-3631b3fd799f7fd9c7634f995b97c0e6_r.jpg)

6、登录后看到桌面，有那味儿了

![](https://pic4.zhimg.com/v2-ff771af077844000224481c9bc576717_r.jpg)

7、打开本地的 windows 盘符，和终端看看

![](https://pic1.zhimg.com/v2-93b254fd761c15210eccd5747ed2efc4_r.jpg)

### Z.1.5. 三、其他技巧

### Z.1.6. 1、windows 的盘符在哪？

window 磁盘放在 `mnt` 目录下，比如，进入 win10 的 C 盘：

`cd /mnt/c`

两个系统原本是使用不同的文件系统，但是微软为了让两种系统文件可以相互访问，使用 WSL 解决方案。一般情况下，可以在两种系统间随意复制文件，但是也有一些问题：  
最常见的一个问题就是，Linux 系统是大小写严格的，Window 则对大小写不敏感。这就导致在一些 Linux 软件在 window 系统的盘符安装时，会出报错，后面会提到。  

### Z.1.7. 2、系统间复制文本

在一个系统复制文本后，在另一个系统右键即可粘贴文本

### Z.1.8. 3、安装 anaconda 报错

Exception: dst exists: '/mnt/f/Ubuntu/anaconda3/share/terminfo/e/eterm'

`/mnt` 是不区分大小写的文件系统（WSL 下的都不区分文件系统），所以必须将程序安装到区分大小写的文件系统上。两种解决方案：

* 保持默认设置，会自动安装到为家目录下  
    
* 设置安装 anaconda3 的目录区分大小写  
    

`sudo apt install attr setfattr -n system.wsl_case_sensitive -v 1 /mnt/f/Ubuntu/anaconda3`

### Z.1.9. 4、修改命令行界面字体及颜色

右键最上端的框，选择 `属性`

![](https://pic1.zhimg.com/v2-a7d0d3be06340e8c600867f26fbf34f4_b.jpg)