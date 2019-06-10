---
layout: post
title: springboot auth2
date: 2019-06-03
tag: springboot
---


## [OAuth 2.0 的一个简单解释-阮一峰的网络日志](http://www.ruanyifeng.com/blog/2019/04/oauth_design.html) 
### OAuth 2.0 是一种授权机制，主要用来颁发令牌（token）,授权机制设计如下
  * 案例为小区门禁系统, 居民小区就是储存用户数据的网络服务,
  * 快递员（或者说快递公司）就是第三方应用，想要穿过门禁系统，进入小区。
  * 我就是用户本人，同意授权第三方应用进入小区，获取我的数据。
  * OAuth 就是一种授权机制。数据的所有者告诉系统，同意授权第三方应用进入系统，获取这些数据。系统从而产生一个短期的进入令牌（token），用来代替密码，供第三方应用使用。
    > * 令牌（token）与密码（password）的作用是一样的，都可以进入系统，但是有三点差异。
    > * （1）令牌是短期的，到期会自动失效，用户自己无法修改。密码一般长期有效，用户不修改，就不会发生变化。
    > * （2）令牌可以被数据所有者撤销，会立即失效。以上例而言，屋主可以随时取消快递员的令牌。密码一般不允许被他人撤销。
    > * （3）令牌有权限范围（scope），比如只能进小区的二号门。对于网络服务来说，只读令牌就比读写令牌更安全。密码一般是完整权限。
    > * 注意，只要知道了令牌，就能进入系统。系统一般不会再次确认身份，所以令牌必须保密，泄漏令牌与泄漏密码的后果是一样的。 这也是为什么令牌的有效期，一般都设置得很短的原因

### [OAuth 2.0 颁发令牌的四种方式](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)
OAuth 2.0 对于如何颁发令牌的细节，规定得非常详细

> * 授权码（authorization-code）
> * 隐藏式（implicit）
> * 密码式（password）：
> * 客户端凭证（client credentials）

注意，不管哪一种授权方式，第三方应用申请令牌之前，都必须先到系统备案，说明自己的身份，然后会拿到两个身份识别码：客户端 ID（client ID）和客户端密钥（client secret）。这是为了防止令牌被滥用，没有备案过的第三方应用，是不会拿到令牌的。

* 1 授权码（authorization code）方式，指的是第三方应用先申请一个授权码，然后再用该码获取令牌。

这种方式是最常用的流程，安全性也最高，它适用于那些有后端的 Web 应用。授权码通过前端传送，令牌则是储存在后端，而且所有与资源服务器的通信都在后端完成。这样的前后端分离，可以避免令牌泄漏。

* 2 隐藏式

有些 Web 应用是纯前端应用，没有后端。这时就不能用上面的方式了，必须将令牌储存在前端。RFC 6749 就规定了第二种方式，允许直接向前端颁发令牌。这种方式没有授权码这个中间步骤，所以称为（授权码）"隐藏式"（implicit）。

* 3 密码式

如果你高度信任某个应用，RFC 6749 也允许用户把用户名和密码，直接告诉该应用。该应用就使用你的密码，申请令牌，这种方式称为"密码式"（password）。

* 4 最后一种方式是凭证式（client credentials）适用于没有前端的命令行应用，即在命令行下请求令牌。

### 令牌的使用
A 网站拿到令牌以后，就可以向 B 网站的 API 请求数据了。

此时，每个发到 API 的请求，都必须带有令牌。具体做法是在请求的头信息，加上一个Authorization字段，令牌就放在这个字段里面。

```
curl -H "Authorization: Bearer ACCESS_TOKEN"  "https://api.b.com"
```

上面命令中，ACCESS_TOKEN就是拿到的令牌。


### 更新令牌
令牌的有效期到了，如果让用户重新走一遍上面的流程，再申请一个新的令牌，很可能体验不好，而且也没有必要。OAuth 2.0 允许用户自动更新令牌。

具体方法是，B 网站颁发令牌的时候，一次性颁发两个令牌，一个用于获取数据，另一个用于获取新的令牌（refresh token 字段）。令牌到期前，用户使用 refresh token 发一个请求，去更新令牌。

```
https://b.com/oauth/token?
  grant_type=refresh_token&
  client_id=CLIENT_ID&
  client_secret=CLIENT_SECRET&
  refresh_token=REFRESH_TOKEN
```

上面 URL 中，grant_type参数为refresh_token表示要求更新令牌，client_id参数和client_secret参数用于确认身份，refresh_token参数就是用于更新令牌的令牌。

B 网站验证通过以后，就会颁发新的令牌。

## [第三方登录的原理](http://www.ruanyifeng.com/blog/2019/04/github-oauth.html)
很多网站登录时，允许使用第三方网站的身份，这称为"第三方登录"。 所谓第三方登录，实质就是 OAuth 授权。

> * A 网站让用户跳转到 GitHub。
> * GitHub 要求用户登录，然后询问"A 网站要求获得 xx 权限，你是否同意？"
> * 用户同意，GitHub 就会重定向回 A 网站，同时发回一个授权码。
> * A 网站使用授权码，向 GitHub 请求令牌。
GitHub 返回令牌.
> * A 网站使用令牌，向 GitHub 请求用户数据。

### spring boot oauth2
因为没有在项目中使用到spring boot Security 做权限校验框架,需要从头开始学习
[学习demo 托管在github](https://github.com/javastar920905/springboot-learn) 
- [x] spring boot 入门
- [x] spring boot Security 入门
- [ ] spring boot oauth2 项目中没有用到没有耐心学习下去啦,有需要的参考下面文档学习吧

## 参考文档
- [理解OAuth 2.0-阮一峰的网络日志](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html)
- [OAuth 2.0 的一个简单解释-阮一峰的网络日志](http://www.ruanyifeng.com/blog/2019/04/oauth_design.html) 
- [社区 Spring Security 从入门到进阶系列教程](http://www.spring4all.com/article/428) 推荐,作者文章给力
- [学习demo 托管在github](https://github.com/javastar920905/springboot-learn) 
- [springboot2整合oauth2](https://blog.csdn.net/qq_37170583/article/details/80704660)

