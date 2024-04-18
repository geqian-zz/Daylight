---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/incredibleimpact/article/details/109733494","title":"VS Code C 语言开发环境配置附图版保姆教程_blog.csdn.net/incredibleeimpact/article/details/10_incredibleimpact 的博客 - CSDN 博客","summary":"CS 自学指南","Created-Date":"2023-09-10 09:30:12","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/VS Code C 语言开发环境配置附图版保姆教程_blog_csdn_net_incredibleeimpact_article_details_10_incredibleimpact 的博客 - CSDN 博客/","dgPassFrontmatter":true}
---

简介  
很多博客上都有 vscode 配置的资料，但是总是不够全面，一些细节没有详细说明，让我这个小白很是头疼，摸索大半天才成功，这篇文章通过整合集装多篇资料加上我自己的经验，给大家一份博客上最最最最详细的 VS Code C 语言开发环境配置，可以根据需求点击目录跳转到文章相应位置，祝大家少走弯路，学业进步！  

### Z.1.1. 文章目录

*   [为什么 VS Code 比其他集成开发环境更加优秀](#VS_Code_3)
*   [如何配置 VS Code C 语言开发环境](#VS_Code_C_11)
*   *   [第一步 安装 VS code](#_VS_code_14)
    *   [第二步 安装编译器 MinGW-W64 GCC](#_MinGWW64_GCC_37)
    *   [第三步 配置环境变量](#__57)
    *   [第四步 配置三个文件 c_cpp_propertise.json、launch.json、tasks.json](#__c_cpp_propertisejsonlaunchjsontasksjson_86)
    *   [第五步 重启与调试](#__105)
*   [其他问题](#_118)
*   *   [终端中文乱码问题](#_119)
    *   [设置字体大小和样式](#_161)

# A. 为什么 VS Code 比其他集成开发环境更加优秀

通过对比 VC++6.0、Dev C++ 5.11 以及 VS Code，可以发现，前两者不需要额外配置插件，安装即可使用，但是在画面美观与功能全面性上 VC++6.0 和 Dev C++5.11 远远逊色于 VS Code, 它们仅能编写运行 C/C++，而 **VS Code 可以通过安装插件配置来实现多种编程语言的编译如 C/C++,JAVA,Python，且 VS Code 在编写代码时具有超强的可读性, 智能性, 观赏性, 用起来方便又好看**，以下附上用 VC++6.0 和 VS Code 编写简单代码的效果对比图，让读者更加直观的看到 VS Code 的强大之处  

![](https://img-blog.csdnimg.cn/ceab295cf1e04eb5b3647b8e32b97d4e.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/9b77fc5f587e4c5d908e01fe25172362.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70)

出现错误时

![](https://img-blog.csdnimg.cn/20201117144432601.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

# B. 如何配置 VS Code C 语言开发环境

以博主的亲身经历为根据，带你们轻松上手 VS Code，分五步走即可完成

## B.1. 第一步 安装 VS code

网址 https://code.visualstudio.com/  

![](https://img-blog.csdnimg.cn/20201117123608728.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

根据自己的操作系统下载相应的版本，点 Stable 那一栏下载

安装时  

![](https://img-blog.csdnimg.cn/202011171507477.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

打开 VS Code  
如果需要汉化，在安装插件栏搜索 chinese，找到简体中文版本，点击 install，安装结束后重启应用即可  

![](https://img-blog.csdnimg.cn/20201117130954802.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

  
_然后我们再来安装用于 C/C++ 的插件_  
1.Code Runner 记得勾选图中的两个选项

![](https://img-blog.csdnimg.cn/20201117131841628.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/20201117131841613.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

2.C/C++

![](https://img-blog.csdnimg.cn/2020111713204799.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

## B.2. 第二步 安装编译器 MinGW-W64 GCC

网址 https://sourceforge.net/projects/mingw-w64/files/  
百度网盘资源放在下面

![](https://img-blog.csdnimg.cn/20201117132323570.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

下载完成后把它解压至新建的文件夹（以后容易找），像我就是先在我的电脑的 D 盘上创建一个叫 VS Code 的文件夹，用 360 解压到里面去，这里提醒大家要一定要记得存放 MG 的地址  
，另外文件夹用英文命名，不要用中文，不要用中文，不要用中文！！！

== 因为有小伙伴用 7-zip 解压完成后按步骤在写入环境变量的环节却失败了，用 360 解压重新弄一遍才成功，我不知道别的解压器能不能完成，保险起见大家尽量用 360 吧，如果你的解压器成功了请发在评论区，让看文章的小伙伴也能知道，那么具体解压的步骤在下面图中 ==

![](https://img-blog.csdnimg.cn/20201119160936980.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/20201117133406737.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

  
下载的时候不知道为什么速度极慢，应读者要求，我把它压缩到百度网盘里了，链接：[https://pan.baidu.com/s/1N1i8dR6QC-KiBSXldv603w](https://pan.baidu.com/s/1N1i8dR6QC-KiBSXldv603w)  
提取码：1234

## B.3. 第三步 配置环境变量

打开 mingw64，点开 bin，将 bin 所在地址复制下来  

![](https://img-blog.csdnimg.cn/20201117135013753.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/20201117135119810.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

点击电脑属性，找到高级设置，依次点击环境变量，Path

![](https://img-blog.csdnimg.cn/20201117140214546.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

点击空白处，将复制好的地址粘贴进去，点击确定，这里算是上图的两个窗口，我们一共要点击三次确定!!!

![](https://img-blog.csdnimg.cn/20201117140301944.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

同样的步骤，在文件夹中找到 inlude，点开，复制地址，粘贴到 Path 中  

![](https://img-blog.csdnimg.cn/2020111714090421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

  

![](https://img-blog.csdnimg.cn/20201117140903909.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

完成后按下 win+r（win 在键盘上的图标是小旗帜），输入 cmd，点击确定  

![](https://img-blog.csdnimg.cn/20201117141228291.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

弹出黑框后输入 gcc -v -E -x c++ -  
若显示结果如图 则配置成功

![](https://img-blog.csdnimg.cn/20201117142113547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

一开始说的其他文章都没提及到的是 添加 include 的环境变量，在没有添加之前我运行之后出现错误，如图

![](https://img-blog.csdnimg.cn/20201118085850439.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

## B.4. 第四步 配置三个文件 c_cpp_propertise.json、launch.json、tasks.json

先在电脑上新建一个文件夹（像我就是在我的电脑上新建一个叫 C 的文件夹），打开它

![](https://img-blog.csdnimg.cn/20201120215303593.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/20201120215036706.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/2020112021505659.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

我们一共要新建三个文件，名字是 **c_cpp_propertise.json、 launch.json、 tasks.json**，如图

![](https://img-blog.csdnimg.cn/20201120215929702.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

解下来把相应内容写进去，因为三个文件的内容较多，请大家移步至这儿查看并完成相关操作  
[文件内容传送门](https://blog.csdn.net/incredibleimpact/article/details/109759947)

## B.5. 第五步 重启与调试

重启 vscode，在文件夹 C 上新建一个以. c 结尾的文件  
这里我们简单编写一个 C 语言的程序，设置断点并调试  

![](https://img-blog.csdnimg.cn/20201117145225806.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

![](https://img-blog.csdnimg.cn/20201117145332767.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70#pic_center)

  
说错的地方欢迎指正，若运行出错请将问题发至评论区，感谢观看！

最后，如果你已经安装好 VS Code 并开始使用了，这里有一份礼物分享给你，祝学习进步！  
[第一次使用 VS Code 时你应该知道的一切配置](https://zhuanlan.zhihu.com/p/62913725)

文章最后，想聊一下很多人跟博主说运行之后发现路径不存在的问题，原因大抵都是路径复制之后粘贴到对应位置后内容不一样了，请大家一定要确保你的路径是准确相同的，有时候粘贴过后内容会改变，可能凭空加了几个字，也可能反斜线变相反了 (/ -> \ )，大家切记注意细节多检查检查。  
----------------------------- 更新 ---------------------------------

# C. 其他问题

## C.1. 终端中文乱码问题

找到 setting.json 文件  
文件 -> 首选项 -> 设置, 输入 setting.josn, 在下图框中位置打开文件  

![](https://img-blog.csdnimg.cn/a836be774daf453a90ba411052fbc74b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70)

在 setting.json 文件中添加以下代码, 如图  

![](https://img-blog.csdnimg.cn/1897d0ec15794a62a620628c0c8ae018.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2luY3JlZGlibGVpbXBhY3Q=,size_16,color_FFFFFF,t_70)

```
{
    "terminal.integrated.profiles.windows": {
        "PowerShell": {
          "source": "PowerShell",
          "overrideName": true,
          "args": ["-NoExit", "/c", "chcp 65001"],
          "icon": "terminal-powershell",
          "env": {
            "TEST_VAR": "value"
          }
        }
      },
    "terminal.integrated.defaultProfile.windows": "PowerShell",
}


```

旧版的 vscode 可能会用以下两种方式, 虽然可以用, 但是 vscode 新版的好像不是很支持, 会给警告, 所以还是推荐用上面那种

```
{
     "terminal.integrated.shellArgs.windows": ["/K chcp 65001 >nul"],
 }

```

```
{
    "terminal.integrated.shellArgs.windows": ["-NoExit", "/c", "chcp 65001"],
}

```

也可以通过将 UTF-8 改为 GBK 格式, 但是只提供一次性的编译, 即你每一次都要通过修改这个编码格式才能解决运行时出现的中文乱码问题, 总之, 还是最上面的方法最好用  

![](https://img-blog.csdnimg.cn/523e144aaa7646d7b6d426ee24ae6fee.png)

## C.2. 设置字体大小和样式

在 setting.josn 文件中添加 `"editor.fontSize": 15,` 可以改变字体大小, 添加 `terminal.integrated.fontFamily:"Courier New",` 可以将字体修改为 “Courier New”.(记得不要漏了逗号)


