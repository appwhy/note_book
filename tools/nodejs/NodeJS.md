# NodeJS

[TOC]

<!-- toc -->

---

Node.js 是一个能够在服务器端运行 JavaScript 的开放源代码、跨平台 JavaScript 运行环境。Node.js 由 Node.js 基金会持有和维护，并与 Linux 基金会有合作关系。Node.js 采用 Google 开发的 V8 运行代码，使用**事件驱动**、**非阻塞**和**异步输入输出**模型等技术来提高性能，可优化应用程序的传输量和规模。这些技术通常用于数据密集的即时应用程序。

Node.js 大部分基本模块都用 JavaScript 语言编写。在 Node.js 出现之前，JavaScript 通常作为客户端程序设计语言使用，以 JavaScript 写出的程序常在用户的浏览器上运行。Node.js 的出现使 JavaScript 也能用于服务端编程。Node.js 含有一系列内置模块，使得程序可以脱离 Apache HTTP Server 或 IIS，作为**独立服务器**运行。

#### Node.js 特点

1. 它是一个 JavaScript 运行环境。
2. 依赖于 Chrome V8 引擎进行代码解释。
3. 事件驱动：在 Node.js 中，客户端请求建立连接，提交数据等行为，会触发相应的事件。Node.js 在一个时刻，只能执行一个事件回调函数，但是在执行一个事件回调函数的中途，可以转而处理其他事件，然后返回继续执行原事件的回调函数。
4. 非阻塞 I/O：Node.js 中采用了非阻塞型 I/O 机制，在执行了访问数据库的代码之后，将立即转而执行其后面的代码，把数据库返回结果的处理代码放在回调函数中，从而提高了程序的执行效率。
5. 轻量可伸缩，适用于实时数据交互应用。
6. 单线程：好处是减少内存开销，不用像多线程编程那样处处在意状态同步的问题。缺点是错误会引起整个应用的退出。

#### Node.js 适用场景

我们从 Node.js 的特点中可以知道 Node.js 擅长处理 I/O，不善于计算（单线程的缺点），因此 Node.js 适用于：当应用程序需要处理大量并发的 I/O，而在向客户端发出响应之前，应用程序内部并不需要进行非常复杂的处理的时候，Node.js 也非常适合与 Web socket 配合，开发长连接的实时交互应用程序。比如：聊天室，博客系统，考试系统等。

#### NPM 介绍

NPM 是随同 Node.js 一起安装的包管理工具。因此当我们安装好 Node.js 的时候，也安装好了 NPM。NPM 是一个命令行工具，用于从 NPM Registry 中下载、安装 Node.js 程序，同时解决依赖问题。

#### PEPL

Node.js REPL（Read Eval Print Loop：交互式解释器）表示一个电脑的环境，类似 Window 系统的终端或 Unix/Linux shell，我们可以在终端中输入命令，并接收系统的响应。我们可以用来执行 JavaScript 代码。

* `_`：上一个表达式的运算结果

REPL 常用命令

- `Ctrl + C` - 退出当前终端。
- `Ctrl + C` - 连续按两次退出 Node REPL。
- `Ctrl + D` - 退出 Node REPL。
- 向上/向下键 - 查看输入的历史命令。



#### 变量

在 JavaScript 中全局对象通常是 window，而在 Node.js 中全局对象是 global。所有全局变量（除了 global 本身以外）都是 global 对象的属性，我们可以直接访问到 global 的属性。

按照 ECMAScript 的定义，满足以下条件的变量是全局变量：

- 在最外层定义的变量。
- 全局对象的属性。
- 隐式定义的变量（未定义直接赋值的变量）。

注：当你定义一个全局变量的时候，这个变量同时也会成为全局对象的属性，反之亦然。在 Node.js 中你不可能在最外层定义变量，因为所有用户代码都是属于当前模块的，而模块本身不是最外层上下文。定义变量一定要使用 `var` 关键字，因为全局变量会污染命名空间。

常用的全局变量和全局函数：

1. `__filename` ：表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。如果在模块中，返回的值是模块文件的路径。
2. `__dirname` ：表示当前执行脚本所在的目录。
3. `setTimeout(callback, ms)` ：全局函数在指定的毫秒（ms）数后执行指定函数（callback），只执行一次函数。
4. `clearTimeout(t)` ：用于停止一个之前通过 `setTimeout()` 创建的定时器。参数 t 是通过 `setTimeout()` 函数创建的定时器。
5. `setInterval(cb, ms)` ：与 `setTimeout(cb, ms)` 类似，不同的是这个方法会不停的执行函数。直到 `clearInterval()` 被调用或窗口被关闭，也可以按 `Ctrl + C` 停止。
6. `console.log()` ：是个全局函数用于进行标准输出流的输出，即在控制台中显示一行字符串，和 JavaScript 中的使用一样。

#### xx

Node.js 应用组成：

1. 引入 required 模块：使用 required 指令来载入 Node.js 模块。
2. 创建服务器：服务器可以监听客户端的请求，类似于 Apache、Nginx 等 HTTP 服务器。
3. 接受请求与响应请求。



#### Node.js 包

包用于管理多个模块及其依赖关系，可以对多个模块进行封装，包的根目录必须包含 package.json 文件。package.json 文件是 CommonJS 规范用于描述包的文件，符合 CommonJS 规范的 package.json 文件一般包含以下字段：

1. name：包名。包名是唯一的，只能包含小写字母、数字和下划线。
2. version：包版本号。
3. description：包说明。
4. keywords：关键字数组，用于搜索。
5. homepage：项目主页。
6. bugs：提交 bug 的地址。
7. license：许可证。
8. maintainers：维护者数组。
9. contributors：贡献者数组。
10. repositories：项目仓库托管地址数组。
11. dependencies：包依赖。

通过命令 `npm install/update/uninstall xxx` 来安装、更新、卸载包。

#### Node.js 模块

在 JavaScript 中，我们通常把 JavaScript 代码分为几个 js 文件，然后在浏览器中将这些 js 文件合并运行，但是在 Node.js 中，是**通过以模块为单位来划分所有功能**的。每一个模块为一个 js 文件，每一个模块中定义的全局变量和函数的作用范围也被限定在这个模块之内，只有使用 exports 对象才能传递到外部使用。Node.js 官方提供了很多模块，这些模块分别实现了一种功能，如操作文件及文件系统的模块 fs，构建 http 服务的模块 http，处理文件路径的模块 path 等。当然我们也可以自己编写模块。

自定义模块示例：

```javascript
// myModule.js
function foo() {
  console.log("hello syl");
}
module.exports.foo = foo;    // module.exports 导出foo，供其他模块使用。
```

每次导出接口成员的时候都通过`module.exports.xxx = xxx` 的方式很麻烦，点儿的太多了。所以，Node.js 为了简化操作，专门提供了一个变量：`exports` 等于 `module.exports`。



在其他模块中引用：

```javascript
//  index.js
var hello = require("./myModule.js");
hello.foo();
```

`require()` 得到的是 `module.exports` 导出的值，导出多个成员可以用 `module.exports` 和 `exports`，导出单个成员只能用 `module.exports`。

注：`require()` 加载模块，以 `/` 为前缀的模块是文件的绝对路径。`./` 为前缀的模块是相对于调用 `require()` 的文件的。

当没有以 `/`、`./` 或 `../` 开头来表示文件时，这个模块必须是一个核心模块或加载自 node_modules 目录。如果给定的路径不存在，则 `require()` 会抛出一个 code 属性为 `'MODULE_NOT_FOUND'` 的 Error。

**核心模块**定义在 Node.js 源代码的 lib/ 目录下。`require()` 总是会优先加载核心模块。例如：`require('http')`  始终返回内置的 HTTP 模块，即使有同名文件。



##### 常用模块

http： 该模块主要用于搭建 HTTP 服务端和客户端，要使用 HTTP 服务器和客户端功能必须调用 http 模块。

util 是一个Node.js 核心模块，提供常用函数的集合，用于弥补核心 JavaScript 的功能 过于精简的不足。

```
const util = require('util');
```

 fs ：   该模块供了一个 API，用于以接近标准 POSIX 函数的方式与文件系统进行交互。

```js
var fs = require("fs");
fs.readFile("./index.html", function(err, data) {
      if (err) {
        console.log("文件读取失败，请稍后重试！");
      } else {
        // data 默认是二进制数据，可以通过 .toString 转为咱们能识别的字符串
      }
    });
```

所有文件系统操作都具有同步和异步的形式。异步方法中回调函数的第一个参数总是留给异常参数（exception），如果方法成功完成，那么这个参数为 null 或者 undefined。

`fs.open(path, flags[, mode], callback);`：

* path：文件的路径
* flags：文件打开的行为。
  * `a`：打开文件用于追加。如果文件不存在，则创建该文件。
  * `ax`：与 `a` 相似，但如果路径存在则失败。
  * `a+`：打开文件用于读取和追加。如果文件不存在，则创建该文件。
  * `ax+`：与 `a+` 相似，但如果路径存在则失败。
  * `as`：以同步模式打开文件用于追加。如果文件不存在，则创建该文件。
  * `as+`：以同步模式打开文件用于读取和追加。如果文件不存在，则创建该文件。
  * `r`：打开文件用于读取。如果文件不存在，则会发生异常。
  * `r+`：打开文件用于读取和写入。如果文件不存在，则会发生异常。
  `rs+`：以同步模式打开文件用于读取和写入。指示操作系统绕开本地文件系统缓存。这对于在 NFS 挂载上打开文件非常有用，因为它允许跳过可能过时的本地缓存。它对 I/O 性能有非常实际的影响，因此除非需要，否则不建议使用此标志。这不会将 fs.open() 或 fsPromises.open() * 转换为同步的阻塞调用。如果需要同步操作，则应使用 fs.openSync() 之类的操作。
  * `w`：打开文件用于写入。创建文件（如果它不存在）或截断文件（如果存在）。
  * `wx`：与 `w` 相似，但如果路径存在则失败。
  * `w+`：打开文件用于读取和写入。创建文件（如果它不存在）或截断文件（如果存在）。
  * `wx+`：与 `w+` 相似，但如果路径存在则失败。
* mode：设置文件模式(权限)，文件创建默认权限为 0o666（可读写）。mode 设置文件模式（权限和粘滞位），但仅限于创建文件的情况。在 Windows 上，只能操作写权限。
* callback：回调函数，带有两个参数如：callback(err, fd)。

`fs.openSync(path, flags[, mode])`：同步打开文件，参数和用法参照异步 `fs.open()`。在 Node.js 中我们大多是用异步的方式。

`fs.close(fd, callback);`：

- fd：通过 `fs.open()` 方法返回的文件描述符。
- callback：回调函数，除了可能的异常，完成回调没有其他参数。

使用 `fs.read()` 和 `fs.write()` 读写文件需要使用 `fs.open()` 打开文件和 `fs.close()` 关闭文件。

异步读取文件的语法格式为：

```js
fs.read(fd, buffer, offset, length, position, callback);
```

参数说明：

- fd：通过 `fs.open()` 方法返回的文件描述符。
- buffer：是数据写入的缓冲区。
- offset：是缓冲区中开始写入的偏移量。一般它的值我们写为 0。
- length：是一个整数，指定要读取的字节数。
- position：指定从文件中开始读取的位置。如果 position 为 null，则从当前文件位置读取数据，并更新文件位置。
- callback：回调函数，有三个参数 `(err, bytesRead, buffer)`。err 为错误信息，bytesRead 表示读取的字节数，buffer 为缓冲区对象。

异步写入文件的语法格式为：

```js
fs.write(fd, buffer, offset, length, position, callback);
```

参数说明：

- fd：从指定的文件写入数据。
- buffer：是数据写入的缓冲区。
- offset：指定要写入的 buffer 部分。
- length：是一个整数，指定要写入的字节数。
- position 指定应该写入此数据的文件开头的偏移量。如果 `typeof position !== 'number'`，则从当前位置写入数据。
- callback：回调有三个参数 `(err, bytesWritten, buffer)`，其中 `bytesWritten` 指定从 `buffer` 写入的字节数。

```js
fs.write(fd, string[, position[, encoding]], callback);
```

参数说明：

- fd：从指定的文件写入数据。
- string：写入的数据，如果不是字符串，则该值将被强制转换为字符串。
- position 指定应该写入此数据的文件开头的偏移量。如果 `typeof position !== 'number'`，则从当前位置写入数据。
- encoding：指定字符串的编码，默认为 'utf8'。
- callback：回调有三个参数 `(err, written, string)`，其中 written 指定字符串中已写入文件的字节数。写入的字节数与字符串的字符数是不同的。

异步读取文件的语法格式为：

```js
fs.readFile(path, [options], callback);
```

参数说明：

- path：文件名或文件描述符。
- options：该参数是一个对象，包含 `{encoding, flag}`。encoding 默认值为 null，flag 默认值为 'r'。
- callback：回调函数。

异步写入文件的语法格式为：

```js
fs.writeFile(file, data, [options], callback);
```

参数说明：

- file：文件名或文件描述符。
- data：要写入文件的数据，可以是 String（字符串）或 Buffer（缓冲）对象。
- options：该参数是一个对象，包含 `{encoding, mode, flag}`。encoding 默认值为：'utf8'，mode 默认值为 0o666，flag 默认为 'w'。
- callback：回调函数。

异步获取文件信息的格式为：

```js
fs.stat(path, callback);
```

参数说明：

- path：文件路径。
- callback：回调函数，带有两个参数如：`(err, stats)`，stats 是 `fs.Stats` 对象。如果出现错误，则 err.code 将是常见系统错误之一。

不建议在调用 `fs.open()`、`fs.readFile()` 或 `fs.writeFile()` 之前使用 `fs.stat()` 检查文件是否存在。而是，应该直接打开、读取或写入文件，并在文件不可用时处理引发的错误。

异步删除文件的语法格式为：

```js
fs.unlink(path, callback);
```

参数说明：

- path：文件路径。
- callback: 除了可能的异常，完成回调没有其他参数。

异步的修改文件名的语法为：

```js
fs.rename(oldPath, newPath, callback);
```

参数说明：

- oldPath：原来的文件名字。
- newPath：新的文件名字。
- callback：回调函数，除了可能的异常，完成回调没有其他参数。

异步创建目录的语法为：

```js
fs.mkdir(path[, options], callback);
```

参数说明：

- path：文件路径。
- options：有两个参数。recursive 表示是否以递归的方式创建目录，默认为 false。mode 设置目录权限，Windows 上不支持。默认为 0o777。
- callback：回调函数，除了可能的异常，完成回调没有其他参数。

异步读取目录的语法为：

```js
fs.readdir(path[, options], callback);
```

参数说明：

- path：文件路径。
- options：有两个参数 `(encoding，withFileTypes)`。encoding 默认值为 'utf8'，withFileTypes 默认值为 false。
- callback：回调函数，回调函数带有两个参数 `(err, files)`。err 为错误信息，files 为目录下的文件数组列表。

异步删除目录的语法为：

```js
fs.rmdir(path, callback);
```

参数说明：

- path：文件路径。
- callback：回调函数，除了可能的异常，完成回调没有其他参数。

#### 函数

在 JavaScript 中，一个函数可以作为另一个函数的参数。

`function xxx(arg1, arg2){ xxx }`

**匿名函数**就是没有命名的函数。语法为：`function(){ xxx }`

ES6 标准新增了一种**箭头函数**，该函数表达式的语法比函数表达式更短，并且没有自己的 `this`，`arguments`，`super` 或 `new.target`。这些函数表达式更适用于那些本来需要匿名函数的地方，并且它们不能用作构造函数。

```js
(arg1, arg2, ... , argN) => {函数声明}

// 相当于：(arg1, arg2, ... , argN) => {return 表达式;}
(arg1, arg2, ... , argN) => 表达式（单一）

// 当只有一个参数时，圆括号是可选的
(arg) => {函数声明}
arg => {函数声明}

// 没有参数的函数应该写成一对圆括号
() => {函数声明}
```

**回调函数**：Node.js 异步编程的直接体现就是回调。回调函数在完成任务后就会被调用，Node.js 使用了大量的回调函数，Node.js 所有 API 都支持回调函数。回调函数一般作为函数的**最后一个参数**出现。

#### 事件

大多数 Node.js 核心 API 构建于惯用的异步事件驱动架构，其中某些类型的对象（又称触发器，Emitter）会触发命名事件来调用函数（又称监听器，Listener）。比如：`fs.readStream` 打开文件时会发出一个事件。

可以通过 `require("events");` 获得 `event` 模块。通常，事件名采用“小驼峰式”（即第一个单词全小写，后面的单词首字母大写，其它字母小写）命名方式。

所有能触发事件的对象都是 `EventEmitter` 类的实例。这些对象有一个 `eventEmitter.on()` 函数，用于将一个或多个函数绑定到命名事件上。当 `EventEmitter` 对象触发一个事件时，所有绑定在该事件上的函数都会被同步地调用。

参数说明：

- eventName：事件名称，string 类型。
- listener：回调函数。
- args：传递的参数，多个，类型为任意。

 **`EventEmitter` 类的实例`emitter`：**

* `addListener(eventName, listener)` 或 `on(eventName, listener)` ：为指定事件注册一个监听器。添加 `listener` 函数到名为 `eventName` 的事件的监听器数组的末尾。不会检查 `listener` 是否已被添加。多次调用并传入相同的 `eventName` 与 `listener` 会导致 `listener` 会被添加多次。

- `prependListener()`：用于将事件监听器添加到监听器数组的开头。默认情况下，事件监听器会按照添加的顺序依次调用。
-  `once(eventName, listener)` ：可以注册最多可调用一次的监听器。当事件被触发时，监听器会被注销，然后再调用。

*  `emit(eventName[, ...args])` ：按照监听器注册的顺序，同步地调用每个注册到名为 eventName 的事件的监听器，并传入提供的参数。如果事件有注册监听返回 true，否则返回 false。

*  `removeListener(eventName, listener)` 或 `off(eventName, listener)`：移除监听器。最多只会从监听器数组中移除一个监听器。我们可以多次调用该方法来一个个的移除我们需要移除掉的监听器。

-  `removeAllListeners([eventName])` 移除全部监听器或指定的 `eventName` 事件的监听器。

*  `setMaxListeners(n)` ：设置同一事件的监听器最大绑定数。默认情况下，如果为特定事件添加了超过 10 个监听器，则 `EventEmitter` 会打印一个警告，这有助于我们发现内存泄露。显然实际编码中并不是所有的事件都要限制 10 个监听器。当值设为 Infinity（或 0）表示不限制监听器的数量。
*  `listenerCount(eventName)` ：查看事件绑定的监听器个数。



一旦事件被触发，所有绑定到该事件的监听器都会按顺序依次调用。也就是说在事件触发之后、且最后一个监听器执行完成之前，`removeListener()` 或 `removeAllListeners()` 不会从 `emit()` 中移除它们。

当 `EventEmitter` 实例出错时，应该触发 'error' 事件。如果没有为`error`事件注册监听器，则当`error` 事件触发时，会抛出错误、打印堆栈跟踪、并退出 Node.js 进程。

#### Web 框架：Express

Express 是一个高度包容，快速而极简的 Node.js Web 框架，提供了一系列强大特性帮助我们创建各种 Web 应用，和丰富的 HTTP 工具。我们可以通过 Express 可以快速地搭建一个完整功能的网站。使用框架的目的就是让我们更加专注于业务，而不是底层细节。

安装：`npm install express`

```js
var express = require("express");
var app = express();

// app.post
app.get("/", function(req, res) {
  res.send("Hello World");
});

app.listen(8080, function() {
  console.log("服务器启动了");
});
```

路由用于确定应用程序如何响应客户端请求，包含一个 URI（路径）和一个特定的 HTTP 请求方法（GET、POST 等）。

每个路由可以具有一个或多个处理程序函数，这些函数在路由匹配时执行。

路由定义采用以下结构：

```js
app.method(path, handler);
```

注：`app` 是 Express 的实例，`method` 是指 HTTP 请求方法（GET、POST 等），`path` 是指服务器上的路径，`handler` 是指路由匹配时执行的函数。

Express 提供了内置的中间件 `express.static` 来设置静态文件如：图片，CSS，JavaScript 等。比如：

```js
// 我们只有公开了 public 目录，才可以直接通过 /public/xx 的方式访问 public 目录中的资源
app.use("/public/", express.static("./public/"));
```



















