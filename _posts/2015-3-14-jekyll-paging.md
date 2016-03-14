---
layout: post
title:  "在 Jekyll 中添加分页"
date:   2015-3-14 14:00:00 +0800
categories: jekyll pagination
---

## 安装 gem 插件

    sudo gem install jekyll-paginate

## 开启 paginate

在配置文件 \_config.yml 中添加以下配置项：

    gems: [jekyll-paginate]

    paginate: 5  
    paginate_path: "page:num"

第一行 ： 因为我们的配置文件 \_config.yml 使用了 paginate 配置项，所以添加 gem 的 jekyll-paginate插件。

第二行 ： 每页文章数量。

第三行 ： [TODO]

## 使用分页

在首页（index.html）中使用，添加以下代码：


## 换页栏
