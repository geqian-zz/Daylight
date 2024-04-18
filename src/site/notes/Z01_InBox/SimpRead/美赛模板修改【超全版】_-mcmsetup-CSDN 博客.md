---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/m0_46161993/article/details/113800924","title":"美赛模板修改【超全版】_\\mcmsetup-CSDN 博客","summary":null,"Created-Date":"2024-02-04 17:21:03","Modified-Date":"2024-04-18 11:52:09","permalink":"/Z01_InBox/SimpRead/美赛模板修改【超全版】_-mcmsetup-CSDN 博客/","dgPassFrontmatter":true}
---

#### 文章目录

*   *   [效果](#_1)
    *   [去掉模板中重复的两个摘要](#_4)
    *   [去掉摘要页的 Summary](#Summary_18)
    *   [添加目录并更改目录页页眉](#_23)
    *   [调整页边距](#_49)
    *   [在目录中显示 References 标题](#References_71)
    *   [表格](#_88)
    *   [伪代码](#_131)
    *   [小文章或书信等的部分](#_179)
    *   [原理、引理与证明](#_187)
    *   [表格、图片、文献等的引用](#_204)

### 效果

由于美赛模板虽然每年都更新，但是有些格式仍然不合适，比如：存在两个摘要页、目录添加后目录上方页数为 1 很不合适、页边距不合适、页眉宽度与文本宽度不符、缺少 [伪代码](https://so.csdn.net/so/search?q=%E4%BC%AA%E4%BB%A3%E7%A0%81&spm=1001.2101.3001.7020) 示例等。因此笔者对美赛模板进行了适应性的修改，具体修改结果大致如下：  

![](https://img-blog.csdnimg.cn/20210213141530634.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 去掉模板中重复的两个摘要

模板中一般会在第一个摘要页后出现一个仍包含标题的摘要页，这一页一般在美赛中没有什么作用，因此直接去掉即可。去掉的方法为，将控制选项的 `titlepage` 改为 `false` 如下即可：

```
\mcmsetup{
    CTeX = false,  % 使用 CTeX 套装时，设置为 true
    tcn = 000000,  % 团队编号
    problem = A,  % 选题分类
    sheet = true,  % 是否输出摘要页
    titleinsheet = true,  % 是否在摘要页输出标题
    keywordsinsheet = true,  % 是否在摘要页输出关键字
    titlepage = false,  % 是否输出标题页 
    abstract = false  % 是否在标题页输出摘要和关键字
}

```

### 去掉摘要页的 Summary

摘要页中一般除过标题之外一般还会有一个 `Summary` 的摘要名，如果你想要将其去掉，只需要在导言部分添加如下命令即可，其中，命令中的高度值可根据你的需要进行更改，但应为负值。如下：

```
\renewcommand{\abstractname}{\vspace{-37.5pt}}  % 去掉摘要页的summary

```

### 添加目录并更改目录页页眉

使用 `\tableofcontents` 和 `\newpage` 可直接生成目录，但生成目录后，页码的起始页会从目录这一页就开始算，导致文章的真正页的起始页数变成了 2 或者 3，如下：  

![](https://img-blog.csdnimg.cn/20210213144836464.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

  
这是我们不想看到的，因此我们需要在正文开始前、目录后添加 `\setcounter{page}{1}` 来设置页数。但这又会带来新的问题，即文章中的页眉可能会显示两个第 1 页，因为目录页目前也显示第一页，如下：  

![](https://img-blog.csdnimg.cn/2021021314525885.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

  
同时由于该目录不好看，建议使用宏 `\usepackage{tocloft}`，来改变目录，改变后目录如下，但带来了新的问题，即目录的 `Contents` 字样不居中，目录的行间距不是特别合适，更重要的是目录页的页眉消失了，这不符合美赛标准，如下：  

![](https://img-blog.csdnimg.cn/20210213145724111.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

  
因此对目录进行终极大修改如下：

```
\usepackage{tocloft}  % 目录所需宏
\usepackage{setspace}  % 调整目录间距所需宏

\newpage  % 新一页，保证目录与摘要分离
\fancypagestyle{plain}{\rhead{Contents}}  % 设置目录独立页眉右侧显示为"Contents"
\renewcommand{\contentsname}{\hfill Contents \hfill}  % 设置Contents标题居中
\setcounter{tocdepth}{3}  % 显示3级目录
\begin{spacing}{1.3}  % 设置目录行间距
	\tableofcontents  % 生成目录
\end{spacing}
\newpage  % 新一页，保证正文与目录分离

\setcounter{page}{1}  % 设置正文起始页为1
\section{Introduction}  % 这是正文开始的部分

```

最终结果如下：  

![](https://img-blog.csdnimg.cn/20210213150256273.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 调整页边距

由于美赛对于文章的页数有一定的要求，而美赛模板所设置的页边距过大，不是很合适，因此需要对页边距进行调整，如下：

```
\usepackage{geometry}  % 页边距所需宏

% \geometry{left=1in,right=0.75in,top=1in,bottom=1in} 官方文档的建议
\geometry{left=0.75in,right=0.75in,top=1in,bottom=1in}  % 页边距设置，单位为英寸

```

但页边距的更改又带来了新的问题，即页眉的宽度与文本宽度不符，如下：  

![](https://img-blog.csdnimg.cn/20210213151016532.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

  
经过查阅多方资料，发现了一个非常关键的参数 `\textwidth`，一定要记住这个参数，在设置图片、表格等宽度上发挥着重要作用。此处仅需添加如下即可：

```
\setlength\headwidth{\textwidth}  % 设置页眉长度以适配文章宽度

```

因此调整页边距应该连带调整的全部代码为：

```
\usepackage{geometry}  % 页边距所需宏

\geometry{left=0.75in,right=0.75in,top=1in,bottom=1in}  % 页边距设置，单位为英寸
\setlength\headwidth{\textwidth}  % 设置页眉长度以适配文章宽度

```

![](https://img-blog.csdnimg.cn/2021021315143297.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 在目录中显示 References 标题

美赛模板中直接添加目录会导致 `References` 标题不在目录中显示，因此需要手动设置，如下：

```
\phantomsection
\addcontentsline{toc}{section}{References}
\tolerance=500
\begin{thebibliography}{99}  % 一下是参考资料部分
	\bibitem{1} D.~E. KNUTH   The \TeX{}book  the American
	Mathematical Society and Addison-Wesley
	Publishing Company , 1984-1986.
	\bibitem{2}Lamport, Leslie,  \LaTeX{}: `` A Document Preparation System '',
	Addison-Wesley Publishing Company, 1986.
	\bibitem{3}\url{https://www.latexstudio.net/}
\end{thebibliography}

```

![](https://img-blog.csdnimg.cn/20210213154554492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 表格

美赛模板中没有提供表格模板，因此提供表格模板如下，在该模板中，对表格的线宽进行了一定的调整，使其变得更加好看：

```
%++++++添加在引言部分++++++
\usepackage{tabularx}  % 表格所需宏
\usepackage{array}
\newlength\savedwidth  % 改变表格间隔线宽
% whline 表格顶端和底端线宽
\newcommand\whline{\noalign{\global\savedwidth\arrayrulewidth
                            \global\arrayrulewidth 0.95pt}
                   \hline
				   \noalign{\global\arrayrulewidth\savedwidth}}
% shline 表格内部线宽
\newcommand\shline{\noalign{\global\savedwidth\arrayrulewidth
				   			\global\arrayrulewidth 0.6pt}
				   \hline
				   \noalign{\global\arrayrulewidth\savedwidth}}
\usepackage{ragged2e}
\newcolumntype{P}[1]{>{\centering}m{#1}}  % 表格左对齐
\newcolumntype{Z}{>{\centering\let\newline\\\arraybackslash}X}  % 表格文字居中 \hspace{5pt}

%++++++添加在需要表格的地方++++++
\begin{table}[h]  % 表格
	\centering
	\vspace{5pt}
	\setlength{\abovecaptionskip}{0cm}  % 调整间距，该句要在caption上方才有效
	\setlength{\belowcaptionskip}{0.1cm}
	\caption{xxxxx2}  % 表标题 
	\renewcommand{\arraystretch}{1.3}  % 更改表格行间距，默认值为1.0
	\begin{tabularx}{\textwidth}{P{2cm} P{2cm} Z}  
		\whline  
			Start & End  & Character Block Name \\  
		\shline  
			3400  & 4DB5 & CJK Unified Ideographs Extension A \\  
			4E00  & 9FFF & CJK Unified Ideographs \\  
		\whline
	\end{tabularx}
	\label{tab:tab_2}  % 对于表格的引用标签应该为"tab:table_name"的格式
	\vspace{5pt}
\end{table}	

```

效果为：  

![](https://img-blog.csdnimg.cn/20210213153050430.png)

### 伪代码

对于伪代码的引用在美赛模板中也没有提及，因此提供如下模板：

```
%++++++添加在引言部分++++++
\makeatletter  % 算法伪代码部分的说明
\newif\if@restonecol  
\makeatother  
\let\algorithm\relax  
\let\endalgorithm\relax  
\usepackage[linesnumbered,ruled,vlined]{algorithm2e}  % linesnumbered 是否显示行号  
\usepackage{algpseudocode}  
\usepackage{amsmath}  
\renewcommand{\algorithmicrequire}{\textbf{Input:}}  % Use Input in the format of Algorithm  
\renewcommand{\algorithmicensure}{\textbf{Output:}} % Use Output in the format of Algorithm 

%++++++添加在需要伪代码的地方++++++
\begin{algorithm}  % 算法
	\caption{Storage node selection}  % 算法名
	\KwIn{input information}  
	\KwOut{output information}  
	  
	\For{ each host server $PM_i$ in the same subnet with $PM_s$ }{  % for循环条件说明
		% do的内容
		\If{ $PM_i$ is not a service providing node or checkpoint image storage node of $S_k$ }{  % if语句条件
			% if 内容
			add $PM_i$ to $candidateList$ \;  
		}  
	}  
	sort $candidateList$ by reliability desc\;  
	init $storageserver$\; 
	clear $candidateList$\;  
	add all other subnets in $pod_s$ to $netList$\;  
	\For{ each subnet $subnet_j$ in $netList$}{  
		clear $candidateList$\;  
		\For {each $PM_i$ in $subnet_j$ }{  
			\If{ $PM_i$ is not a service providing node or checkpoint image storage node of $S_k$ }{  
				add $PM_i$ to $candidateList$\;  
			}  
		}  
		sort all host in $candidateList$ by reliability desc\; 
	} 
	\While(hhh){condition}{while information}  % while语句
	\textbf{final} \;  
	\textbf{return} $storageserver$;  
\end{algorithm} 

```

效果为：  

![](https://img-blog.csdnimg.cn/20210213153350461.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 小文章或书信等的部分

一般美赛都会要求写一篇 1~2 页的小文章或者一封书信等，这一部分一般放在正文最后、参考资料之前，且在标题前不显示标号，因此这部分的标题应该这样设置：

```
\addcontentsline{toc}{section}{Article}  % 在目录中添加，"Article"为该部分的名字
\tolerance=500  % 字号大小，这个与其他保持一致，一般不需要更改
\section*{Article}  % 去掉编号且不在目录显示，这也是为何上面要单独设置在目录中显示的原因

```

![](https://img-blog.csdnimg.cn/2021021315494492.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzQ2MTYxOTkz,size_16,color_FFFFFF,t_70)

### 原理、引理与证明

有时需要用到原理引理与证明，具体使用如下：

```
\begin{Theorem}  % 原理
	The theorem itself.
	\label{thm:thm_name}
\end{Theorem}
\begin{Lemma}  % 引理
	The lemma of theorem.
	\label{lem:lem_name}
\end{Lemma}
\begin{proof}  % 证明
	The proof of theorem.
\end{proof}

```

![](https://img-blog.csdnimg.cn/202102131602478.png)

### 表格、图片、文献等的引用

为了方便对表格、图片、文献等进行引用，防止引用编号出错，使用如下方法完成引用：

```
\ref{fig:fig_name}  % 图片引用，里面填"fig:图片名"
\ref{tab:tab_name}  % 表格引用，里面填"tab:表格名"
\ref{thm:thm_name}  % 定理引用，里面填"thm:定理名"
\ref{lem:lem_name}  % 引理引用，里面填"lem:引理名"
\eqref{equ_name}  % 公式引用，里面填公式名
\cite{1}  % 参考引用，里面填参考文献编号

```