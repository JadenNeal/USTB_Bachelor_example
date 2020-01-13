# 北京科技大学本科毕业论文LaTex模板
本模板是针对**北京科技大学本科生毕业设计**的latex模板，硕士、博士不可使用。

主要特性：
- 支持跨平台使用，兼容最新的 TeX Live, MacTeX 和 MikTeX 发行版，
  并向后兼容到 2016 年的版本
- 不支持已经过时的 CTeX 套装
- 数学符号遵循国内的排版习惯
- 参考文献格式符合 GB/T 7714

## 模板的构成
模板中提供了以下文件。

| 文件 | 说明 |
|----|----|
| **Sublime Text3配置Latex.md** | 编辑器配置教程 |
| **ustbbachelor-numerical.bst**   | 国标参考文献样式 |
| **ustbbachelor.dtx**   | 模板源文件 |
| **ustbbachelor.ins**   | 模板安装驱动 | 
| **ustbbachelor.cls\***   | 生成的文档类 |
| **main.tex** | 主文档（可作测试用） |
| **chapters** | 主文档的章节文件 |
| **format** | 学校的排版要求 |
| **figures** | 图片目录 |
| **bibs** | 文献数据库目录 |

其中，带`*`的可由`.dtx`和`.ins`自动生成。

在`.ins`的目录下打开`shell`，运行`xelatex ustbbachelor.ins`即可得到`.cls`文件。

## 模板的使用
使用前，请一定先编译生成模板的使用说明`ustbbachelor.pdf`：
```
latexmk -xelatex ustbbachelor.dtx
```
仔细阅读完之后，日后可以作为字典使用。

生成了`.cls`文件后，就可以开始写文档了。

`main.tex`是论文的主框架。`chapters`目录下存放着各个章节，`figures`存放着图片，`bibs`则存放着参考文献，请按需要改写。

## 注意事项
有以下几点：
1. 封面页以及扉页的设置过于麻烦，故未作更改，需要同学们自行使用word模板编写后打印。
2. 不建议使用linux系统进行编写，因为需要自行配置字体。
3. 模板中，已设置1.3倍行距为默认值。即重定义后的行距默认为1.3倍，并将其设置为了标准的1。
4. 正文章标题的调用命令已定义为`\textchapter`，且不能再在目录中使用短标题，请注意。
5. **关于后期的审阅问题，建议直接提交pdf，在pdf上批注。**

---
如有问题或改进意见，请提交**issue**或通过以下方式联系我：

* email: longweicai1997@163.com
* QQ:    1433535963