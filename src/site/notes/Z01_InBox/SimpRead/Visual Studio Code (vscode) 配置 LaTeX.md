---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/166523064","title":"Visual Studio Code (vscode) 配置 LaTeX","summary":null,"Created-Date":"2023-08-08 17:58:02","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/Visual Studio Code (vscode) 配置 LaTeX/","dgPassFrontmatter":true}
---




## Z.1. 前言

**LaTeX** 作为一种强大的排版系统，对于理工科，特别是公式比较多的数 (tu) 学 (tou) 专业，其重要性自不必多说，不在本文探讨范围之内。

而选择一个比较好的编译器是很重要的，至少对笔者而言是如此。笔者前期使用的 **TeXstudio** 进行文档的编译的，但是其编译速度比较慢，并且页面不是很美观。最让人头疼的是，当公式比较长的时候，使用的括号就比较多，但 **Texstudio** 的代码高亮功能实在是....（它对于括号根本就没有高亮，头秃）

而 **Visual Studio Code** 呢？话不多说，直接上图！

![](https://pic1.zhimg.com/v2-47f995b53b3ffb7d9bd13243ca9e9ccc_r.jpg)

可以看到，它不仅能够对代码高亮，不同级别括号用不同颜色标注了，颜值也很高。vscode 最突出的特点就是其强大的插件功能，每个使用者都能够根据自己的需求和想法下载相应的插件，从而将之配置为高度个性化的编辑器。可以这么说，每个使用者的 vscode 都不一样，为其专属定制编辑器。

笔者配置了好久，找了很多资料，很多博主也只是贴上了配置代码，没有详细的介绍说明。为了让更多人能够有一个比较清晰的了解，以此可以随时对自己的配置代码进行更改，笔者写下了此文。希望能够对大家有所帮助。

**注 1 ：**本文使用图片均为笔者自身编辑器截图或笔者朋友的编辑器截图（经过对方同意），且所有引用在文中或文末注明了来源，其余均为原创内容（代码不算哈哈哈）。

**注 2 ：**若您的 vscode 页面和笔者所用图片中展示的页面有略微不同，均为笔者所安装的其余插件以及其余设置所致，并不影响本文中所说的所有配置，您无需担心，只需按照图片中所指向图标进行配置即可。

**注 3 ：**文末有完整的个人配置代码（有的地方需要更改路径，有具体说明）。

**在正式看本文之前，还请各位读者能够读一下我下面这段话，不甚感激**

本文是笔者初次探索 VScode 所写下的文章，花了三周的时间。首先非常感谢大家能够对本文的认可，谢谢大家

这里主要想要对大家说对不起，真的对不起，后期好多读者配置过程中有问题，但是我都没有回复。但是，其实是我真的无能为力了。因为这篇文章已经把我所有知道的东西写出来了，有的读者出现了本文意料之外的问题，会评论，会私信，但其实，你们问我的每一个问题，如果是本文内容涉及到的，还请认真阅读本文。如果是本文以外的，我其实，也不知道，也真的只是一个小白而已，在挣扎。

另外，读者们出现的问题，我其实也是需要去网上查的，其实绝大部分都能查到的，既然选择使用 LaTeX，必然是拥有这方面能力的。所以，还请各位读者朋友们能够善用网络。另外，如果本文真的对您有所帮助，我也不需要点赞或者什么，如果您能再花费一些额外的时间，帮评论区朋友们解决一些出现的问题的话，不甚感激。

另，没有办法经常看知乎了，请各位见谅啊。  

## Z.2. TeX Live 下载与安装

笔者选用的 Tex 系统是 TeX Live ，如果您想了解 TeX Live 和 MiKTeX 的区别，可以查看此篇文章：

[（译）在 Windows 上使用 TeX：TeX Live 与 MiKTeX 的对比](https://link.zhihu.com/?target=https%3A//www.cnblogs.com/liuliang1999/p/12656706.html)

接下来是 TeX Live 的 **下载与安装说明**：

① 通过网址 ：

[Acquiring TeX Live as an ISO image](https://link.zhihu.com/?target=http%3A//tug.org/texlive/acquire-iso.html)

进入 ISO 下载页面，点击图示红框圈画位置进入随机的镜像网站。

![](https://pic1.zhimg.com/v2-8a250fb74061547b79689d0206b1e588_r.jpg)

② 可以看到的是，笔者进入了清华大学镜像网站，点击红框圈画链接进行 TeX Live 下载。

![](https://pic2.zhimg.com/v2-9d56e7f966e487e22395179c8261199d_r.jpg)

③ 如果 **下载速度过慢**，可以返回前一页面，进行重新点击，随机进入另一镜像网站进行下载尝试，直到下载速度在您的可接受范围内即可。或者在前一页面，点击 **"mirror list"** 进入镜像列表

![](https://pic4.zhimg.com/v2-1f6a48df96b0c18cbc6a0e3db67e5ed3_r.jpg)

然后手动选择某一镜像网站进行下载：

![](https://pic3.zhimg.com/v2-5a87555591c462962b55e6fc6fdf00ea_r.jpg)

④ 找到下载好的压缩包，右键，在打开方式中选择 **“Windows 资源管理器 "** 打开

![](https://pic2.zhimg.com/v2-4ec3eda449f70e5c676b58a922343645_r.jpg)

⑤ 找到 **"install-tl-windows"** 文件，为了后面不必要的麻烦，右键 **以管理员身份运行**

![](https://pic4.zhimg.com/v2-2f29568230f2b17c4f72dde10d7f6007_r.jpg)

⑥ 会先出现下图，无需理会，等会儿会消失

![](https://pic1.zhimg.com/v2-4250c2abb56eff32c38834396e88ede4_b.jpg)

⑦ **基本更改：**出现下图后，需要进行路径的更改；由于 TeX Live 自带的 TeXworks 不怎么好用，并且此文主要将 vscode 作为 LaTeX 的编辑器，故而取消 **安装 TeXworks 前端** 的选项，再点击安装

![](https://pic1.zhimg.com/v2-c52fd778b93f735d04d71a5df602d2a8_b.jpg)

⑧ **个性化安装：** 如果您需要个性化程度高的话，那么可以点击上图左下角的 **Advancde** ，根据您的需要进行相应的更改，但 **建议** 在不明白各个选项的作用时，不要对其进行修改，以免后期使用产生奇怪的问题。要注意的是，**Adjust searchpath** 这个选项一定要选中，将之添加到环境变量，否则后期手动添加比较麻烦；

而对于我们大部分人来说，只需要更改下图框选出的部分即可，也就是上图所完成的功能，再点击 **安装** 即可

![](https://pic3.zhimg.com/v2-62ab1fa73c53f8421df62828c498d036_r.jpg)

⑨ **进行安装：**接着就会出现下图，具体的安装指标已在下图标明，可根据其数字来判断安装所需时间。

![](https://pic1.zhimg.com/v2-24be6bfb89fa079cb1436aa62222eaa0_r.jpg)

当上面标示的时间安装完之后，会出现一些配置文件的安装运行写入，进行等待即可，几分钟左右：

![](https://pic2.zhimg.com/v2-94d8416c76ff3c139063a4b8b71cba3d_r.jpg)

当出现下图所示弹窗时，说明安装完毕，点击关闭即可。

![](https://pic3.zhimg.com/v2-908faffd78dca6bd35a0445aea0d521e_r.jpg)

⑩ 检查安装是否正常： 按 **win + R** 打开运行，输入 **cmd**，打开命令行窗口；然后输入命令 **xelatex -v** ，如下图

![](https://pic2.zhimg.com/v2-c19eeb1b3a7558c834a4bea2a85b9a7d_r.jpg)

如上图所示，若输出了一些版本信息，则安装正常。

## Z.3. vscode 下载

官网下载：

[Click here to download Visual Studio Code](https://link.zhihu.com/?target=https%3A//code.visualstudio.com/)

点进去之后就可以进行下载了。具体安装过程与常见的软件安装过程一致，这里就不作赘述。笔者只对几个 **要点** 进行提及：

① 记得 **修改安装路径**

② 根据个人想法可以选择是否在开始菜单文件夹创建 vscode 的快捷方式

![](https://pic3.zhimg.com/v2-e2039abadd095a9647fa50fdd639726e_r.jpg)

③ 一定要选上 **" 添加到 PATH”** 这个选项，能省很多麻烦。其余如图所示，自行选择。

![](https://pic2.zhimg.com/v2-024c709b63c2682dade44540642737e5_r.jpg)

安装好之后，打开 vscode，应如下图页面所示：

![](https://pic3.zhimg.com/v2-b7f200c44ede6c2a452d2615d09c08ee_r.jpg)

## Z.4. 中文语言环境配置

vscode 的中文环境需要下载插件来进行支持。如下图所示：

① 点击拓展图标，打开拓展；

② 输入 **"Chinese"**，选择第一个 Chinese (Simplified) Language Pack for Visual Studio Code 插件；

③ 点击 **"install"** 进行安装，等待安装完成；

![](https://pic1.zhimg.com/v2-11ec6ecc7dacfbfdf6a0d3ab1fe0f9a4_r.jpg)

④ 点击页面右下角跳出窗口中的 **"Restart now"**，进行 vscode 重启。

![](https://pic1.zhimg.com/v2-57860a05da184fa4226a2104513d8f1c_r.jpg)

⑤ 完成中文环境配置，显示如下：

![](https://pic4.zhimg.com/v2-563a1bd8d874db37e2a3130ab6c570e3_r.jpg)

## Z.5. LaTeX 的支持插件 LaTeX Workshop 安装

① 点击拓展图标，打开拓展；

② 输入 **"latex workshop"**，选择第一个 LaTeX Workshop 插件；

③ 点击 **"install"** 进行安装，等待安装完成；

![](https://pic3.zhimg.com/v2-37df048ea711ccd6191a06763899d952_r.jpg)

④ 若在安装完该插件之后在 vscode 页面右下角跳出如下弹窗，无需在意，只是提醒该插件已经更新到了 8.11.1 版本。若您想要了解新版本增加的功能，可以点击 **"Change log"** 进行查看；若不想了解，点击 **"Disable this message"** 即可。

![](https://pic1.zhimg.com/v2-4a9aec61bb403f89fa84b9f2f0ae46fc_r.jpg)

## Z.6. 打开 LaTeX 环境设置页面

① 点击设置图标

② 点击设置

③ 转到 UI 设置页面

![](https://pic3.zhimg.com/v2-9f7cd81aeac1a5565d3f0e39c902ab02_r.jpg)

④ 点击下图 **1** 处打开 json 文件，进入代码设置页面

![](https://pic3.zhimg.com/v2-8a214dc687d81cf4ecb25c5e5e9ea69e_r.jpg)

**注 4 ：** UI 设置页面和 JSON 设置页面均为设置页面，其功能是一样的。不同的是，UI 设置页面交互能力较强，但一些设置需要去寻找，比较麻烦；而 JSON 设置页面虽然相对 UI 而言不那么直观，但却可以对自己想要的功能直接进行代码编写，且代码设置可以直接克隆别人的代码到自己的编辑器中，从而直接完成相应设置，比较便捷。

**注 5 ：**可以直接按 **Ctrl + ，**进入设置页面。

## Z.7. LaTeX 环境的代码配置

## Z.8. LaTeX 配置代码展示

先给出效果图：

![](https://pic2.zhimg.com/v2-175b476a0cf425370065156bf807e205_r.jpg)

LaTeX 配置代码如下（不包含外部 pdf 查看器设置）：

```
{
    "latex-workshop.latex.autoBuild.run": "never",
    "latex-workshop.showContextMenu": true,
    "latex-workshop.intellisense.package.enabled": true,
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        },
    ],
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ],
    "latex-workshop.latex.autoClean.run": "onFailed",
    "latex-workshop.latex.recipe.default": "lastUsed",
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"
}

```

**注 6 ：** 若您不想要配置外部查看器以及了解内部查看和外部查看之间切换操作，可以直接复制上述代码至 json 文件中，即可完成 LaTeX 的配置，从而可以对 LaTeX 代码进行编译。

**注 7 ：**根据 json 文件编写规则，每个代码语句（除了代码块儿最后一句）都需要加上英文状态下的 `,`，否则就会报错；而每个代码块儿的最后一句是不需要加上 `,` 的。从上文整个代码块儿可以看出此规则。

如果您日后需要在上述代码之后再添加其他代码，请记得在最后一句

```
"latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"

```

后添加上 `,`，即变为

```
"latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",
......

```

其中的 `......` 为您添加的其余代码。

**切记！**

## Z.9. LaTeX 配置代码解读

如果您对此不感兴趣，可以跳过该小节。下面进行代码 **注释解读**：

```
"latex-workshop.latex.autoBuild.run": "never"

```

设置何时使用默认的 (第一个) 编译链自动构建 LaTeX 项目，即什么时候自动进行代码的编译。有三个选项：

1. **onFileChange**：在检测任何依赖项中的文件更改 (甚至被其他应用程序修改) 时构建项目，即当检测到代码被更改时就自动编译 tex 文件；

2. **onSave** : 当代码被保存时自动编译文件；

3. **never**: 从不自动编译，即需编写者手动编译文档

此项笔者设置为 **never**。

```
"latex-workshop.showContextMenu": true

```

启用上下文 LaTeX 菜单。此菜单默认状态下停用，即变量设置为 **false**，因为它可以通过新的 LaTeX 标记使用（新的 LaTeX 标记能够编译文档，将在下文提及）。只需将此变量设置为 **true** 即可恢复菜单。即此命令设置是否将编译文档的选项出现在鼠标右键的菜单中。

下两图展示两者区别，第一幅图为设置 **false** 情况，第二幅图为设置 **true** 情况。可以看到的是，设置为 **true** 时，菜单中多了两个选项，其中多出来的第一个选项为进行 tex 文件的编译，而第二个选项为进行正向同步，即从代码定位到编译出来的 pdf 文件相应位置，下文会进行提及。

![](https://pic2.zhimg.com/v2-d614a4ecc4b7da18624926b5a49f144d_b.jpg)

![](https://pic3.zhimg.com/v2-c66892ca1a278e961fe9fdb124896126_b.jpg)

笔者觉得菜单多了此选项较方便，故此项笔者设置为 **true**

```
"latex-workshop.intellisense.package.enabled": true

```

设置为 **true**，则该拓展能够从使用的宏包中自动提取命令和环境，从而补全正在编写的代码。

```
"latex-workshop.message.error.show"  : false,
"latex-workshop.message.warning.show": false

```

这两个命令是设置当文档编译错误时是否弹出显示出错和警告的弹窗。因为这些错误和警告信息能够从终端中获取，且弹窗弹出比较烦人，故而笔者设置均设置为 **false**。

```
"latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ]

```

这些代码是定义在下文 recipes 编译链中被使用的编译命令，此处为默认配置，不需要进行更改。其中的 `name` 为这些命令的标签，用作下文 recipes 的引用；而 `command` 为在该拓展中的编译方式。

可以更改的代码为，将编译方式: pdflatex 、 xelatex 和 latexmk 中的 `%DOCFILE` 更改为 `%DOC`。`%DOCFILE` 表明编译器访问没有扩展名的根文件名，而 `%DOC` 表明编译器访问的是没有扩展名的根文件完整路径。这就意味着，使用 `%DOCFILE` 可以将文件所在路径设置为中文，但笔者不建议这么做，因为毕竟涉及到代码，当其余编译器引用时该 tex 文件仍需要根文件完整路径，且需要为英文路径。笔者此处设置为 `%DOCFILE` 仅是因为之前使用 TeXstudio，导致路径已经是中文了。

更多详情可以访问 github 中 LaTeX-Workshop 的 Wiki:

[https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#placeholders](https://link.zhihu.com/?target=https%3A//github.com/James-Yu/LaTeX-Workshop/wiki/Compile%23placeholders)

```
"latex-workshop.latex.recipes": [
        {
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ]

```

此串代码是对编译链进行定义，其中 `name` 是标签，也就是出现在工具栏中的链名称；`tool` 是 `name` 标签所对应的编译顺序，其内部编译命令来自上文 `latex-workshop.latex.recipes` 中内容。

定义完成后，能够在 vscode 编译器中能够看到的编译顺序，具体看下图：

![](https://pic2.zhimg.com/v2-42b419223d07a18fd406ecd54f674fd1_r.jpg)

可以看到的是，在编译链中定义的命令出现在了 vscode 右侧的工具栏中。

**注 8 ：PDFLaTeX** 编译模式与 **XeLaTeX** 区别如下：

1. PDFLaTeX 使用的是 TeX 的标准字体，所以生成 PDF 时，会将所有的非 TeX 标准字体进行替换，其生成的 PDF 文件默认嵌入所有字体；而使用 XeLaTeX 编译，如果说论文中有很多图片或者其他元素没有嵌入字体的话，生成的 PDF 文件也会有些字体没有嵌入。  
2. XeLaTeX 对应的 XeTeX 对字体的支持更好，允许用户使用操作系统字体来代替 TeX 的标准字体，而且对非拉丁字体的支持更好。  
3. PDFLaTeX 进行编译的速度比 XeLaTeX 速度快。

引用自 _蛐蛐蛐先生的博客_ ：

[PDFLaTeX 和 XeLaTeX 有什么区别_qysh123 的专栏 - CSDN 博客_xelatex 和 pdflatex 哪个更好](https://link.zhihu.com/?target=https%3A//blog.csdn.net/qysh123/article/details/11833649%3Futm_source%3Dtuicool)

**注 9 ：** 编译链的存在是为了更方便编译，因为如果涉及到**.bib** 文件，就需要进行多次不同命令的转换编译，比较麻烦，而编译链就解决了这个问题。

```
"latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ]

```

这串命令则是设置编译完成后要清除掉的辅助文件类型，若无特殊需求，无需进行更改。

```
"latex-workshop.latex.autoClean.run": "onFailed"

```

这条命令是设置什么时候对上文设置的辅助文件进行清除。其变量有：

1. **onBuilt** : 无论是否编译成功，都选择清除辅助文件；

2. **onFailed** : 当编译失败时，清除辅助文件；

3. **never** : 无论何时，都不清除辅助文件。

由于 tex 文档编译有时需要用到辅助文件，比如编译目录和编译参考文献时，如果使用 `onBuilt` 命令，则会导致编译不出完整结果甚至编译失败；

而有时候将 tex 文件修改后进行编译时，可能会导致 pdf 文件没有正常更新的情况，这个时候可能就是由于辅助文件没有进行及时更新的缘故，需要清除辅助文件了，而 `never` 命令做不到这一点；

故而笔者使用了 `onFailed`，同时解决了上述两个问题。

```
"latex-workshop.latex.recipe.default": "lastUsed"

```

该命令的作用为设置 vscode 编译 tex 文档时的默认编译链。有两个变量： 1. **first** : 使用 `latex-workshop.latex.recipes` 中的第一条编译链，故而您可以根据自己的需要更改编译链顺序； 2. **lastUsed** : 使用最近一次编译所用的编译链。

笔者选择使用 **lastUsed**。

```
"latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"

```

用于反向同步（即从编译出的 pdf 文件指定位置跳转到 tex 文件中相应代码所在位置）的内部查看器的快捷键绑定。变量有两种：

1. **ctrl-click** ： 为默认选项，使用 Ctrl/cmd + 鼠标左键单击

2. **double-click** : 使用鼠标左键双击

此处笔者使用的为 **double-click**。

## Z.10. tex 文件编译

## Z.11. tex 测试文件下载

为了测试 vscode 功能是否比较完整，笔者编写了一份简单的 tex 文件，以此测试其是否支持中英文，能否编译目录，能否插入图片，能否进行引用，能否编译参考文献（编译 bixtex 文件）等功能。

测试所用的 tex 文件可以从 github 下载：

[Ali-loner/Ali-loner.github.io](https://link.zhihu.com/?target=https%3A//github.com/Ali-loner/Ali-loner.github.io)

**下载步骤** 如图：

![](https://pic3.zhimg.com/v2-f2d5103563e0bb9db364c4f946de22d2_r.jpg)

**注 10 ：** 若因网络原因无法连接到 github 导致无法下载，可以使用自己的 tex 文件进行测试，或者复制以下代码进行文档的简单编译测试，但其只能测试一部分功能：

```
\documentclass[a4paper]{article}
\usepackage[margin=1in]{geometry} % 设置边距，符合Word设定
\usepackage{ctex}
\usepackage{lipsum}
\title{\heiti\zihao{2} This is a test for vscode}
\author{\songti Ali-loner}
\date{2020.08.02}
\begin{document}
    \maketitle
\begin{abstract}
    \lipsum[2]
\end{abstract}
\tableofcontents
\section{This is a section}
Hello world! 你好，世界 ！
\end{document}

```

## Z.12. tex 测试文件编译

**① 打开测试文件所在文件夹**

![](https://pic1.zhimg.com/v2-cc8b54b9dd5e44f7ff79b988c5d214d4_r.jpg)

**② 点击选中 tex 文件**，进行文件内容查看

![](https://pic4.zhimg.com/v2-2938ac1763f64723cc7f2812923ccf07_r.jpg)

**③ 开始编译文件。** 由于进行测试的文件中涉及参考文献的引用（**.bib** 的编译），故而选择 `xelatex -> bibtex -> xelatex*2` 编译链。

![](https://pic3.zhimg.com/v2-c42deeda6c6dd52e46ca85f780d77a6e_r.jpg)

**注 11 ：**为了更方便进行编译，可对其设置快捷键，设置快捷键步骤如下：

![](https://pic2.zhimg.com/v2-f9c5c82990dbeac2895ec2593bbff1c5_r.jpg)

笔者将快捷键设置为 **Ctrl+Alt+R**。

**选中 tex 文件的代码页面**（若未选中，则无法进行编译），然后按下该快捷键，在编辑器页面上端进行编译链选择，如下图：

![](https://pic3.zhimg.com/v2-c9fb99fa3eab73827ecfe822ea24f316_r.jpg)

**④ 编译成功**

当发现页面下方出现 **√** 符号时，说明编译成功，相反，如果出现 **×** 符号，说明编译失败，就要找失败原因了。

**a.** 左侧工具栏

当编译成功后，选中 tex 文件中任意的代码，以此来选中 tex 文件，然后进行图示操作。其中侧边栏所展现的就是上文提及的新的 LaTeX 标记。

![](https://pic3.zhimg.com/v2-7581b1033a9c201fc13c9c1ebb05d01e_r.jpg)

**b.** 快捷键

选中 tex 文件中任意的代码，然后按 **Ctrl+Alt+V**，出现编译好的 pdf 页面。该快捷键为默认设置。若您想要更改，可以根据上文进行配置。

![](https://pic4.zhimg.com/v2-880a90f3a4feb0e1628d21b7765acaa3_r.jpg)

注意到，现在编译的结果为内部查看器查看。

**⑤ 正向同步测试**，即从代码定位到 pdf 页面相应位置。有以下三种方法：

**a.** 使用侧边工具栏

![](https://pic2.zhimg.com/v2-26481bfc0f4bccff10394e3746ad61e1_r.jpg)

**b.** 使用右键菜单

![](https://pic4.zhimg.com/v2-5f13291f73b7182ec16cfb5585d729f7_r.jpg)

**c.** 使用快捷键

选中需要跳转的代码所在行，按 Ctrl+Alt+J，右侧就会跳转到相应行。这里的快捷键为默认设置，可自行通过上文方式设置为您想要的快捷键。

**⑥ 反向同步测试**, 即从 pdf 页面定位到代码相应位置

在编译生成的 pdf 上，选中想要跳转行，鼠标 **左键双击** 或 **ctrl + 鼠标左键单击**，跳转到对应代码。此处快捷键的选择为上文设置，若使用笔者的代码，则为 **鼠标左键双击**。

![](https://pic3.zhimg.com/v2-2297f86ee5e2ed18067fbbb82c6c539a_r.jpg)

## Z.13. SumatraPDF 安装设置（可选）

您可自行选择是否需要设置此部分内容。

有的时候，由于想要看到 pdf 文件的完整展现效果，使用内置查看器已无法满足需求，这时可以使用外部查看器进行查看。

外部查看器的优势是能够看到 pdf 文件在查看器中的目录，可以实时进行跳转；且根据笔者使用来看，外部查看器展示出来的 pdf 默认会放大一些，使得字体变大，要更加让人舒服一些。

笔者选择 **SumatraPDF** 作为外部查看器，该软件的优点在于在具有 pdf 阅读功能的同时很轻量，安装包不到 10MB 大小，且支持双向同步功能。通过调整其与 vscode 的窗口位置，能够在拥有这些优势的同时，达到与内置 pdf 查看具有相同的效果。

## Z.14. SumatraPDF 下载与安装

官网下载：

[Click here to download SumatraPDF](https://link.zhihu.com/?target=https%3A//www.sumatrapdfreader.org/download-free-pdf-viewer.html)

![](https://pic4.zhimg.com/v2-3173f5fb7cc1a8dcc5f2c349565e5997_r.jpg)

其安装很简单，与通用软件安装过程一致，记得更改安装路径并记住，下文配置需要使用其路径。

## Z.15. 使用 SumatraPDF 查看的代码配置

### Z.15.1. 代码展示

```
{
    "latex-workshop.view.pdf.viewer": "external",
    "latex-workshop.view.pdf.ref.viewer":"auto",
    "latex-workshop.view.pdf.external.viewer.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    "latex-workshop.view.pdf.external.viewer.args": [
        "%PDF%"
    ],
    "latex-workshop.view.pdf.external.synctex.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    "latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"F:/Microsoft VS Code/Code.exe\" \"F:/Microsoft VS Code/resources/app/out/cli.js\" -r -g \"%f:%l\"", // 注意修改路径
        "%PDF%"
    ]
}

```

此代码仅为展示所用，让您进行查看，为下文解读之用。如需写入到 json 文件内，可直接完整复制文末笔者的个人配置到自己的编译器内。

### Z.15.2. 代码解读

```
"latex-workshop.view.pdf.viewer": "external"

```

设置默认的 pdf 查看器，有三种变量参数：

1. **tab** : 使用 vscode 内置 pdf 查看器；

2. **browser** : 使用电脑默认浏览器进行 pdf 查看；

3. **external** : 使用外部 pdf 查看器查看。

此处选择 **external** 参数，使用外部查看器。

**注 12 ：** 此参数为下文进行 pdf 内部查看和外部查看进行切换的关键参数。

```
"latex-workshop.view.pdf.ref.viewer":"auto"

```

设置 PDF 查看器用于在 **\ref** 命令上的 [View on PDF] 链接，此命令作用于 **\ref** 引用查看。有三个参数变量：

1. **auto** : 由编辑器根据情况自动设置；

2. **tabOrBrowser** : 使用 vscode 内置 pdf 查看器或使用电脑默认浏览器进行 pdf 查看；

3. **external** : 使用外部 pdf 查看器查看。

此处设置为 **auto**。

```
"latex-workshop.view.pdf.external.viewer.command": "F:/SumatraPDF/SumatraPDF.exe"// 注意修改路径

```

使用外部查看器时要执行的命令，设置外部查看器启动文件 **SumatraPDF.exe** 文件所在位置，此处需要您根据自身情况进行路径更改，正常情况下只需更改磁盘盘符即可。

**请注意** 中间为 **"/"** 而不是 **"\"** ，不然会报错。

```
"latex-workshop.view.pdf.external.viewer.args": [
        "%PDF%"
    ]

```

此代码是设置使用外部查看器时，`latex-workshop.view.pdf.external.view .command` 的参数。`%PDF%` 是用于生成 PDF 文件的绝对路径的占位符。

```
"latex-workshop.view.pdf.external.synctex.command": "F:/SumatraPDF/SumatraPDF.exe" // 注意修改路径

```

此命令是将生成的辅助文件 **.synctex.gz** 转发到外部查看器时要执行的命令, 设置其位置参数，您注意更改路径，此路径为 **SumatraPDF.exe** 文件路径。与上文相同。

```
"latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"F:/Microsoft VS Code/Code.exe\" \"F:/Microsoft VS Code/resources/app/out/cli.js\" -r -g \"%f:%l\"", // 注意修改路径
        "%PDF%"
    ]

```

当 **.synctex.gz** 文件同步到外部查看器时 `latex-workshop.view.pdf.external.synctex` 的参数设置。`%LINE%` 是行号，`%PDF%` 是生成 PDF 文件的绝对路径的占位符，`%TEX%` 是当触发 syncTeX 被触发时，扩展名为 **.tex** 的 LaTeX 文件路径。

上面代码串中记得进行 **Microsoft VS Code** 路径修改，修改如下图:

![](https://pic2.zhimg.com/v2-a477f108729117b53b2f0fd611357f81_r.jpg)

此处感谢 [@可爱又迷人的反派](https://www.zhihu.com/people/Dota-Data) 对于笔者的代码提出的修改，让一部分读者存在的 SumatraPDF 无法进行正常反向同步操作的问题得到了解决。

## Z.16. SumatraPDF 的使用

将完整代码复制到自己的 json 文件内后，即可使用 SumatraPDF 作为自己的 pdf 外部查看器了。以下为具体操作：

① 点击编辑页面任意位置来选中 tex 文件；

② 按 Ctrl+Alt+V，打开编译出的 pdf 文件；

③ 出现如下图页面。可以看到的是，原本内嵌输出的 pdf 变为了在 SumatraPDF 上查看，且侧面带有书签：

![](https://pic4.zhimg.com/v2-9b6ca459e3d476f0212ea73054a42513_r.jpg)

④ 为了出现和内嵌输出具有相同的效果，可以将 vscode 和 SumatraPDF 进行分屏，且根据需要关闭标签，如下图：

![](https://pic1.zhimg.com/v2-a2220a77580118d76a4d8e2cc787316c_r.jpg)

⑤ 且同样支持双向同步（正向同步和反向同步），其操作步骤与内嵌输出 pdf 时操作步骤相同，此处就不再赘述。查看效果图：

![](https://pic3.zhimg.com/v2-44c5bc95722bbc6c6440baf3a0eee47a_r.jpg)

## Z.17. pdf 内部查看与外部查看的切换

以下展示由外部查看转为内部查看的操作，由内转外操作相同。

共有两种操作方式：**UI 界面设置** 或 **Json 界面设置** 。具体见下图：

![](https://pic4.zhimg.com/v2-f8721aaa72da52d9050f11d97b8177e3_r.jpg)

您可根据个人适应选择相应的方法。

## Z.18. 个人完整配置



```
{
 //------------------------------LaTeX 配置----------------------------------
    // 设置是否自动编译
    "latex-workshop.latex.autoBuild.run":"never",
    //右键菜单
    "latex-workshop.showContextMenu":true,
    //从使用的包中自动补全命令和环境
    "latex-workshop.intellisense.package.enabled": true,
    //编译出错时设置是否弹出气泡设置
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
    // 编译工具和命令
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    // 用于配置编译链
    "latex-workshop.latex.recipes": [
        {
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
    //文件清理。此属性必须是字符串数组
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ],
    //设置为onFaild 在构建失败后清除辅助文件
    "latex-workshop.latex.autoClean.run": "onFailed",
    // 使用上次的recipe编译组合
    "latex-workshop.latex.recipe.default": "lastUsed",
    // 用于反向同步的内部查看器的键绑定。ctrl/cmd +点击(默认)或双击
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",



    //使用 SumatraPDF 预览编译好的PDF文件
    // 设置VScode内部查看生成的pdf文件
    "latex-workshop.view.pdf.viewer": "external",
    // PDF查看器用于在\ref上的[View on PDF]链接
    "latex-workshop.view.pdf.ref.viewer":"auto",
    // 使用外部查看器时要执行的命令。此功能不受官方支持。
    "latex-workshop.view.pdf.external.viewer.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    // 使用外部查看器时，latex-workshop.view.pdf.external.view .command的参数。此功能不受官方支持。%PDF%是用于生成PDF文件的绝对路径的占位符。
    "latex-workshop.view.pdf.external.viewer.args": [
        "%PDF%"
    ],
    // 将synctex转发到外部查看器时要执行的命令。此功能不受官方支持。
    "latex-workshop.view.pdf.external.synctex.command": "F:/SumatraPDF/SumatraPDF.exe", // 注意修改路径
    // latex-workshop.view.pdf.external.synctex的参数。当同步到外部查看器时。%LINE%是行号，%PDF%是生成PDF文件的绝对路径的占位符，%TEX%是触发syncTeX的扩展名为.tex的LaTeX文件路径。
    "latex-workshop.view.pdf.external.synctex.args": [
        "-forward-search",
        "%TEX%",
        "%LINE%",
        "-reuse-instance",
        "-inverse-search",
        "\"F:/Microsoft VS Code/Code.exe\" \"F:/Microsoft VS Code/resources/app/out/cli.js\" -r -g \"%f:%l\"", // 注意修改路径
        "%PDF%"
    ]
}

```

**写在最后** ：

笔者也只是一个初学者，文中如果出现错误的地方，欢迎您在评论区批评指正，笔者会虚心接受这些产生错误的地方，争取以后学得更扎实再编写这些文字。

笔者已经将自己所知道的全部写在了本文中，据读者反应能够基本解决配置问题。而如果您在阅读完此文章之后，依旧产生了意外的配置问题，抱歉啊，笔者能力有限，可能无法依据自身能力为您解答，也是只能上网搜索解决办法。而我所能搜到的，相信您自身也能够搜到。所以若您有额外产生的问题，可以在评论区中评论，看是否有其他读者能够解决相应问题。【抱拳】

另：若您感觉此文写得还行，希望您能够不吝点赞，以激发笔者的创作热情，从而能在日后写下更多更好的文章。非常感谢您！！！

## Z.19. 参考：

[undefined](https://zhuanlan.zhihu.com/p/38178015)