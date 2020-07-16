# VS Code

[TOC]

<!-- toc -->

------

VS Code 的定位是`编辑器`，而非`IDE`。但 VS Code 又比一般的编辑器的功能要丰富许多。

VS Code 自带了 TypeScript 和 Node.js 的支持。也就是说，你在书写 JS 和 TS 时，是自带智能提示的。

## 面板命令

上面：

`Ctrl+Shift+ P` 或 `F1`：打开仪表盘，可以搜索所有命令



左边：

`Ctrl+B`：打开/关闭左边的文件导航（sidebar）。隐藏/显示侧边栏

`Ctrl+ Shift+E`：打开Explorer

`Ctrl+ Shift+F`：搜索所有文件

`Ctrl+ Shift+ G`：打开源代码管理（git）

` CtrI+ Shift+ D`：打开Debug

`Ctrl+ Shift+X`：打开扩展 extension



下面：

`Ctrl+J`：快速打开/关闭下方的Panel

`CtrI+ Shift+ M`：打开"errors and warnings"窗口。message。按第二次可以关闭

`CtrI+ Shift+ U`：打开Output窗口。按第二次可以关闭

**Ctrl + `**：打开terminal。按第二次可以关闭



文件跳转：

`Ctrl+\`：split editor。按 `Ctrl+1/2/3`进行跳转

`Ctrl+F4` ：关闭当前打开的文件

`Ctrl+Tab`：显示当前打开的所有文件。按`tab` 进行选择

`Alt+←/→`：选择前/后一个文件。前后是指你浏览文件的前后，不是打开文件在屏幕上的前后。

------

## 命令板

`Ctrl+P`：键入文件名，会快速打开某个文件

- 直接输入文件名，`Enter`后打开该文件， `Ctrl+Enter` 则会在水平窗口中打开。
- 键入文件名后，按`→` 键，会打开相应文件，但不退出命令板，可以继续打开其他文件
- `?`：列出当前可执行的命令。命令后面跟一个空格，则会进入下一级。如键入`term+space`，就会出现一个下拉列表，包含所有terminal名字。
- `@`：显示所有symbol。 跳转到 `symbol`（搜索变量或者函数），也可以 `Ctrl+Shift+O` 直接进入
- `@:`：分类显示symbol
- `:`：跳到某行。可以使用`Ctrl+G`快速打开
- ?  `#` 根据名字查找 `symbol`，也可以 `Ctrl+T`



`Ctrl+R`：快速打开最近打开过的文件夹或workspace

------

## 光标操作

- `Ctrl+Home` ： 光标移到文件开头
- `Ctrl+End`：光标移到文件结尾。
- `Ctrl+U`：光标退回上一个位置。
- `Ctrl+←/→`：光标左移/右移一个单词
- `Ctrl+Backspace`：删除光标前一个单词
- `Ctrl+Delete`：删除光标后面的一个单词

## 多光标编辑

`Shift + ←/↑/→/↓` : 选择块

`Shift+Alt + 光标选择`：选择方块内容，会在方块的每一行中都有一个光标

`Ctrl+Alt + ↑/↓` : 在上/下一行添加光标

`Ctrl+Shift+L`：选择所有的单词（当前光标所处的单词），在单词后添加光标

- `Ctrl+F2` : Change all Occurrences of Current Word
- `Ctrl+Shift+L` : Select All Occurrences of Current Selection

`Ctrl+D`：选中当前光标处的单词，再按一次，则选中下一个相同的单词

多光标：按住Alt键，然后在页面中希望中现光标的位置点击鼠标。

`Alt + Shift + i`：在选中的文本的每一行的末尾都创建一个光标。

## 文本编辑

- `Ctrl+Shift+K`：删除当前行。
- `Ctrl + Enter`：在当前行下面新增一行然后跳至该行。
- `Ctrl + Shift + Enter`：在当前行上面增加一行并跳至该行。
- `Alt+↑↓`：将当前行向上/下移动。
- `Shift+Alt+↑/↓`：复制当前行到上/下一行
- `Ctrl+C `：复制选中内容或者复制当前行
- `Ctrl+X`：切剪选中内容或者当前行
- `Ctrl+F`：查找。光标定位不在搜索框时，使用F3进行上下查找
- `Ctrl+Shift+F`：文件夹中查找（在多个文件中查找字符串）
- `Ctrl+H`：替换
- `Ctrl+/`：行注释
- ？ `Shift+Alt+A`：块注释

---

* `Ctrl+[/]`：将当前行进行左右缩进

## IntelliSense

VS Code 为当前工作文件夹中的所有文件，以及安装在标准位置的 Python 包提供了代码补全和智能提示 。

VS Code 收集代码的范围是基于当前工作区文件夹，和`settings.json` 中的 `python.pythonPath` 参数而定的。

如果引用的项目既不在工作区内，也不在 Python 库文件夹里，VS Code 无法知道它在哪。这时候需要提供额外的路径去搜寻代码，如下：

```json
# .vscode\settings.json
{
    "python.autoComplete.extraPaths": ["any/path"],
}
```



`Ctrl+Space`：代码提示，因为热键冲突，将其改为了 `Alt+/`



## linting（代码静态检查）

代码分析工具（pep8、flake8、pylint）

VS Code 默认的静态检查工具是 pylint 。

官方的默认配置：

```json
{
    "python.linting.pylintPath": "global/path/to/pylint",
    "python.linting.pylintArgs": [
        "--disable=all",
        "--enable=F,E,unreachable,duplicate-key,unnecessary-semicolon,global-variable-not-assigned,unused-variable,binary-op-exception,bad-format-string,anomalous-backslash-in-string,bad-open-mode",      
    ],
}
```

注：可以使用单词描述，也是用使用代号，如`E0401`。

`python.linting.pylintPath` 的作用是指定 pylint 的路径，如果不填则默认使用当前工作区指定的 Python 环境中的 pylint。如果虚拟环境多的话，每一个环境中都要安装一遍 pylint，很麻烦，可以全局使用同一个 pylint。

使用全局 pylint 有一点需要注意，因为不同环境中安装的包不一样，必须在静态检查是引入相关的环境下的包，在 `--init-hook`中把虚拟环境下第三方包的路径导入`sys.path`即可。

```json
{
    "python.linting.pylintArgs": [
        "--init-hook",
        "import sys; sys.path.insert(0, './modules'); sys.path.extend(['${workspaceFolder}/venv/Lib/site-packages',]); ",
    ]
}
```



## 重命名

`F2`：重命名某个symbol。注，先把光标放到要重命名的symbol上，跟它相关的symbol会闪烁。

`Ctrl+F2`：重命名当前光标所在的单词（全文替换）。 类似 `Ctrl+H`替换

## Formatting

自动格式化代码。目前支持 autopep8、black 和 yapf。

常用的是 `autopep8`：

```json
# .vscode/settings.json
{
    "python.formatting.autopep8Path": "/path/to/Python/Scripts/autopep8",
}
```



`Shift+Alt+F`：重新组织代码，也可以使用右键进行选择

`Ctrl+K Ctrl+F`：只对当前选中部分（current selection）起作用

## 折叠

`Ctrl+Shift+[/]`：折叠/展开当前块

`Ctrl+K Ctrl+[/]`：递归折叠/展开当前块 

`Ctrl+K Ctrl+0/J`：折叠/展开整个文件中的所有块



## 源文件浏览（Go to References）

`Ctrl+鼠标单击` 或 `F12`：快速跳转到源文件

`Alt+F12`：打开一个peek，不跳转到源文件

`Shift+F12`：打开一个peek，查看源文件的所有引用

`Shift+Alt+F12`：在左边的sidebar显示所有symbol的引用



## git

`F7` / `Shift+F7` ：进入单文件diff，按 `Enter`重新回到双文件diff。



## 其他

按住`Alt` ，然后滚动，可以比直接滚动更快。

`Shift+Alt+←/→`：Shrink / expand selection。扩大/缩小选择范围

`Ctrl+K Ctrl+X`：快速去除不必要的空格。只能去除行尾的



`Ctrl+D`：选中光标所在的单词



`Ctrl+←/→`：每次光标移动一个单词，而不是一个字符



排序import语句：右键选择“排序import语句”



提取方法/变量需要安装Python库 `rope`

---

选中字符串， `Ctrl+Shift+P` 调出命令面板，找到命令 “Transform to Lowercase/Uppercase”。





## 关于code的命令行



```bash
# open code with current directory
code .

# open the current directory in the most recently used code window
code -r .

# create a new window
code -n

# change the language
code --locale=es

# open diff editor
code --diff <file1> <file2>

# open file at specific line and column <file:line[:character]>
code --goto package.json:10:5

# see help options
code --help

# disable all extensions
code --disable-extensions .
```



## 单元测试

VS Code 还支持单元测试框架 pytest、unittest 和 nosetest。

## 调试

- `tasks.json`：Task Runner

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "echo",
            "type": "shell",
            "command": "echo hello world",
        },
        {
            "label": "ls",
            "type": "shell",
            "command": "ls -al"
        }
    ]
}
```



* `launch.json`：debugger

```json
{
     "name": "Python: startup.py",
     "type": "python",
     "request": "launch",
     "program": "${workspaceFolder}/startup.py",
     "console": "integratedTerminal",
     "args" : ["--port", "1593"],
     "preLaunchTask": "ls"
},
```

默认参数：

* `name` : 该调试显示的名称
* `type` : 调试类型。如 `node` 、`python`
* `program` :  调试的具体文件，一般有2种写法
  * `${workspaceFolder}/file.py` : 某个具体的文件
  * `${file}` ： 调试当前文件
* `console` : 
  * `internalConsole` :  在vscode的调试控制台(Debug Console)中输出结果
  * `integratedTerminal` : 在vscode 集成的terminal 中输出结果
  * `externalTerminal` : 打开另外的terminal输出结果
* `request` : 
  * `launch` ： VSCode 会打开这个程序然后进入调试
  * `attach` ： 通过`Process ID`，对正在运行的程序进行调试

其他参数：

* `python` : 自定义Python解释器的位置
  * 添加参数： `"python": ["<path>", "<arg>",...]`

* `args` : 一些（自定义）的参数。
* `cwd` ：程序运行的工作目录，默认为 `${workspaceFolder}`
* `preLaunchTask` : 在调试前运行的命令，需要在task.json中编写



## PYTHONPATH

有2处可以修改`PYTHONPATH`：

1：settings.json

```json
"terminal.integrated.env.windows": {        # windows可以替换为linux，看自己机器
        "PYTHONPATH": "${workspaceFolder}"
    },
```

2：`.env` 文件：

```
# settings.json
"python.envFile": "${workspaceFolder}/.vscode/.env",

# .env
PYTHONPATH="${workspaceFolder}"
```



> When the terminal settings are used, PYTHONPATH affects any tools that are run within the terminal by a user, as well as any action the extension performs for a user that is routed through the terminal such as debugging. However, in this case when the extension is performing an action that isn't routed through the terminal, such as the use of a linter or formatter, then this setting will not have an effect on module look-up.

> When PYTHONPATH is set using an `.env` file, it will affect anything the extension does on your behalf and actions performed by the debugger, but it will not affect tools run in the terminal.



## 常用占位符

* `${workspaceFolder}` ：项目根目录（VS Code打开的目录）
* `${file}` : 当前打开的文件
* `${relativefile}`：当前文件相对于 `${workspaceFolder}` 的路径
* `${cwd}`：current working directory on startup



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
