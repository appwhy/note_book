



# python



## timezone

timezone是tzinfo的子类, tzinfo是一个描述时区信息对象的抽象基类。
timezone 一个实现了 tzinfo 抽象基类的子类，用于表示相对于 世界标准时间（UTC）的偏移量。

```
In [131]: timezone
Out[131]: datetime.timezone

In [132]: tzinfo
Out[132]: datetime.tzinfo

In [133]: issubclass(timezone, tzinfo)
Out[133]: True
```

datetime.datetime所代表的时间缺省是不包括时区信息的。时区是一个社会和法律的概念。

[盘一盘 Python 特别篇 18 - 时区|夏令时](https://cloud.tencent.com/developer/article/1655617)



[Python datetime 格式化字符串：strftime()](https://www.cnblogs.com/fwl8888/p/9635505.html)



## pip重装包

该包的所有依赖包都会被重装
```bash
pip install --upgrade --force-reinstall --no-cache-dir -i https://pypi.tuna.tsinghua.edu.cn/simple python-dateutil
```



删包再装包

```bash
pip uninstall python-dateutil
pip install python-dateutil
```



## sqlalchemy

使用反射，查出来的数据对象类型

```
指定完整的model：
<class 'sqlalchemy.ext.automap.user_info'>
该对象有 x.__dict__ 属性

使用model的几项：
<class 'sqlalchemy.util._collections.result'>
该对象有 x._asdict() 属性
```







## python相关小工具



展示pickle内容
`python -m pickle x.pickle`

展示pickle的每个字节
`python -m pickletools x.pickle`

将字符串转成json
`echo '{"json":"obj"}' | python -m json.tool`



## 假DB: TinyDB

实际上是使用json文件模拟相关操作

```bash
pip install tinydb
```



```python
from tinydb import TinyDB, Query
db = TinyDB('db.json')
```

https://tinydb.readthedocs.io/en/latest/getting-started.html



## FPT：Python搭建FTP服务器

```bash
pip install pyftpdlib
```



参考： [python搭建FTP服务器](https://cloud.tencent.com/developer/article/1569297)

server：

```python
import os

from pyftpdlib.authorizers import DummyAuthorizer
from pyftpdlib.handlers import FTPHandler
from pyftpdlib.servers import FTPServer

def main():
    # 实例化用户授权管理
    authorizer = DummyAuthorizer()
    authorizer.add_user('user', '12345', 'path', perm='elradfmwMT')#添加用户 参数:username,password,允许的路径,权限
    authorizer.add_anonymous(os.getcwd())#这里是允许匿名用户,如果不允许删掉此行即可

    # 实例化FTPHandler
    handler = FTPHandler
    handler.authorizer = authorizer

    # 设定一个客户端链接时的标语
    handler.banner = "pyftpdlib based ftpd ready."

    #handler.masquerade_address = '151.25.42.11'#指定伪装ip地址
    #handler.passive_ports = range(60000, 65535)#指定允许的端口范围

    address = (ipaddr, 21)#FTP一般使用21,20端口
    server = FTPServer(address, handler)#FTP服务器实例

    # set a limit for connections
    server.max_cons = 256
    server.max_cons_per_ip = 5

    # 开启服务器
    server.serve_forever()

if __name__ == '__main__':
    main()
```



client:

```python
from ftplib import FTP

ftp=FTP()
ftp.connect('localhost', 21)#localhost改成服务器ip地址
ftp.login(user='user', passwd='12345')

file=open('/data/test.txt', 'wb')
ftp.retrbinary("test.txt", file.write, 1024)#从服务器上下载文件 1024字节一个块
ftp.set_debuglevel(0)
ftp.close()
```



## 其他

[Python3.7 dataclass使用指南](https://www.cnblogs.com/apocelipes/p/10284346.html)



```python
from dataclasses import asdict, astuple

from dataclasses import is_dataclass
```



[Python 正则表达式](https://www.runoob.com/python/python-reg-expressions.html)



[深入理解 Python 中的上下文管理器](https://www.cnblogs.com/wongbingming/p/10519553.html)







## 常用的有用包

### stackprinter：打印更详细的错误堆栈信息

```bash
pip3 install stackprinter
```



在程序的开头写以下代码，会对未被捕获的异常打印详细堆栈信息

```python
import stackprinter
stackprinter.set_excepthook()
```

其他包：

* https://github.com/Qix-/better-exceptions
* https://github.com/andy-landy/traceback_with_variables





## 自己建包

[Python 小技巧: Namespace Package](https://dboyliao.medium.com/python-%E5%B0%8F%E6%8A%80%E5%B7%A7-namespace-package-9587368e5329)

[打包命名空间包](https://www.osgeo.cn/python-packaging/guides/packaging-namespace-packages.html)

```python
setup(
    name="dboy-package1",
    packages=setuptools.PEP420PackageFinder.find(),
    namespace_packages=["dboy"],
    zip_safe=False
)
```

参考谷歌包：`google-cloud-bigquery` 与`google-cloud-dataproc`

[setup.py里的几个require](https://note.qidong.name/2018/01/python-setup-requires/)
