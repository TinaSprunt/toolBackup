# 个人工具

## github加速
1. 下载油猴脚本
2. 在chromean安装暴力猴(Violentmonkey)插件
3. 在暴力猴插件中加入[油猴脚本](./github_accelerated_oil_monkey.txt)
![](./image/github_accelerate.png)
4. 打开github网页链接选择快速克隆链接


## git 基础命令

#### 常用
```shell
$ git branch -a   #查看当前所有分支
$ git checkout 分支名   #切换到指定
$ git clone 项目地址 -b tag号   #拉取指定tag号的代码（没有与该tag号同名的分支会报warning但是没关系）
$ git clone 项目地址 -b 分支名 新项目名   #拉取指定分支代码到本地并重命名
```


#### 日志查看
```shell
$ git log 
$ git log --pretty=oneline   # 精简log信息
$ git reflog    #全部log信息，包括被回滚的记录
```

#### 版本回退
```shell
$ git reset --hard  xxx版本号    #回滚到指定版本号
```
> 本地的版本回退不会影响到远程，除非进行提交
> 回退后如果不提交到远程，在回滚的基础上进行修改会无法push



#### 缓存区与工作区概念
![缓存区与工作区概念](https://static.liaoxuefeng.com/files/attachments/919020037470528/0)
> 工作区指未add之前
> 缓存区包括 add 以及 commit 



#### 撤销本地修改及提交
```shell

$ git checkout -- xxx文件名 #撤销指定文件的修改

$ git reset -- xxx文件名    #撤销指定文件的add提交，恢复到modify状态

$ git reset xxx版本号  #撤销commit提交，回滚到指定版本号(回滚到误提交的上一次版本号即可)

```
> 只要commit成功就会产生一个版本号，无论是否push


#### 创建和删除分支并推送到远程

```shell

$ git branch -b xxx分支名 #当前分支为基准创建一个新分支

$ git branch -d xxx分支名 #删除指定分支

```
> 执行完成后本地分支立即生效，但是还没有推送到远程
> 此时检查工作树也是空的，因为git status无法检查分支的变更情况
> 分支的创建和删除需要单独add
 
```shell

$ git remote -v #检查当前分支修改是否add,有输出就是已经add了

$ git remote add origin xxx仓库clone地址 # 如果没有add就使用此命令需要添加

$ git push origin xxx新建的分支名  #推送新建分支的变更到远程
$ git push origin :xxx被删除的分支名   #推送删除分支的变更到远程，注意冒号前有空格

$ git remote remove origin   #如果add错了分支变更，可以remove删除分支add

```

#### 合并分支并推送到远程
```shell

$ git checkout A分支名 # 切换到 A 分支 

$ git merge B分支名 # 将 B 分支内容合并到 A 分支

$ git push # 将合并推送到远程

$ git checkout A分支名 # 切换回 A 分支 

```