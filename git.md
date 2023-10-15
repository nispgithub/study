## 一、引言

> 在单人开发过程中，需要进行版本管理，以利于开发进度的控制；
>
> 在多人开发过程中，不仅需要版本管理，还需要进行多人协同控制。

## 二、介绍

> Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目；
>
> Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件；
>
> 官网：https://git-scm.com/

## 三、Git安装

### 下载Git

下载Git https://git-scm.com/downloads

### 安装

> 安装，除了安装位置外，其他一直下一步即可

### 基本配置

安装后，打开cmd

```cmd
git config --global user.name "Your Name"  #用户名
git config --global user.email "email@example.com"  #邮箱
# 查看信息
git config -l 
```

### 测试

> 测试：CMD中执行 ,查看git版本

```cmd
git version  
```

### 四、架构

> 版本库：工作区中有一个隐藏目录 `.git`，这个目录不属于工作区，而是git的 `版本库`，是git管理的所有内容；
>
> 暂存区（stage）：版本库中包含一个临时区域，保存下一步要提交的文件；
>
> 分支：版本库中包含若干分支，提交的文件存储在分支中。

### 五、仓库

> 对应的就是一个目录，这个目录中的所有文件被git管理起来；
>
> 以后会将一个项目的根目录，作为仓库；
>
> 仓库中的每个文件的改动都由git跟踪。

### 本地仓库

#### 新建仓库

> 选择一个目录，执行指令：`git init`

#### 工作区

> 执行`git init`的目录即为工作区，如上例，`D:\repo1`目录即为工作区(不包含`.git`目录)
>
> 所有文件，都首先在工作区新建，然后可以存入仓库(版本库)，进行版本控制。

#### 暂存区

> 暂存区也在`.git`目录内，工作区的文件进入仓库时，要先进入暂存区。

####  分支

> 版本控制，简单说，就是记录文件的诸多版本，分支就是这些版本的最终记录位置。

#### 基本操作

git status   查看仓库状态 

git add .    将工作区中的文件全部存入暂存区

git commit -m "这里写提交的描述信息"  作用是将暂存区的文件存入分支，形成一个版本

### 远程仓库

当多人协同开发时，每人都在自己的本地仓库维护版本。

但很重要的一点是，多人之间需要共享代码、合并代码，此时就需要一个远程仓库（公共）。

#### 远程仓库选型

> 有很多远程仓库可以选择，比如 :
>
> - Github(https://github.com/)
> - 码云(https://gitee.com/)
>
> 此两种可以注册自己测试使用，但如果是商业项目，需要更多支持需要付费

##### 命令汇总

| 命令                                   | 描述                                         |
| -------------------------------------- | -------------------------------------------- |
| git remote add 标识名(master) 远程地址 | 本地关联远程仓库                             |
| git push 标识名 master                 | 将本地仓库内容上传到远程仓库                 |
| git pull 标识名 master                 | 从远程仓库下载内容到本地仓库                 |
| git clone 远程地址                     | 将远程仓库复制到本地，并自动形成一个本地仓库 |
| git branch [分支名]                    | 查看[创建]当前仓库的分支                     |
| git checkout 分支名                    | 切换分支                                     |
| git log                                | 查看分支的提交日志                           |
| git merge 分支名                       | 合并分支                                     |

##### 合并冲突

> 两个分支进行合并，但它们含有对同一个文件的修改，则在合并时出现冲突，git无法决断该保留改文件哪个分支的修改。
>
> 冲突内容用<<<<   ==== >>>>做了分割

###### 冲突解决

> 出现冲突后，如要由两个开发人员当面协商，该如何取舍，为冲突文件定义最终内容。
>
> 解决方案：
>
> 1. 保留某一方的，删除另一方的
> 2. 保留双方的
> 3. 但无论如何，要记得删除 <<<< ==== >>>> 这些
> 4. 本质是两人协商为冲突的内容，定制出合理的内容。

## 六、idea使用git

详见文档

## 七、经典问题

> 在使用https协议做push时，如果曾经使用过码云，但密码有过改动，此时会报错

|                      使用https协议报错                       |
| :----------------------------------------------------------: |
| ![坑1](https://study.code2048.tech/assets/%E5%9D%911-58684f4d.jpg) |

> 解决方案: `控制面板-凭据管理器`删除对应凭证，再次使用时会提示重新输入密码。

|             删除之前的码云凭证，然后重新push即可             |
| :----------------------------------------------------------: |
| ![坑2](https://study.code2048.tech/assets/%E5%9D%912-cdf31714.jpg) |