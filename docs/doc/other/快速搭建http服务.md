# 快速搭建http服务

[TOC]

<!-- toc -->

---

有时想要通过浏览器来浏览linux上的相关文件，此时可以在linux上运行http服务。

## 方法1： python自带服务

### python2

可以通过如下命令快速启动一个简单的http服务：

```bash
python -m SimpleHTTPServer port
```

注：SimpleHTTPServer是linux机器上python2自带的一个WEB服务器，不需要自己安装。

### python3

```bash
python -m  http.server 8000
```





## 方法2：`jupyter notebook`

使用python安装jupyter，然后启动notebook服务。



### 方法3：nodejs的http-server

首先需要在linux上安装nodejs，如果是非root用户，可以下载二进制包，然后把对应的bin目录添加到PATH变量中。（不将其加入PATH变量，直接运行可能会出错）



然后安装 http-server ：

```bash
npm install -g http-server
```

启动http服务：

```bash
http-server -p 8000
```























