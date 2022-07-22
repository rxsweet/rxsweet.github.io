---
layout: post
title: 经验技术 - 4.Jekyll的search免插件使用
date:   2022-03-30 
tags: [经验技术]
categories: 经验技术
img: 
---

* content
{:toc}

## Jekyll个人博客实现搜索功能

本来这个博客是没有搜索功能的，随着博客文档数越来越多，那么如果我想搜索某个博客重新回顾学习一下，那可是很糟糕的体验呀，所以个人博客有搜索功能是必不可少的。

到网上一搜，发现资料还是挺少的，而且都还不一定能实现，这搜索结果还是挺让人失望的。下面就来看看我是如何实现在jekyll个人博客的基础上来现实搜索功能吧。

<!--more-->

# 初步介绍思路

首先我是参考的Github上的一个开源库[Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search)

通过这个库的README可以知道，是可以实现搜索功能的，所以，我们就用这个库来实现吧。

先下载这个仓库到本地

```
https://github.com/christian-fei/Simple-Jekyll-Search  
```

# Step 1. 创建search.json文件

在个人博客的根目录下创建一个`search.json`的文件，然后打开下载的文件夹目录`Simple-Jekyll-Search/example/`，复制里面的`search.json`的代码到这个文件。

下面是search.json文件内容(可以直接新建`search.json`复制下面内容)：

```
{% raw %}
---
layout: none
---
[
  {% for post in site.posts %}
    {
      "title"    : "{{ post.title | escape }}",
      "category" : "{{ post.category }}",
      "tags"     : "{{ post.tags | join: ', ' }}",
      "url"      : "{{ site.baseurl }}{{ post.url }}",
      "date"     : "{{ post.date }}"
    } {% unless forloop.last %},{% endunless %}
  {% endfor %}
]
{% endraw %}
```

# Step 2. 复制js文件到js目录下

打开之前下载的`Simple-Jekyll-Search/example/js/`目录，发现会有两个js文件，一个是`simple-jekyll-search.js`和`simple-jekyll-search.min.js`。先别管这两个文件是什么内容了，直接复制到自己博客根目录下的`/js/`下。

# Step 3. 在主页和菜单栏分别添加搜索功能

## 主页添加搜索功能
在`index.html`文件里找到自己想添加的位置，粘贴下面代码:
```
<!--添加搜索框开始-->
<div class="side">
	<div>
		<i class="fa fa-tags"></i>
		Search
	</div>
	<div class="tags-cloud">
		<!-- HTML elements for search 搜索元素-->
		<input type="text" id="search-input" placeholder="搜索-标题/Tags..." style="width:230px;"/>
		<ul id="results-container"></ul>

		<!-- script pointing to jekyll-search.js -->
		<script src="/js/simple-jekyll-search.min.js"></script>

		<script>
		SimpleJekyllSearch({
		searchInput: document.getElementById('search-input'),
		resultsContainer: document.getElementById('results-container'),
		json: '/search.json',
		searchResultTemplate: '<li><a href="{url}" title="{desc}">{title}</a></li>',
		noResultsText: '没有搜索到文章',
		limit: 20,
		fuzzy: false
		})
		</script>
	</div>
</div>
<!--添加搜索框结束-->  
```

## 菜单栏添加搜索功能

### (1). 在菜单栏添加search

在page目录下添加`search.html`文件，并复制如下代码到该文件。

```
---
layout: page
title: search
permalink: /search/
icon: search
type: page
---


<!-- HTML elements for search -->
<input type="text" id="search-input" placeholder="搜索博客 - 输入标题/日期/Tags.." style="width:380px;"/>
<ul id="results-container"></ul>

<!-- script pointing to jekyll-search.js -->
<script src="/js/simple-jekyll-search.min.js"></script>

<script>
SimpleJekyllSearch({
    searchInput: document.getElementById('search-input'),
    resultsContainer: document.getElementById('results-container'),
    json: '/search.json',
    searchResultTemplate: '<li><a href="{url}" title="{desc}">{title}</a></li>',
    noResultsText: '没有搜索到文章',
    limit: 20,
    fuzzy: false
  })
</script>

```

### (2).下面是老版jekyll我在菜单栏添加搜索一栏

修改`_includes/sidebar.html`内容，添加一行。
```
<li class="menu-items"><a class="menu-links" href="{{site.baseurl}}/search/">search</a></li>
```

### (3). search功能添加完成

这部分也就是搜索的主要核心代码了。到此，搜索功能也就完成了。

P.S. 以上部分Liquid代码，为了不被jekyll执行，需要用`{% raw %} and {% endraw %}`包起Markdown语法。

---

原文作者地址：
[https://zoharandroid.github.io/2019-08-01-jekyll个人博客实现搜索功能/](https://zoharandroid.github.io/2019-08-01-jekyll个人博客实现搜索功能/)

[https://github.com/princeliebe/princeliebe.github.io](https://github.com/princeliebe/princeliebe.github.io)
