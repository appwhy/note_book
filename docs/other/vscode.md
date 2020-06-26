# VS Code

[TOC]

<!-- toc -->

---

@sort:installs sublime text



左边：

`Ctrl+ Shift+E`：打开Explorer

`Ctrl+ Shift+F`：搜索所有文件

`Ctrl+ Shift+ G`：打开源代码管理（git）

` CtrI+ Shift+ D`：打开Debug

`Ctrl+ Shift+X`：打开扩展 extension



下面：

`Ctrl+J`：快速打开/关闭下方的Panel

`CtrI+ Shift+ M`：打开"errors and warnings"窗口。message。按第二次可以关闭

`CtrI+ Shift+ U`：打开Output窗口。按第二次可以关闭

`Ctrl+Shift+ P`：打开仪表盘，可以搜索所有命令

Ctrl + `：打开terminal。按第二次可以关闭



`Ctrl+B`：打开/关闭左边的文件导航（sidebar）



文件跳转：

`Ctrl+\`：split editor。按 `Ctrl+1/2/3`进行跳转

`Ctrl+F4` ：关闭当前打开的文件

`Ctrl+Tab`：显示当前打开的所有文件。按`tab` 进行选择

`Alt+←/→`：选择前/后一个文件

---

## 多光标编辑

`Shift + ←/↑/→/↓` : 选择块

`Shift+Alt + 光标选择`：选择方块内容，会在方块的每一行中都有一个光标

`Ctrl+Alt + ↑/↓` : 在上/下一行添加光标

`Ctrl+Shift+L`：选择所有的单词（当前光标所处的单词），在单词后添加光标

* `Ctrl+F2` : Change all Occurrences
* `Ctrl+Shift+L` : Select All Occurrences of Find Match

`Ctrl+D`：选中当前光标处的单词，再按一次，则选中下一个相同的单词

## IntelliSense

`Ctrl+Space`：代码提示，有趣热键冲突，将其改为了 `Alt+/`



## 行操作

`Shift+Alt+↑/↓`：复制当前行到上/下一行

`Ctrl+Shift+K`：删除当前行

`Ctrl+C`：复制当前行，或复制选中内容

`Ctrl+X`：切剪当前行，或切剪选中内容。可以当作删除当前行来用



`Alt+↑/↓`：移动当前行到上/下一行

`Ctrl+/`：注释当前行



### 重命名

`F2`：重命名某个symbol。注，先把光标放到要重命名的symbol上，跟它相关的symbol会闪烁。

`Ctrl+F2`：重命名当前光标所在的单词（全文替换）。 类似 `Ctrl+H`替换

## Formatting

`Shift+Alt+F`：重新组织代码，也可以使用右键进行选择

`Ctrl+K Ctrl+F`：只对当前选中部分（current selection）起作用

## 折叠

`Ctrl+Shift+[/]`：折叠/展开当前块

`Ctrl+K Ctrl+[/]`：递归折叠/展开当前块 

`Ctrl+K Ctrl+0/J`：折叠/展开整个文件中的所有块



## 命令板

`Ctrl+P`：键入文件名，会快速打开某个文件

* 键入文件名后，按`→` 键，会打开相应文件，但不退出命令板，可以继续打开其他文件
* `?`：会提供相应提示。命令后面跟一个空格，则会进入下一级。如键入`term+space`，就会出现一个下拉列表，包含所有terminal名字
* `@`：显示所有symbol
* `@:`：分类显示symbol
* `:`：跳到某行。可以使用`Ctrl+G`快速打开



`Ctrl+R`：快速打开最近打开过的文件夹或workspace

## 其他

按住`Alt` ，然后滚动，可以比直接滚动更快。

`Shift+Alt+←/→`：Shrink / expand selection

`Ctrl+K Ctrl+X`：快速去除不必要的空格。只能去除行尾的



`Ctrl+D`：选中光标所在的单词



`Ctrl+鼠标单击` 或 `F12`：快速跳转到源文件

`Alt+F12`：打开一个peek，不跳转到源文件

`Shift+F12`：打开一个peek，查看源文件的所有引用

`Shift+Alt+F12`：在左边的sidebar显示所有symbol的引用



## git

`F7` / `Shift+F7` ：进入单文件diff，按 `Enter`重新回到双文件diff。



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







## .vscode

* `tasks.json`：Task Runner
* `launch.json`：debugger







---

## 直播



```bash
conda create -n learn_python36 python=3.6

conda env list
```



Pylint: Python代码静态检查

yapf:自动整理Python代码工具





## 插件

Python DocstringGenerator

Python注释自动生成：`Ctrl+Shift+2`



vscode-icons： 这是一个美化VS Code图标的插件。



git插件：

* GitLens
* Git History
* Git Graph



提取方法/变量需要安装Python库 `rope`







---

常见操作：

•Intellisense

•配置静态代码检查工具pylint

•配置Python代码自动格式化工具black/yapf

•排序import语句

•移动语句块

•提取方法

•多光标编辑

•自动路径补全

•Python交互式运行界面

•调试控制台

---

format简略写法：

```python
print('a+b={}'.format(a+b))
print(f'a+b={a+b}')
```



---

vscode配置

```json
    "files.exclude": {
        "**/__pycache__": true,
        "python.linting.pylintArgs": [
            "--init-hook",
            "import sys; sys.path.insert(0, './lib'); sys.path.insert(0, './src')",
            "--disable=all",
            "--enable=F,E,unreachable,duplicate-key,unnecessary-semicolon,global-variable-not-assigned,unused-variable,binary-op-exception,bad-format-string,anomalous-backslash-in-string,bad-open-mode"
        ]
    }
```

disable与enable是官方推荐



---

























