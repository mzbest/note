# Hugo Github Pages 

## Getting Started With Hugo

https://youtu.be/hjD9jTi_DQ4?si=e_MkDyK4bCq905sk

Hugo 是一个静态页面生成器，类似于Jekyll，但略有不同。

gethugo.io  获得 Hugo

静态网站：快速；易用性。

动态网站：需要链接数据库，后端，比较慢；同时也比较复杂。

安装Hugo

1. 使用对应系统的Hugo包管理工具来安装

2. 安装Hugo

3. 为了安装Hugo，需要安装Scoop

   ```powershell
    # 以下代码可解决在admin状态下安装scoop失败的问题
    iex  "& {$(irm get.scoop.sh)} -RunAsAdmin "
   ```

Hugo使用

```shell
hugo new site hugo-demo -f yml # 好像-f yml 参数在这里是没有用的，都会生成hugo.toml配置文件，虽然有些不适应，但也勉强能看懂。
```

会在shell打开位置建立一个新的静态网页文件

进入hugo-demo目录

```shell
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1  #虽然能用，但是不建议这样做，是因为会在git的时候，发生一些问题。可以用hugo网页quick start中的方法。下面请看：
hugo new site quickstart
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke  # 将主题模块作为了git子模块，这样在后面提交到github的时候少了两个git模块之间的冲突。
echo "theme = 'ananke'" >> hugo.toml
hugo server
```

然后就会在hugo-demo/theme/文件夹下面出现PaperMod主题文件，没有下载之前，theme文件夹下面是空的。

在vscode中编辑hugo-demo的配置文件：

hugo.toml

```toml
baseURL = ''
languageCode = 'en-us'
title = 'Demo for Hugo'
theme = "PaperMod"  # 单引号或者双引号都是可以的，但是如果是不加引号，就会在执行 hugo serve 命令的时候报错，显示无法load 配置文件
```

修改完毕后执行

```shell
hugo serve(r) 
```

即可在本地访问。

添加新内容

```shell
hugo new content content/posts/my-first-post.md

# 生成的my-first-post.md 开头便是如下内容
# draft 草稿的意思  如果值为 true，那么执行`hugo srever`命令的时候，便会看不到。那怎么办呢，两个办法，1. 将true改为false,也就是说不是草稿，已经可以发布了；2. `hugo server --buildDrafts` 或者`hugo server -D`，这样在后面加了参数，便可以在hugo构建的时候，将草稿构建进去，在本地的网站上便能看见了。
+++
title = 'My First Post'
date = 2024-01-14T07:07:07+01:00
draft = true
+++
```

那么，剩下的就是把hugo项目发布到github上面，可是呢，发布上去以后，却会发现github Pages地址打开后是404，为什么呢，是因为hugo与jekyll不同，由jekyll打包的项目能直接在xxx.github.io显示。而hugo的，不可以。下面说一下该怎么配置：（也非常简单，但我摸索了有一会儿。）

方法在 https://gohugo.io/hosting-and-deployment/hosting-on-github/

**Host on GitHub Pages**  在GitHub Pages上托管

先决条件：

1. 创建一个Github 账号
2. 电脑上安装了 Git
3. 在本地已经用 `hugo server`创建了一个Hugo 站点

……后面我就不啰嗦了。按照刚才的蓝色链接去看就行。

**注意：**

……

第五步

Create an empty file in your local repository.

```shell
.github/workflows/hugo.yaml # 注意，这个配置文件不要不小心建在了public目录下，不要，不要，不要。
```

第六步

Copy and paste the YAML below into the file you created. Change the branch name and Hugo version as needed.

注意上面，有两点根据需要要进行修改，分别是`branch name` 和 `Hugo version`，而`branch name`配置文件中写的是 `main`，而Gighub里面好像默认是`master`分支，如果不改，便无法在代码提交以后，GitHub pages通过gitAction自动部署，只能手动去点了。

那如果说，你有两个分支，一个`main`分支，还有一个比如叫做`gh-pages`分支吧，那你会想到把`gh-pages`添加到第六步当中的YAML配置文件中，这是没错的，然后也会出发Github Action，build的过程没问题，在deploy过程就会失败，会提示安全限制类似的提醒，那么我们就需要更改以下：

github repository中——settings——Environments ，将`gh-pages`添加进去就好了。然后你从新更改，提交，部署，就会看到会出发Github Action，然后就能看到自己网页的变化了。

目前我的进展就是这样，hugo还有很多需要学习，先记录在这里，作为阶段的学习成果。





