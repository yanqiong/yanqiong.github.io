---
layout: post
title:  "在 Jekyll 中添加分页"
date:   2016-3-14 14:00:00 +0800
categories: jekyll pagination
---

## 在 Jekyll 中添加分页

### 安装 gem 插件

    sudo gem install jekyll-paginate

### 开启 paginate

在配置文件 \_config.yml 中添加以下配置项：

    gems: [jekyll-paginate]

    paginate: 5  
    paginate_path: "page:num"

第一行 ： 因为我们的配置文件 \_config.yml 使用了 paginate 配置项，所以添加 gem 的 jekyll-paginate插件。

第二行 ： 每页文章数量。

第三行 ： 分页页面路径配置。

### 使用分页

在首页（index.html）中使用

{% highlight html %}
{% raw %}
{% for post in paginator.posts %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}
       {{ post.categories | array_to_sentence_string  }}

    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h2>
  </li>
{% endfor %}
{% endraw %}
{% endhighlight %}

**使用时请去掉转义字符 \% => % , \{ => { , \} => }**

### 换页栏

paginator 对象

| 属性 | 说明 |
|---|---|
| page | 当前页码  |
| per_page | 每页文章数量 |
| posts | 当前页的文章列表 |
| total_posts | 总文章数 |
| total_pages | 总页数 |
| previous_page | 上一页页码 或 nil |
| previous_page_path | 上一页路径 或 nil |
| next_page | 下一页页码 或 nil |
| next_page_path | 下一页路径 或 nil |

*注意，[TODO] 记得修改表格样式*

{% highlight html %}
{% raw %}
{% if paginator.total_pages > 1 %}
  <div class="pagination">
    {% if paginator.previous_page %}
      <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a>
    {% else %}
      <span>&laquo; Prev</span>
    {% endif %}

    {% for page in (1..paginator.total_pages) %}
      {% if page == paginator.page %}
        <em>{{ page }}</em>
      {% elsif page == 1 %}
        <a href="{{ '/index.html' | prepend: site.baseurl | replace: '//', '/' }}">
          {{ page }}
        </a>
      {% else %}
        <a href="{{ site.paginate_path | prepend: '/' | replace: '//', '/' | replace: ':num', page }}">
          {{ page }}
        </a>
      {% endif %}
    {% endfor %}

    {% if paginator.next_page %}
      <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a>
    {% else %}
      <span>Next &raquo;</span>
    {% endif %}
  </div>
{% endif %}
{% endraw %}
{% endhighlight %}

**注意： 目前的根路径是 / ， site.baseurl 使用起来有问题**

**raw & endraw 暂时性的禁用的标签的解析**


## 在 Jekyll 中添加分类
