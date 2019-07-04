# GradeSystem

jetbrain 快捷键：

ctrl + c 复制当前行

ctrl + x 剪切当前行

ctrl + tab 切换窗口

ctrl + home 光标定义到文件开头

ctrl + end 光标定义到文件结尾

ctrl + left/right 一个单词一个单词的转跳

ctrl + a 全选

ctrl + alt + l 格化选中内容

ctrl + l 注释选中内同

ctrl + y 快速删除一行

**笔记**
***2019/7/1***

do：建立git仓库以及Django项目，连接数据库

1. 创建git 项目

ssh-keygen 生成git公钥

git init

git remote add origin XXXXXX


2. git新建项目时因为有readme导致git pull不成功，出现错误的主要原因是github

中的README.md文件不在本地代码目录中[：pull=fetch+merge]

使用 git pull --rebase origin master 



3. 新建django框架后 添加app 在命令行中输入

python manage.py startapp users

在setting的INSTALLED_APPS = [] 添加新建的app名字



4. 连接MySQL数据库
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        #'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
        'NAME': 'GradeSystem',
        'USER': 'root',
        'PASSWORD': 'root.',
        'HOST': '127.0.0.1',
        'PORT': '3306',
    }
}
```


django.core.exceptions.ImproperlyConfigured: Error loading MySQLdb module.错误

在init添加
```
import pymysql

pymysql.install_as_MySQLdb()
```
```
django.core.exceptions.ImproperlyConfigured: mysqlclient 1.3.13 or newer is required; you have 0.9.3.
Python36-32\Lib\site-packages\django\db\backends\mysql\base.py下的 
 if version < (1, 3, 13):
     raise ImproperlyConfigured('mysqlclient 1.3.13 or newer is required; you have %s.' % Database.__version__)
```
注释掉



AttributeError: 'str' object has no attribute 'decode'错误

同上的operations.py 的decode改成encode

python manage.py makemigrations  与 python manage.py migrate 对数据库进行操作。

******

***2019/07/03***
1. 迭代器
当创建一个列表后,你就可以一个接着一个地读取它的元素, 这种操作就叫做迭代(iteration):

2. 生成器
除了把[]换成()之外，生成器看起来和列表推导式没有什么不同。但是，调用之后，你不能再次使用for i in mygenerator，因为生成器只可以被迭代一次：它计算出0，然后计算出1，同时丢弃掉0，然后最终计算出4，丢弃掉1，一个接着一个。

计算空间的时候，迭代器存储生成的全部元素，但是生成器就只存储地址，在要使用数据的时候才加以生成相应的元素

yield关键字

yield是一个类似与return的关键字，只是这个函数会返回的是一个生成器（Generator）

***2019/07/04***

1.  列表为中括号[]，可修改内部元素，元组为小括号，不可修改内部元素，集合为大括号。  
2. 类和对象，类是泛指，对象是对类的实例化。  
3. __init__是一个特殊方法用于在创建对象时进行初始化操作，在Python中，属性和方法的访问权限只有两种，也就是公开的和私有的，如果希望属性是私有的，在给属性命名时可以用两个下划线作为开头。  

大多数Python程序员会遵循一种命名惯例就是让属性名以单下划线开头来表示属性是受保护的，本类之外的代码在访问这样的属性时应该要保持慎重。这种做法并不是语法上的规则，单下划线开头的属性和方法外界仍然是可以访问的，所以更多的时候它是一种暗示或隐喻。  

面向对象有三大支柱：封装、继承和多态。  

封装的理解是“隐藏一切可以隐藏的实现细节，只向外界暴露（提供）简单的编程接口”。我们在类中定义的方法其实就是把数据和对数据的操作封装起来了，在我们创建了对象之后，只需要给对象发送一个消息（调用方法）就可以执行方法中的代码，也就是说我们只需要知道方法的名字和传入的参数（方法的外部视图），而不需要知道方法内部的实现细节（方法的内部视图）。