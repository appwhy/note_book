# vagrant

[TOC]

<!-- toc -->

---

vagrant主要用来快速搭建虚拟机， 一般和virtual box配合使用。

首先下载安装vagrant（只有命令行，无图形界面）和virtual box。

查看vagrant是否安装成功： `vagrant version`



## 创建虚拟机

首先创建一个空目录，然后在该目录下执行：`vagrant init centos/7` ， 使用centos7初始化



## 常用命令

```bash
# 以下操作均在安装镜像的那个目录（有Vagrantfile配置文件所在的目录）运行

# 安装及启动虚拟机
vagrant up

# 登录进入虚拟机的控制台,进入之后，就和操作一台linux机器是一样的。 user:vagrant pwd: vagrant
vagrant ssh

# 停止这台虚拟机
vagrant halt

# 销毁这台虚拟机
vagrant destroy

# 将当前运行的虚拟机实例打包成文件，以box后缀结尾
vagrant package

# 使用box文件
vagrant box add '自定义名称' xx.box
```


## vagrant备份

1. package打包
    `vagrant package --output newbox_name.box`: 在当前目录下运行的vagrant打包成box文件
    * --base NAME：virtualbox程序里面的虚拟机的名称，不是box的名字也不是Vagrantfile里面的虚拟机名称.默认是打包当前目录下面的虚拟机。
    * --output NAME：要打包成的box名称，不会自动添加.box后缀，要手动加.默认值package.box
    * --include FILE...            打包时包含的文件名，你可以把.box文件理解为一个压缩包
    * --vagrantfile FILE           打包时包含的Vagrantfile文件，原理和上面类似
2. `box add`
3. `init`
4. 修改Vagrantfile文件
`config.ssh.username = "vagrant"`
`config.ssh.password = "vagrant"`
5. 重启: reload

