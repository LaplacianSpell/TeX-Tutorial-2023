

<style>
.center
{
  width: auto;
  display: table;
  margin-left: auto;
  margin-right: auto; 
}
</style>

# Preface

大家好，我是物理 11 班的盘笛，现在是物理系科协技术部的部员，很高兴认识大家。

技术部开这个培训的初衷是为了教大家快速上手一些好用的工具，按照物理系的培养方案，物理系大一的同学在春季学期会开始修 **基础物理实验**，同时多数同学会在今年暑假接触到 **计算机程序设计** ，在明年暑假会接触到 **实验物理的大数据方法**，之后高年级还有 **近代物理实验** 这门课。这些课程或需要 **撰写报告**，或需要能够 **设计程序来完成指定的任务**.

我们希望能够在你们上这些课之前教会你们一些计算机相关的小知识，同时让你们学会一些小技能，**快速上手一些常用工具**。以便于你们能适应之后的学习。因此，讲座本身会将大多数工具的细节进行封装，目的是在最短的时间里面让大家学会怎么使用工具以及下手去学习怎么使用工具（たぶん...

至于细节本身，我们也会提供相关的资源供感兴趣的同学去了解。~~物理系的同学不要在这些细节上花太多时间，好好的学物理。~~

这份讲稿的目标就是让各位看完之后：

+ 能够独立的写出一份实验报告
+ 能够知道 LaTeX 排版中的问题怎么解决（包括向学长提问，使用搜索引擎）

同时，我的水平十分的有限，讲稿中有任何的错误欢迎指出，如果觉得线下不太方便也可以通过<a href="mailto:pd20@mails.tsinghua.edu.cn">我的邮箱</a>与我联系。

然后就是，我想让讲稿~~变得有趣一点，不至于看睡着~~，所以写作风格会比较有个人特色（高情商），~~说白了就是嗯整烂活~~，有点长也是因为嗯整烂活。如果你讨厌这种文风 ~~那还真是抱歉呢（笑）~~ 去看我的 PPT 或者是给出的参考文献吧，PPT 近似于一个随用随查的笔记本，而参考文献则是我认为写的比我好得多的教程。~~请各位轻点喷我~~

~~我写这个主要是想列一列我要讲的东西~~

左侧边栏是讲稿的目录。行文的思路放在下面：

+ 介绍 LaTeX 的历史，为什么需要学习 LaTeX
+ 介绍 LaTeX 的工作原理：语法 - 编译器 - 文件
+ 介绍怎么安装编译器
+ 介绍一个完整的 LaTeX 工程是怎么样的
  + 导言区内容
    + 设置文件文本类型
    + 添加标题等 metainfo.
    ...
  + 主体区内容
    + 缩进
    + 文本格式，写公式
    + 怎么插入图片以及表格
    ...

# $\LaTeX$ 快速入门

## $\LaTeX$ 的历史？

+ **怎么读 LaTeX :** 首先说一下，这个单词读 `/ˈlɑːtɛk/`（~~镴斄醘~~, 拉泰克）而不是“拉泰克斯”(~~其实你这么读也不会有人打你~~)，Donald Knuth 这个获得 [Turing 奖](https://amturing.acm.org/) 的巨佬因为嫌弃当时技术文章的烂排版，发明了 $\TeX$ 这玩意。这个名字是他将希腊字母 $\tau\epsilon\chi$ 变体得到，而这三个希腊字母事 $τέχνη$ 的 *abbr.* , 而这个词又事希腊文里面**艺术**和**技术**的统称，也事 technical 这个洋文单词的词根，~~事不事很好玩（小并感）~~

+ **和 TeX 是什么关系：** 甚么，你问 $\TeX$ 和 $\LaTeX$ 事什么关系？实际上他们并不是一个东西。你只需知道现在没什么人写原生的晦涩的 $\TeX$ 语言了。下面我引用[这篇文章](https://zhuanlan.zhihu.com/p/202799658)的一段话，感兴趣的同学可以深入了解。

  >TeX 与 LaTeX 并不是鸡与蛋的关系，论孰者先，引申到形而上学领域，探究宇宙生命起源。TeX 与 LaTeX 的关系很简单，就像你与你兄弟的「真实关系」，因为你一般会自称你兄弟的爸爸。没错，我们可以认为 TeX 是 LaTeX 的爸爸！
  >LaTeX 是基于 TeX 的一组宏集<font color = "red">（1）</font>，相当于对 TeX 进行了一次封装。
  >
  ><font color = "red">转载注释 (1)</font>: 宏，你可以简单理解成 **替代**，在原生的 TeX 上可能需要很复杂晦涩的一些语句才能完成一些任务，LaTeX 相当于把这些语句 **封装和简化** 成了容易读容易写的样子，你用 LaTeX 写完之后他会把相应地方替换成相应的 TeX 语句然后在编译器上跑出精美的 PDF。

不想了解一点也不妨碍你去用他们。

---

## Why $\LaTeX$ ? 的三个理由

相信大家都在 **写作与沟通** 上用过 [Microsoft Word](https://en.wikipedia.org/wiki/Microsoft_Word)（或者是 WPS）这些软件进行文书工作。在这些软件上，我们能够直接在文本上进行调节：调节字体，调节大小，插入图片，插入链接等等。从而改变文本的布局

这种模式也叫做 **所见即所得 (W<font size = 1>hat</font>Y<font size = 1>ou</font>S<font size = 1>ee</font>I<font size = 1>s</font>W<font size = 1>hat</font>Y<font size = 1>ou</font>G<font size = 1>et</font>)**，也即我们可以用鼠标直接修改字体，颜色，用鼠标画出表格等等，只需要用鼠标在指定菜单里面 click 几下就行了。而后文本打印出来的结果和你在 Word 界面上看到的结果是一模一样的。

但是！

+ 我们撰写科技论文，更应该专注于**内容**，使用 Word 需要我们花费大量的时间调节合适的字体字号，调节缩进等等排版的问题上，并且 Word 的排版 **并 不 好 看**。
+ 同时，Word 对于公式编辑的支持体验感不太好。尽管有 [MathType](https://www.wiris.com/en/mathtype/) 这种东西能够帮助你在 Word 上更快的编辑公式，在这上面写公式的体验感依然一言难尽，~~而且画出来像腊肠一样的积分号巨丑~~。
+ 同时，几乎所有的学术性组织（比如：[APS](https://www.aps.org/) ，就事出版著名的 *Physical Review Letters/A/B/C/D/E/X*... 这些东西的学术组织）都有相关的 LaTeX 模板（比如： [REVTeX](https://journals.aps.org/revtex) 模板），~~并且或明确或隐晦地拒绝 Word 形式的投稿~~。

LaTeX 被设计为“**所想即所得 (WYTIWYG)**”，我见过一个十分生动的比喻是这样的：

> *用 LaTeX 写文章，你专注的是“这一段是否应该属于上一节呢？”， “这句话跟我这章的主题符合吗？”，“是否应该开始新的一章呢？”，“这个概念读者是否容易理解呢？”*
> 
> *而你需要告诉 LaTeX 的 是：“这是一章开始”，“这个单词应该强调”， “这里是一段诗”等等，就像在对他的秘书口授机宜。而不是告诉她：“这是第 3 章，应该用黑体三号字，开头有一个‘双 S'”，“这个单词用斜 体楷体小四”， “左右缩进各一英寸，右边不要对齐，换用小一号花体”这些是秘书的事情，不用你操心。"*

而且这个东西不仅仅能写出好康的公式和文章，还能做 PPT，甚至还能“写”象棋棋盘，“写”有机物的结构简式，“写”乐谱，“写”费曼图（效果可以看看[这里](https://zhuanlan.zhihu.com/p/348242068)），只需要你导入相应的包，按照规则写，然后剩下的事情就交给编译器好啦！

有小朋友就会问：

<center>

“LaTeX 会不会很难学啊。”

</center>

然后前辈就会告诉他：

<center>

“LaTeX 不用学，只要会用就行了。”

</center>

我们玩游戏不需要知道游戏的代码是什么也可以体会到游戏的乐趣！我们用电脑不需要知道电脑事怎么工作的也能体会到他为我们日常生活带来的便利！学会用这玩意搞点好康的，理论上只需要半个小时，半个小时你就能写出像模像样的东西力！

所以为了快点写出好康的文章

<center>

> 我正有写一点东西的必要了
> 
> &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;   -- 鲁迅（~~这话迅哥儿真说过~~）
> 

</center>


もう待ちきれないよ！早く出してくれ！(急迫)

---

## $\LaTeX$ 事怎么工作的

我们先来大概了解一下 LaTeX 事怎么工作的。

LaTeX 是一种排版系统，我们通过一定的语法（计算机语言就是人与计算机交流的一门 **外语**），**告诉** LaTeX 如何排版我们写的东西，比如像下面这样

```LaTeX
这事作用量 % 空一格告诉 LaTeX 你该另起一段了

\begin{equation} % \begin{} ... \end{} 告诉 LaTeX 这里是某种特殊的结构
S = \int_{t_0}^{t_1}L(q,\dot{q},t)dt % 这里是 equation 表示里面是一个公式
\end{equation}

其中 $ L(q,\dot{q},t) $ 就事系统的 \textbf{Lagrangian}，这里我手动给字体加粗了，然后在这里我又手动给字体加了斜体 \textit{hahahahaha}。

如果你想另起一段，只需要空一行之后继续写就可以了，不用调节缩进
```

最后的效果像下面这样：

>这事作用量
>
>$$ \begin{equation}
S = \int_{t_0}^{t_1}L(q,\dot{q},t)dt 
\end{equation} $$
>
>其中 $L(q,\dot{q},t)$ 就事系统的 $\textbf{Lagrangian}$，这里我手动给字体加粗了，然后在这里我又手动给字体加了斜体 $\textit{hahahahaha}$。
>
>如果你想另起一段，只需要空一行之后继续写就可以了，不用手动调节缩进
>

让我们这么去理解，从写到输出一个 PDF 文件大致分成下面三步

+ 你按照 LaTeX 的语法，写出你想要的排版方式以及内容。
+ 把你写出来的文件喂给一个读得懂你写的东西，并且能够自动转换为对应的排版的软件（也就是 **编译器**）
+ 编译器会吐出对应排版的精美 PDF 文件（实际上这个过程远远没有这么简单，但是，还是那句话，对于物理系的学生，我们只需要会用就行了。）
+ 当然，如果违反了一些语法规定，**编译器就会报错**，并且返回一些错误信息。你可以根据这些错误信息读出是哪里出问题了，在叫其他人帮你 debug 的时候也不要忘了给他错误信息

---

## ~~怎么安装编译器~~

都什么年代了，还在用本地编译器！

请允许我向你隆重介绍 [Overleaf](https://www.overleaf.com/) 这个东西，他为物理系学生免去了下载 TeXLive，配置环境等等比较令人不爽的过程。把编译环境部署到了云端，随开随用，还是那句话，~~物理系的同学好好学物理~~。

并且，THU 是有[自己的 Overleaf 网站](https://overleaf.tsinghua.edu.cn/project)的，诸多功能免费，不用白不用。下面的所有内容都建议你打开这个网站来感受一下如何使用。

当然，我们也有关于如何在本地进行环境配置的相关推送，戳[这里](https://mp.weixin.qq.com/s/5imPndNICS7O1Q2qZ5H--g)

---

## 一个完整的 LaTeX 工程是怎么样的

**注：下面的内容强烈建议边看边自己动手改一改敲一敲*

一个 LaTeX 工程在 Overleaf 上就是一个文件夹。现在暂时需要修改的就是里面以 `.tex` 结尾的文件。你可以把下面这段代码复制到你的工程里面，这是最简单的一段。其他的内容都在这个基础之上进行添加和修改。

```LaTeX
\documentclass[12pt, letterpaper]{article}
\usepackage[utf8]{inputenc}

\title{A study on 24-year-old students}
\author{yjsp}
\date{1919/8/10}

%%%%%%我%是%分%割%线%%%%%%

\begin{document}

\maketitle

Foo...Bar...Baz...

Pon! Pon!

\end{document}
```

### 导言区

对于上面的这一块，也叫 **Preamble**，**导言区**

```LaTeX
\documentclass[12pt, letterpaper]{article} % 标记文章的类别
\usepackage[utf8]{inputenc} % 宏包，zyf学长介绍

\title{LaTeX}
\author{Author}
\date{March 2023}

```

+ `\documentclass[12pt, letterpaper]{article}` 告诉编译器文档应该排版成什么类型，用来控制文档的整体外观。

  + `{}` 可以自己试一试诸如 `article` 和 `book` `report` 等等外观，article 文档类型适合较短的文章，比如期刊文章和短篇报告。其他文档类型包括 report（适用于更长的多章节的文档，比如博士生论文），proc（会议论文集），book 和 beamer。更多外观可以自行查阅相关内容。

  + 而 `[]` 内则是一些参数，比如这里给出的 `[12pt，letterpaper]` 指明了字体大小，和纸张大小。当然还有很多参数可以查阅了解。


  同时参数可以不使用，软件提供了默认值，比如默认字体大小为 10pt。参数的调节完全看各位的审美。你可以尽情在上面整活。

+ `\usepackage[utf8]{inputenc}` 调用了外部宏包 `inputenc`，LaTeX 上有很多可用的外部宏包。宏包扩展了 LaTeX 的功能。
  + 如果希望文档支持中文，请导入包 `\usepackage[UTF8]{ctex}` 并使用 `xeLaTeX` 编译器。

+ 我们可以在导言区添加标题，作者以及日期信息：
  + `\title{LaTeX}` 标题为 LaTex
  + `\author{Author}` 作者名字
    + `\thanks{Funded by ...}:` 可以添加在作者下面，感谢 ~~金主~~ ，比如某某机构之类的
  + `\date{March 2023}`可以自己写日期，也可以用 `\today` 自动使用当前排版的日期。

### 主体区

文章的主体是下面这部分，也就是 `\begin` `\end` 括起来的地方，叫做**body**，**主体**，你大部分的文章内容都需要在这里面编辑。end 之后的所有内容都会被编译器忽略

```LaTeX
\begin{document} % 写注释这么写，编译器不会看

\maketitle % 将刚刚在导言区写的标题作者等等东西渲染出来

% 你的文章内容就在这里面写
% 尝试改一改，编译看看结果

Foo...Bar...Baz...

Pon! Pon!

\end{document}
```

在我们试水之前，首先说一些关于空格，换行，章节，段落等的知识。请复制粘贴

```LaTeX

\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}

\tableofcontents

\chapter{chapter}

This is a chapter, I added some s\ p\ a\ c\ e.

And there is an indent.

\noindent And I cancelled it.

And the new \\ line

\newpage

how about new page?

\section{section}

I added index.

\tableofcontents

\subsection{subsection}

\subsubsection{subsubsection}

\paragraph{paragraph}

\subparagraph{subparagraph}

```

1. LaTex 里面事忽略空格的，编译器会自动添加。如果需要手动添加空格，可以手动用 `\` 来 `添\ 加\ 空\ 格` ，结果就像这样

<center>

>$1234$ 变成了 $1\ 2\ 3\ 4$

</center>

2. LaTeX 里面有章（Chatpers）、节（Sections）和小节（Subsections）之分。通过下面的指令可以添加对应排版并添加小标题。同时 LaTeX 里面还可以添加摘要

3. LaTeX 里面不需要手动添加缩进。LaTeX 对默认每个章节第一段首行顶格，之后的段落首行缩进（不喜欢就加一个 `\noindent`就没有缩进了，如果想图省事全部都不缩进，那么`\setlength{\parindent}{0pt}` 命令之后的缩进全部都没了）。当你需要另起一段的时候，空一行接着写就好。当你想要另起一行但是不想另起一段的时候就使用 `\\`

4. LaTeX 会自动调整页，如果你希望另起一页，在想要的地方加上 `\newpage` 即可

5. 使用 `\tableofcontents` 命令可以在命令添加处添加目录。
6. `{}` 中的内容会被看作一个整体
7. \# \$ % ^ & _ { } ~ \ 这些都是 **保留字**，你需要在每次输入时添加 `\`，比如 `\# \$ \% \^{} \& \_ \{ \} \~{}`，`^` 和 `~` 字符的时侯需要在后面紧跟一对闭合的花括号，否则他们就会被解释为字母的上标

下面基本上的就是告诉各位如何在 body 区里面搞事情了。一切都变得索然无味。

---

## 怎么调节文本格式，写公式

### 写公式

学完如何写公式，事实上剩下的这些你都可以随用随搜了，网上的模板一大把。只需要你按照你的需要填空即可。所以今天没掌握也不要着急，明白一个工程结构的概念就好。

+ 告诉编译器我要写公式了：`$$` 与 `$`
  
  我们所有的公式如果需要嵌入在文章之中，则使用 **一个刀乐**，以 `$ 这里是公式 $` 这样的形式嵌入到需要的地方。（当然，你不嫌麻烦的话，还可以使用`\begin{math}`以及`\end{math}`）

  如果我需要将公式以 **单独一行** 的形式嵌入在文章里面，则
  
  (1) Historically 使用 **两个刀乐**，以 `$$这是另一个公式$$` 这样的形式嵌入到需要的地方。现在不建议这么做。
  
  (2) Modernly `\[ 这是另另一个公式 \]` 或者 `\begin{equation}` 以及 `\end{equation}`（建议使用后者，因为可以添加编号）。

+ 公式的基本语法：
  基本哲学：特殊符号模板就是 `\` + 这个符号的名字（很好记的），然后上下标都是可以随便粘到想要的地方
  + 写希腊字母：
    + `\alpha`  $\rightarrow \alpha$，`\beta` $\rightarrow \beta$，`\gamma` $\rightarrow \gamma$
    + `\Omega\omega\epsilon\varepsilon\pi\varpi` $\rightarrow\Omega\omega\epsilon\varepsilon\pi\varpi$...
  + 给字母加一些奇怪的编号
    + `h^\prime` $h^\prime$
    + `\hbar\bar{h}` $\hbar\bar{h}$
    + `\tilde{a}` $\tilde{a}$
    + `\bar{s}` $\bar{s}$

  + 写二元运算符：
    + `\times` $\rightarrow \times$，~~`\plus\minus`(这是用不了的，兄啊，键盘上就有加号和减号)~~ $\rightarrow+-$，~~`\divide`(兄啊，都事大学生了，哪还有写除号的啊)~~ `\frac{A}{B}` 分号 $\frac{A}{B}$...
    + 微分是用分号搭积木搭起来的

      + `\frac{\partial f}{\partial x}` $\frac{\partial f}{\partial x}$

    + `\int` $\int$， `\oint` $\oint$
  + 上下标
    + `2^3` $2^3$; `^3He` $^3\mathbf{He}$; `D_3` $D_3$; `^4_2He` $^4_2He$


太乐展开

`f(x) = \sum_{i=0}^{\infty} \frac{f^{(i)}(x_0)(x-x_0)^i}{i!}`

$$
f(x) = \sum_{i=0}^{\infty} \frac{f^{(i)}(x_0)(x-x_0)^i}{i!}
$$

~~还有什么符号自己去 Bing 查，大家都是随用随查的~~

### 调节字体

**温馨提示：复制粘贴去试试吧*

```LaTeX
\textit{words in italics}
\textsl{words slanted}
\textsc{words in smallcaps}
\textbf{words in bold}
\texttt{words in teletype}
\textsf{sans serif words}
\textrm{roman words}
\underline{underlined words}
```

用命令将相应的内容包含起来就好了。

### 表格

无序表格

```LaTeX
\documentclass{article}
\begin{document}

\begin{itemize}
  \item The individual entries are indicated with a black dot, a so-called bullet.
  \item The text in the entries may be of any length.
\end{itemize}

\end{document}
```
+ The individual entries are indicated with a black dot, a so-called bullet.
+ The text in the entries may be of any length.


有序表格

```LaTeX
\documentclass{article}
\begin{document}

\begin{enumerate}
  \item This is the first entry in our list.
  \item[-] The list numbers increase with each entry we add.
\end{enumerate}

\end{document}
```

1. This is the first entry in our list.
2. The list numbers decrease with each entry we add.

没有边框的表格

```LaTeX
\begin{center}

% 这{c c c}里面的这几个告诉的是列信息
% c表示该列居中对齐，l，r分别表示左对齐和右对齐
\begin{tabular}{c c c} 

 cell1 & cell2 & cell3 \\ % &用来分割列，\\用来换行
 cell4 & cell5 & cell6 \\  
 cell7 & cell8 & cell9    
\end{tabular}

\end{center}
```

有边框的表格

```LaTeX
% 如果是 |c|c|c| 则会在列之间绘制竖线.
\begin{center}
\begin{tabular}{|c|c|c|} 
 \hline % 表示在这里插入一个贯穿所有列的横着的分割线
 cell1 & cell2 & cell3 \\ 

 \cline{1-2}  % 会在第一列和第二列的竖线之间插入一个横着的分割线。
 cell4 & cell5 & cell6 \\ 
 cell7 & cell8 & cell9 \\ 
 \hline % 表示在这里插入一个贯穿所有列的横着的分割线；
\end{tabular}
\end{center}
```

也就是说，我们可以人为的给行和列在需要的地方加横线和竖线。实现任何想要的表格

矩阵 (矩阵也是表格),太细节的我就不说了，[这里](https://zhuanlan.zhihu.com/p/266267223)说的比我好

```LaTeX
\begin{matrix}
a & b \\
c & d \\
\end{matrix}
\begin{pmatrix}
a & b \\
c & d \\
\end{pmatrix}
\begin{bmatrix}
a & b \\
c & d \\
\end{bmatrix}
\begin{vmatrix}
a & b \\
c & d \\
\end{vmatrix}
```

$$
\begin{matrix}
a & b \\
c & d \\
\end{matrix}
$$
$$\begin{pmatrix}
a & b \\
c & d \\
\end{pmatrix}
$$
$$\begin{bmatrix}
a & b \\
c & d \\
\end{bmatrix}
$$
$$\begin{vmatrix}
a & b \\
c & d \\
\end{vmatrix}$$

### 图片

```LaTeX
\usepackage{graphicx} % 需要使用这个包
\usepackage{float}
\begin{document}

\begin{figure}[H] % 这个参数是告诉编译器把图片放什么位置的，我这里是告诉他放在原地.
  \centering % 使用命令使得图片居中对齐
  \includegraphics[scale=0.8]{pic.png} % 同一文档之下的图片，或者可以使用参数height=0.4 weight=0.3
  \caption{Title of picture} % 图的题目
\end{figure}.

\end{document}
```

~~你终于学会写 LaTeX 力！~~（后面变懒了）

# Reference

一些我觉得比我写的好的多的教程，我写的是各种教程的杂糅

+ [oiwiki 的 LaTeX 入门](https://oi-wiki.org/tools/latex/)

+ [Overleaf 上的 30min LaTeX](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
