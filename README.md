# Jekyll 博客
* [Jekyll 搭建博客 总结文档](https://javastar920905.gitee.io/mdbook/#/books/enjoy/1.3jekyll)
## [目录结构介绍](http://jekyllcn.com/docs/structure/)
```
.
├── _config.yml 保存项目配置数据
├── _drafts     drafts（草稿）是未发布的文章。这些文件的格式中都没有
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes   
|   ├── footer.html
|   └── header.html (包含一些 百度统计等代码)
    └── side-panel.html (全屏首页/和左侧边栏)
├── _layouts    layouts（布局）是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。
|   ├── default.html  项目默认页面
|   └── page.html   点击左侧导航栏,跳转页面
    └── post.html   点击右侧_posts,进入博客详情页面
├── _posts      这里放的就是你的文章了。
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _site       一旦 Jekyll 完成转换，就会将生成的页面放在这里
├── .jekyll-metadata
└── index.html /blog 页面
```
* 修改_config.yml 需要重启项目才生效
* side-panel.html 为全屏首页/和左侧边栏
* pages url 要以/xxx/ 开头和结尾
* 跳转到博客列表 url为 /#blog
* 新建post 文件名尽量别用中文, 文件格式很重要，必须要符合: YEAR-MONTH-DAY-title.MARKUP
* 用标签  {% include file.ext %} 来把文件 _includes/file.ext 包含到布局或者文章中

### 使用条件
* Jekyll 支持 Mac 、Windows、ubuntu 、Linux 操作系统                     
* Jekyll 需要依赖：Ruby、bundler

# 使用leopard 博客模板
[leopard](http://baixin.io) 是一个简洁的博客模板，如果你也喜欢请帮 Star ， 谢谢 😄.

### 提示

>* 如果你想使用我的模板，请把 _posts/ 目录下的文章都去掉。
>* 修改 _config.yml 文件里面的内容为你自己的个人信息。

如果在部署博客的时候发现问题，可以直接在[Issues](https://github.com/leopardpan/leopardpan.github.io/issues)里面提问。        


### 把这个博客变成你自己的博客

根据上面【提示】修改过后，在你的github里创建一个username.github.io的仓库，username指的值你的github的用户名。      
创建完成后，把我的这个模板使用git push到你的username.github.io仓库下就行了。
搭建博客如果遇到问题可以看看我教程[Jekyll搭建个人博客](http://baixin.io/2016/10/jekyll_tutorials1/)。


#### 感谢   

本博客在[Vno Jekyll](https://github.com/onevcat/vno-jekyll)基础上修改的。  