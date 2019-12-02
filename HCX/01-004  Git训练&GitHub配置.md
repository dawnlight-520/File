# 004  git  / git hub

## 1.创建github社区账号

### 	通过百度搜索github 进入到git社区中，创建自己的账号

## 2.创建自己的仓库

### 	点击右上角+号，选择新存储库选项，然后创建库

​	![Alt text](/home/han/桌面/Git/创建git仓库.png)

### 3.安装本地git软件

### 		3.1.打开终端  输入命令：sudo apt-get install git

### 		3.2.验证git是否安装成功，输出命令：git version

### 		3.3.配置用户名和邮箱，输入命令：	

```
git config --global user.name "XXXX"         配置用户名，用户名为上面自己创建的github的账号
git config --global user.email  "XXXXXXXXXX"    配置邮箱，确保邮箱存在且正确
```

### 		3.4.查看是否配置成功，输入命令：git config --list

### 		3.5.配置Git的私钥和公钥.密码为空.  输入命令：

```
	ssh-keygen -t rsa  -C "用户邮箱"      注：出来需要输入的东西，直接回车
```

### 		3.6.证书已经生成成功，进入指定路径下，输入命令：

```
cd ~/.ssh/                                    ：查看是否生成成功
```

### 		3.7.打开github社区，选择头像下的设置选项中的SSH和GPC密钥被选项

​	![Alt text](/home/han/桌面/Git/上传密钥.png)

### 		3.8.看到上面的GitHub的SSH配置后,在新建一个SSH Key.

​		![](/home/han/桌面/Git/密钥名字及密钥.png)

### 		3.9.vim 打开Git的公钥证书.(在上述查看证书的文件夹下)

```
vim id_rsa.pub         
```

### 		3.10.打开证书文件，复制文件中全部的文字，到GitHub中的key中	

​		注：无需换行![](/home/han/桌面/Git/复制证书密钥.png)

### 		3.11.验证Git是否配置成功

```
ssh git@github.com                       ：出现下述话语，配置成功
```

![](/home/han/桌面/Git/验证是否配置成功.png)

## 4.Git仓库基础操作

注：在你用户目录中创建一个文件夹，进入之后输入下面命令：

#### 4.1.创建新仓库

* ## 创建文件夹

  cd /			回到根目录/$

  cd~			回到家目录~$

  cd   			回到主目录~/$

  mkdir 文件夹名			创建文件夹名

  touch / vim  文件名				创建文件名

* ## 添加和提交

```
git init            注：初始化当前文件夹为Git本地仓库，
git add 文件名					提出更改（把它们添加到暂存区）
git commit -m "first commit"				提交注释信息
git remote add origin https://github.com/dawnlight-520/521.git
git push -u origin master				此时改动已经在本地仓库HEAD中，执行命令将改动提交到远程端仓库

```

* ## 推送改动

创建一个新远程的仓库

邀请组员

组员克隆文件；修改/往远程仓库推送

组长整理到提交推送

han@han-ThinkPad-T420:~/four$ vim 4.txt

han@han-ThinkPad-T420:~/four$ git init

han@han-ThinkPad-T420:~/four$ git add 4.txt

han@han-ThinkPad-T420:~/four$ git commit -m "first commit"

han@han-ThinkPad-T420:~/four$ git remote add origin https://github.com/dawnlight-520/521.git

han@han-ThinkPad-T420:~/four$ git push -u origin master

han@han-ThinkPad-T420:~/four$ git branch

han@han-ThinkPad-T420:~/four$ git checkout -b hcx
切换到一个新分支 'hcx'

han@han-ThinkPad-T420:~/four$ vim 1.txt

han@han-ThinkPad-T420:~/four$ git add 1.txt

han@han-ThinkPad-T420:~/four$ git commit -m '提交文件'

han@han-ThinkPad-T420:~/four$ git push origin hcx:hcx

获取新分支han@han-ThinkPad-T420:~/four$ git fetch -a                                                                          展开对象中: 100% (6/6), 完成.
来自 https://github.com/dawnlight-520/521

*[新分支]          ppp        -> origin/ppp

*[新分支]          yu         -> origin/yu

han@han-ThinkPad-T420:~/four$ git merge origin/ppp

han@han-ThinkPad-T420:~/four$ git merge origin/yu

han@han-ThinkPad-T420:~/four$ git status
位于分支 hcx
未跟踪的文件:
  （使用 "git add <文件>..." 以包含要提交的内容）

	查看是否有未提交文件，若有则使用"git add ."进行再次提交即可

提交为空，但是存在尚未跟踪的文件（使用 "git add" 建立跟踪）

han@han-ThinkPad-T420:~/four$ git checkout master

han@han-ThinkPad-T420:~/four$ git branch

han@han-ThinkPad-T420:~/four$ git merge hcx
更新 c267e4c..8567e16
Fast-forward
 1.txt | 1 +
 5.txt | 0
 a.txt | 4 ++++
 3 files changed, 5 insertions(+)
 create mode 100644 1.txt
 create mode 100644 5.txt
 create mode 100644 a.txt

han@han-ThinkPad-T420:~/four$ git status

han@han-ThinkPad-T420:~/four$ git add .
han@han-ThinkPad-T420:~/four$ git commit -m '远程提交'

han@han-ThinkPad-T420:~/four$ git push origin master:master
对象计数中: 7, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (6/6), 完成.
写入对象中: 100% (7/7), 811 bytes | 811.00 KiB/s, 完成.
Total 7 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/dawnlight-520/521.git
   c267e4c..7e4bb3a  master -> master

han@han-ThinkPad-T420:~/four$ git checkout hcx
切换到分支 'hcx'

han@han-ThinkPad-T420:~/four$ vim a.txt
han@han-ThinkPad-T420:~/four$ vim 5.txt
han@han-ThinkPad-T420:~/four$ vim 1.txt
han@han-ThinkPad-T420:~/four$ git checkout master
M	5.txt
M	a.txt
切换到分支 'master'
您的分支与上游分支 'origin/master' 一致。
han@han-ThinkPad-T420:~/four$ git status
位于分支 master
您的分支与上游分支 'origin/master' 一致。

尚未暂存以备提交的变更：
  （使用 "git add <文件>..." 更新要提交的内容）
  （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

```
修改：     5.txt
修改：     a.txt
```

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
han@han-ThinkPad-T420:~/four$ git add .
han@han-ThinkPad-T420:~/four$ git commit -m '修改'
[master 0722fd3] 修改
 2 files changed, 10 insertions(+), 1 deletion(-)
han@han-ThinkPad-T420:~/four$ git push origin master:master
对象计数中: 4, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (4/4), 完成.
写入对象中: 100% (4/4), 602 bytes | 602.00 KiB/s, 完成.
Total 4 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/dawnlight-520/521.git
   7e4bb3a..0722fd3  master -> master
han@han-ThinkPad-T420:~/four$ git checkout master
已经位于 'master'
您的分支与上游分支 'origin/master' 一致。
han@han-ThinkPad-T420:~/four$ git checkout hcx
切换到分支 'hcx'

# 5.注意事项

本地及远程更新:git push -u origin master -f

![](/home/han/桌面/Git/注意事项.png)