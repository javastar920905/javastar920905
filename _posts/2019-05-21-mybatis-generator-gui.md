---
layout: post
title: mybatis-generator界面工具
date: 2019-05-21
tag: mybatis
---

mybatis-generator界面工具，让你生成代码更简单更快捷

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


## 针对spring boot 手脚架进行定制 [spring-boot-api-project-seed](https://github.com/java-frame/spring-boot-api-project-seed)
* [x] 自定义修改完成 [查看github  spring-boot-api-project-seed分支](https://github.com/javastar920905/mybatis-generator-gui/tree/spring-boot-api-project-seed) 
* [x] 添加生成controller和service 代码的功能  
* [x] 完善生成代码注释 [目录结构分析](http://localhost:3000/#/books/3.java/java_gui)

```
1 找到生成代码入口 MainUIController#generateCode
GeneratorConfig generatorConfig = getGeneratorConfigFromUI(); 从ui界面获取到的配置 保存在GeneratorConfig对象中

2 在 MybatisGeneratorBridge#generate 读取配置的属性,添加生成自定义代码功能

```