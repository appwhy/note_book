# windows配置

[TOC]

<!-- toc -->

---

配置windows的相关环境，安装相关软件。

## 编程环境

* C与C++
  * dev c++
* python（？Anaconda）
  * PyCharm
* Node.js
* java
  * myeclipse

---

* 命令行cmd，是否有优化版本，比如pycharm中的cmd
* ？power shell：
  * https://sspai.com/post/52868
  * https://www.yiibai.com/powershell/
* windows terminal：整合cmd、power shell。

## 相关软件

* office 三件套
* subline，VS code
* Adobe Acrobat DC：操作pdf
* everything：搜索文件
* Beyond Compare：比较文件异同
* Xshell+Xftp：操作远程服务器
* Typora：编辑markdown文件
* Oracle VM VirtualBox 或 VMware：虚拟机
* git 和 Github Desktop
* git图形化管理工具：SourceTree，TortoiseGit
* 7-Zip：压缩文件，使用tar.gz格式



## git

参考网站：

* **git官网中文教程**：https://git-scm.com/book/zh/v2
* **git线上实验**：http://try.github.io/

* github线上文档：https://help.github.com/cn/github
* github线上实验：https://lab.github.com/
* github视频：https://www.youtube.com/user/GitHubGuides/playlists
* gitlab用户文档：https://docs.gitlab.com/ee/user/index.html



下载最新版本的git，然后配置：

```bash
git config --global user.name "appwhy"
git config --global user.email "appwhy@qq.com"

# 在 Git 中缓存 GitHub 密码
git config --global credential.helper wincred

git config --global color.ui true   #语法高亮，显示加颜色
git config --list   #查看全局配置
```

配置ssh秘钥：

```bash
# 打开git bash，生成秘钥。
ssh-keygen -t rsa -b 4096 -C "appwhy@qq.com"
ssh-keygen -t rsa -b 4096 -C "appwhy@qq.com" -f gitlab_rsa  # -f 指定输出文件
```

## github

常用快捷键：

* 

| 键盘快捷键 | 描述           |
| :--------: | -------------- |
|  ?   | 列出可用于该页面的键盘快捷键 |
| **站点快捷键** | |
|   s 或 /   | 聚焦于搜索栏。 |
|    esc     | 退出聚焦       |
| **仓库** | |
| g d        | 转到github.com(dashboard)                |
| g c        | 转到 **Code（代码）** 选项卡                |
| g i        | 转到 **Issues（议题）** 选项卡。            |
| g p        | 转到 **Pull requests（拉取请求）** 选项卡。 |
| **源代码编辑** | |
| alt g | 跳至行 |
| control f  | 开始在文件编辑器中搜索 |
| **源代码浏览** | |
| t    | 激活文件查找器 |
| b    | 打开追溯视图（blame view）。 |
| y    | 将 URL 展开为其规范形式。 |

## subline

参考：

* 完全介绍：https://www.w3cschool.cn/sublimetext/4qo5cozt.html
* 不同代码运行环境配置：https://zhuanlan.zhihu.com/p/35669986
* 官网：http://www.sublimetext.com/
* 官网文档：http://www.sublimetext.com/docs/3/

---

通用（General）

- Alt：调出菜单
- Ctrl + Shift + P：调出命令板（Command Palette）
- Ctrl + `：调出控制台

编辑（Editing）

- Ctrl + Enter：在当前行下面新增一行然后跳至该行。
- Ctrl + Shift + Enter：在当前行上面增加一行并跳至该行。
- Ctrl + ←/→：进行逐词移动
- Ctrl + Shift + ←/→进行逐词选择
- Ctrl + ↑/↓移动当前显示区域，不会改变文件。
- Ctrl + Shift + ↑/↓移动当前行

选择（Selecting）

- Ctrl + D：选择当前光标所在的词并高亮该词所有出现的位置，再次Ctrl + D选择该词出现的下一个位置，在多重选词的过程中，使用Ctrl + U进行回退，使用Esc退出多重编辑。会在每个词后出现光标。
- Ctrl + Shift + L：在选中的多行后插入光标。
- Ctrl + J：把当前选中区域合并为一行，以空格分隔。
- Ctrl + M：在起始括号和结尾括号间切换
- Ctrl + Shift + M：快速选择括号间的内容
- Ctrl + Shift + J：快速选择同缩进的内容
- Ctrl + Shift + Space：快速选择当前作用域（Scope）的内容

查找&替换（Finding&Replacing）

- F3：跳至当前关键字下一个位置
- Shift + F3：跳到当前关键字上一个位置
- Alt + F3：选中当前关键字出现的所有位置
- Ctrl + F/H：进行标准查找/替换，之后：
- Ctrl + Shift + F：多文件搜索&替换

跳转（Jumping）

- Ctrl + P：跳转到指定文件，输入文件名后可以：
  - @ 符号跳转：输入@symbol跳转到symbol符号所在的位置
  - `#`关键字跳转：输入#keyword跳转到keyword所在的位置
  - : 行号跳转：输入:12跳转到文件的第12行。
- Ctrl + R：跳转到指定符号
- Ctrl + G：跳转到指定行号

窗口（Window）

- Ctrl + Shift + N：创建一个新窗口
- Ctrl + N：在当前窗口创建一个新标签
- Ctrl + W：关闭当前标签，当窗口内没有标签时会关闭该窗口
- Ctrl + Shift + T：恢复刚刚关闭的标签

屏幕（Screen）

- F11：切换普通全屏
- Shift + F11：切换无干扰全屏
- Alt + Shift + 2：进行左右分屏
- Alt + Shift + 8：进行上下分屏
- Alt + Shift + 5：进行上下左右分屏
- 分屏之后，使用Ctrl + 数字键跳转到指定屏，使用Ctrl + Shift + 数字键将当前屏移动到指定屏





## vs code

参考：

* https://www.w3cschool.cn/visualstudiocode/visualstudiocode-iy3422zb.html
* https://segmentfault.com/a/1190000017949680
* 官方文档：https://code.visualstudio.com/docs/?dv=win
* 中文翻译（差）：https://jeasonstudio.gitbooks.io/vscode-cn-doc/content/



VS Code 的定位是`编辑器`，而非`IDE`。但 VS Code 又比一般的编辑器的功能要丰富许多。

VS Code 自带了 TypeScript 和 Node.js 的支持。也就是说，你在书写 JS 和 TS 时，是自带智能提示的。

命令面板是vscode快捷键的主要交互界面，可以使用`f1`或者Ctrl+Shift+P打开。

在 `Ctrl+P` 窗口下还可以:

- 直接输入文件名，跳转到文件
- `?` 列出当前可执行的动作
- `!` 显示 `Errors`或 `Warnings`，也可以 `Ctrl+Shift+M`
- `:` 跳转到行数，也可以 `Ctrl+G` 直接进入
- `@` 跳转到 `symbol`（搜索变量或者函数），也可以 `Ctrl+Shift+O` 直接进入
- `@` 根据分类跳转 `symbol`，查找属性或函数，也可以 `Ctrl+Shift+O` 后输入:进入
- `#` 根据名字查找 `symbol`，也可以 `Ctrl+T`

常用快捷键：

* Ctrl+Home ： 光标移到文件开头
* Ctrl+End：光标移到文件结尾。
* Ctrl+Shift+K：删除当前行。
* Ctrl + Enter：在当前行下面新增一行然后跳至该行。
* Ctrl + Shift + Enter：在当前行上面增加一行并跳至该行。
* Alt+↑↓：将当前行向上/下移动。
* Ctrl+U：光标退回上一个位置。
* Alt + Shift + I：在选中的文本的每一行的末尾都创建一个光标。
* 多光标：按住Alt键，然后在页面中希望中现光标的位置点击鼠标。
* 选中某个文本，然后反复按快捷键Ctrl + D， 即可将全文中与光标当前所在位置的词相同的词逐一加入选择。

## PyCharm

参考：

* https://www.jianshu.com/p/2bfc19e1381c
* https://www.yiibai.com/pycharm/

---

* settings/
  * Editor/
    * Font：调整编辑器的字体、大小等。
    * Color Schema：设置编辑文件时的背景颜色。
      * Console Font：调整控制台的字体、大小
    * Code Style/
      * Python：设置 tab size为4，使用4个空格代替Tab键。
    * File Encoding：调整文件编码，有3个地方，都设置为utf-8。
    * File and Code Templates：用于设置模板文件，便于省略部分代码的编写。

---

- 定位

- - Search Everywhere（双击Shift）：可以搜文件名、目录名(后面加/)、类名、方法名、函数名。
  - Ctrl+光标
    - 当按住Ctrl，鼠标移到标识符上面时，会显示一些信息。
    - 当按住Ctrl，并点击时，可以跳到定义处。快捷键Ctrl+B也有该作用。
    - 当在定义处按住Ctrl，并点击时，会弹框列出所有引用的地方，只有一个地方引用时，会直接跳转。
  - 最近打开的文件（Ctrl+E）：弹出一个提示框，显示最近打开的文件。Ctrl+Tab好像也有这个功能。
  - 目录树的“雷达”：会将目录树定位到当前文件（正在编辑的那个文件）。
  - 查找
    - Ctrl+F：当前文件查找
    - Ctrl+Q：查找当前方法的注释信息。
    - Ctrl+Shift+A：搜索IDE的功能，比如想看看这个文件的历史，就键入history 可以找到 Local history。Help -> Find Action
  - Ctrl+P：调用方法时查看参数，在括号内按下，就知道当前位置该给啥参数。
    - Ctrl+Shift+F：全局查找，可以分别在项目内、模块内、目录内查找。
    - 目录树某个目录右键，Find in Path，可以只在这个目录范围内进行查找
  
- 补全

- - Tab
  - 万能的Alt+Enter：不同场景有不同的动作。
    - 比如当在一个未找到引用的变量按下Alt+enter时，会弹窗，让你选择自动import、创建函数参数、重命名到一个已有的变量等。
    - 在还没import（install）模块名时，自动添加import（install）相对应的模块。
    - 在方法名上使用补注释。
  - 在测试中使用帮你补充断言代码。
  - Surroud with（Ctrl+Alt+T）：快速将若干行代码包裹起来，如 `try... except...`。
  - Emmet：使用特定的语法来展开小段代码，它类似CSS选择器，使其成为完整的HTML代码。在编写完成后按Tab键就能进行展开。
  
- 编辑

- - Basic
    - Ctrl+C(复制)。在没选择范围的情况下会复制当前行，而不需要先选择整行再复制。
    - Ctrl+V(粘贴)。Ctrl+Shift+V可以在剪贴板历史中选择一个去粘贴。
    - Ctrl+X(剪切)
    - Ctrl+S(保存)
    - Ctrl+Z(撤销)。Ctrl+Shift+Z反撤销。
    - Ctrl+/(注释)。注释后光标会自动到下一行，方便注释多行。
    - Ctrl+D(复制当前行)
    - Ctrl+Shift+U(转换大小写)
    - **Ctrl+Alt+L(格式化)**
    - **Ctrl+Alt+O(优化import)**
    - Shift+Alt+↑↓(上下移动行)、**Shift+Ctrl+↑↓**（上下移动语句。一个语句可能有多行。并且会决定要不要进块内和出块外）。简单的说，一个是物理移动行，一个是逻辑移动语句。
    - Shift+enter(在下面新开一行)。Ctrl+Alt+Enter在上面新开一行。
    -  Shift+←→左右移动带选择。Ctr+←→单词级别的移动。 Ctrl+Shift+←→左右移动单词带选择。
    - Ctrl+[]，光标移动到块首/块尾。Ctrl+Shift+[]，光标移动到块首/块尾，并带有选择功能。
    - Alt+↑↓：光标移动到上一个方法/下一个方法。
    - Alt+←→：切换文件。
    - Ctrl+L(Find/ Move to next Occurrence)
  - Extend Selection/ Shrink Selection（Ctrl+W / Ctrl+Shift+W）：用来选中单词、两个引号或括号之间的内容。而不是用鼠标费劲的去选。
  - 多光标
    - Alt+点击：在不同地方执行该命令，可得到多个光标。按ESC可以取消光标。
    - Alt+鼠标拖动：选择多行，并在每行都有光标。按ESC可以取消光标。注意最开始的光标。
    - Ctrl+G：跳到第几行几列，用冒号隔开

- 重构

  - Rename：将一个变量rename,右键单击，选择Refactor->Rename，所有用到这个变量的地方都自动跟着变。
  - Safe delete：删除一个文件，如果该文件被其他文件所引用，就会给出提示，让其谨慎删除操作。
  - Extract（Ctrl+Alt+M）：提取选中的代码块生成一个新的变量、属性、方法、参数等

- 调优

  - Help->Edit Custom VM Options，配置多点内存，使流畅。
  - 禁用掉没用的插件。

- 颜值：装插件Material Theme UI。好看很多。

- 其它

  - 在配对符号'")]}的关闭符号前，按相同按键，会忽略并移动光标到后面，不用老远的去按→方向键。

  - Smart Keys(Settings->Editor->General->Smart Keys设置)

    * 输入单个字符时插入一对引号或括号。
  
    - 当选中的时候输入引号或括号，在两边加上引号或括号，而不替换选择的内容。
    - 换行时智能缩进
    - 在语句内换行时会自动拼上反斜杠\
  - 定义方法时自动插入self
  
- ？贤者模式(免打扰模式进行编码)
  
- New Scratch File： 临时编辑文件时用。
  
- Copy Reference：比如在某个函数右键Copy Reference，粘贴到shell里面方便import。
  
- 静态分析。比如找出重复代码、检查代码是否符合pep8等。在左侧目录树上单击右键，选择“Inspect Code”。
  
- 在目录树新建文件的时候，可以多层，连目录一起创建。类似mkdir -p的效果。比如输入foo/bar/baz.py，如果没有目录foo和bar，会自动创建。
  
- 在编辑器内选择后，可以右键“search with google”、“execute selected in console”
  
- ？编辑代码的时候，行号右边会有标记，插入、删除、修改是不同标记，可点击进行diff和rollback
  
  - 在目录树右键->Local History，可显示改动历史，并可还原到某个历史。(注：跟git没关系)
  
  - 变量或表达式的最后键入`.(点)`，会出现提示，看最下面的部分有各种代码模板，例如现有变量a，在下一行键入 a.print 然后键入`Tab`，代码会变成`print(a)`，还有if,else等各种常用的代码模板。
  
  - Help->Tip of the Day：显示各种快捷操作。

## anaconda

anaconda组件解释：

* Anaconda Navigator是一个桌面图形用户界面（GUI），无需使用命令行即可启动应用程序并轻松管理conda程序包，环境和通道（？类似软件源）。Navigator可以在Anaconda Cloud或本地Anaconda存储库中搜索软件包。

* conda：命令行程序conda既是程序包管理器又是环境管理器。pip只是一个程序包管理器。
  * Conda包是二进制文件，Pip安装包为wheels或源代码。 Pip安装Python包，而conda安装包可能包含用任何语言编写的软件的包。

* Spyder是一个IDE，和其他的Python开发环境相比，它最大的优点就是模仿MATLAB的“工作空间”的功能，可以很方便地观察和修改数组的值。
* jupyter qtconsole，可以看做是ipython的加强版，能够在shell里直接显示绘图结果。

conda创建虚拟环境：

```bash
conda create --name venv36 python=3.6    # 创建一个名为venv36的虚拟环境

conda activate venv36    # 激活环境
conda deactivate         # 退出虚拟环境

conda info --envs        # 列出所有环境
conda env list 
```

