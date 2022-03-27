# win10下的latex

# 即texlive和texstudio的安装调试

## 0 参考

内容参考：

[LaTeX学习：Texlive 2019和TeX studio的安装及使用](https://blog.csdn.net/Mikchy/article/details/94448707)

[win10下安装texlive2019和texstudio（安装不好你来打我） latex学习（从0开始）](https://blog.csdn.net/qq_44970368/article/details/104127158)

图片URL

[URL生成](https://sm.ms/)



## 1 引言

为了进行数学建模并拥有一个好的论文写作，决定进行latex的学习。

Latex是一种排版系统，需要在texlive的环境下进行，同时需要texstudio作为编辑器。

类比一下Latex是python，texlive就是anaconda(提供环境)，texstudio就是pycharm(作为编辑器提供编写窗口)。



## 2 texlive2021的下载及安装

### (1) 下载

[镜像链接](http://mirrors.sjtug.sjtu.edu.cn/ctan/systems/texlive/Images/)

[清华镜像链接](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)

[官方链接(科学上网)](http://www.tug.org/texlive/)

ps：如果用官网，则按照以下方法进入

![](https://i.loli.net/2021/11/02/pYB4QsvwadhTS1H.png)



![](https://i.loli.net/2021/11/02/52DhlZMt1Wbwsur.png)





![](https://i.loli.net/2021/11/02/1CxbvLeFigaQsKP.png)

**最后寻找合适的最新版本就可**

像本例：texlive2021-20210325.iso即可

![](https://i.loli.net/2021/11/02/xSjlNQPkivnEupJ.png)

最终下载得到

![](https://i.loli.net/2021/11/02/lPAy6csF3IpR4nq.png)



### (2) 安装

将下载好的iso 文件进行解压，然后双击打开其中的**install-tl-windows.bat**文件。

![](https://i.loli.net/2021/11/02/Np2LAMltUQeCvmF.png)

点击**Advanced**

![](https://i.loli.net/2021/11/02/7rke6BKlXZVc39t.png)

然后依次按下图操作，修改安装目录，点击安装，一般不要安装在C盘里

![](https://i.loli.net/2021/11/02/puqDQA6BaxJ3yPm.png)

**同时可以修改以下操作**（一般不用动就行，除非内存十分不够）

1 处可以选择安装语言

2 处可以选择是否安装texworks，也是一个编辑器，比较小，比较简单

![](https://i.loli.net/2021/11/02/mO3yCKNhF1Wf2iA.png)

接下来就是一个等待的过程，一般要安装**一个小时**左右。

当安装结束后

点击`win+R`，输入`cmd`，从而调出windows系统下的cmd

输入

```cmd命令
tex -version
```

如果出现版本号

```cmd命令
TeX 3.141592653 (TeX Live 2021/W32TeX)
```

即**安装成功**。

图示如下：

![](https://i.loli.net/2021/11/02/7UZJHaMkVGQpIWq.png)



## 3 texstudio4.0.3的下载及安装

### (1)下载

[镜像链接](http://texstudio.sourceforge.net/)

[官方链接(科学上网)](https://www.texstudio.org/)

进入官网后，点击那个大大紫色按钮即可（**可能出现问题，关闭之后再进入或者刷新几次**），如图：

![](https://i.loli.net/2021/11/02/gUk3eQAzJGw47Xj.png)

最终下载得到

![](https://i.loli.net/2021/11/02/olw9LJnQBUFxm6f.png)

### (2)安装

双击按提示安装即可。

除了**安装位置**(不要放在C盘)，没有需要改的地方，较为简单。



## 4 texstudio的配置和调试

### (1)设置中文界面

依次点击：Options—> **Configure Texstudio** —> General—> Language—> zh_CN

上述加粗的那个下面截图没显示出来，对照一下就可，中文为**设置TeXstudio**。

![](https://i.loli.net/2021/11/02/Mkx4dL3gRuzTs8H.png)

### (2) 添加行号

添加段落行号，这样可以很方便查看段落的某句话所在的位置，尤其是在运行报错时，有行号就非常方便查看错误的位置了。

当然也可以不添加。

依次点击：选项—>设置 Texstudio —>搜索“**行号**”—>编辑器—>显示行号—>所有行号

![](https://i.loli.net/2021/11/02/mbhOx2WDRui8d4G.png)

### (3) 设置编译器与编码

为了正常的输出中文，我们需要把编译器改成**xelatex**，**utf-8**编码
如果是为了编写英文论文的，那就下面第一张图不要改成“xelatex”，**英文**论文要用“**pdflatex**”

![](https://i.loli.net/2021/11/02/3jPBhOrqU2Ks56t.png)

![](https://i.loli.net/2021/11/02/zVQfHRtkUu9haIX.png)

### (4) 第一个简单程序

```c
% 导言区
\documentclass{article} 

% 导入中文宏
\usepackage{ctex}

% 构建命令,取别名，使用degree 代替 ^ circ
\newcommand\degree{^\circ}

\title{\heiti 浅谈勾股定理}
\author{\kaishu wmh}
\date{\today}
% 正文区
\begin{document}
    \maketitle
    hello world!
    
    勾股定理可以用现代的语言描述如下：
    
    直角三角形斜边的平方等于两腰的平法和。
    
    可以用符号语言描述为：设直角三角形 
    $\angle C=90\degree $则有：
    $$ 
    	AB^2 = BC^2 + AC^2 
    $$
    这就是勾股定理
\end{document}

```

新建一个 .tex 文件后，将上述代码复制粘贴进去，然后，点击下图中的**编译并查看**

![](https://i.loli.net/2021/11/02/aDWbGeirR8VI9xC.png)

右侧即为编译后的界面。



## 5 扩展

LaTeX主要的就是利用模板。

所以一般如果写论文的，导师或者投稿的那里都会有模板拿来使用的，因此最主要的就是知道如何编写数学公式

推荐使用**Mathpix**

[Mathpix](https://mathpix.com/)

`ctrl+alt+m`可以自动调用mathpix的捕捉系统

捕获成功后会生成Latex语法代码或者公式图片化的URL链接，主要是前一种结果的使用。

会产生如下图所示的四种结果：其中，第一种是不包含公式标识符的纯Latex代码，第二种是常用的Latex文件和Markdown文件中的行内公式，第三种是Markdown中常用的单行公式，第四种则是Tex文件常用的公式格式。选择其中一种拷贝即可。

现在个人有两个邮箱都注册了账号：

`1085382995@qq.com`  50

`201952045@mail.dlut.edu.cn` 100



再贴一个github的软件，有时间可以看一看。

[MathpixCsharp: C#实现的Mathpix Windows开源客户端](https://github.com/itewqq/MathpixCsharp)

作者同时开发了网页版

[网页版mathf](https://mathf.itewqq.cn/)



还有论文写作的时候，要有参考文献，一般一个个加参考文献，但是这种情况下，对于少量参考文献还可以。

当有大量的参考文献存在时，就会很麻烦

推荐使用**JabRef**

[jabRef](https://www.jabref.org/)



当然也有一些在线的软件，暂时没有找到很合适的，就先不贴了，随后有了再更新。



## 6 声明

本文档仅限本人及亲朋好友学习安装使用，不用于任何盈利形为。



## 7 补充

处理参考文献

![](https://i.loli.net/2021/11/02/YhZdBQnLVmu2ky6.png)

最后，如果需要处理参考文献，还需设定命令参数。在TeXstudio中，打开：选项/设置TeXstudio/命令，设置成如下图红框所示：

![](https://i.loli.net/2021/11/02/FlA1cmjg6zOPTHn.png)















