---
layout: post
title: GFW - Github连接访问的几种方法
date:   2022-03-29 
tags: [github,GFW]
categories: github
img: 
---

* content
{:toc}


# 1.镜像站点

*这几个网站是整站访问的替代品，你可以浏览项目，也支持下载检出。

*但是不建议登陆自己的账号，毕竟不是直接访问到原站.

### - hub -

1. [https://hub.fastgit.xyz](https://hub.fastgit.xyz/)

2. [https://hub.gitfast.tk](https://hub.gitfast.tk)

3. [https://hub.verge.tk](https://hub.verge.tk)

4. [ProGo.cc  - GitHub链接 - 加速访问](https://www.progo.cc/#/)

5. [GitHub 加速下载 - toolwa.com](http://toolwa.com/github/)

### - raw -

1. [https://raw.gitfast.tk](https://raw.gitfast.tk)

2. [https://raw.gitslow.tk](https://raw.gitslow.tk)

3. [https://raw.verge.tk](https://raw.verge.tk)

* * *

# 2.文件中转加速下载

- 该方案利用Cloudflare Workers对 release以及项目文件进行加速，部署无需服务器。

- 如果对自建感兴趣，可以访问gh-proxy。
1. [https://ghproxy.com/](https://ghproxy.com/)

2. [https://gh.api.99988866.xyz/](https://gh.api.99988866.xyz/)

3. [https://mirror.ghproxy.com/](https://mirror.ghproxy.com/)

4. [ProGo.cc - GitHub链接 - 加速访问](https://www.progo.cc/#/)

5. [GitHub 加速下载 - toolwa.com](http://toolwa.com/github/)

* * *

# 3.Raw加速

- jsDelivr不支持exe文件下载，使用方法参考例子
1. [https://raw.sevencdn.com/](https://raw.sevencdn.com/) 替换掉 [https://raw.githubusercontent.com/](https://raw.githubusercontent.com/)

2. [https://raw.githubusercontents.com/](https://raw.githubusercontents.com/)在网址后面加个"s"  - [https://raw.githubusercontent"s".com/](https://raw.githubusercontent"s".com/)

3. https://cdn.jsdelivr.net/gh/你的用户名/你的仓库名@发布的版本号/文件路径

eg. https://cdn.jsdelivr.net/gh/lion12776/kejilion@main/v2ray

* * *

# 4.油猴脚本 - ☆☆☆

- [Github 增强【脚本】 - github/XIU2/](https://greasyfork.org/zh-CN/scripts/412245) - 脚本页里有好多镜像站

---

# 5.Hosts
简单粗暴的使用方法
手动添加hosts

访问 [https://hosts.gitcdn.top/hosts.txt](https://hosts.gitcdn.top/hosts.txt) ， 将其全部内容粘贴到你的hosts文件中，即可。

Linux / MacOS hosts路径：/etc/hosts
Windows hosts路径：C:\Windows\System32\drivers\etc\hosts

fetch-github-hosts是主要为解决访问Github过慢或其他问题而提供的免费的Github hosts同步服务，项目开源

Fetch Github Hosts：[http://hosts.gitcdn.top/](http://hosts.gitcdn.top/)

开源仓库：[https://github.com/Licoy/fetch-github-hosts](https://github.com/Licoy/fetch-github-hosts)

---

[Github RAW 加速服务 - 7ED Service](https://www.7ed.net/gra/) - 大佬访问github的方法https://www.7ed.net/gra/
