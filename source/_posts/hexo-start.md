---
title: hexo start!
date: 2019-07-07 01:10:20
tags:
- hexo
---



# 搭建博客（采用hexo框架+部署到github）

## 操作步骤

### 1. 下载git

官网下载:  https://git-scm.com/download/win

安装与使用：见git笔记

安装后验证：git  --version

安装好git后， 后续命令均采用 git bash 执行。

### 2. 下载并安装node.js

官网下载：https://nodejs.org/en/

安装与使用：见node笔记

安装后验证：node -v 

### 3. 命令行安装cnpm 

命令：npm install -g cnpm --registry==https://registry.npm.taobao.org

安装后验证：cnpm -v 

### 4. 命令行安装hexo

命令：cnpm install -g hexo-cli

安装后验证：hexo  -v

### 5. 在github上创建仓库

新建一个名为你的用户名.github.io的仓库

比如说，如果你的github用户名是test，那么你就新建test.github.io的仓库（必须是你的用户名，其它名称无效），将来你的网站访问地址就是 http://test.github.io 了，每一个github账户最多只能创建一个这样可以直接使用域名访问的仓库。

```
### 配置SSH免密登录
第一步：首先打开电脑文件夹，找到C:\Users\bona\.ssh文件夹并删除

第二步：在C:\Users\bona 文件夹下右键打开Git Bash Here
输入命令：ssh-keygen -t rsa -C github邮件地址   
生成.ssh秘钥，输入后连敲三次回车

第三步：最终生成了一个新的 C:\Users\bona\.ssh文件夹，打开这个文件夹，找到.ssh\id_rsa.pub文件，记事本打开并复制里面的内容

第四步：打开你的github主页，进入个人设置 -> SSH and GPG keys -> New SSH key，把复制的内容粘贴进去，title随便填，保存即可，我们的公钥就添加成功了

第五步：检测是否设置成功：
输入命令：  $ ssh -T git@github.com # 注意邮箱地址不用改
如果提示Are you sure you want to continue connecting (yes/no)?，输入yes，然后会看到：
Hi fenghuayangyi! You've successfully authenticated, but GitHub does not provide shell access.
看到这个信息说明SSH已配置成功！

第六步：此时你还需要配置：
$ git config --global user.name "bona"// 你的github用户名，非昵称
$ git config --global user.email  "bona@126.com"// 填写你的github注册邮箱
```

## 使用 hexo搭建博客

### 初始化

- 新建文件夹 note

- git bash

  - hexo init

  - hexo g # 生成

  - hexo s  #启动服务， 打开浏览器访问 http://localhost:4000 即可看到内容

    如果端口冲突，参考这篇文章https://www.runoob.com/w3cnote/windows-finds-port-usage.html 

### npm组件 & hexo配置

- npm install hexo-deployer-git --save

  必须安装后，才能使用 : hexo d

  

- 编辑 hexocode目录下的 _config.yml 文件, 在文件末尾添加如下内容

  deploy:
    type: 'git'
    repository: git@github.com:zshlovely/zshlovely.github.io.git
    branch: master



-  报错和 time有关时，需要安装该组件

- npm install hexo-reading-time --save

  

- 安装后，才能使用搜索功能

- npm install hexo-generator-searchdb --save

  

- 创建分类

  hexo new page categories

  ```
  ---
  title: categories
  date: 2020-04-03 16:19:59
  type: categories
  ---
  ```

  

- 创建标签

  hexo new page  tags

  ```
  ---
  title: tags
  date: 2020-04-03 16:19:59
  type: tags
  ---
  ```

  

- 创建搜索

  hexo new page  search

  

- 自定义排序

  在某一类别下，排序比较混乱，需要按照文章的date排序，或者按照中文的一、二、三等命名。

  npm install hexo-generator-topindex --save

  

- 创建新文章

  ```
  // [layout] 为布局，可选项为 `post`、`page`、`draft`，这将决定文章所在文件路径。
  // <title> 为文章标题
  hexo new [layout] <title>
  
  eg. hexo new post "hello_word"
  ```

  



- 文章例子

  ```
  ---
  title: 每天一个linux命令
  date: 2017-01-23 11:41:48
  top: 1
  categories:
  - linux
  tags:
  - linux命令
  ---
  ```

### 常用命令

- hexo init
- hexo clean
- hexo g (generate)
- hexo s (start)
- hexo d (deploy)







### 部署优化

