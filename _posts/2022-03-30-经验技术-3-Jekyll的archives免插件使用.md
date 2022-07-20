---
layout: post
title: 经验技术 - 3.Jekyll的archives免插件使用
date:   2022-03-30 
tags: [经验技术]
categories: 经验技术
img: 
---

* content
{:toc}

# Jekyll的archives免插件使用

### Post Archives

按照站点选择的方式或主题不同而各有异同。

<!--more-->

主要的语法是：

#### archives.html 文件

通常`archives.html`文件会放在站点根目录下方便访问和放置。它的主要内容是：

```
{% raw %}

{% for post in site.posts %}
  {% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
    {% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
        {% if month != nmonth %}
              {% if forloop.index != 1 %}</ul>{% endif %}
                    <h5>{{ post.date | date: '%B %Y' }}</h5><ul>
                        {% endif %}
                          <li><span class="time">{{ post.date | date: "%d/%m/%Y" }}</span>    <a href="{{ post.url }}">{{ post.title }}</a></li>
                          {% endfor %}
                          
{% endraw %}                     
```

`archives.html`中包含YAML头信息格式：
```
---
layout: default
title: 
author: RXsweet
comments: false
published: true
---
```
或使用个人使用YAML头信息格式：
```
---
layout: post
title: archives
permalink: /archives/
---
```

文件的作用就是按时间为分类list post。那么，我们需要在某个或某些页面放置一个链接，方便访问。以本站点为例，这个链接放置在侧栏中：

```
<li class="sidebar-nav-item"><a href="{{ site.baseurl }}/archives/">Posts Archives</a></li>

```

或者，有时你需要在主页上放置一个链接，例如：

```
{% raw %}
{% if page.archives %} <a href='{{ site.baseurl }}{{ page.archives }}'> Posts</a>{% endif %}
{% endraw %}
```

根据站点的实际情况进行修改即可。

P.S. 以上部分Liquid代码，为了不被jekyll执行，需要用{% raw %}and{% endraw %}包起Markdown语法。

---

原文作者地址：
[https://soyee.me/2018/03/22/website-note/](https://soyee.me/2018/03/22/website-note/)
[https://github.com/princeliebe/princeliebe.github.io](https://github.com/princeliebe/princeliebe.github.io)
