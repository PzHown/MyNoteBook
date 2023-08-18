# Git
日期：2023.08.18

---

[toc]

## 1. Git基本概念
+ **仓库（Repository）：** Git用仓库来存储代码，仓库可以保存所有的版本历史记录。
+ **分支（Branch）：** 分支是Git中一个重要的概念。通过创建分支，你可以在代码的不同版本之间切换。
+ **提交（Commit）：** 在Git中，每次对代码进行的更改都需要提交。提交可以记录下当前代码的状态，并保存在Git的历史记录中。
+ **合并（Merge）：** 在Git中，你可以合并不同的分支，将它们合并成一个版本。
+ **远程仓库（Remote Repository）：** 远程仓库是指存储在其他计算机或服务器上的Git仓库。你可以通过Git与远程仓库进行交互，例如推送代码、拉取代码等。

## 2. Git基础命令
``` shell
git init #初始化一个新的Git仓库。
git add <file> #将一个文件添加到Git的暂存区。
git commit -m "<message>" #将暂存区的文件提交到Git仓库，并附带一条提交信息。
git push #将本地仓库中的代码推送到远程仓库。
git pull #从远程仓库拉取最新的代码到本地仓库。
git status #查看当前仓库的状态，包括哪些文件已修改、哪些文件已经添加到暂存区等等。
git log #查看提交历史记录。
```

## 3. 从远程库克隆
``` shell
git clone <remote-url> ( <directory-name> )
```

## 4. 打标签
### 列标签
``` shell
git tag (-l "v1.8.5*")
```
可带上可选的 -l 选项 --list
### 创建标签
#### 轻量标签：
``` shell
git tag 标签名称
```
#### 附注标签:
``` shell
git tag -a 标签名称 -m '标签注释信息’
```
#### 通过指定commitId 创建:
1. 通过 `git log ` 查看历史提交记录获取commitId
2. `git tag -a 标签名称 commitId`

#### 删除标签
``` shell
git tag -d 标签名称
```
删除远程标签：
``` shell
git push test :refs/tags/标签名称
```
#### 将标签提交到远程仓库
``` shell
git push remote别名 标签名称
```