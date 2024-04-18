---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://www.cnblogs.com/thinkgone/p/16348956.html","title":"VsCode-C/C++ 编译环境配置","summary":null,"Created-Date":"2023-09-23 17:07:35","Modified-Date":"2024-04-18 11:52:10","permalink":"/Z01_InBox/SimpRead/VsCode-C_C++ 编译环境配置/","dgPassFrontmatter":true}
---

## 前期准备

### 下载 VsCode

官网地址：[Code Editing](https://code.visualstudio.com/)

### 下载 MinGW64 编译器

官网地址：[MinGW64](https://www.mingw-w64.org/)

## 配置系统环境变量

Win+I 打开系统设置  
找到 **编辑系统环境变量**  
点击 **高级** > **环境变量** > **选定 Path 进行编辑**  
添加进你安装的 MinGW64 编译器的 **路径**  
例如我的就是：D:\Program\mingw-w64\mingw64\bin  
[](https://s2.loli.net/2022/05/01/SZj5xDITXehoyW9.png)

[![](https://s2.loli.net/2022/05/01/SZj5xDITXehoyW9.png)](https://s2.loli.net/2022/05/01/SZj5xDITXehoyW9.png)

## 配置相关文件

### 安装 C/C++ 扩展

进入 VsCode 找到左侧栏的 Extensions  
一般安装如下扩展：

*   C/C++
*   Chinese (Simplified)(简体中文)
*   Code Runner

### 设置编译器路径

新建 Code 文件夹用来保存项目文件  
在 Code 文件夹中右键点击 **用 Code 打开** 进入 VsCode  
接下来配置编译器路径  
按快捷键 Ctrl+Shift+P 调出命令面板，输入 C/C++，选 **Edit Configurations(UI)** 进入配置  
[](https://s2.loli.net/2022/05/01/RWZGvOlSV8dxzLK.png)

[![](https://s2.loli.net/2022/05/01/RWZGvOlSV8dxzLK.png)](https://s2.loli.net/2022/05/01/RWZGvOlSV8dxzLK.png)

  
在里面找到 **编译器路径** 修改成 MinGW64 路径，再将下方的 InteliSense 模式 改为 **gcc-x64** 即可  
这时我们可以发现文件夹中多了一个 **.vscode** 的文件夹，证明配置成功  
接下来配置三个主要的文件

### c_cpp_properties.json

```
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "compilerPath": "D:/Program/mingw-w64/mingw64/bin/g++.exe",//编译器的路径
            "cStandard": "c17",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-x64"
        }
    ],
    "version": 4
}


``` 

### tasks.json

接下来，创建一个 tasks.json 文件来告诉 VS Code 如何构建（编译）程序  
该任务将调用 g++ 编译器基于源代码创建可执行文件  
按快捷键 Ctrl+Shift+P 调出命令面板，输入 tasks，选择 **Tasks:Configure Default Build Task**  
[](https://s2.loli.net/2022/05/01/OHUebX3C1SPmzKG.png)

[![](https://s2.loli.net/2022/05/01/OHUebX3C1SPmzKG.png)](https://s2.loli.net/2022/05/01/OHUebX3C1SPmzKG.png)

  
再选择 **C/C++: g++.exe build active file**  
[

![](https://s2.loli.net/2022/05/01/Hv5Jqiwl6Yhu1QI.png)

](https://s2.loli.net/2022/05/01/Hv5Jqiwl6Yhu1QI.png)  
接下来在 .vscode 文件夹中就会出现 **tasks.json** 的配置文件  
可以参考我的配置：

```
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cppbuild",
			"label": "g++.exe build active file",
			"command": "D:/Program/mingw-w64/mingw64/bin/g++.exe",//编译器路径
			"args": [
				"-fdiagnostics-color=always",
				"-g",
				"${file}",
				"-o",
				"${fileDirname}\\${fileBasenameNoExtension}.exe"
			],
			"options": {
				"cwd": "D:/Program/mingw-w64/mingw64/bin"
			},//bin为存放编译器和调试器的文件夹
			"problemMatcher": [
				"$gcc"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"detail": "编译器: D:/Program/mingw-w64/mingw64/bin/g++.exe"
		}
	]
}


``` 

### launch.json

点击菜单栏的 **Debug-->Start Debugging** 或者直接按键盘 **F5**  
会在 .vscode 文件夹中生成一个 **launch.json** 的配置文件  
我的配置如下：

```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [

        {
            "name": "(gdb) Launch",
            "preLaunchTask": "g++.exe build active file",//调试前执行的任务，就是之前配置的tasks.json中的label字段
            "type": "cppdbg",//配置类型，只能为cppdbg
            "request": "launch",//请求配置类型，可以为launch（启动）或attach（附加）
            "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",//调试程序的路径名称
            "args": [],//调试传递参数
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": true,//true显示外置的控制台窗口，false显示内置终端
            "MIMode": "gdb", 
            "miDebuggerPath": "D:\\Program\\mingw-w64\\mingw64\\bin\\gdb.exe",//调试器路径
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}


``` 

## 运行测试

写一个 hello world! 的程序测试下环境配置是否成功  
记得要在末尾插入 **system("pause")** 的代码，不然程序会闪一下就消失了  
出现如图所示结果则成功：  
[](https://s2.loli.net/2022/05/01/rcnTyzsLo21SNRY.png)

[![](https://s2.loli.net/2022/05/01/rcnTyzsLo21SNRY.png)](https://s2.loli.net/2022/05/01/rcnTyzsLo21SNRY.png)

*   [前期准备](#前期准备)
*    [下载 VsCode](#下载-vscode)
*    [下载 MinGW64 编译器](#下载-mingw64编译器)
*   [配置系统环境变量](#配置系统环境变量)
*   [配置相关文件](#配置相关文件)
*    [安装 C/C++ 扩展](#安装-cc-扩展)
*    [设置编译器路径](#设置编译器路径)
*    [c_cpp_properties.json](#c_cpp_propertiesjson)
*    [tasks.json](#tasksjson)
*    [launch.json](#launchjson)
*   [运行测试](#运行测试)

  

__EOF__

[

![](https://cdn.luogu.com.cn/upload/usericon/392796.png)

](https://cdn.luogu.com.cn/upload/usericon/392796.png)

*   **本文作者：** [ThinkGone](https://www.cnblogs.com/thinkgone)
*   **本文链接：** [https://www.cnblogs.com/thinkgone/p/16348956.html](https://www.cnblogs.com/thinkgone/p/16348956.html)
*   **关于博主：** 评论和私信会在第一时间回复。或者 [直接私信](https://msg.cnblogs.com/msg/send/thinkgone) 我。
*   **版权声明：** 本博客所有文章除特别声明外，均采用 [BY-NC-SA](https://creativecommons.org/licenses/by-nc-nd/4.0/ "BY-NC-SA") 许可协议。转载请注明出处！
*   **声援博主：** 如果您觉得文章对您有帮助，可以点击文章右下角**【[推荐](javascript:void(0);)】**一下。