---
layout: post
title: 经验技术 - Legacy和UEFI装机方法
date:   2022-06-09 
tags: [经验技术]
categories: 经验技术
img: 
---

* content
{:toc}


# Legacy和UEFI装机方法

---

###名词介绍：

BIOS，全称"Basic Input Output System"，中文名称"基本输入输出系统"。

UEFI，全称"Unified Extensible Firmware Interface"，中文名称"统一的可扩展固件接口"。

GPT分区，全称"GUID Partition Table"，中文名称"全局唯一标识磁盘分区表"。

MBR分区，全称"Master Boot Record"，中文名称"主引导记录"。

<!--more-->

---

Legacy : 32+64位系  +  MBR模式

BIOS+MBR模式：（Legacy+MBR）
1、这种启动模式兼容性较好
2、可以安装32位和64位系统
3、硬盘分区最大支持支持2TB
4、理论支持安装Windows所有版本的系统；

---

UEFI : 	64位系统  +  GPT模式

UEFI+GPT模式：
1、只能安装64位系统
2、硬盘分区最大支持18EB，基本上算是无限大
3、启动速度更快
4、为用户提供更高级的图形界面
5、支持鼠标使用
6、安全启动，防止在启动前环境中运行的恶意软件和rootkit
7、提供独立于CPU架构的模块化接口，也为基于EFI驱动程序（称为EBC-EFI字节码）的应用和设备提供模块化接口
8、能够与BIOS并行运行
9、理论仅支持win8以上的操作系统

---

UEFI 转 Legacy ( WIN10 x64 换 Win7 x64 )

win10更换win7的方法的两个步骤：

  （1）.设置BIOS支持Legacy启动:
	进入"Security" — "Secure Boot",将其设为Disabled;
	Lunch CSM选项设为Enabled;
	启动模式Boot Mode[UEFI/Legacy]设置为Legacy模式。

  （2）.将硬盘的分区表类型由GUID变为MBR模式。(Disk Genius软件，右键硬盘 GPT to MBR)
  
---

Legacy 转 UEFI （UEFI下安装WIN7 x64）

在我们解决安装uefi安装win7卡在正在启动windows界面前大家分析一下uefi装win7要注意的一些事项：

我们在安装win7系统时，如果采用的uefi模式，默认csm兼容模式是开启不了的，只有当设置为legacy模式，csm兼容模式才可以开启，那么不开启的代价就是会一直卡在"启动windows界面或安装程序正在更新注册表设置"界面，直到安装了win7显卡驱动后才可能进入桌面，那么问题来了，如果是原版系统肯定就没有集成win7显卡驱动，所要以采用本站提供的WIN7系统。

1、现在2020新主板大部分品牌主板不支持传统模式了，只能在uefi模式下安装win7，注意uefi模式下无法开启兼容模式也没有选项开启，所以在安装win7时需要采用本站自带的镜像或提前注入usb驱动和集显驱动，要不然在安装win7时会卡在启动画项一直进不了系统。

2、需要注意在bios中"关闭安全启动"(secure boot control为Disable;)。

3、uefi模式安装win7注意只能采用64位操作系统。

4、uefi模式安装win7分区类型要采用gpt分区(Disk Genius软件，右键硬盘MBR or GPT)。

5、uefi模式安装win7时，如果有csm选项的情况建议一定要开启(Lunch CSM选项设为Enabled)，特别是独立显卡的机器。

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@UEFI+GPT分区安装Windows7@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

UEFI+GPT分区安装Windows7 

虽然 Windows 7 已经停止了技术支持，虽然六代以后的 Intel CPU 也不再支持 Windows 7 了，但是 Windows 7 依然有着广泛的受众。

2020年了为什么还要装Win7？

?
都2020年了，为什么还有人会无脑吹win7比win10好用？?
某乎的沙雕问题,在某乎上，总有一些奇奇怪怪的人（一般都是无脑的小学生），提出一些引战类的问题。每个人需求不同，这种人忽略掉就行了。

Windows 7 目前依旧适合很多人群：
?对于中年人日常办公支持很好，学习成本低并且稳定；
?对于打印机、老版工业软件、较老驱动的支持也很好；
?对于程序员，虚拟机跑一些过时软件；
?等等…

除此之外，Windows 7 还有一些独到的优势：
?对于老旧电脑、机械硬盘电脑、少内存的电脑很友好；
?对于主流软件依旧支持最新版，Office 365 依然支持；
?对于新设备依旧兼容良好，比如无线/蓝牙鼠标，新格式U盘；
?基本上没有 Windows Update 更新了，免打扰；
?Microsoft Security Essentials 依旧能够保护 Windows 7；
?好看！好看！好看！
?等等…

为什么要用UEFI+GPT安装？

可能有人会问，为什么要用 UEFI + GPT 安装 Win7，而不用 Legacy + MBR 安装呢？当然是因为好看啊！你不觉的把 BIOS 改成 Legacy 后，启动画面会变难看吗，左上角有个 _ 光标一直在闪，完全没有 UEFT 启动只有个 Logo 下方有个圈圈再转的这样子好看嘛~

还有个原因是，今天的主角是我淘汰了的 DELL Inspiron 7537，这台机器是 四代 Intel Haswell，预装的是 Windows 8 操作系统，原生支持 UEFI。

---

下面开始安装步骤：

前置条件
?CPU 必须是第六代 Intel Skylake，以及之前。从第七代 Intel Kaby Lake 之后便不再支持 Windows7；
?UEFI Windows 7 只能安装 x64；
?电脑主板支持 CSM 或者支持 Legacy + UEFI 混合启动模式，一般 Skylake 以及之前的电脑主板都支持；

注意，以上条件并不是刚性的，因为部分情况可以通过 命令行、CGI-Plus、手动引导、手动写入驱动等，解决一部分电脑的问题。

Windows 7 64 版本原生支持 UEFI 安装，但是有限制

安装前的准备工作

首先我们需要下载 64 位的 Windows 7 和 Windows 8 操作系统。对，必须是 64 位，必须是两个系统镜像都要下载：

Windows 7 (旗舰版) 下载最后版本的镜像：

Windows 8 下载第一个版本的镜像：
 
下载完毕后，用 Rufus 写入 Win7 镜像到 U盘中，用 FAT32 格式、UEFI 模式。

写入完成后，载入 Win8 的镜像，将 \efi\boot\bootx64.efi 这个文件拷贝出来，放到 Win7 写好的U盘相同路径中覆盖即可。

BIOS 的设置

首先先进入 BIOS，需要在 boot 选项下把 CMS 打开，然后新增的选项全选成 UEFI。对于没有 CMS 选项的 (比如 DELL Inspiron 7537)，寻找一个叫 Legacy + UEFI 混合模式的选项。然后，再把安全启动 Security Boot 选项关闭。

---

接下来就可以尝试安装的，但是你可能会遇到一些问题：

问题一：U盘启动后，卡在 Win7 启动 Logo 的地方了，而且 Win7 Logo 也不动了？

再次进入 BIOS，把 Intel 快速启动、Intel 快速存储技术 这两个选项先禁用。等到安装完成了再打开。

问题二：选择U盘启动后，卡在 Win7 启动 Logo 的地方了，但是 Logo 还在动？

这种情况你只需要等待即可，我当时等了有是十多分钟了吧，才进入安装进程的。

之后，你应该顺利的进入 Win7 的安装过程，在选择磁盘的时候，他会警告你你正在使用 GPT分区表，直接忽略它继续安装即可。




























