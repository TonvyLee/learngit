Git is a version control system;
Git is free software;
Git is a version control system;
Git is free software;

本地创建：ssh key
ssh -keygen -t sa -C "your_email@youremail.com"

会在~/路径下生成.ssh文件夹，进去将id_rsa.pub里面的key复制到github上的ssh keys

验证是否成功：ssh -T git@github.com
显示 ：you have successfully authenticated

设置username和email，因为github每次commit都会记录他们：
git config --global user.name "yourname"
git config --global user.email "youremail"

然后进入到要上传的仓库，右键git bash，添加远程地址：
git remote add origin git@github.com:yourName/yourRepository.git
( 链接到远程仓库，并为该仓库建立别名，别名为origin，可以自定义，通常就这个，在后续的pull或者push的时候会用到这个别名)

创建upstream，并将本地代码并将本地代码通过这个 upStream 推送到 别名为 origin 的仓库中的 master 分支上
git push -u origin master

修改本地代码，然后提交：
git add .
git commit -m "提交说明"//将修改后的代码先提交到本地仓库
git pull		//多人协作开发，一定先pull，将github代码拉取到本地，这样在merge解决冲突的时候稍微简便些。默认拉取到master分支，如果只是自己做该项目，可以忽略pull

git push		//将代码push到github，默认推送到别名为origin的仓库中的master分支上。

注意事项：
如果有多个分支或者多个仓库，并且需要将代码推送到仓库指定的分支上，那么需要在pull或者push的时候，就需要按照下面的格式：
git pull 仓库名 仓库分支名
git push 仓库名 仓库分支名
