# Python

 - 下载地址：
 
支持Win7-32位：[python3.8.10 - https://www.python.org/downloads/release/python-3810/](https://www.python.org/ftp/python/3.8.10/python-3.8.10.exe)

最新版：[Win10以上 - https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

 - 教程[https://www.runoob.com/python3/python3-tutorial.html](https://www.runoob.com/python3/python3-tutorial.html)

## 1.安装
 1、下载Python进入软件安装界面，“Install Now”选项是软件默认安装选项，小编建议点击“Customize Installation”选择自定义安装。然后您可以勾选【Add Python to PATH】添加环境变量。
![](https://img.jbzj.com/file_images/article/202001/2020115103230553.png)
 2、把Optional Features全部勾选上，点击“Next"
![](https://img.jbzj.com/file_images/article/202001/2020115103230554.png)
 3、Advanced Options勾选2/3/4项，然后选择安装路径，点击”Install“，等待安装完成('add python to environment variables'环境变量)
![](https://img.jbzj.com/file_images/article/202001/2020115103230555.png)
 4、页面出现Successful字样，说明安装成功。
 5、按win+R，输入”cmd“，回车，输入”python“，如果能如下正常回显，则成功。
 
## 2.Python环境变量配置
 1、找到计算机，点击鼠标右键在弹出的选项中点击【属性】。
 2、然后点击【高级系统配置】。
 3、点击【环境变量】。
 4、在系统变量找到Path，双击在变量值末尾添加一个英文的分号";"，将python软件安装路径复制就可以了。'D:\python3'
 5、点确定,打开命令行，输入python，出现以下提示即为配置成功
 
```
如果Step1中未勾选下面的Add Python3.8 to PATH，安装成功后就需要配置环境变量。
因此通过我的电脑 - 属性 - 高级设置 - 环境变量 - 编辑Path - 新建（Win10）/直接添加路径，路径以分号隔开（Win7）。
```
 
## 3.其他

pip install --upgrade pip
`pip升级失败的时候，去目录C:\Users\Administrator\AppData\Local\Temp\pip-uninstall-inufijea下面复制pip的3个文件到python安装目录下‘Scripts’文件夹里`
pip install requests
`遇到import requests问题`

# 将.py文件转换成.exe文件

### 一、使用pip安装PyInstaller

①python3.x需要使用PyInstaller才能进行转exe文件。

②在cmd命令行窗口，用命令pip install pyinstaller安装。

### 二、将.py文件转换成.exe文件
① PyInstaller命令输入参数：

-F 生成单个可执行文件
-w 去掉控制台窗口
-p 自定义需要加载的类路径
-i 可执行文件的图标，其后面可以加上图片的路径
②转到.py文件所在目录，使用PyInstaller命令打包exe文件（F:/main.py是需要转换的py文件的路径）
  pyinstaller -F main.py
  1）准备好需要转换的.py文件
  2）.py文件所在的目录打开cmd，（转到这个目录下的话，生成exe文件时会直接保存到这个目录下）
  3）使用命令pyinstaller -F main.py -w，转换成功。
  4）在目录下，会多出3个文件夹，dist文件夹下即为转换好的.exe文件
  
总结命令

Pyinstaller -F main.py 打包exe

Pyinstaller -F -w main.py 不带控制台的打包

Pyinstaller -F -i xx.ico main.py 打包指定exe图标打包

平常我们只需要这三个就好了，足够满足所有需求了。
  
*注：如果不转换目录，默认生成后的.exe文件在 C:\Users\Administrator\dist\目录下。如下面的步骤所示。
*输入命令，打包成功，显示打包好的exe文件在 C:\Users\Administrator\dist\main.exe 目录下。
*在C:\Users\Administrator\dist\目录下，看到成功打包好的exe文件，成功！！！
![](https://img-blog.csdnimg.cn/20210831011041721.png)  