# GradeSystem

**笔记**
***2019/7/1***
1. 创建git 项目

ssh-keygen 生成git公钥

git init

git remote add origin XXXXXX


2. git新建项目时因为有readme导致git pull不成功，出现错误的主要原因是github

中的README.md文件不在本地代码目录中【注：pull=fetch+merge]

使用 git pull --rebase origin master 

3. 新建django框架后 添加app 在命令行中输入

python manage.py startapp users

在setting的INSTALLED_APPS = [] 添加新建的app名字


