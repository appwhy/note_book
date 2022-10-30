# vscode-插件

[TOC]

<!-- toc -->

---

## 插件

- Python Docstring Generator : Python注释自动生成：`Ctrl+Shift+2`

- vscode-icons： 这是一个美化VS Code图标的插件。

- git插件：
  - GitLens
  - Git History
  - Git Graph

#### 更强大的自动补全

搜索Kite。然后需要安装一个叫 [Kite Engine](https://link.zhihu.com/?target=https%3A//kite.com/) 的软件，直接前往官网下载对应的系统版本即可：

#### TabNine

基于GPT-2语言模型的自动补全工具。

传统的补全工具更多的是根据上下文信息和第三方库进行补全，换句话说就是基于**既有**的内容进行补全。而TabNine更多的是偏向**推理**，它能够根据开发者前面输入的内容快速推理接下来要输入的代码，甚至参数、字符串、符号它都能够准确的推理并补全。

#### Bookmarks

常用命令：

* `Bookmarks: Toggle` :  添加书签。快捷键 `Ctrl+Alt+K`
* `Bookmarks: Toggle Labled` : 为书签添加别名，显示时就不会显示代码，而是别名。
* `Bookmarks: List` :  列出当前文件的书签
* `Bookmarks: List from All Files` :  列出所有文件的书签
* `Bookmarks: Focus on Explorer View` : 在左边的侧边栏显示所有书签
* `Bookmarks: Clear` : 清除当前文件的书签
* `Bookmarks: Clear from All Files` : 慎用

#### TODO Highlight

我们在开发过程中，有时会为了测试或某种原因，某段代码需要之后进行修改和完善。如果就不做一些标记，时间久了、需要修改的多了，就很难区分出哪些是需要修改的、哪些是不需要修改的。因此养成做标记的好习惯对提升开发效率具有很大的帮助。

配置可以写在 `User` 级别上，可以全局应用。

主要是2个命令：

* `TODO-Highlight: Toggle highlight` : 启动/关闭 相关标记的高亮显示
* `TODO-Highlight: List highlight annotations` :  在下方的OUTPUT窗口中显示所有标记

`DEBUG`  、`TODO` 是两个内置的标记，其他的需要自己配置

#### Code Runner

这是一款支持C、C++、Java、Python等主流编程语言快速运行的插件，它能够便捷的运行当前活动页代码文件、能够运行选定代码段、运行自定义命令，对于调试代码具有很大的帮助。

#### 文件及文件夹图标

默认的VSCode图标没有那么详细，只有几个重要文件类型的图标提示，可以安装vscode-icons解决，

#### 生成注释格式

docstring，由Nils Werner开发的autoDocstring，

#### 画图: Plantuml，Graphviz，Drawio

Plantuml我主要用来绘制流程图，时序图，非常强大，这两种图用代码描述起来直观方便，有时也能替代一些思考过程。
Drawio绘制一些复杂的图，像一些教材上的那种展示图，比如《深入理解Linux内核》中那些数据结构的图片，用Plantuml就难以绘制。但使用Drawio加上自带手绘风格，比较漂亮，对标Visio

Graphviz一般是在代码中自动生成的的，展示一些数据流，Profile结果什么的，基本上不会去手动写。

#### json插件：pretty json

#### Increment Selection: vscode同时编辑多行，插入递增数字

`Ctrl+shift+i`：会插入递增数字，从0开始。如果已经选中了某个数字，则会以该数字为起点递增

#### Code alignment：使代码的某个地段对其，只对每行的第一次出现起作用

---

## Alignment

**Alignment**这款插件能够根据=、:、*=、+=、=>、/=等符号对选中代码快速对齐，这样有助于创建干净、格式化的代码。

## **Better Align**

整洁的代码，是一个优秀程序员必须要做到的。当我们阅读那些大型公司开源的代码时，会发现，它的设计模式、它的编程规范都让人赞叹不已。

**Better Align**就是这样一款能够实现代码规范的工具，它主要用于代码的**上下对齐**。

它能够用冒号（：）、赋值（=，+=，-=，*=，/=）和箭头（=>）对齐代码。

## Project Manager

功能：

- 将任何文件夹另存为**项目**
- 将任何工作空间另存为**项目**
- 自动检测**的Git**，**水银**或**SVN**存放区
- 在相同或新窗口中打开项目
- 识别*已删除/重命名的*项目
- 一个**状态栏**标识当前项目
- 专用**侧栏**



## Debug Visualizer

调试过程可视化是一项非常有价值且急需的功能。

当实现一个算法时，中间数据经历的过程我们看不见、摸不着，只能通过开发者自身的水平去把控。

如果忽略了中间的某些细节，只能从最终结果中发掘有问题，回头定位的成本会很高。

而有了**Debug Visualizer**，它可以让调试过程更直观的展示在你眼前，这样不仅对于编程语言初学者理解算法有很大帮助，对有一定经验的开发者也能够很大程度上提升开发效率。

目前这款插件对JavaScript/TypeScript能够全面支持，功能比较丰富。对Go、Python、C#、PHP、Java、C++、Swift、Rust也提供了基础的支持，通过一些简单的配置同样可以实现调试过程可视化。



## 彩虹括号 ,让括号更易识别

名称: Rainbow Brackets

括号颜色成对出现

##  **Bracket Pair Colorizer**

给`()`、`[]`、`{}`这些常用括号显示不同颜色，当点击对应括号时能够用线段直接链接到一起，让层次结构一目了然。除此之外，它还支持用户自定义符号。

## 路径补全

名称: Path Intellisense

## **Rainbow csv**

Rainbow csv是一款提升CSV查看和编辑效率的神器。

Rainbow csv提供了几项强大的特性轻松解决VS Code在CSV文件中遇到的问题：

- 高亮，轻松区分每一列
- 悬浮，能够区分每一列的标题头信息
- 自动检查CSV文件一致性
- 列模式编辑
- 能够用空格对齐
- 能够用类SQL语言搜索查询



##  **Codelf**

使用时只需要选中变量名，然后**右键**选择CodeIf就可以跳转到网页，显示候选命名。

## **local history**

安装这款插件之后在侧边栏会出现**LOCAL HISTORY**的字样，每当我们保存更改时，它都会备份一份历史文件，当我们需要恢复之前版本时，只需要点击一下对应的文件即可。此外，它还会在编辑框显示**对比详情**，能够让你对修改位置一目了然。



## **Partial Diff**



**文件比较**是一种即常用有实用的一项功能，例如，我们想查看哪里修改了代码、查看输出的日志信息有什么区别等等，如果用肉眼逐个词的去分辨，显然是无法承受的。

选中一代码，右键**Select Text for Compare**，选中另外一部分代码，右键**Compare Text with Previous Selection**即可。



## TODO Tree

**TODO Tree**则不同，它不仅可以实现**标签高亮**，还可以在活动栏添加一个选项卡，它能够以不同视图展示我们标记的位置，单击对应标签就能够快速定位到指定位置。

## 翻译(translate to chinese)

Ctrl+Shift+T：右下角弹出中文翻译


## vscodez支持json5插件： JSON5 syntax

将.json与json5绑定
```json
    "files.associations": {
        "*.json": "json5"
    },
```

## 自动激活python虚拟环境

```json
"python.terminal.activateEnvironment": false,
```

## html预览

live server



## Draw.io Integration 在vscode中画流程图












