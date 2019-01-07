# GitStudy
Git学习笔记
撰写本文的目的有两个，其一是记录自己学习github过程中我用到的文献，方便以后自己忘记之后在做查找。其二是练习使用markdown语法。
## github入门级教程
1.注册
登录[GitHub](https://github.com/)，点击sign up注册，如果已经有账号，点击sign in登录。
2.创建Repository
登录后点击人物头像旁边的小加号
在里面创建新项目
* 注意:在里面可以点上一个√，会自动创建一个README.md文件 *
3.配置git环境
先下载git文件 [点击此处下载git](https://git-scm.com/downloads)，下载完成后，自己安装，安装完成后开始菜单点击GitBash，输入
```
$ git config --global user.name "Your Name" 
$ git config --global user.email "email@example.com"
```
进行链接你的GitHub。
* 这块直接设么设置不行。此处这么设置的本意是以后在提交的时候都不需要输入用户名和密码，但是方法不对，不输入用户名密码可以在git clone时候使用ssh方式，或者配置秘钥，不推荐，因为不安全。 *
链接完成后，选择一个合适的位置，创建一个本地库文件夹，有两种方式创建本地库。
1.在github建好的库中copy库的地址，然后在文件夹中右击，git bash here，然后输入
```
git clone ...
```
其中...部分用从github中copy的网址替代，这样git就会自动在本地建立一个库，用来写东西。
2.通过git init来把这个目录变成Git可以管理的仓库：
```
git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```
在文件夹中自己新建一个文件。如readme.txt，然后就可以在里面编辑了。（最好不要用自带的txt）
4.上传代码
在上一步创建的文件夹下，右击，gitbash，使用git add命令将文件上传到暂存区
```
git add readme.txt
```
此时可能出现错误
```
$ git add .
warning: LF will be replaced by CRLF in git学习笔记.md.
The file will have its original line endings in your working directory
```
可以用
```
$ git config --global core.autocrlf false
```
来解决，原因是路径中存在 / 的符号转义问题，false就是不转换符号默认是true，相当于把路径的 / 符号进行转义，这样添加的时候就有问题。
然后使用git commit命令添加到暂存区
```
git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```
引号中间的部分是对本次修改的描述，方便以后检查。
最后可以用git push 来上传代码。
```
git push origin master
```
* 附:git命令合集 *
git log 查看历史版本
git reset --hard HEAD^ 恢复到上一个版本HEAD^^上上个版本，HEAD~100前100个版本，如果记得后面版本的版本号的话，还可以用git reset --hard HEAD 1094a 来恢复到后面的版本。其中，1094a是版本号的前几位，可以在git log中查看过去的版本号，在git reflog查看未来的版本号。
cat readme.md 查看文件内容。
*写在最后:用一个简单的比喻来说明这几个步骤，一个小兵(文档)，排队上直升机(add)，上了直升机直升机没起飞(commit)，飞机起飞了(push)，小兵排队时候挨了一枪(状态改变)的状态(status 红色)，挨了一枪的小兵排队(status 绿色)。*

参考资料:[廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)