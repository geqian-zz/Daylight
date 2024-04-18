---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":null,"title":"VIM 常用快捷键","summary":null,"Created-Date":"2023-09-20 20:22:25","Modified-Date":"2024-04-18 11:52:12","permalink":"/Z01_InBox/SimpRead/VIM 常用快捷键_博客园/","dgPassFrontmatter":true}
---

# A. 一、移动光标

h,j,k,l 上，下，左，右  
ctrl-e 移动页面  

w 跳到下一个字首，按标点或单词分割  
W 跳到下一个字首，长跳，如 end-of-line 被认为是一个字  
e 跳到下一个字尾  
E 跳到下一个字尾，长跳  
b 跳到上一个字  
B 跳到上一个字，长跳  
0 跳至行首，不管有无缩进，就是跳到第 0 个字符  
^ 跳至行首的第一个字符  
$ 跳至行尾  
gg 跳至文首  
G 调至文尾  
5gg/5G 调至第 5 行  
gd 跳至当前光标所在的变量的声明处  
fx 在当前行中找 x 字符，找到了就跳转至  
; 重复上一个 f 命令，而不用重复的输入 fx  
* 查找光标所在处的单词，向下查找  
# B. 查找光标所在处的单词，向上查找

# C. 二、删除复制

dd 删除光标所在行  
dw 删除一个字 (word)  
d 删除到行末删除当前字符删除前一个字符复制一行复制一个字删除到行末删除当前字符删除前一个字符复制一行复制一个字/Y 复制到行末  
p 粘贴粘贴板的内容到当前行的下面  
P 粘贴粘贴板的内容到当前行的上面

# D. 三、插入模式

i 从当前光标处进入插入模式  
I 进入插入模式，并置光标于行首  
a 追加模式，置光标于当前光标之后  
A 追加模式，置光标于行末  
o 在当前行之下新加一行，并进入插入模式  
O 在当前行之上新加一行，并进入插入模式  
Esc 退出插入模式

# E. 四、编辑

J 将下一行和当前行连接为一行  
cc 删除当前行并进入编辑模式  
c$ 擦除从当前位置至行末的内容，并进入编辑模式  
s 删除当前字符并进入编辑模式 
S 删除光标所在行并进入编辑模式  
xp 交换当前字符和下一个字符  
u 撤销  
ctrl+r 重做  
~ 切换大小写，当前字符  
>> 将当前行右移一个单位  
<<将当前行左移一个单位 (一个 tab 符)  
== 自动缩进当前行

# F. 五、查找替换

/pattern 向后搜索字符串 pattern  
?pattern 向前搜索字符串 pattern  
"\c" 忽略大小写  
"\C" 大小写敏感

n 下一个匹配 (如果是 / 搜索，则是向下的下一个，? 搜索则是向上的下一个)  
N 上一个匹配 (同上)  
:%s/old/new/g 搜索整个文件，将所有的 old 替换为 new  
:%s/old/new/gc 搜索整个文件，将所有的 old 替换为 new，每次都要你确认是否替换

# G. 六、退出编辑器

:w 将缓冲区写入文件，即保存修改  
:wq 保存修改并退出  
:x 保存修改并退出  
:q 退出，如果对缓冲区进行过修改，则会提示  
:q! 强制退出，放弃修改

# H. 七、多文件编辑

vim file1.. 同时打开多个文件  
:args 显示当前编辑文件  
:next 切换到下个文件  
:prev 切换到前个文件  
:next！ 不保存当前编辑文件并切换到下个文件  
:prev！ 不保存当前编辑文件并切换到上个文件  
:wnext 保存当前编辑文件并切换到下个文件  
:wprev 保存当前编辑文件并切换到上个文件  
:first 定位首文件  
:last 定位尾文件  
ctrl+^ 快速在最近打开的两个文件间切换  
:split[sp] 把当前文件水平分割  
:split file 把当前窗口水平分割, file  
:vsplit[vsp] file 把当前窗口垂直分割, file  
:new file 同 split file  
:close 关闭当前窗口  
:only 只显示当前窗口, 关闭所有其他的窗口  
:all 打开所有的窗口  
:vertical all 打开所有的窗口, 垂直打开  
:qall 对所有窗口执行：q 操作  
:qall! 对所有窗口执行：q! 操作  
:wall 对所有窗口执行：w 操作  
:wqall 对所有窗口执行：wq 操作  
ctrl-w h 跳转到左边的窗口  
ctrl-w j 跳转到下面的窗口  
ctrl-w k 跳转到上面的窗口  
ctrl-w l 跳转到右边的窗口  
ctrl-w t 跳转到最顶上的窗口  
ctrl-w b 跳转到最底下的窗口

# I. 八、多标签编辑

:tabedit file 在新标签中打开文件 file  
:tab split file 在新标签中打开文件 file  
:tabp 切换到前一个标签  
:tabn 切换到后一个标签  
:tabc 关闭当前标签  
:tabo 关闭其他标签  
gt 到下一个 tab  
gT 到上一个 tab  
0gt 跳到第一个 tab  
5gt 跳到第五个 tab

# J. 九、执行 shell 命令

1、在命令模式下输入 ":sh"，可以运行相当于在字符模式下，到输入结束想回到 VIM 编辑器中用 exit，ctrl+D 返回 VIM 编辑器  
2、可以 "!command"，运行结束后自动回到 VIM 编辑器中  
3、用 “Ctrl+Z“回到 shell，用 fg 返回编辑  
4、:!make -> 直接在当前目录下运行 make 指令

# K. 十、VIM 启动项

-o[n] 以水平分屏的方式打开多个文件  
-O[n] 以垂直分屏的方式打开多个文件

# L. 十一、自动排版

在粘贴了一些代码之后，vim 变得比较乱，只要执行 gg=G 就能搞定

# M. 十二、如何在 vim 中编译程序

在 vim 中可以完成 make, 而且可以将编译的结果也显示在 vim 里，先执行 :copen 命令，将结果输出的窗口打开，然后执行 :make  
编译后的结果就显示在了 copen 打开的小窗口里了，而且用鼠标双击错误信息，就会跳转到发生错误的行。

# N. 十三、buffer 操作

1、buffer 状态  
- （非活动的缓冲区）  
a （当前被激活缓冲区）  
h （隐藏的缓冲区）  
% （当前的缓冲区）  
# O. （交换缓冲区）  
= （只读缓冲区）  
+ （已经更改的缓冲区）

# P. 十四、 VIM 操作目录

1. 打开目录  
vim .  
vim a-path/

2. 以下操作在操作目录时生效  
p,P,t,u,U,x,v,o,r,s

c 使当前打开的目录成为当前目录  
d 创建目录  
% 创建文件  
D 删除文件 / 目录  
- 转到上层目录  
gb 转到上一个 bookmarked directory  
i 改变目录文件列表方式  
^l 刷新当前打开的目录

mf - 标记文件  
mu - unmark all marked files  
mz - Compress/decompress marked files  
gh 显示 / 不显示隐藏文件 (dot-files)  
^h 编辑隐藏文件列表  
a 转换显示模式, all - hide - unhide  
qf diplay infomation about file  
qb list the bookmarked directories and directory traversal history  
gi Display information on file

mb  
mc  
md - 将标记的文件 (mf 标记文件) 使用 diff 模式  
me - 编辑标记的文件, 只显示一个，其余放入 buffer 中  
mh  
mm - move marked files to marked-file target directory  
mc - copy  
mp  
mr  
mt

vim 中复制, 移动文件  
1, mt - 移动到的目录  
2, mf - 标记要移动的文件  
3, mc - 移动 / 复制

R 移动文件

打开当前编辑文件的目录  
:Explore  
:Hexplore  
:Nexplore  
:Pexplore  
:Sexplore  
:Texplore  
:Vexplore