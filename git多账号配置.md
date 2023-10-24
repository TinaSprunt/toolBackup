# git 多账号配置

## 1. 清除 git 的全局设置

```shell
git config --global user.name "your_name"
git config --global user.email  "your_email"
```

## 2. 生成新密钥(有几个账号重复几次本步骤)

```shell
# 账号 yang@163.com
ssh-keygen -t rsa -C "githubEmail@163.com"

# 回车后会出现下面这句话：
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/Administrator/.ssh/id_rsa):

# 此时请根据不同账号进行命名 如 github_id_rsa, 同名的会进行覆盖
```

<<<<<<< Updated upstream
## 3. 在`/Users/Administrator/.ssh/`目录下修改 config 文件
=======
## 3.在`/Users/Administrator/.ssh/`目录下修改 config 文件
>>>>>>> Stashed changes

- Host 是域名地址，必须准确
- HostName 建议和域名地址一样
- User 是用户名
- IdentityFile 是密钥地址

```
Host github.com
HostName github.com
User xxxx1
IdentityFile C:/Users/Administrator/.ssh/github_id_rsa

Host gitlab.com
HostName gitlab.com
User xxxx2
IdentityFile C:/Users/Administrator/.ssh/gitlab_id_rsa
```

## 测试连接

```shell
# 测试账号链接 ssh -T git@对应的Host名称

# 如：测试账号xxx1连接
ssh -T git@github.com

# 如：测试账号xxx2连接
ssh -T git@gitlab.com
```

# 正式使用

```shell
# 在每个git clone 下来的项目中，根据项目的地址，设置不同的 local 用户名及邮箱

# 如用xxx1账号从github clone下来的项目：
git config --local user.name xxxx1
git config --local user.email githubEmail@163.com


# 如用xxx2账号从gitlab clone下来的项目：：
git config --local user.name xxxx1
git config --local user.email gitlabEmail@163.com
```
