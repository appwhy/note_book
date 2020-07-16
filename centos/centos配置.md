# 模板

[TOC]

<!-- toc -->

---

### screen

**root**用户可以直接用`yum install screen`命令安装screen

如果没有root权限，可以采用源码编译安装的方法。

参考：[参考博客](https://blog.csdn.net/m0_37584687/article/details/88958204)

相关源码地址：

* screen：http://ftp.gnu.org/gnu/screen/
* ncurses：http://ftp.gnu.org/gnu/ncurses/



下载screen源码，解压后进入源码目录，执行以下命令安装：

```bash
./configure --prefix=/home/username/screen_dir
```

如果出现如下错误信息：

```bash
configure: error: !!! no tgetent - no screen
```

说明缺乏ncurses依赖，下载源码安装：

```bash
# 进入ncurses源码目录
./configure --prefix=/home/username/ncurses_dir
make
make install

# 如果第一条命令运行后有Error，可用如下命令尝试替换：
# ./configure --refix=/home/username/ncurses_dir --with-shared --without-debug --without-ada --enable-overwrite
```

之后就可以安装screen了：

```bash
# 配置相关环境变量
export LDFLAGS='-L/home/username/ncurses_dir/lib'
export CPPFLAGS='-I/home/username/ncurses_dir/include'

# 安装screen
./configure --prefix='/home/username/screen_dir'
make
make install

```

这样就能将screen安装到screen_dir目录下了。接着在.bashrc文件里设置screen执行路径，加入export PATH=/home/username/screen_dir/bin:$PATH，接着执行source .bashrc更新PATH，在终端输入screen就能进入screen界面了。

### java jdk

非root用户安装java。

将下载好的tar包进行解压，然后进行配置文件，在命令行敲入  vi ~/.bashrc，在这个文件中配置java的路径，添加以下：

配置 `~/.bashrc` 文件：

```bash
export JAVA_HOME=/path/to//jdk
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH   
```





