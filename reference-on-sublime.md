---
title: sublime Text3插入参考文献问题
date: 2019-12-27 14:44:26
tags: latex
---
最近在使用sublime Text3写latex，一切顺利，结果到了最后的插入参考文献部分却遇到了问题。于是将问题记录下来。

由于本人是个新手，所以先到网上找一找教程。结果大体都是这么说的：

1. 找到**bibTex**格式的文献，复制粘贴将其保存为`.bib`格式的文件。
2. 在latex文档中插入以下几条命令。
```latex
\renewcommand\refname{参考文献} % 可选 
% 这是为了将默认的reference标题改成参考文献，注意documentclass是article。
% 若是book格式，改成\renewcommand/bibname{参考文献}。
\bibliographystyle{plain} % 必选 
% 类型，plain为标准格式，按照字母的序号排列，次要比较为作者、年度和标题。
% unsrt，按照插入参考文献的顺序依次插入。
% alpha，用作者名首字母+年份后两位作标号，以字母顺序排列。
% abbrv，类似plain，将月份全拼改为缩写，更显紧凑。
% ieeetr，国际电气电子工程师协会期刊样式。
% acm，美国计算机学会期刊样式。
% siam，美国工业和应用数学学会期刊样式
% apalike，美国心理学学会期刊样式
\bibliography{ref}   % 必选
% 前面创建的.bib文件，名称为ref.bib，这里只需要填写后缀前的名称即可
% 因此只需要维护ref.bib文件就能完成参考文献的管理。
```
3. 然后，对于需要引用参考文献的位置，插入`\cite{keyword}`，这个`keyword`为`@article`后面的内容。这里也举个例子。比如有一段参考文献是下面这样的：
```bibtex
@article{神经网络自适应学习率改进,
author={朱振国 and 田松禄},
title={基于权值变化的BP神经网络自适应学习率改进研究},
journal={计算机系统应用},
year={2018},
volume={27},
number={7},
pages={205-210},
month={8},
}
```
那么这个`keyword`就是`神经网络自适应学习率改进`。
4. 然后是四次编译。

    + 先用xelatex编译\*.tex文件
    + 再用bibtex编译\*.bib文件
    + 再用xelatex编译\*.tex文件
    + 再用xelatex编译\*.tex文件

5. 然后，我也是按照该流程先编译了`*.tex`文件，然后想要编译`*.bib`文件时，却发现根本没有`bibtex`的编译选项!但是搜来搜去大家都是这么说的，于是我就迷茫了。
6. 寻找答案的路程是辛苦的，不卖关子，直接上解决方法。

其实，`sublime text3`不需要编译`.bib`文件，因为`Latex Tools`会自动帮你完成，因此，你只要做一件事，使用**`script builder`**编译`.tex`文件即可。  
但是，首先需要配置该编译选项（主要是windows那里，其他系统不敢保证）。
<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcVMxx.jpg" alt="EcVMxx.jpg" border="0" height="50%" width="50%"></div>  
其中`xelatex`为推荐的选项，当然也可以改成古老的`pdflatex`或者还有点bug的`lualatex`。改完这一句后，保存后重启软件即可。  
接着，记得切换为英文输入法，然后按`ctrl+shift+B`选择`script builder`即可。也可以`tools -> build with -> script builder`。  
然后就能看到结果了。

最后举一个自己的实例。  
首先，创建`.bib`文件，名称为`ref.bib`。
<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcVlM6.jpg" alt="bib.jpg" border="0" height="50%" width="50%"></div>

接着，在自己的文档中，确切地说在`\begin{document}`和`end{document}`中间插入以下语句：
```latex
\renewcommand\refname{参考文献}
\bibliographystyle{plain}
\bibliography{ref}     % 需要维护ref.bib文件
```
<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcV1sK.jpg" alt="code_1.jpg" border="0" height="50%" width="50%"></div>
确保能使用参考文献。  
然后，在需要引用的地方加上`\cite{keyword}`。  
<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcVni9.jpg" alt="code_2.jpg" border="0" height="50%" width="50%"></div>  
然后，快捷键`ctrl+shift+B`选择`script builder`

<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcVKR1.jpg" alt="build.jpg" border="0" height="50%" width="50%"></div>

即可看到编译成功以及结果显示。  
<div align="center"><img src="https://s2.ax1x.com/2019/05/08/EcVuGR.jpg" alt="EcVuGR.jpg" border="0" height="70%" width="70%"></div> 




