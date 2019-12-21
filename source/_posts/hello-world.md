---
title: 这个博客是怎么来的
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-14 17:27:18
password:
summary:
tags: 随笔
categories: 随笔
---
# 这个博客是怎么来的

效果预览：

![](https://raw.githubusercontent.com/LiXiaoRan/PicGoBed/master/img/20191214172126.png)

## 做法
根据参考文献中的内容，我配置了环境

首先是安装Hexo

在合适的地方新建一个文件夹，用来存放自己的博客文件，比如我的博客文件都存放在`D:\study\program\blog`目录下。

在该目录下右键点击`Git Bash Here`，打开git的控制台窗口，以后我们所有的操作都在git控制台进行，就不要用Windows自带的控制台了。

定位到该目录下，输入`npm i hexo-cli -g`安装Hexo。会有几个报错，无视它就行。

安装完后输入`hexo -v`验证是否安装成功。

然后就要初始化我们的网站，输入`hexo init`初始化文件夹，接着输入`npm install`安装必备的组件。

这样本地的网站配置也弄好啦，输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器，然后浏览器打开http://localhost:4000/，就可以看到我们的博客啦，效果如下：

![img](https://godweiyang.com/2018/04/13/hexo-blog/5.jpg)

然后第二步就比较关键了：

打开https://github.com/，新建一个项目，然后如下图所示，输入自己的项目名字，后面一定要加`.github.io`后缀，README初始化也要勾上。**名称一定要和你的github名字完全一样，比如你github名字叫`abc`，那么仓库名字一定要是`abc.github.io`。**

![img](https://godweiyang.com/2018/04/13/hexo-blog/2.jpg)

然后项目就建成了，点击`Settings`，向下拉到最后有个`GitHub Pages`，点击`Choose a theme`选择一个主题。然后等一会儿，再回到`GitHub Pages`，就可以看到咱们的博客链接了。点击链接，就会出现自己的网页，效果如下：

![img](https://godweiyang.com/2018/04/13/hexo-blog/4.jpg)



---

以上只是环境，有了环境后，就可以随心配置了。

这里我下载了https://github.com/godweiyang/hexo-matery-modified 的源码，然后直接修改。

下载后首先要解压`node_modules`,然后运行`npm install`接下来:

- 根目录配置文件`_config.yml`和主题目录配置文件`_config.yml`中修改个人信息。

- 根目录配置文件中修改`deploy`一栏的`repository`。

- 根目录配置文件中修改`baidu_url_submit`一栏的`token`。

- 主题配置文件中修改`gitalk`一栏，修改方法见下文。

```shell
hexo g  # 生成博客网页文件
hexo s  # 本地预览博客
hexo d  # 上传网页文件到github
```

如果样式没有发生变化，就在这三步操作之前先运行一下

```sh
hexo clean
```

#### 配置gitalk 

首先打开[github](https://github.com/settings/applications/new)申请一个应用，要填四个东西：

```sh
Application name //应用名称，随便填 
Homepage URL //填自己的博客地址 
Application description //应用描述，随便填 
Authorization callback URL 

```

然后点击注册，会出现两个字符串`Client ID`和`Client Secret`，这个要复制出来。

然后去主题的配置文件`_config.yml`下修改`gitalk`那里：

```sh
gitalk: 
		enable: true 
		owner: 你的github用户名 
		repo: 你的github用户名.github.io 
		oauth: 
				clientId: 粘贴刚刚注册完显示的字符串 
				clientSecret: 粘贴刚刚注册完显示的字符串 
		admin: 你的github用户名
```

以后写文章的时候，只要在文章页面登陆过github，就会自动创建评论框，**记得每次写完文章后打开博客文章页面一下**。



## 写文章和发布文章

首先在博客根目录下右键打开git bash，安装一个扩展`npm i hexo-deployer-git`。

然后输入`hexo new post "article title"`，新建一篇文章。

然后打开`D:\study\program\blog\source\_posts`的目录，可以发现下面多了一个文件夹和一个`.md`文件，一个用来存放你的图片等数据，另一个就是你的文章文件啦。

编写完markdown文件后，根目录下输入`hexo g`生成静态网页，然后输入`hexo s`可以本地预览效果，最后输入`hexo d`上传到github上。这时打开你的github.io主页就能看到发布的文章啦。

##### 还有一些新文章的标题配置如下图所示：

![](https://raw.githubusercontent.com/LiXiaoRan/PicGoBed/master/img/20191214174513.png)



完。

## 参考文献

- https://godweiyang.com/2018/04/13/hexo-blog/
- 超详细Hexo+Github博客搭建小白教程 - godweiyang的文章 - 知乎  https://zhuanlan.zhihu.com/p/35668237