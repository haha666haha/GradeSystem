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

4. 连接MySQL数据库

DATABASES = {

    'default': {

        'ENGINE': 'django.db.backends.mysql'
        ,
        #'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),

        'NAME': 'GradeSystem',

        'USER': 'root',

        'PASSWORD': 'root.',

        'HOST': '127.0.0.1',

        'PORT': '3306',

    }

}

django.core.exceptions.ImproperlyConfigured: Error loading MySQLdb module.错误

在init添加

import pymysql

pymysql.install_as_MySQLdb()

django.core.exceptions.ImproperlyConfigured: mysqlclient 1.3.13 or newer is required; you have 0.9.3.

Python36-32\Lib\site-packages\django\db\backends\mysql\base.py下的 
# if version < (1, 3, 13):

#     raise ImproperlyConfigured('mysqlclient 1.3.13 or newer is required; you have %s.' % Database.__version__)

注释掉

AttributeError: 'str' object has no attribute 'decode'

同上的operations.py 的decode改成encode

python manage.py makemigrations  与 python manage.py migrate 对数据库进行操作。

