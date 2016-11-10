---
title: Hexo一站式搭建
tags:
  - hexo
  - 博客
categories: hexo相关
---

最近刚用 hexo 搭建了一个自己的博客,虽然比较简单,但是过程中也遇到了一点小麻烦。所以最后还是想把整个过程记录下来。这样，一来是想帮助那些同样准备使用 hexo 搭建博客的朋友们少走点弯路，二来也是想留个记录，毕竟自己记性差，怕没过多久忘掉。

在此先送上 **科学上网** 神器 [XX-net](https://github.com/XX-net/XX-Net),以备不时之需。

好，废话不多少，直接上正题。这篇文章将主要介绍：
* hexo 的搭建、配置、部署
* 域名的绑定（github、coding）
* 主题的相关设置
* 第三方支持

<!--more-->

# hexo 搭建、配置与部署 #

## hexo 是什么？##

[hexo](https://hexo.io/zh-cn/) 是一款快速、简洁且高效的博客框架。他不用你去编写代码，只需要做一些简单的配置，就可以做出一个简单实用的博客。

## hexo 的搭建 ##

### 准备 ###
安装 hexo 前，你要确保自己电脑上已经安装 nodejs 和 git。前者为 hexo 的运行环境，后者主要用于后期博客部署与代码管理。具体说明请参考官网：
* [nodejs](https://nodejs.org/zh-cn/)
* [git](https://git-scm.com/)    (mac 系统安装了 xcode 的会自带 git，另送上 [git 使用教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/))

### 安装 ###
本文以 mac 系统为例，介绍目前最新的 3.2.0 版本的安装.

首先安装 hexo-cli，打开控制台，执行

    npm install -g hexo-cli

安装完成之后我们可以执行下面代码检查一下版本号

    hexo -v

如果执行的结果是一堆版本号，那么恭喜你，第一步安装成功了(部分 mac 用户可能会因为权限问题安装不成功，可在 npm 前面加个 sudo 试试)。

### 创建博客 ###
首先先 `cd` 到要搭建博客的指定的文件夹，然后执行代码

    hexo init blog

这里的 blog 是你要建的博客项目名，名字随便你填写。接下来系统会自动初始化并安装项目依赖。若依赖没有自动安装，则 `cd` 到 项目里执行

    npm install

安装成功后，项目的目录结构为

    .
    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── source
    |   ├── _drafts
    |   └── _posts
    └── themes

其中
* `_config.yml`     为博客的配置文件
* `package.json`    为项目的包管理配置文件
* `scaffolds`       为 hexo 的模板文件夹
* `source`          为资源文件夹，存放用户资源。
* `themes`          为主题文件夹，存放博客主题皮肤

搭建完成后执行

    hexo server

等待片刻，当控制台显示

    INFO  Start processing
    INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.

此时你就可以访问本地4000端口([http://localhost:4000/](http://localhost:4000/))来查看自己的静态博客了

## hexo 的配置与使用 ##

### 配置文件 ###
hexo 的配置文件是项目根目录下的 `_config.yml`,用户可根据个人需求自行修改里面的内容进行配置。具体可参考文档 [hexo 配置文档](https://hexo.io/zh-cn/docs/configuration.html)

### 写作 ###
执行

    hexo new [layout] <title>

这里的 layout 就是为文章布局，默认为配置文件中 `default_layout` 参数值。title 为文章名。hexo 推荐使用 Markdown 渲染引擎来解析文章，所以这里会生成一个 `.md` 结尾的文件，通过 [Markdown语法](http://www.appinn.com/markdown/)，我们就可以很容易的写出一篇属于自己的博文了。

## hexo 部署 ##
之前所做的一切只能够让你在本地启动一个简单的服务器来运行你的博客，但这并不能像上其他博客网站那样，在别的终端的浏览器里输入你的地址就能够打开你的博客。不过没关系，接下来我们要做的就是把自己的博客部署到互联网上，让他成为一个真正的博客！

出于经济的考虑，这里我们可以使用 [github](https://github.com/), [coding](https://coding.net/) 等一些代码管理平台提供地免费的静态服务。如果没有相关的账号，可以自行注册。

下面我们来创建这两个主页

### github 主页 ###

1. 如图所示，首先点击右上角的加号，选择 `New repository` 来新建一个你的代码仓库。
![](/images/hexo/lesson/github1.png)

2. 仓库名为 xxx.github.io ，其中 xxx 须与你账号的用户名一致。
![](/images/hexo/lesson/github2.png)

3. 创建好之后，点击项目上方的 Settings
![](/images/hexo/lesson/github3.png)

4. 往下翻，找到下面这一行网址，通过它，你就可以访问自己的 github 主页了。
![](/images/hexo/lesson/github4.png)
当然这个时候你点击它出来的是 github 的 404 页面，那是因为你还没有往里面添加自己的个人主页。

### coding 主页 ###

1. 如图点击 `创建新项目` 来创建一个仓库。
![](/images/hexo/lesson/coding1.png)

2. 仓库命名为 xxx ，其中 xxx 最好与用户名一致。
![](/images/hexo/lesson/coding2.png)

3. 创建好之后，点击项目上方的 `Pages服务`，然后继续点击立即开启。
![](/images/hexo/lesson/coding3.png)

4. 开启后你就可以通过 `http://xxx.coding.me` 来访问自己的 coding 主页了。
![](/images/hexo/lesson/coding4.png)

### hexo 部署 github 和 coding ###

1. 首先需要安装 hexo-deploy-git 模块，项目根目录下执行

    npm install hexo-deployer-git \-\-save

2. 然后打开根目录下的 `_config.yml` 配置文件，添加代码
        # Deployment
        ## Docs: https://hexo.io/docs/deployment.html
        deploy:
          type: git
          repo:
            github: <your github path>
            coding: <your coding path>
          branch: master

    这里的 github 和 coding 参数后面的两个地址，分别对应其仓库地址，具体地址获取方法如下图
    ![](/images/hexo/lesson/github5.png)
    ![](/images/hexo/lesson/coding5.png)

    这里要注意 Https 和 SSH 的区别，https 的方式需要你每次部署的时候输入账号密码，而使用 ssh 的方式可以避免这个问题，具体怎么添加 ssh，这里就不详细描述了。

3. 每次写完文章想要部署的时候，可以通过执行 `hexo g -d` 来一键完成静态文件的生成和部署。
   当然，你也可以先执行 `hexo generate` 先生成静态文件，再执行 `hexo deploy` 来完成部署。

上面讲的都是一些基础的东西，学会它，就能满足我们博客的基本需求了。下面将要说一些补充的东西，这些东西主要是一些定制化的功能，如果有这些需求，你也可以参考。


# 域名绑定 #
github 和 coding 的个人主页都支持域名绑定，通过它，你可以使用其它域名来实现个人主页的访问。不过前提是你要拥有自己的域名。如果没有，你可以去一些域名服务商购买，一个普通的域名一年才几十块钱。下面就来绑定我们的域名。

## 域名解析 ##
这里推荐使用 CNAME 解析的方式，这种解析方式可以将域名指向主机服务商提供的另一个域名。

首先，在项目的 source 目录下新建一个文件命名为 CNAME。然后在 CNAME 文件里写下自己的域名，这里要注意几点：
* CNAME 最好是建在项目 source 里，如果直接在 github 上的更目录添加，下次部署会被删除。
* CNAME 必须全部大写
* CNAME 里只允许填写一个域名，这里推荐使用二级域名。填写时不要包含 http，如我的域名为 `blog.kuangshy.cn`

写好 CNAME 后我们需要添加域名解析，大家可以使用 [DNSPod](https://www.dnspod.cn/) ,也可以使用一些其他的工具，由于我的域名在阿里云上买的，所以我是直接在阿里云上面做的解析，原理都是一样。

添加解析需要填写的几个参数：
* 记录类型：我们使用的是 CNAME 解析，所以选择 CNAME。
* 主机记录：填写域名前缀。例如我的域名为 blog.kuangshy.cn,填写 blog 即可。
* 主机线路：默认，你也可以选择特定的线路
* 记录值：需要指向的域名。(如 `xxx.github.io.` 或者 `xxx.coding.me.`,这里的 `XXX` 为你的用户名)
* TTL：默认10分钟，无特殊需求不需要修改。

## 利用 github 和 coding 搭建一个快速访问的博客 ##
github 是全球最大的开源代码管理平台，但是由于它的服务器在国外，所以国内的 ip 访问相对较慢，加之国内时不时的墙了它，经常会出现登不上的情况，这就造成了我们部署在 github 上的站点极不稳定。为了解决这个问题，我们需要使用 coding，coding 的服务器在国内，因此访问速度非常快。具体的解决办法就是，当通过国内 ip 访问我们域名的时候解析到 coding 主页，国外 ip 访问时解析到 github 主页。如下图：
![](/images/hexo/lesson/dns.png)
你只需要把上面标出来的换成你自己的，然后静等几分钟，你就可以享受你自己的急速博客了。


# 主题与第三方支持 #
hexo 官方默认的主题是 landscape，这个主题简洁大方，但是功能相对较少。好在强大的 hexo 第三方主题非常多，在网上我们可以找到很多好看实用的 [hexo主题](https://github.com/hexojs/hexo/wiki/Themes),通过这些主题，我们能实现很多第三方功能。这里，笔者推荐一款人气度很高的主题 \-- [Next](http://theme-next.iissnan.com/)

## Next主题 ##
