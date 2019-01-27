---
title: Hexo使用NexT主题配置评论系统
tags:
  - hexo
  - next
categories:
  - 建站
abbrlink: e5c0ece1
date: 2019-01-22 15:27:06
---

## 使用next主题，配置评论系统

next内置集成多种评论系统，通过简单的设置即可让网站增加评论功能，目前支持以下几种

{% code %}
# Disqus
# Changyan
# Valine
# LiveRe
# Gitment
# Gitalk
{% endcode %}
<!-- more -->

我这里使用Disqus评论系统，到 https://disqus.com 网站注册账号，然后按提示一步步下来即可，注意申请时的shortname
申请完成后，打开next主题下的_config.yml文件，找到

{% code %}
disqus:
  enable: false
  shortname: #填写申请到的shortname
  count: true
  lazyload: false
{% endcode %}

将enable改为true, shortname填上之前申请时生成的shortname，网站的disqus评论功能就可以使用了。


## 关闭自建page的评论功能

通过上面步骤设置完disqus评论后，发现除了“首页”以及“归档”两个系统自带的模块外，其它自建的页面（如：标签,分类)都可以直行评论，这并不符合实际需求，所以需要单独关闭这些page的评论功能

进入站点的source目录（hexo根目录下的source目录）然后找到对应的page目录，例如categories(分类),打开该目录下的index.md文件，在Front-matter处增加字段comments: false ,该页面的评论功能就被关闭了，以此类推，分别修改所有自建page即可
{%quote%}
title: 分类
date: 2019-01-22 12:31:13
type: categories
comments: false
{%endquote%} 


## 修改scaffolds文件夹下的page.md文件
修改scaffolds文件夹下的page.md文件，添加comments: false，这样以后所有新建的page默认都是关闭评论功能