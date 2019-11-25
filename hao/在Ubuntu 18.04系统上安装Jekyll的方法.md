#### 在Ubuntu 18.04系统上安装Jekyll的方法

参考网址：https://ywnz.com/linuxyffq/4335.html

#### 组长流程：

1；创建库:  mkdir 库名

2；打开库：cd 库名

3；设置为git仓库： git int

4；创建文件：touch 文件名

5；添加文件：git add 文件名（git add . 是添加全部文件）

6；提交+注释： git commit -m "注释"

7；git remoteadd origin ...

8；git push -u origin master

9；查看本地所有分支： git branch

10；在Git社区给组员发克隆连接并发送邮箱邀请

11；切换到新分支： git  checkout  -b 分支名

12；查看本地所有分支： git branch

13；创建库:  mkdir 库名

14；打开库：cd 库名

15；创建文件：touch 文件名

16；添加文件：git add 文件名（git add . 是添加全部文件）

17；提交+注释： git commit -m "注释"

18；推送自己的分支：git push origin 支名：支名

19；查看本地所有分支： git branch

20；将远程最新内容拉到本地：git fetch -a

21；一个一个合并：git merge origin/组员分支名

22；查看：ls

23；查看当前状态：git  status

24；切换到master分支：git checkout master

25；查看本地所以分支： git branch

26；在自己master中合并自己支名：git merge 支名

27；查看本地所以分支： git branch

28；添加全部文件：git add .

29；提交+注释： git commit -m "注释"

30；推送的远程仓库：git push origin master:master

#### 组员流程：

1；建立自己的文件                命令  mkdir  文件名

2；进入到自己的文件下     命令   cd  /

3；clone 别人的网址      命令   git clone 

4；ls 查看有那些目录      命令  ls

5；进入到他的目录下      命令  cd 别人的目录

6；建立自己的分支        命令   git checkout -b   分支名11

7；在自己的分支下上传你的文件    命令   git add  文件名

8；提交文件        命令  git commit -m   '别名'

9；推送到远程      命令   git push  -u  origin      分支名11:随意的别名



>