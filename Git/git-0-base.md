# Git Base

## Git 介绍

> Git is a free and open source distributed version control system designed to
> handle everything from small to very large projects with speed and efficiency

Git 是一个开源的文件版本控制器

- 在云端仓库, 本地仓库, 任意位置传输文件
- 记录代码和文件的改动及状态
- 回溯到已记录的某个节点
- 分布式版本控制器

## 安装

[Git 官网](https://git-scm.com/)下载安装

```bash
 $ git --version                                 # 检查 git 是否安装
 > git version 1.8.3.1
```

```bash
 $ yum install git                               # Centos Redhat 系统使用 yum 安装
 $ sudo apt-get install git                      # Ubuntu Debian 系统使用 apt
```

## 配置

> git-config - Get and set repository or global options

将文件或代码上传云端时, 需要设置用户名和邮箱, Git 用户和邮箱有 3 个等级

| leve |      file        |introduce                               |
|:----:|     :----:       |:--                                     |
|`system`|`/etc/gitconfig`|系统上每一个用户及他们仓库的通用配置(不常用)|
|`global`|`~/.gitconfig`  |当前系统用户, 这会对你系统上所有的仓库生效  |
|`local` |`.git/config`   |在仓库内默认使用 local 配置(优先级最高)    |

### 查看 git 配置

```bash
 $ git config --list --show-origin               # 查看所有配置及所在的文件, 早期版本不支持

 $ git config --system --list                    # 查看系统的 git 配置
 $ git config --global --list                    # 查看系统当前用户的 git 配置
 $ git config --local --list                     # 查看当前库的 git 配置
 $ git config --list                             # 列出上述所有配置, 可能出现重复项
 > color.ui=true
 > user.name=facser
 > core.editor=vim
```

### 修改 git 配置

```bash
 $ git config -e                                 # 编辑配置文件
 $ git config --global core.editor vim           # 修改系统当前用户的 git 编辑器为 vim
 $ git config --global color.ui true             # 系统当前用户的 git 输出显示颜色
 $ git config --global commit.template <file>    # 设置 commit 签名模板
```

```bash
 $ git config --global user.name facser          # 设置系统当前的 git 用户名为 facser
 $ git config user.name                          # 查看当前使用的 git 用户名

 $ git config --global user.email abc@email      # 设置系统当前的 git 邮箱为 abc@email
 $ git config user.email                         # 查看当前使用的 git 用户名
```

## 仓库

|区域   |位置       |介绍                                    |
| :---: |    :--:  |                  :--:                  |
|本地仓库|当前 .git |记录文件当前状态生成一个版本并保存至本地仓库|
|远程仓库|网络平台  |将当前记录的所有版本上传到远程仓库         |

### 本地仓库

在本地任意位置使用 `git init` 即可创建一个本地仓库

- Untracked
- Changes not staged for commit
- Changes to be committed

|区域|描述|状态|
|:--:|:--:|:--:|
|Untracked|新增文件|工作区, 未被追踪|
|Changes not staged for commit|有新修改的文件|工作区, 新修改未被追踪|
|Changes to be committed|无修改的文件|暂存区, 修改已追踪|

工作区 -- `git add` --> 暂存区 -- `git commit` --> 本地仓库

### 远程仓库

将本地仓库上传到远程仓库, 或从远程仓库下载文件到本地