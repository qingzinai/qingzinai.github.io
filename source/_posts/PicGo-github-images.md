
---
title: 关于如何搭建一个github图床并用PicGo管理
reward: fasle
tags: 图床
categories: 紫奈的技术分享
---

# 关于如何搭建一个github图床并用PicGo管理

## 什么是图床
> 图床，就是指一些可以把图片存放到自己或者第三方并且引用到其他网站使用的服务，就像以前的网络相册。

## 图床的好处
1. 节约存储成本
2. 可以在有网络的时候随时访问
3. 可以使用免费的第三方加速服务

## 本次教程的优点
> 这次我所用的服务和工具都属于开源服务，点一下玩一年不花一分钱。下面让我们开始图床的搭建。

## 教程开始

### tips
> 本次教程针对有一定基础的同学，我没有写在教程里的东西在网上都有。
> github可能会显示图片裂开的情况,可以科学上网或者改hosts 这里就不写如何解决。

### 创建github仓库
1. 首先你需要登录自己的github创建一个新的库
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/20210126165151.png)
2. 然后填写你的库资料，自己加描述 
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122010052-449120149.png)
1. 成功后会显示下面页面 
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/WX20210126-165633@2x.png)

### 使用jsDelivr加速
> 因为github是国外网站所以图片加载可能很慢，这里就需要用第三方的cdn加速，我这里用的是jsDelivr,有其他加速的同学们也可以用自己的加速服务。
> 使用方法，非常简单，即把图片地址链接域名改为 CDN 的域名。格式如下：
> https://cdn.jsdelivr.net/gh/<你的github用户名>/<你的图床仓库名>@<仓库版本号>/图片的路径
> 这里的版本号指的是分支名以前github默认为masrter现在是main不要搞错
> 这里放出一份改完后的图片地址:https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/WX20210126-165633@2x.png
> 其他说明，可参考 jsDelivr 官网介绍

### 创建github图床Token
1. 首先你需要创建一个token
> 点击右上角账号上的 settings
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122010906-24503404.png)
> 然后左侧点击 developer settings ，再点击 personal access tokens ，然后点击 generate new token。
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122011123-386794180.png)
> 最后说明自己创建token的用途,然后 scopes 只需要选 repo 的所有选项即可
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122011409-863250092.png)
> 拉到底部，点击 generate token ，即可成功。
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122011668-1781832056.png)
> 最后一定要记住自己生成的token
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/1714084-20201031122011850-1358770775.png)

### 使用PicGo对图床进行管理
> PicGo是github一个开源的图床管理工具 [PicGo下载地址](https://github.com/Molunerfinn/PicGo)
> 在 PicGo 中，找到图床设置 -> GitHub图床。
> 仓库名即为你的github账号/图片仓库名
> 分支名就用默认的 main
> Token 就填写刚才我们生成的 Token
> 存储路径如果需要指定子目录可以填写例如 img/ 。我这里没有填，就会上传到我图片仓库的根目录。
> 自定义域名就填写 jsDelivr 的域名，即图片访问地址，不包括图片路径的前半部分，我这里就是 https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main。
> 最后设为默认图床，下次在 typora 上传图片就会自动上传到 github 图床了。
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/WX20210126-171805@2x.png)

### 使用插件同步github图床
> 也许会有人问如果我github删除了图片PicGo不就和github不同步了吗？
> 这里我提供一个解决方法,PicGo拥有丰富的插件系统可以解决
> 在PicGo插件设置里搜索github-plus
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/WX20210126-172255@2x.png)
> 安装完成后点击配置uploder-githubPlus
> 按照下图把仓库信息填写进去
![avatar](https://cdn.jsdelivr.net/gh/qingzinai/qingzinai-image@main/AC17B77F-07C4-471E-B479-D3480E17DA15.png)
> 然后点击 pull origin 就可以同步仓库了
> 更多使用详情请参考插件开发者的文档 [插件文档地址](https://github.com/zWingz/picgo-plugin-github-plus)

### 后记
> 以上就是创建图床的全部教程如果遇到困难可以在下方的评论系统提出。