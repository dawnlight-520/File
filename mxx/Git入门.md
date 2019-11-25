## Git入门

使用Git前，需要先建立一个仓库(repository)。您可以使用一个已经存在的目录作为Git仓库或创建一个空目录。

使用您当前目录作为Git仓库，我们只需使它初始化。

### 提交流程如下：

```
git init   初始化
git add README.md   添加需要提交的文档
git commit -m "first commit"   提交文档并添加注释
git remote add origin https://github.com/mxlxx/ss.git   连接git服务器
git push -u origin master   推送至git仓库
```

```
从命令行推送现有存储库
git remote add origin https://github.com/mxlxx/ss.git
git push -u origin master
 
 从另一个存储库导入代码
<a href="https://github.com/mxlxx/ss/import">地址<a>
```

git init

使用我们指定目录作为Git仓库。

```
git init newrepo
```

从现在开始，我们将假设您在Git仓库根目录下，除非另有说明。

### 添加新文件

---

我们有一个仓库，但什么也没有，可以使用add命令添加文件。

```
git add filename
```

可以使用add... 继续添加任务文件。

### 提交版本

---

git现在我们已经添加了这些文件，我们希望它们能够真正被保存在Git仓库。

为此，我们将它们提交到仓库。

```
git commit -m "Adding files"
```

如果您不使用-m，会出现编辑器来让你写自己的注释信息。

当我们修改了很多文件，而不想每一个都add，想commit自动来提交本地修改，我们可以使用-a标识。

```
git commit -a -m "Changed some files"
```

git commit 命令的-a选项可将所有**被修改或者已删除的且已经被git管理的文档**提交到仓库中。

*** **千万注意，-a不会造成新文件被提交，只能修改。**

### 发布版本

我们先从服务器克隆一个库并上传。

```
git clone ssh://example.com/~/www/project.git
```

现在我们修改之后可以进行推送到服务器。

```
git push ssh://example.com/~/www/project.git
```

### 取回更新

如果您已经按上面的进行push，下面命令表示，当前分支自动与唯一一个追踪分支进行合并。

```
git pull
```

从非默认位置更新到指定的url。

```
git pull http://git.example.com/project.git
```

### 删除

如何你想从资源库中删除文件，我们使用rm。

```
git rm file
```

### 分支与合并

分支在本地完成，速度快。要创建一个新的分支，我们使用branch命令。

```
git checkout -b 分支名字     创建分支并进入该分支 
git branch test git    进入该分支
```

branch命令不会将我们带入分支，只是创建一个新分支。所以我们使用checkout命令来更改分支。

```
git checkout test       checkout 检测
```

第一个分支，或主分支，被称为"master"。

```
git checkout master    切换分支
```

对其他分支的更改不会反映在主分支上。如果想将更改提交到主分支，则需切换回master分支，然后使用合并。

```
git checkout master
git merge test
```

如果您想删除分支，我们使用-d标识。

```
git branch -d test
```

配置用户名密码本机下次不用重新输入：

git config --global credential.helper store

---

#### 操作更新

本地操作之后需要和远端同步更新一下，即输入以下命令

git push -u origin 分支名字 -f



# git分支操作

git鼓励使用分支：
查看分支：git branch
查看所有分支列表：git branch -a
创建分支：git branch name
切换分支：git checkout name
创建+切换分支：git checkout -b name
合并某分支到当前分支：git merge name
删除分支：git branch -d name

	迁移时所有代码、提交记录、分支等均保持了原来的
	
	1

迁移后已迁移的无需重新下载，直接命令行修改下push的远程仓库地址：

修改命令 ：git remote set-url origin
例：git remote set-url origin ssh://git@bitbucket.aaa.com:7999/cc/aa.git
git pull <远程库名> <远程分支名>:<本地分支名>
例如：git pull origin develop:develop
git checkout 分支名称 ----->进入这个分支后，
git pull origin 目标分支 就会将目标分支代码拉到此分支；
如何撤销git pull ？
本来想把github上的newpbft合并到本地的newpbft分支上，由 于没有查看当前分支，直接运用git pull origin newpbft，结果将newpbft合并到了master分支中。
1、运行git reflog命令查看你的历史变更记录；
2、然后用git reset --hard HEAD@{n}，（n是你要回退到的引用位置）回退。 git reset --hard 40a9a83

    如果是想要将feature-xx分支拉develop上的代码，为git pull origin develop:feature-xx；如果拉去失败，可以通过git或对应的git远程仓库界面工具对比featrue-xx与develop分支差异，手动更新到最新，在进行新需求开发；
    
    1

如何将本地修改提到分支上：

1.git将当前分支上修改的东西转移到新建分支
比如我在A分支做了一些修改，现在由于某种原因(如A分支已经合并到master)不能把A分支上修改的东西保留下来但是需要把A分支上修改的东西继续在新分支继续修改。那么现在我们可以有两种简单的做法完成这一需求。
第一种方法
我们不需要在A分支做commit,只需要在A分支新建B分支，然后切换过去。这个时候你会发现修改的东西在A，B分支都有。这个时候在B分支commit，那么这些修改保留在B分支上，再切换到A分支上会发现修改都没有保留下来。
第二种方法
使用git stash 将A分支暂存起来，然后在某一个分支（如master分支）新建一个分支B，然后在B分支上使用git stash pop 将修改弹出到B分支上，然后这些修改就在B分支上了。