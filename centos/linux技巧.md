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







