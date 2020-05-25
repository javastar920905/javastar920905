---
layout: post
title: 使用jekyll创建博客
date: 2019-05-07 23:01:00 
tag: 工具
---

本教程会使用一系列技术栈,教你免费云端开发部署一个个人博客

> * 首先我们会先注册一个 cloud studio 账号,使用云开发环境完成环境搭建
> * 根据 jekyll  中文文档 完成 ruby 环境的安装
> * 启动博客系统,开始编写博客

## 工具准备
* [注册腾讯云开发者平台- coding dev ops](https://dev.tencent.com/login) 微信登录即可
  > * 修改唯一用户名(如: linying1223)
  > * 使用新建项目,部署时url就是 username.coding.me 
  > * 平时可以使用 任务看板 安排自己的计划
  
* 使用命令行推送已存在的仓库
  > * [访问 cloud studio 主页](https://javabus.cloudstudio.net/dashboard/workspace)
  > * 新建工作空间,选择nodejs 运行环境(以前有现成的jekyll环境,现在没有了)
  > * 选择克隆一个已有的仓库 https://gitee.com/javastar920905/javastar920905.git

* 同时推送到 github 和 gitee  代码仓库 
  ```
  # 使用 gitee 作为国内源,方便日常访问提速
  git remote set-url --add --push origin https://gitee.com/javastar920905/javastar920905.git 
  # 使用 github  做主要代码库 
  remote set-url --add --push origin https://github.com/javastar920905/javastar920905.git
  # git remote -v  查看配置结果
  ```
  

## 安装ruby 环境
  > * jekyll  中文文档  https://www.jekyll.com.cn/docs/

  ```
   //1 安装 ruby 环境
   sudo apt-get install ruby-full build-essential zlib1g-dev # Debian 或 Ubuntu 系统
   //2 配置命令
   vim  ~/.bashrc
        # Install Ruby Gems to ~/gems
        export GEM_HOME="$HOME/gems"
        export PATH="$HOME/gems/bin:$PATH"
   source ~/.bashrc

   //3 安装 jekyll
   gem install jekyll bundler

   //4 更换为国内源 (bundler就像java 里面的 maven 和 gradle,js 的 npm)
   gem sources -l 
   gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
   bundler install  # [Gemfile 入门-类似maven pom.xml依赖定义](https://www.jekyll.com.cn/docs/ruby-101/)

   // 5 构建网站并启动一个本地服务器。
   bundle exec jekyll serve        
  ```

##  部署项目到coding pages
  > * 返回注册腾讯云开发者平台>选择当前博客项目
  > * 代码浏览,开启pages服务,等待代码构建完成
  > * [查看演示demo](http://linying1223.coding.me)
  > * 如果下次push的代码没有生效,可以在pages服务页面 点击刷新按钮

congratulation! 博客搭建完成. 以后就可以继续使用cloud studio 进行写博客了

## 使用cloud studio 云环境写博客
* [直接打开 cloud studio ](https://studio.dev.tencent.com/dashboard/workspace)
  > * gem install jekyll bundler (安装 jekyll,gem 是ruby包管理工具)
  > * bundle install 
  > * chmod +x start.sh 
  > * ./start.sh 
  > * cloud studio 右侧添加访问链接,端口为3000 即可预览效果了
  > * 以后只需要在_post 目录下编写markdown博客即可
  > * 发现一个bug, 今天520 日期,精确到时分秒后,文章无法生成. [解决:保留到当前日期即可]

 * 之前版本的教程(可忽略) 
  > * 进入工作空间 运行以下命令
  > * wget https://javabus.oss-cn-beijing.aliyuncs.com/jekyll-blog.zip 获取博客模板
  > * apt-get install zip unzip 安装unzip 软件
  > * 解压文件 unzip -o jekyll-blog.zip
  > * git remote -v 检查推送地址
  > * git add * && git commit -m "blog init" 
  > * git config --global credential.helper store  记住接下来的用户名和密码
  > * git push 

## 尝试自己修改博客样式
- [x] 查看项目readme 熟悉目录结构
- [ ] 修改成自己喜欢的样式

## Markdown 教程
[cmd Markdown](https://www.zybuluo.com/mdeditor) 作业部落出版的Markdown编辑器 




<br>

参考文档：[jekyll  中文文档](https://www.jekyll.com.cn/docs/) » [点击阅读原文](https://www.jekyll.com.cn/docs/installation/)  
