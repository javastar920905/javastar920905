---
layout: post
title: springboot回顾之划重点
date: 2019-05-20
tag: springboot
---

spring boot 用了几年了,可是突然回想一下,我又说不出所以然.基础不扎实啊.
所以今天特意回顾一下spring boot,并且画出重点部分.

本文不是spring boot 入门教程,记录的目的是对spring boot的快速回顾. 如果没有使用过spring boot 的童鞋,请在下面参考文档中找入门教程资源.

## 参考文档
* [spring boot 系列资源](https://javastar920905.gitee.io/mdbook/#/books/3.java/2.spring)

因为上面文档列举了大量学习资源,所以可以直接使用别人比较系统的文档进行要点回顾

## 基础知识回顾
* 使用spring boot前后对比
  * 以前spring开发需要配置一大堆的xml,后来spring加入了annotaion，使得xml配置简化了很多，当然还是有些配置需要使用xml,比如申明component scan等
  * https://start.spring.io/ 直接就可以生成一个可以跑的spring boot项目
* 项目构建相关
  * [Spring Boot改变JDK编译版本](https://412887952-qq-com.iteye.com/blog/2291587)
* jdbc
  * 使用JdbcTemplate 
  * spring boot druid
  * spring boot mybatis
* mvc
  * 修改端口号 server.port=9090  server.servlet.context-path= /article
  * 全局异常捕获
  * [处理静态资源(默认资源映射)【从零开始学Spring Boot】](https://412887952-qq-com.iteye.com/blog/2292086)
  * [59. Spring Boot Validator校验【从零开始学Spring Boot】](https://412887952-qq-com.iteye.com/blog/2312356)
  * 使用模板（thymeleaf-freemarker）
  * HandlerInterceptor 拦截器
  * 集成shiro 
  * [Spring Boot之静态资源版本映射(解决js/css缓存问题)](https://412887952-qq-com.iteye.com/blog/2342354)
* 单元测试
  * [spring boot单元测试restfull API【从零开始学Spring Boot】](https://412887952-qq-com.iteye.com/blog/2306429)
* [监控 spring-boot-actuator](https://412887952-qq-com.iteye.com/blog/2293900)
* 中间件
  * [Spring Boot发送邮件【从零开始学Spring Boot】](https://412887952-qq-com.iteye.com/blog/2305992)
  * redis 
  * mq 
* spring boot 原理
  * [徒手撸一个 Spring Boot 中的 Starter ，解密自动化配置](https://www.javaboy.org/post/ff4f3baf.html) 
  * CommandLineRunner和ApplicationRunner 项目启动加载
  * @ConfigurationProperties 使用
  * [ Spring Boot轻松理解动态注入，删除bean【从零开始学Spring Boot】](https://412887952-qq-com.iteye.com/blog/2348445)

## 最后给大家带来一个520 彩蛋
* [520 表白神器](https://javastar920905.gitee.io/mdbook/lovestory.html)
  
  







