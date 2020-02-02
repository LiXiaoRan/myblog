---
title: 用 git 追踪 Word 文档的版本
top: false
cover: false
toc: true
mathjax: true
date: 2020-02-02 15:54:41
password:
summary:
tags:Git
categories:日常技能
---

在写文章的时候，我们经常会遇到许多需要追踪文件版本的难题。不论是随着你的编辑和修改不断变化的文件版本，还是和其他合作者一起编写文章，要想保留文档的修改痕迹往往要费时费力，效果还差强人意。

## 如何做

1. 安装pandoc

   ```shell
    brew install pandoc
   ```

2. 在用户根目录下即`~/.gitconfig`或者c:\Documents and Settings\user.gitconfig" (Windows) 打开或者创建文件。添加如下内容：

   ```shell
    [diff "pandoc"]
      textconv=pandoc --to=markdown
      prompt = false
    [alias]
      wdiff = diff --word-diff=color --unified=1
   ```

3. 在仓库目录下创建文件 `.gitattributes`添加如下内容：

   ```shell
    *.docx diff=pandoc
   ```

   

现在修改文件可以看到颜色差异了

```shell
git wdiff file.docx
```

也可以通过以下命令看到所有的更改

```shell
git log -p --word-diff=color file.docx
```



## 参考文献

[1]	Martin Fenner's ["Using Microsoft Word with git"](http://blog.martinfenner.org/2014/08/25/using-microsoft-word-with-git/).