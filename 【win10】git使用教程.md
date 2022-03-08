﻿**这里以上传至gitee为例，GitHub类似**



# 一、配置

## 1. git安装
git官网下载链接：[https://git-scm.com/download/win](https://git-scm.com/download/win)
安装一直点击下一步，或者自行搜索一遍安装教程的博客：[安装教程](https://blog.csdn.net/mukes/article/details/115693833)

安装完成后`win+R`打开命令提示符输入`git --version`查看git版本即知道是否安装成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/8cc26c3eabb445728fbf07f30ae69b1c.png)


## 2. 自行注册gitee账号

## 3. 生成SSH公钥
由于我们的本地 git仓库和 gitee仓库之间的传输是通过SSH加密的，所以我们需要配置SSH公钥。
打开`cmd`命令行，输入命令
```cpp
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"
```
> 注意：这里的xxxxx@xxxxx.com只是生成的 sshkey 的名称，并不约束或要求具体命名为某个邮箱。

![在这里插入图片描述](https://img-blog.csdnimg.cn/fa38f32fee7a451ba7bf5ced57dbdbc0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)

按照提示完成`三次回车`，即可生成ssh key。
进入公钥位置对应目录用`文本文件`打开
![在这里插入图片描述](https://img-blog.csdnimg.cn/e80471bc1ed54d98a85c9ad024546581.png)
全部`复制`


## 4. 配置SSH公钥
在`gitee`网站点击`设置`->`SSH公钥`
![在这里插入图片描述](https://img-blog.csdnimg.cn/d57e518ad3754d0c937d391e968806a1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
将你复制的SSH公钥直接粘贴到框中，`确定`
![在这里插入图片描述](https://img-blog.csdnimg.cn/13579dfcb385432b814a3e842eb8296a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
添加成功！
![在这里插入图片描述](https://img-blog.csdnimg.cn/2113322ea20c4e18bdd358a0235519fb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)



# 二、测试

## 5. 创建一个项目
点击右上角的 +号，新建仓库
![在这里插入图片描述](https://img-blog.csdnimg.cn/eddea7ad8b2745c9933a0ffe4b0f8ba6.png)
如下，填写仓库信息，最后点击创建即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/506eb6c73dd64a99b11403bace035d0f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
<br>

## 6. 实例
本地电脑新建一个文件夹`gitee`，目录空白处鼠标`右键`，点击`Git Bash Here`。
![在这里插入图片描述](https://img-blog.csdnimg.cn/09e782d8b6794b8bade57c8e13472a02.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)

### （1）克隆仓库到本地
点击`克隆/下载`，然后点击`SSH`，`复制git链接`
![在这里插入图片描述](https://img-blog.csdnimg.cn/3223cacf68094f0faf7e3c35b11d1d99.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
输入`git clone 刚刚的git链接`，如下
```cpp
git clone git@gitee.com:zdbya/mytest.git
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ed08fe93fb66427dbf466f1607d732f1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
成功后，本地目录即可看到克隆下来的mytest文件夹。


### （2）本地初始化
进入到本地的某个目录后输入`git init`，使这个目录变成git可以管理的仓库。
```cpp
git init
```
上面语句会生成一个`.git`文件


### （3）设置个人信息
尽量与git网站注册信息一致
```cpp
git config --global user.name "你的名字"
git config --global user.email "邮箱"
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/7b6b494398fe475dbffef18e7782cc63.png)


### （4）关联本地工程到远程仓库
有时候，我们可能是先在本地有了工程文件，然后再在gitee上创建仓库的。
此时，可在本地库上使用命令 `git remote add`把它和gitee的远程库关联，如下
```cpp
git remote add origin https://gitee.com/zdbya/mytest.git
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/0caaa57b799b4ec4b009b97a2d65404a.png)
如果报错说已存在远程库，就先删除，再关联
>注意：删除已有的远程库指令如下：`git remote rm origin`

`git remote -v`可以查看关联的远程库
```cpp
14051@LAPTOP-7NLRI4B2 MINGW64 /d/gitee/mytest (master)
$ git remote -v
origin  git@gitee.com:zdbya/mytest.git (fetch)
origin  git@gitee.com:zdbya/mytest.git (push)
```

### （5）上传文件到远程库

在本地添加文件，如下，我们打算将它上传`gitee`
![在这里插入图片描述](https://img-blog.csdnimg.cn/98a02f28020448babe1f6fd4b5adcd8c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)
<br>

**执行git命令，提交文件**
用到下面这几条命令
```cpp
git add *
git status
git commit -m "提交内容注释"
git push
```

1、先进入对应路径下
```cpp
14051@LAPTOP-7NLRI4B2 MINGW64 /d/gitee (master)
$ cd mytest/
```

2、`git add -A` 添加文件
```cpp
14051@LAPTOP-7NLRI4B2 MINGW64 /d/gitee/mytest (master)
$ git add -A
```
`git status`可以查看暂存区状态，再把 暂存区 代码提交到 本地仓库
![在这里插入图片描述](https://img-blog.csdnimg.cn/887e0e330ac848d4b699024d03dc8f4e.png)


3、`git commit` 文件
```cpp
14051@LAPTOP-7NLRI4B2 MINGW64 /d/gitee/mytest (master)
$ git commit -m "项目初始化提交"
[master 291598d] 项目初始化提交
 1 file changed, 2663 insertions(+)
 create mode 100644 "\343\200\212LeetCode\343\200\213\346\225\260\346\215\256\347\273\223\346\236\204\345\205\245\351\227\250\346\235\277\345\235\227.md"
```

4、`git push`文件
```cpp
14051@LAPTOP-7NLRI4B2 MINGW64 /d/gitee/mytest (master)
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 16.60 KiB | 1.19 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: Powered by GITEE.COM [GNK-6.2]
To gitee.com:zdbya/mytest.git
   1167115..291598d  master -> master
```
### （6）测试成功
![在这里插入图片描述](https://img-blog.csdnimg.cn/919eb84ecc7546038fb3ee92864d67d4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAemRi5ZGA,size_20,color_FFFFFF,t_70,g_se,x_16)


## 7. 常用的git命令
```cpp
git init                        #把当前目录变成git可以管理的仓库
git add readme.txt              #添加一个文件，也可以添加文件夹
git add -A                      #添加全部文件
git rm test.txt                 #删除一个文件，也可以删除文件夹
git commit -a -m "some commit"  #提交修改
git status                      #查看是否还有未提交
git log                         #查看最近日志
git reset --hard HEAD^          #版本回退一个版本
git reset --hard HEAD^^         #版本回退两个版本
git reset --hard HEAD~100       #版本回退多个版本
git remote add origin +地址     #远程仓库的提交（第一次链接）
git push -u origin master       #仓库关联
git push                        #远程仓库的提交（第二次及之后）
```



# 三、参考博客

[https://blog.csdn.net/linxinfa/article/details/108709835](https://blog.csdn.net/linxinfa/article/details/108709835)
[https://blog.csdn.net/qq_45069279/article/details/106378699](https://blog.csdn.net/qq_45069279/article/details/106378699)
[https://blog.csdn.net/weixin_45230019/article/details/115385447](https://blog.csdn.net/weixin_45230019/article/details/115385447)
[https://blog.csdn.net/qq_45069279/article/details/106174340](https://blog.csdn.net/qq_45069279/article/details/106174340)
