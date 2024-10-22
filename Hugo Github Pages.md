# Jekyll Github Pages 

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
hugo new site hugo-demo -f yml
```

会在shell打开位置建立一个新的静态网页文件

进入hugo-demo目录

```shell
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
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
hugo serve
```

即可在本地访问。

添加新内容

```shell
hugo new posts/first.md
```





