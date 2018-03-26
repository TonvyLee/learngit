Git is a version control system;
Git is free software;
Git is a version control system;
Git is free software;

1、本地创建：ssh key
ssh-keygen -t rsa -C "your_email@youremail.com"

会在~/路径下生成.ssh文件夹，进去将id_rsa.pub里面的key复制到github上的ssh keys

2、验证是否成功：ssh -T git@github.com
显示 ：you have successfully authenticated

3、设置username和email，因为github每次commit都会记录他们：
git config --global user.name "yourname"
git config --global user.email "youremail"

4、然后进入到要上传的仓库，右键git bash，添加远程地址：
git remote add origin git@github.com:yourName/yourRepository.git
( 链接到远程仓库，并为该仓库建立别名，别名为origin，可以自定义，通常就这个，在后续的pull或者push的时候会用到这个别名)

5、创建upstream，并将本地代码并将本地代码通过这个 upStream 推送到 别名为 origin 的仓库中的 master 分支上
git push -u origin master

6、修改本地代码，然后提交：
git add .
git commit -m "提交说明"//将修改后的代码先提交到本地仓库
git pull		//多人协作开发，一定先pull，将github代码拉取到本地，这样在merge解决冲突的时候稍微简便些。默认拉取到master分支，如果只是自己做该项目，可以忽略pull

7、git push		//将代码push到github，默认推送到别名为origin的仓库中的master分支上。

8、注意事项：
如果有多个分支或者多个仓库，并且需要将代码推送到仓库指定的分支上，那么需要在pull或者push的时候，就需要按照下面的格式：
git pull 仓库名 仓库分支名
git push 仓库名 仓库分支名

出现failed to push some refs to ....的办法：
执行：git pull --rebase origin master


9、分支：

假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险，怎么办？

你可以创建一个属于自己的分支，别人看不见，还继续在原来的分支上工作，而你在自己的分支上进行开发，等开发完毕，合并即可。

在开源世界中，需用大量的程序员共同维护一个项目。也是需要使用分支，如Jquery。

基本操作有如下几个：

-1. 查看当前分支 （git branch）

-2. 创建分支 （git branch 分支名）

-3.切换分支（git checkout 分支名）

-4.分支上的常规操作

-5.分支的合并 （git checkout master + git merge 分支名）
		分支的合并，一定是在 主分支上进行的。
		只能在主分支合并其它分支。
		需要两步：
		1） 切换到主分支
		2） 使用git merge 分支名 进行合并

-6.分支的删除（git branch -d 分支名）

查看当前分支 （git branch），其中的 * 表示 当前分支。默认情况下，只有一个master主分支。

/*************************************************************************
分为如下几个步骤：

1.创建一个git裸服务器 （git init --bare）

2.从裸服务器将版本库克隆至本地（git clone ）

3.本地常规操作

4.推送版本至服务器 （git remote +  git push origin master）

5.从远程服务器拉取版本（git pull）

一般而言，我们需要在Linux服务器上来搭建我们的git版本服务器，每个公司都会有。

由项目负责人开始。

利用其他局域网的电脑测试你的仓库
ourunix@ubuntu:~/test$ git clone ssh://你的用户名@你的IP/home/～/testgit/.git 
git clone host160:/tmp/test1.git
/*************************************************************************