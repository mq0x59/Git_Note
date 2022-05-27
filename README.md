# Git学习笔记

## Git简介

Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git与常用的版本控制工具CVS，Subbversion等不同，它采用分布式版本库地方式，不必服务端软件支持。

## 基本概念--Git结构

1. 工作区
2. 暂存区
3. 本地库

<img src="C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220526190048819.png" alt="image-20220526190048819" style="zoom: 50%;" />


## 基本操作

#### 创建仓库命令

| 命令 | 说明 |
| :--- | :--- |
| `git init` | 初始化仓库 |
| `git clone` | 拷贝一份远程仓库，也就是下载一个项目 |

#### 提交与修改

| 命令 | 说明 |
| :--- | :--- |
| `git add` | 添加文件到暂存区 |
| `git status` | 查看仓库当前的状态，显示有变更的文件 |
| `git diff` | 比较文件的不同，即暂存区和工作区的差异 |
| `git commit` | 提交暂存区到本地仓库 |
| `git reset` | 回退版本 |
| `git rm` | 删除工作区文件 |
| `git mv` | 移动或重命名工作区文件 |

#### 提交日志

| 命令 | 说明 |
| :--- | :--- |
| `git log` | 查看历史提交记录 |
| `git blame<file>` | 以列表形式查看指定文件的历史修改记录 |

#### 远程操作
| 命令 | 说明 |
| :--- | :--- |
| `git remote` | 远程仓库操作 |
| `git fetch` | 从远程获取代码库 |
| `git pull` | 下载远程代码并合并 |
| `git push` | 上传远程代码并合并 |

## Git命令行操作

#### 本地库操作

##### 1. 本地库初始化

命令：git init
注意：.git目录中存放的是本地库相关的子目录和文件，不要删除，也不要随意修改。

- 设置签名：
    - 形式：
        - 用户名
        - Email地址
        - 作用：区分不同开发人员的身份
    - 辨析：这里设置的签名和登录远程库(代码托管中心)的账号、秘密没有任何关系
    - 命令：
        - 项目级别/仓库级别：仅在当前本地库范围内有效
            - git config user.name xxxx
            - git config user.email xxxxxxxxxx
            - 信息保存位置：仓库文件夹/.git/config文件
        - 系统用户级别：登录当前操作系统的用户范围
            - git config --global user.name xxxx
            - git config --global user.email xxxxxxxxxx
            - 信息保存位置：C:/Users/用户名/.gitconfig文件<img src="C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220527060441077.png" alt="image-20220527060441077"  />
        - 级别优先级：
            - 就近原则：项目级别优先于系统用户级别，二者都有时采用项目级别的签名
            - 如果只有系统用户级别的签名，就以系统用户级别的签名为准
            - 二者都没有不允许

##### 2. 基本操作

1. 状态查看操作

>git status
>查看工作区、暂存区状态

2. 添加操作

> git add [file name]
>
> 将工作区的 “新建/修改” 添加到暂存区

3. 提交操作

> git commit -m "commit message" [file name]
>
> 将暂存区的内容提交到本地库

4. 查看历史记录

> git log
>
> ![image-20220527081851674](C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220527081851674.png)
>
> > 多屏显示控制方式:
> >
> > 空格向下翻页
> >
> > b 向上翻页
> >
> > q 退出
>
> git log --pretty=online
>
> ![image-20220527082159727](C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220527082159727.png)
>
> git log --oneline
>
> ![image-20220527082235732](C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220527082235732.png)
>
> git reflog
>
> ![image-20220527082338618](C:\Users\小六\AppData\Roaming\Typora\typora-user-images\image-20220527082338618.png)
>
> > HEAD@{移动到当前版本需要多少步}

5. 前进后退

> 本质：HEAD指针
>
> - 基于索引值操作
>    - git reset --hard [局部索引值]
>    - git reset --hard fb11604
>    
> - 使用^符号
>
> - 使用~符号

##### 3. 分支管理

--------------------------------------------------

#### 远程库操作

- git remote add Git_Note https://github.com/xl34/Git_Note.git

