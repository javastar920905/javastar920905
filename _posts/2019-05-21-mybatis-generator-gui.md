---
layout: post
title: mybatis-generator界面工具
date: 2019-05-21
tag: mybatis
---

mybatis-generator界面工具，让你生成代码更简单更快捷

如果你用的是idea 进行开发,更加推荐 EasyCode插件 [EasyCode 个人有道云笔记总结 配置备份](http://note.youdao.com/noteshare?id=1602e6bf67f66b7df774a78a0eb61076&sub=07E9AE76FFDE49088BB2A6BEF96304C7)


## gui界面工具加载
* [点击直接下载构建好的工具](https://javabus.oss-cn-beijing.aliyuncs.com/mybatis-generator-gui.jar)
* 或者自助构建  [github 地址](https://github.com/javastar920905/mybatis-generator-gui)
```
  git clone https://github.com/zouzg/mybatis-generator-gui
  cd mybatis-generator-gui
  mvn jfx:jar
  cd target/jfx/app/
  java -jar mybatis-generator-gui.jar
```

## 使用教程
* [查看Wiki教程]  [有道云总结](http://note.youdao.com/noteshare?id=67cc459245c8d1390700f96381ca3f9d&sub=4DC8E9A1697C4B6690E0907659037FEA)(https://github.com/zouzg/mybatis-generator-gui/wiki/Usage-Guide)
  * 配置数据源
  * 配置项目信息 (项目所在目录,实体类包名,Mapper接口包名)

<img src="/images/posts/mybatisgui/mybatis_gui.png"   >  


## 针对spring boot 手脚架进行定制 
> 改源码: 想加一个生成controller和service 代码,同时集成通用mapper的功能
* [x] 项目结构分析,完善项目代码注释
* [x] 添加生成controller和service 代码的功能  
* [x] 基于spring boot 手脚架项目进行自定义修改 [查看github  spring-boot-api-project-seed分支](https://github.com/javastar920905/mybatis-generator-gui/tree/spring-boot-api-project-seed) 

```
1 找到生成代码入口 MainUIController#generateCode
GeneratorConfig generatorConfig = getGeneratorConfigFromUI(); 从ui界面获取到的配置 保存在GeneratorConfig对象中

2 在 MybatisGeneratorBridge#generate 读取配置的属性,添加生成自定义代码功能

```

## 基于自定义模板ftl 生成controller, service
> 通过修改源码,添加了功能: 基于自定义模板ftl 生成controller, service ,mybatis 代码 (只计划维护 mysql数据库)

本工具发布jar 包和 exe 形式 (大小和方便程度,供用户选择): 
* [jar包方式 需要命令行启动 java -jar mybatis-generator-gui.jar -13MB](https://javabus.oss-cn-beijing.aliyuncs.com/code-gen-gui-jar.zip)
* [双击启动exe 文件方式 - 100MB](https://javabus.oss-cn-beijing.aliyuncs.com/code-gen-gui-jar.zip)
* [github 地址](https://github.com/javastar920905/mybatis-generator-gui/tree/gen-controller-service-mybatis)  查看 **gen-controller-service-mybatis** 分支
 
自定义ftl模板说明,请查看解压后的 readme.txt