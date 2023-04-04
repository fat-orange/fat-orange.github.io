---
title: 记录hexo多台电脑安装过程
date: 2023-04-03 18:04:53
tags: hexo安装
categories: hexo
---

# 多台电脑安装hexo

## 老电脑上的操作

3. 实现的原理，主要是使用git分支来实现同步，所以我们需要先在gihub上新建一个分支。

   [图片](/img/hexo-1.jpeg)
   
4. 标号1为需要输入新的分支，标号2为创建分支，标号3打开设置。 
   [图片](/img/hexo-2.jpeg)
   
5. 标号1选择分支，标号2选择分支，标号3选择默认分支

6. 接下来需要在老电脑上，首先clone仓库到本地

   ```c
   git clone git@github.com:username/username.github.io.git
   ```
   
   注:git@github.com指的是你github注册的邮箱,username指的是你github的用户名

5. 接着只留下了.git文件夹,其他的文件和文件夹全部删除(如果找不到.git文件夹，那么可能是你的隐藏文件的选项没有勾上)

6. 然后再跳到原来存放hexo文件的位置，将除了.deploy_git，其余都复制到clone的文件夹中。

   注意:1.存放hexo文件的位置应当有一个 .gitignore文件，这个文件用来表示这些文件不需要git上传,如果没有重新创建一个即可

   ```c
   .DS_Store
   Thumbs.db
   db.json
   *.log
   node_modules/
   public/
   .deploy*/
   ```

## 新电脑上操作

1. hexo安装在多台电脑上，主要使用了git和nodejs工具

2. 在新电脑上首先需要安装git和nodejs，

   git 淘宝镜像链接[CNPM Binaries Mirror (npmmirror.com)](https://registry.npmmirror.com/binary.html?path=git-for-windows/)

   nodejs 官网 [Node.js (nodejs.org)](https://nodejs.org/zh-cn)

3. 通过下面命令生成新的ssh key

   ```C
   ssh-keygen -t rsa -C "your_email@example.com"
   ```

   注:这个your_email@example.com指的是你自己github注册的邮箱

   如果已经有了SSH key，可以通过下面命令查找id_rsa.pub(公钥)和id_rsa(私钥)的位置

   ```C
   ls -al ~/.ssh
   ```

4. 将新的id_rsa.pub(公钥)添加到你的github账户

5. 新建一个hexo文件夹用来存放新的hexo文件，在hexo文件夹右键点击GIt bash here。输入下面命令

   ```
   git clone git@github.com:username/username.github.io.git
   ```

   注:git@github.com指的是你github注册的邮箱,username指的是你github的用户名

6. 此时依次执行

   ```C
   npm install hexo
   npm install
   npm install hexo-deployer-git
   hexo g
   hexo d
   ```

   接下来就可以在新电脑开始编写文章了

注：1. 可能有部分同学会发现hexo 命令会提示无法发现没有hexo，这是因为环境变量没有安装好，自己安装一下即可

  2. 一定要在编写文章之前进行git pull ，以此保证文章同步

  3. 编写完之后，一定要执行下列指令

     ```
     git add .
     git commit –m add_branch
     git push
     ```

     