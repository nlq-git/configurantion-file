# 1、拉团队

不需要成员的SSH KEY

# 2、github创建开发分支

dev分支用来开发发布版，从master分支上创建的，所以与master分支内容一致。

# 3、Fork项目到个人仓库

点击fork，选择自己的账号。

# 4、Clone项目到本地

clone地址推荐用SSH，clone自己仓库里的项目

`git clone 链接`

```
##此时只能看见master分支，看不到dev分支。

git branch          ##查看本地分支，会发现本地也只有master分支

git branch -a       ##查看所有分支，可看见远程分支。

新建一个本地分支dev，把dev的内容放到本地dev分支里。

git checkout -b dev origin/dev      ##创建一个dev分支（-b），并把远程dev分支（origin/dev）的内容放在该分支内。接着切换到该分支（checkout）

git branch    ##查看两个分支，用ls  dir可看见dev内容

git checkout master     ##切回主支


```
# 5、和团队项目保持同步

先查看有没有设置upstream
```
git remote -v    ##查看upstream

如果没有显示upstream，则使用

git remote add upstream 团队项目地址

再次使用git remote -v，出现了upstream远程库连接就设置好了

git fetch upstream   ##获取最新版本项目

git merge upstream/dev    ##讲缘分支dev合并到当前分支
```

# 6、提交commit并push修改至自己的仓库

`git commit -m "... "             ##提交到本地库`

`git push       ##在当前分支用push会Push到与这个分支相关联的远程分支。`

# 7、请求合并

首先到你的GitHub上，进入你Fork的仓库里。点击红框处的Pull request

当然，在发送请求之前，你可以检查一下你都改了哪些东西。在上面那个页面往下拉，就可以看到两者的对比。

以上操作结束后，团队成员的流程就结束了。最后一步交给团队项目负责人来完成。

# 8、团队项目负责人审核及同意合并请求

首先进入GitHub的团队项目仓库中。此时右边的Pull requests显示当前项目有几个Pull request。点击进入查看。

项目负责人审核有两个要注意的地方

1、一定要看清楚是合并到哪个分支。这里是从schaepher的dev分支合并到fzu2015的dev分支。

2、点击File changed，就可以查看该Pull request对项目做了哪些修改。这样如果有问题，可以及时发现，并关闭该Pull request。

如果没有问题，可以点击Merge pull request。这样就合并好了


