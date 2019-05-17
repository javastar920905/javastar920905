---
layout: post
title: 使用jekyll创建博客
date: 2019-05-07 23:01:00 
tag: 工具
---

本教程会使用一系列技术栈,教你免费云端开发部署一个个人博客

## 工具准备
* [注册腾讯云开发者平台- coding dev ops](https://dev.tencent.com/login) 微信登录即可
  > * 修改唯一用户名(如: linying1223)
  > * 使用新建项目,部署时url就是 username.coding.me 
  > * 平时可以使用 任务看板 安排自己的计划
  
* 使用命令行推送已存在的仓库
  > * [访问 cloud studio 主页](https://studio.dev.tencent.com/dashboard/workspace)
  > * 新建工作空间,选择jekyll 运行环境
  > * 进入工作空间 运行以下命令
  > * wget https://javabus.oss-cn-beijing.aliyuncs.com/jekyll-blog.zip 获取博客模板
  > * apt-get install zip unzip 安装unzip 软件
  > * 解压文件 unzip -o jekyll-blog.zip
  > * git remote -v 检查推送地址
  > * git add * && git commit -m "blog init" 
  > * git config --global credential.helper store  记住接下来的用户名和密码
  > * git push 

* 部署项目到coding pages
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

## 尝试自己修改博客样式
- [x] 查看项目readme 熟悉目录结构
- [ ] 修改成自己喜欢的样式

## Markdown 教程
[cmd Markdown](https://www.zybuluo.com/mdeditor) 作业部落出版的Markdown编辑器 



<br>

参考文档：[javabus.cn](http://javastar920905.coding.me/mdbook/) » [点击阅读原文](https://javabus.cn/#/books/1.enjoy/1.3jekyll)  
