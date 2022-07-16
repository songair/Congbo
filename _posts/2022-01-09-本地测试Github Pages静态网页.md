---
layout: mypost
title: 本地测试Github Pages静态网页
categories: [Github]
---

### 安装Jekyll并开启本地服务

* 打开terminal，进入repo文件夹里：`cd /Documents/GitHub/"repo name"/`
* 检查是否有Ruby 2.1.0 以上版本：`ruby -v`
* 如果没有Ruby的话可以打开这个[链接](https://www.ruby-lang.org/zh_cn/documentation/installation/)安装ruby
* 然后安装Bundle：`gem install bundler`
* Pages主题文件里面应该有Gemfile文件。如果将来需要安装什么Jekyll的插件，可以在这个文件里加入：gem “plugin_name”。
* 然后安装Jekyll：`bundle install`

### 生成网页

* 在repo文件夹里运行：`bundle exec Jekyll serve`来在本地生成你的网页。
* 可以在浏览器里面输入`localhost:4000`浏览网页。

### 参考

<https://dlsong.com/tech/jekyll/>
