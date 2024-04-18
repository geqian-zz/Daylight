---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/yujia_666/article/details/116173652","title":"Win10 下将 CapsLock 键 (大小写锁定键) 转换映射成 Ctrl 键_大小写和 ctrl 互换_牛牛 Blog 的博客 - CSDN 博客","summary":null,"Created-Date":"2023-08-12 09:09:00","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/Win10 下将 CapsLock 键 (大小写锁定键) 转换映射成 Ctrl 键_大小写和 ctrl 互换_牛牛 Blog 的博客 - CSDN 博客/","dgPassFrontmatter":true}
---


之前用过 Edit plus、NotePad++、[Sublime](https://so.csdn.net/so/search?q=Sublime&spm=1001.2101.3001.7020) Atom (MyEclipse、 IntelliJ IDEA 不在属于集成开发环境，不在此列)，在 Vim 之前一直以为 Atom 是最好用的，直到学了 Vim 才发现之前自己用的编辑器都是屎！  
不管您是不是职业码农，都强烈推荐您学学 (将我孩子一定要从娘胎里开始教他用，哈哈)  
扯远了，Vim 经常要用到 Ctrl 键，而 CapsLock(大小写锁定键) 基本上不用，着实浪费下面介绍怎样把 CapsLock(大小写锁定键) 映射为 Ctrl 键:

* 第一步：将下面的内容复制到一个文件里


```
Windows Registry Editor Version 5.00
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout]
"Scancode Map"=hex:00,00,00,00,00,00,00,00,02,00,00,00,1d,00,3a,00,00,00,00,00 
```

![](https://img-blog.csdnimg.cn/img_convert/abbe3ad07c07510d887abc2ec4161f78.png)

大小写锁定键映射左 Ctrl 键. jpg

* 第二步：文件可以任意命名，但是后缀一定得是. reg, 然后系统会问你是否要改变文件的后缀，确定要改。然后文件的图标就会变成注册表的图标，例如：aaa.reg
    
    ![](https://img-blog.csdnimg.cn/img_convert/f7cc041e4965485780aa30191abf62c8.png)
    
    reg.jpg
    
* 第三步：双击执行，这时候会问你是否确定要执行这个文件，点击确定
    
* 第四步：查看注册表编辑器是否修改成功  
    1.Windows 键 + R 打开运行对话框  
    2. 对话框中输入 regedit
    
    ![](https://img-blog.csdnimg.cn/img_convert/3b73b9c55803d4273e2efa212b5a80c4.png)
    
    run.jpg
    
     
    
    3. 依次打开：
    

![](https://img-blog.csdnimg.cn/img_convert/fee5d25d2079cd28c68d0c77e27ef4db.png)

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout


```

大小写锁定键映射左 Ctrl 键注册表. jpg

* 第五步：重启电脑  
    大功告成