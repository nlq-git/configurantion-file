##  1.安装git

 `sudo apt-get install git` 
##  2.生成密钥，将密钥添加到github
 ```
 cd ~
 ssh-keygen -t rsa -C "123456@qq.com"     //填自己邮箱，最好用github的注册邮箱
 cd ~/.ssh/
 vim id_rsa.pub     //i一下复制
 ```
 - 登录github右上角settings
 
   打开“Account settings”，“SSH Keys and GPG keys”页面
   
   然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容即可。
   
   最后“Add Key”
   
   //！允许添加多个Key，把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。

 在GitHub上免费托管的Git仓库，任何人都可以看到（但只有你自己才能改）。
 - 创建仓库
 点Create a new repo可以看见提示了
  
## 3.配置本地用户和邮箱
 ```
  git config --global user.name "reber-9"
 
  git config --global user.email "123456@qq.com"
  
 ```
## 4.按提示关联+同步
```
 #进入要同步工程目录
 
 #新建本地仓库：
 git init  
 
 #添加文件到本地仓库：
 git add XX     //所有文件用 git add.
 
 
 #提交到本地库并备注，此时变更仍在本地
 git commit -m "first commit"

 #完成后增加远程服务器别名：
 git remote add origin https://github.com/xxx/xxx.git     //https这一部分就是网页工程主页的链接复制过来
 
                              //origin远程库名
 
 #推送：
 git push -u origin master    //master分支名
 

 
 #会提示输入github账号密码
 ```
 


## 附
-若是已有某文件夹已经同步过github了，之后往里面新增了文件，想要把它添加到github的库中，需要三步即可
 ```
    git add
    git commit -m “XXX”
    git push -u origin master
 ```
-远程同步至本地
 ```
 git pull remotename branchname       //fetch+merge两个操作
 或
 git pull git://github.com/tom/test.git  //用链接同步某个文件
 
 ```
 -克隆
 `git clone git@github.com:用户名/工程名.git`
 
 
# 团队开发（仓库连接版）

## 确定项目拥有者，让他建立一个github组织，邀请所有成员。

-成员在自己电脑中生成一个ssh key，每个人的都发送给拥有者，拥有者添加密钥（！队友不能在github使用这个密钥）
-所有人连接这个仓库
-成员现在本地clone我的项目

`git clone https://github.com/nlq-git/ship-collision-prevention      ##(我的为例)`

-初始化
`git init`

-将本地仓库与远程仓库连接起来
`git remote add https://github.com/nlq-git/ship-collision-prevention`
`git remote -v               ##可查看连接上的仓库`

-可以添加上传文件  
`git add.            ##.是所有文件，可具体文件名，如下：`
`git   add  html/test.html`

-本地提交 
`git commit -m "一般是第几次提交或版本号" `
`git pull  ##可加仓库地址，查看本地仓库是否更新为最新的，不成功可能没连接上仓库`

-推送
git push （可加仓库地址）

