---
layout: post
title: 使用jekyll创建博客
date: 2020-05-26 00:40:00 
tag: 工具
---

本教程会使用一系列技术栈,教你免费云端开发部署一个个人博客

> * 首先我们会先注册一个 cloud studio 账号,使用云开发环境完成环境搭建
> * 根据 jekyll  中文文档 完成 ruby 环境的安装
> * 启动博客系统,开始编写博客

## 工具准备
* [注册腾讯云开发者平台- coding dev ops](https://dev.tencent.com/login) 微信登录即可
  * 平时可以使用 任务看板 安排自己的计划
  
* 使用命令行推送已存在的仓库
  * [访问 cloud studio 主页](https://javabus.cloudstudio.net/dashboard/workspace)
  * 新建工作空间,选择ubuntu 18.x 运行环境(以前有现成的jekyll环境,现在没有了)
  * 选择克隆一个已有的仓库 https://gitee.com/javastar920905/javastar920905.git

* 同时推送到 github 和 gitee  代码仓库 
  ```
  # 使用 gitee 作为国内源,方便日常访问提速
  git remote set-url --add --push origin https://gitee.com/javastar920905/javastar920905.git 
  # 使用 github  做主要代码库 
  git remote set-url --add --push origin https://github.com/javastar920905/javastar920905.git
  # git remote -v  查看配置结果
  git config --global credential.helper store  记住接下来的用户名和密码
  git push 
  ```
  

## 安装 Jekyll (需要Ruby 开发环境,Jekyll 是基于 Ruby 开发的)
 * 参考jekyll 中文文档  https://www.jekyll.com.cn/docs/
  ```
   //1 安装 ruby 环境
   sudo apt-get install ruby-full build-essential zlib1g-dev # Debian 或 Ubuntu 系统
   //2 配置命令
   vim  ~/.bashrc
        # Install Ruby Gems to ~/gems
        export GEM_HOME="$HOME/gems"
        export PATH="$HOME/gems/bin:$PATH"
   source ~/.bashrc

   //3 安装 jekyll  耗时挺久的 5min+
   gem install jekyll bundler
   gem install bundler --version '1.17.2'

   //4 更换为国内源 (bundler就像java 里面的 maven 和 gradle,js 的 npm)
   gem sources -l 
   gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
   bundler install  报错了 can't find gem bundler (>= 0.a) with executable bundler
   解决办法：
　　gem uninstall bundler
　　gem install bundler --version '1.17.2'
   然后重新运行命令 bundler install 

   // 5 构建网站并启动一个本地服务器。
   bundle exec jekyll serve
   以后只需要在_post 目录下编写markdown博客即可        
  ```

##  部署项目到gitee pages
```
   进入到你的博客,所在代码仓库
   代码浏览,选择"服务"菜单,开启gitee pages服务,等待代码构建完成
   [查看演示博客](https://javastar920905.gitee.io)
   如果下次push的代码没有生效,可以在pages服务页面 点击刷新按钮(一般有几分钟的延迟)
```
congratulation! 博客搭建完成. 以后就可以继续使用cloud studio 进行写博客了


## 尝试自己修改博客样式
- [x] 查看项目readme 熟悉目录结构
- [ ] 修改成自己喜欢的样式

## Markdown 教程
[cmd Markdown](https://www.zybuluo.com/mdeditor) 作业部落出版的Markdown编辑器 


 * 之前版本的教程(可忽略) 
 ```
  进入工作空间 运行以下命令
  wget https://javabus.oss-cn-beijing.aliyuncs.com/jekyll-blog.zip 获取博客模板
  apt-get install zip unzip 安装unzip 软件
  解压文件 unzip -o jekyll-blog.zip
  git remote -v 检查推送地址
  git add * && git commit -m "blog init" 
  git config --global credential.helper store  记住接下来的用户名和密码
  git push 
```  

<br>

参考文档：
[jekyll  中文文档](https://www.jekyll.com.cn/docs/) » [点击阅读原文](https://www.jekyll.com.cn/docs/installation/)  

[Gemfile 入门-类似maven pom.xml依赖定义](https://www.jekyll.com.cn/docs/ruby-101/)