配置Latex环境前需要安装texlive发行版，建议从[清华镜像](https://mirrors4.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)下载（**下载texlive 2019.iso即可**），注意texlive安装不是运行exe文件，但也很简单，搜一下教程即可。

Latex只是一种语言，推荐使用[Sublime Text3](https://www.sublimetext.com/)或者[Vs Code](https://code.visualstudio.com/)编写，这里就只讲Sublime配置Latex的方法。

vs code配置latex非常简单，参见[这里](https://zhuanlan.zhihu.com/p/71432461)。

# 安装准备
1. Sublime Text 3：软件
2. Sumatra PDF：PDF阅读器，主要用于双向搜索
3. ImageMagick、GhostScript **(可选)**：公式和插图的实时预览

# 环境配置
## 安装Sublime Text 3
从官网下载安装即可，没什么注意点。值得一提的是，Sublime Text 3是收费软件，但是试用版能够使用所有的功能，偶尔会弹出购买的对话框（正版600多）。所以要么消费支持，要么就一直试用版好了，也不会到期，没必要某宝找激活码。

### 安装Package Control
依次点击`Tools -> Install Package Control`即可，注意软件窗口左下角的消息提示，稍等片刻就好了。

**安装结束后，重启软件，继续下面的操作。**

### 安装插件
要安装插件有以下三个：

1. LaTexTools：环境配置
2. LaTex-cwl：代码自动补全
3. LaTexXYZ：数学公式自动补全

安装步骤也分成以下三步：

1. 打开上一步安装好的`Package Control`（快捷键`ctrl + shift + p`）
2. 输入`picp`，找到`Package Control: Install Package`，回车
3. 稍等片刻会再次弹出，这时输入`latex`，找到上述的三个插件，回车安装即可。

**同样，安装结束后，重启软件。**

### LaTex Tools配置
依次点击`Preferences -> Package Settings -> LaTeXTools -> Settings-User`，打开设置文件。

设置包括以下几部分：

1. 通用设置：参考文献、交叉引用等常用功能的监视器与触发器开关
2. 预览设置：与数学公式、插图相关的设置
3. 辅助文件设置：指明哪些是辅助文件，以确认在使用 Ctrl+L,Backspace 时所需清理的辅助文件。
4. **平台设置：**与平台相关的设置，如发行版路径、发行版类型、终端平台、编辑器平台等等。要修改的有三个：

    - texpath：指定发行版路径，如果要用两种发行版的话，就不填，留空即可，系统会自动配置该参数。
    - distro：指定发行版类型，默认为MiKTex。TexLive的需要修改。
    - sumatra：sumatra pdf 路径  
    见下图windows的例子：
    <div align="center"><img src="https://s2.ax1x.com/2020/01/01/lJwUbR.jpg" alt="lJwUbR.jpg" border="0" /></div>

5. 输出目录设置：日志之类的文件输出设置
6. 构建器设置：一般不涉及，使用默认即可
7. 构建面板设置：错误、警告信息相关设置
8. 阅读器设置：默认值与平台相关
9. 可于代码中打开的文件类型设置：主要用于插图时的提示
10. 参考文献设置：如使用 BibTeX 还是 BibLaTeX，参考文献应用时格式的自动生成等。
11. 缓存选项

最后，指定编译器引擎为`xelatex`，即：
```latex
% !TEX program = xelatex  (pdflatex,lualatex...)
```
pdflatex太老，lualatex还有bug。

## 安装Sumatra PDF
从[官网](https://www.sumatrapdfreader.org/download-free-pdf-viewer.html)下载安装即可。**进去不要怀疑，虽然看起来十分山寨，但真的是官网。**

### 配置双向搜索
值得一提的是，由于最新版本的 Sumatra PDF 关闭了直接设置反向搜索选项功能，所以我们需要先编译一个简单的 tex 文档，然后才能够进行配置。

测试样例如下，将其复制粘贴后保存（名字不能含有中文），然后将其编译。`Tools -> Build`或者快捷键`ctrl + B`。
```latex
\documentclass{article}

\begin{document}
  Hello, \LaTeX{}.
\end{document}
```

接下来用Sumatra PDF打开生成的pdf，然后点击左上角->设置->选项，在最下方添加以下内容：
```markdown
"D:\LaTexSuite\Sublime Text 3\sublime_text.exe" "%f:%l"  
```
如图所示：
<div align="center"><img src="https://s2.ax1x.com/2020/01/01/lJt6Jg.png" alt="lJt6Jg.png" border="0" /></div>
这里的`xxxxx\xxx.exe`是自己安装sublime text 3的路径。

## 安装ImageMagick & GhostScript（可选）
**这两个插件安装过程有些麻烦，并且效果一般，稍不注意bug还不少**。因此有时间有精力就可以继续安装这两个插件。

### 安装ImageMagick
从[官网](http://www.imagemagick.org/script/download.php)下载，windows平台的安装包在页面最下面。

安装过程中的一步，勾选**添加环境变量、安装实用工具**，见下图：
<div align="center"><img src="https://s2.ax1x.com/2020/01/01/lJ0O6e.jpg" alt="lJ0O6e.jpg" border="0" /></div>
<center>图片来自[有龙则灵](https://htharoldht.com)</center>

### 安装GhostScript
从[官网](https://ghostscript.com/download/gsdnld.html)下载安装即可。

至此，所有安装过程就结束了。

最后，检查安装。依次点击`Preferences -> Package Setting -> LaTex Tools -> Check System`，如图：
<div align="center"><img src="https://s2.ax1x.com/2020/01/01/lJDnDH.jpg" alt="lJDnDH.jpg" border="0" /></div>

主要是中间部分，全绿即可。如果有部分插件不可用，检查对应步骤。

最后，关于插入参考文献的问题，可以参考[这篇文章](https://blog.csdn.net/HollyRan/article/details/89977696)

# 参考
1. [有龙则灵](https://htharoldht.com)关于配置的方法
2. [texlive安装流程](https://zhuanlan.zhihu.com/p/36240727)