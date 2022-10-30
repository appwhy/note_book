## linux

`:e` ：vim刷新正在浏览的文件。



python脚本运行区别：

* `#!/usr/bin/env python` ：如果当前设置了python虚拟环境，该命令会找到虚拟环境中的python
* `#!/usr/bin/python` ：硬编码，根据路径查找python





tree：显示目录结构。参数：

* `-d`：只显示目录，不显示文件
* `-C`：给文件目录加上颜色，用以区分
* `-a`：显示所有，包括 隐藏文件、目录
* `-L n`：只显示前n层目录



nohup：后台运行命令（不挂断地运行）

`nohup cmd&`

查看后台进程：`jobs -l`

### 常用命令

删除文件夹下的某些文件： `find venv -name  "*.pyc" | xargs rm -rf` ，删除venv目录下的所有pyc文件

`find . -name '__pycache__' -type d -exec rm -rf {}\;` : 删除pycache


## date命令：时间戳转换

```bash
date
# 输出:
# Sat Oct  8 16:32:43 CST 2022

date +%s
# 输出:  当前时间戳
# 1665217954

date -d '2021-08-29 19:25:18' +%s
# 输出:  当前时间戳
# 1630236318

date -d @1630236318
# 输出:
# Sun Aug 29 19:25:18 CST 2021

# 指定格式
date -d @1630236318 +"%Y-%m-%d %H:%M:%S"
# 输出:
# 2021-08-29 19:25:18
```





## 查看进程相关信息

[Linux 使用strace命令查找进程卡死原因](https://blog.csdn.net/chenyulancn/article/details/123525842)



## gdb调试python进程



https://devguide.python.org/advanced-tools/gdb.html

https://www.cnblogs.com/vincenshen/articles/8470617.html

https://www.likecs.com/show-203875452.html



```bash
# python+pyenv调试正在运行的进程
vim ~/.gdbinit
# 添加以下内容
# add-auto-load-safe-path /path/to/python3.6-gdb.py

gdb attach pid
```



## 查看文件编码

```bash
file -i filename

file -i a.go
# 输出:
# a.go: text/x-c; charset=utf-8
```



## awk使用

awk打印单引号, 需要在单引号前面加上'\\'
打印双引号, 只需要在双引号前加上反斜杠。



```bash
# 将日志中的shi'ji
cat xx | awk '{"date -d @\""$1"\" +\"%Y-%m-%d %H:%M:%S\"" | getline var;printf("【%s】 %s\n",var, $0)}'
```







## 编码转换

```
iconv -f [from_encoding] -t [utf8] -o [output_file_name] [input_file_name]
```



## mv移动隐藏目录、文件

```bash
mv .[^.]* ../xx/
# .[^.]* 的意思是：以.开头，加不是.的一个任意字符，再加其他任意字符
```







