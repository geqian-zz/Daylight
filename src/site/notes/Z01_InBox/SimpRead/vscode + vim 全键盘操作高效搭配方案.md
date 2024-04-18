---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://zhuanlan.zhihu.com/p/430603620","title":"vscode + vim 全键盘操作高效搭配方案","summary":null,"Created-Date":"2023-09-24 09:45:13","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/vscode + vim 全键盘操作高效搭配方案/","dgPassFrontmatter":true}
---

## Z.1. 更新内容

2021-11-28 以更新 windows 快捷键，见文章末尾

## Z.2. 基础知识

## Z.3. **vscode-vim**

vscode-vim 是一款 vim 模拟器，它将 vim 的大部分功能都集成在了 vscode 中，你可以将它理解为一个嵌套在 vscode 中的 vim。

由于该 vim 是被模拟的的非真实 vim，所以原生 vim 中有些功能它并不支持，如宏录制功能，但这依然不妨碍 vscode-vim 插件的优秀。

![](https://pic1.zhimg.com/v2-95d7211a74a10d458af487dbeadbb9b0_b.jpg)

其实在 vscode 的扩展商店中，还有一个 vscode neovim 的插件也十分不错，但是相较于 vscode-vim 来说依然存在一些让我难以接受的缺点，比如 visual 模式下的选择并非真正的 vscode 选择等，基于种种原因我还是考虑使用 vscode-vim，尽管它可能占用了更大的内存。

## Z.4. **安装使用**

我们需要在插件商店中搜索 vim 插件，然后安装：

![](https://pic2.zhimg.com/v2-861fea0b09d22d0f9f2361a2d24c5945_b.jpg)

安装完成之后，需要做一些基础配置。

1）仅 MAC 用户，关闭 MAC 的重复键：

```
 $ defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false  

```

2）设置相对行号，在 settings.json 中添加上以下配置项：

```
 "editor.lineNumbers": "relative",

```

3）关闭自动传参建议和代码补全建议，使用按键手动触发（可选）：

```
 "editor.parameterHints.enabled": false,
 "editor.quickSuggestions": false,

```

4）控制资源管理器中的键盘导航无法自动触发：

```
 "workbench.list.automaticKeyboardNavigation": false,

```

## Z.5. 配置文件

## Z.6. **基础配置项**

vscode-vim 插件由于是一款模拟器，所以它的配置文件是放在 settings.json 文件中，而不是 vimrc 文件中，个人也并不推荐将配置放在 vimrc 文件中，因为这会导致多端同步变的复杂，尽管这款插件可以支持从 vimrc 文件中读取配置。

下面是一些我会在使用 vscode-vim 插件时配置的 vim 选项，直接放入到 settings.json 文件中即可：

```
 {
   // 绑定vim前导键
   "vim.leader": "<space>",
   // 启用easymotion插件
   "vim.easymotion": true,
   // 启用系统粘贴板作为vim寄存器
   "vim.useSystemClipboard": true,
   // 由vim接管ctrl+any的按键，而不是vscode
   "vim.useCtrlKeys": true,
   // 突出显示与当前搜索匹配的所有文本
   "vim.hlsearch": true,
    // 普通模式下的非递归按键绑定
   "vim.normalModeKeyBindingsNonRecursive": [],
    // 插入模式下的非递归按键绑定
   "vim.insertModeKeyBindings": [],
   // 命令模式下的非递归按键绑定
   "vim.commandLineModeKeyBindingsNonRecursive": [],
   // 可视模式下的非递归按键绑定
   "vim.operatorPendingModeKeyBindings": [],
   // 下面定义的按键将交由vscode进行处理，而不是vscode-vim插件
   "vim.handleKeys": {
     "<C-a>": false,
     "<C-f>": false
   }
 }

```

## Z.7. **热键配置项**

基本上 vim 的所有模式你都可以配置在下面的 4 个选项中：

```
 // 普通模式下的非递归按键绑定
 "vim.normalModeKeyBindingsNonRecursive": [],
 // 插入模式下的非递归按键绑定
 "vim.insertModeKeyBindings": [],
 // 命令模式下的非递归按键绑定
 "vim.commandLineModeKeyBindingsNonRecursive": [],
 // 可视模式下的非递归按键绑定
 "vim.operatorPendingModeKeyBindings": [],
 // 下面定义的按键将交由vscode进行处理，而不是vscode-vim插件
 "vim.handleKeys": {
     "<C-a>": false,
     "<C-f>": false
 }

```

一个简单的例子，在 INSERT 模式下使用 jj 退回到 NORMAL 模式：

```
   "vim.insertModeKeyBindings": [
     {
       "before": [
         "j",
         "j"
       ],
       "after": [
         "<Esc>"
       ]
     },
   ],

```

下面的示例将演示如何在 NORMAL 模式下按下快捷键执行 COMMAND 的命令，如按下 <C-n> 后，取消高亮搜索：

```
   "vim.normalModeKeyBindingsNonRecursive": [
     {
       "before": [
         "<C-n>"
       ],
       "commands": [
         ":nohl"
       ]
     },
   ],

```

除此之外，你也可以定义在按下一些按键后，调用 vscode 下的命令 API，比如在 NORMAL 模式下按下 <leader>gc 后，调用 vscode 的全局命令：

```
   "vim.normalModeKeyBindingsNonRecursive": [
     {
       "before": [
         "<leader>",
         "g",
         "c"
       ],
       "commands": [
         "workbench.action.showCommands"
       ]
     }
   ],

```

注意！leader 键只在代码编辑区域生效，它无法做到全 vscode 生效。

针对一些刚接触 vscode 不久的朋友，可能不知道怎么拿到 vscode 的热键映射命令，其实你可以从 vsocde 的键盘快捷键中复制命令 ID 获得。

![](https://pic2.zhimg.com/v2-77f7e16b5c20f79d8972a84df73792c1_r.jpg)

## Z.8. **自用热键方案**

下面是个人自用的 vim+vscode 全键盘热键方案，对于非代码编辑区的热键将其定义在 keybindings.json 中，对于代码编辑区且属于 vim 的热键将其定义在 settings.json 文件中。

我目前使用的是 mac 平台，所以 cmd 按键会比 ctrl 按键更加常用，如果是 windows 或者 linux 平台，则将 cmd 替换为 ctrl 按键即可：

```
 cmd + g c ： 显示命令面板
 cmd + g s ： 打开设置页面
 cmd + g k ： 打开热键映射
 cmd + g m ： 打开一个目录
 cmd + g f ： 打开一个文件
 cmd + g h ： 打开最近记录
 cmd + g n ： 新建vscode实例
 cmd + g q ： 关闭vscode示例
 ​
 cmd + f n ： 新建文件
 cmd + f o ： 打开文件
 cmd + f e ： 另存为文件
 cmd + f s ： 保存文件
 cmd + f w ： 保存所有文件
 cmd + f q ： 关闭文件
 cmd + f a ： 关闭所有文件
 ​
 cmd + n [ ： 切换侧边栏显示状态
 cmd + n 1 ： 显示文件资源管理器
 cmd + n 2 ： 显示TODO Tree
 cmd + n 3 ： 显示全局搜索
 cmd + n 4 ： 显示debug
 cmd + n 5 ： 显示版本控制
 cmd + n 6 ： 显示SQL Tools
 cmd + n 7 ： 显示Docker
 cmd + n 8 ： 显示测试
 cmd + n 9 ： 显示插件商店
 ​
 cmd + p ] ： 切换面板显示状态
 cmd + p 1 ： 显示问题
 cmd + p 2 ： 显示输出
 cmd + p 3 ： 显示终端
 cmd + p 4 ： 显示调试控制台
 cmd + p 5 ： 显示SQL CONSOLE

```

以下是编辑区域操作控制方案：

```
 cmd + q ：关闭当前选项卡或分屏
 cmd + e ：聚焦在第一个选项卡中
 cmd + , ：切换到上一个选项卡
 cmd + . ：切换到下一个选项卡
 ​
 cmd + w s ：拆分一个上下分屏
 cmd + w v ：拆分一个左右分屏
 ​
 cmd + w k ：将光标向上移动1屏
 cmd + w j ：将光标向下移动1屏
 ​
 cmd + w h ：将光标向左移动1屏
 cmd + w l ：将光标向右移动1屏

```

代码控制区域：

```
 cmd + h ： 触发帮助提示
 cmd + j ： 触发参数提示
 cmd + k ： 触发建议提示
 cmd + n ： 移动到下一个建议
 cmd + p ： 移动到上一个建议
 tab ： 选择下一个建议
 enter ： 选择当前建议
 ​
 cmd + alt + l ： 格式化代码（个人习惯）
 ​
 cmd + = ： 放大字体
 cmd + - ： 缩小字体

```

在 settings.json 中配置的代码控制区域热键方案：

```
 jj ： 退出INSERT模式
 zz ： 切换代码折叠（原生vim的zz不是切换折叠）
 ​
 H ：跳转行首、取代^
 L ：跳转行尾、取代$
 ​
 g[ ： 跳转到上一个问题
 g] ： 跳转到下一个问题

```

## Z.9. **我的配置文件**

以下是 settings.json 文件中关于代码编辑区的一些操作配置项：

```
   "vim.normalModeKeyBindingsNonRecursive": [
     {
       "before": [
         "H"
       ],
       "after": [
         "^"
       ]
     },
     {
       "before": [
         "L"
       ],
       "after": [
         "$"
       ]
     },
     {
       "before": [
         "z",
         "z",
       ],
       "commands": [
         "editor.toggleFold"
       ]
     },
     {
       "before": [
         "g",
         "[",
       ],
       "commands": [
         "editor.action.marker.prevInFiles"
       ]
     },
     {
       "before": [
         "g",
         "]",
       ],
       "commands": [
         "editor.action.marker.nextInFiles"
       ]
     },
   ],
   // 插入模式下的非递归按键绑定
   "vim.insertModeKeyBindings": [
     {
       "before": [
         "j",
         "j"
       ],
       "after": [
         "<Esc>"
       ]
     },
   ],
   // 命令模式下的非递归按键绑定
   "vim.commandLineModeKeyBindingsNonRecursive": [],
   // 可视模式下的非递归按键绑定
   "vim.operatorPendingModeKeyBindings": [],

```

以下是 keybindings.json 文件，基本的键位设置就如同上面看到的一样，但是做了一些额外的限制条件，比如 <C-a> 和 < C-c > 以及 < C-v > 等 vscode 原生命令在代码编辑区域中非 NORMAL 模式下是不生效的：

```
 [
     // --- 全局命令
     // 显示命令面板
     {
         "key": "cmd+g c",
         "command": "workbench.action.showCommands"
     },
     // 打开设置页面
     {
         "key": "cmd+g s",
         "command": "workbench.action.openSettings"
     },
     // 打开热键映射
     {
         "key": "cmd+g k",
         "command": "workbench.action.openGlobalKeybindings"
     },
     // 打开一个目录
     {
         "key": "cmd+g m",
         "command": "workbench.action.files.openFolder"
     },
     // 打开一个文件
     {
         "key": "cmd+g f",
         "command": "workbench.action.files.openFile"
     },
     // 打开最近记录
     {
         "key": "cmd+g h",
         "command": "workbench.action.openRecent"
     },
     // 新建vscode实例
     {
         "key": "cmd+g n",
         "command": "workbench.action.newWindow"
     },
     // 关闭vscode实例
     {
         "key": "cmd+g q",
         "command": "workbench.action.closeWindow"
     },
     // --- 文件命令
     // 新建文件
     {
         "key": "cmd+f n",
         "command": "welcome.showNewFileEntries",
     },
     // 打开文件
     {
         "key": "cmd+f o",
         "command": "workbench.action.files.openFileFolder"
     },
     // 另存为文件
     {
         "key": "cmd+f e",
         "command": "workbench.action.files.saveAs"
     },
     // 保存文件
     {
         "key": "cmd+f s",
         "command": "workbench.action.files.save"
     },
     // 保存所有文件
     {
         "key": "cmd+f w",
         "command": "workbench.action.files.saveAll"
     },
     // 关闭文件
     {
         "key": "cmd+f q",
         "command": "workbench.action.closeActiveEditor"
     },
     // 关闭所有文件
     {
         "key": "cmd+f a",
         "command": "workbench.action.closeAllEditors"
     },
     // -- 侧边栏命令
     // 切换侧边栏显示状态
     {
         "key": "cmd+n [",
         "command": "workbench.action.toggleSidebarVisibility"
     },
     // 显示文件资源管理器
     {
         "key": "cmd+n 1",
         "command": "workbench.files.action.focusFilesExplorer"
     },
     // 显示TODO Tree
     {
         "key": "cmd+n 2",
         "command": "todo-tree-view.focus"
     },
     // 显示全局搜索
     {
         "key": "cmd+n 3",
         "command": "workbench.action.replaceInFiles",
     },
     // 显示debug
     {
         "key": "cmd+n 4",
         "command": "workbench.view.debug",
         "when": "viewContainer.workbench.view.debug.enabled"
     },
     // 显示版本控制
     {
         "key": "cmd+n 5",
         "command": "workbench.view.scm",
         "when": "workbench.scm.active"
     },
     // 显示SQL Tools
     {
         "key": "cmd+n 6",
         "command": "workbench.view.extension.sqltoolsActivityBarContainer"
     },
     // 显示Docker
     {
         "key": "cmd+n 7",
         "command": "workbench.view.extension.dockerView"
     },
     // 显示测试
     {
         "key": "cmd+n 8",
         "command": "workbench.view.testing.focus"
     },
     // 显示插件商店
     {
         "key": "cmd+n 9",
         "command": "workbench.view.extensions",
         "when": "viewContainer.workbench.view.extensions.enabled"
     },
     // --- 面板命令
     // 切换面板显示状态
     {
         "key": "cmd+p [",
         "command": "workbench.action.togglePanel"
     },
     // 显示问题
     {
         "key": "cmd+p 1",
         "command": "workbench.panel.markers.view.focus"
     },
     // 显示输出
     {
         "key": "cmd+p 2",
         "command": "workbench.action.output.toggleOutput",
         "when": "workbench.panel.output.active"
     },
     // 显示终端
     {
         "key": "cmd+p 3",
         "command": "workbench.action.terminal.toggleTerminal",
         "when": "terminal.active"
     },
     // 显示调试控制台
     {
         "key": "cmd+p 4",
         "command": "workbench.debug.action.toggleRepl",
         "when": "workbench.panel.repl.view.active"
     },
     // 显示SQL CONSOLE
     {
         "key": "cmd+p 5",
         "command": "workbench.view.extension.sqltoolsPanelContainer"
     },
     // --- 编辑区命令
     // 关闭当前选项卡或分屏
     {
         "key": "cmd+q",
         "command": "workbench.action.closeActiveEditor"
     },
     // 聚集在第一个选项卡中
     {
         "key": "cmd+e",
         "command": "workbench.action.focusFirstEditorGroup"
     },
     // 切换到上一个选项卡
     {
         "key": "cmd+,",
         "command": "workbench.action.previousEditor"
     },
     // 切换到下一个选项卡
     {
         "key": "cmd+.",
         "command": "workbench.action.nextEditor"
     },
     // 拆分一个上下分屏
     {
         "key": "cmd+w s",
         "command": "workbench.action.splitEditorDown"
     },
     // 拆分一个左右分屏
     {
         "key": "cmd+w v",
         "command": "workbench.action.splitEditor"
     },
     // 将光标向上动1屏
     {
         "key": "cmd+w k",
         "command": "workbench.action.focusAboveGroup"
     },
     // 将光标向下动1屏
     {
         "key": "cmd+w j",
         "command": "workbench.action.focusBelowGroup"
     },
     // 将光标向左移动1屏
     {
         "key": "cmd+w h",
         "command": "workbench.action.focusLeftGroup"
     },
     // 将光标向右移动1屏
     {
         "key": "cmd+w l",
         "command": "workbench.action.focusRightGroup"
     },
     // --- 代码编辑命令
     // 触发帮助提示
     {
         "key": "cmd+h",
         "command": "editor.action.showHover",
         "when": "editorTextFocus"
     },
     // 触发参数提示
     {
         "key": "cmd+j",
         "command": "editor.action.triggerParameterHints",
         "when": "editorHasSignatureHelpProvider && editorTextFocus"
     },
     {
         "key": "cmd+j",
         "command": "closeParameterHints",
         "when": "editorFocus && parameterHintsVisible"
     },
     // 触发建议提示
     {
         "key": "cmd+k",
         "command": "editor.action.triggerSuggest",
         "when": "editorHasCompletionItemProvider && textInputFocus && !editorReadonly"
     },
     {
         "key": "cmd+k",
         "command": "hideSuggestWidget",
         "when": "suggestWidgetVisible && textInputFocus"
     },
     // 移动到下一个建议
     {
         "key": "cmd+n",
         "command": "selectNextSuggestion",
         "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
     },
     // 移动到上一个建议
     {
         "key": "cmd+p",
         "command": "selectPrevSuggestion",
         "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
     },
     // 格式化代码
     {
         "key": "cmd+alt+l",
         "command": "editor.action.formatDocument",
         "when": "editorHasDocumentFormattingProvider && editorTextFocus && !editorReadonly && !inCompositeEditor"
     },
     // 放大字体
     {
         "key": "cmd+=",
         "command": "editor.action.fontZoomIn"
     },
     // 缩小字体
     {
         "key": "cmd+-",
         "command": "editor.action.fontZoomOut"
     },
     // --- window 用户删除以下重映射，这里是为MAC用户准备的
     {
         "key": "cmd+r",
         "command": "extension.vim_ctrl+r",
         "when": "editorTextFocus && vim.active && vim.use<C-r> && !inDebugRepl"
     },
     {
         "key": "ctrl+r",
         "command": "-extension.vim_ctrl+r",
         "when": "editorTextFocus && vim.active && vim.use<C-r> && !inDebugRepl"
     },
     {
         "key": "cmd+a",
         "command": "extension.vim_ctrl+a",
     },
     {
         "key": "ctrl+a",
         "command": "-extension.vim_ctrl+a",
         "when": "editorTextFocus && vim.active && vim.use<C-a> && !inDebugRepl"
     },
     {
         "key": "cmd+x",
         "command": "extension.vim_ctrl+x",
     },
     {
         "key": "ctrl+x",
         "command": "-extension.vim_ctrl+x",
         "when": "editorTextFocus && vim.active && vim.use<C-x> && !inDebugRepl"
     },
     {
         "key": "cmd+u",
         "command": "extension.vim_ctrl+u",
         "when": "editorTextFocus && vim.active && vim.use<C-u> && !inDebugRepl"
     },
     {
         "key": "ctrl+u",
         "command": "-extension.vim_ctrl+u",
         "when": "editorTextFocus && vim.active && vim.use<C-u> && !inDebugRepl"
     },
     {
         "key": "cmd+d",
         "command": "extension.vim_ctrl+d",
         "when": "editorTextFocus && vim.active && vim.use<C-d> && !inDebugRepl"
     },
     {
         "key": "ctrl+d",
         "command": "-extension.vim_ctrl+d",
         "when": "editorTextFocus && vim.active && vim.use<C-d> && !inDebugRepl"
     },
     {
         "key": "cmd+i",
         "command": "extension.vim_ctrl+i",
         "when": "editorTextFocus && vim.active && vim.use<C-i> && !inDebugRepl"
     },
     {
         "key": "ctrl+i",
         "command": "-extension.vim_ctrl+i",
         "when": "editorTextFocus && vim.active && vim.use<C-i> && !inDebugRepl"
     },
     {
         "key": "cmd+o",
         "command": "extension.vim_ctrl+o",
         "when": "editorTextFocus && vim.active && vim.use<C-o> && !inDebugRepl"
     },
     {
         "key": "ctrl+o",
         "command": "-extension.vim_ctrl+o",
         "when": "editorTextFocus && vim.active && vim.use<C-o> && !inDebugRepl"
     },
     // --- 取消一些vim插件的额外功能
     {
         "key": "cmd+a",
         "command": "-extension.vim_cmd+a",
         "when": "editorTextFocus && vim.active && vim.use<D-a> && !inDebugRepl && vim.mode != 'Insert'"
     },
     {
         "key": "alt+cmd+down",
         "command": "-extension.vim_cmd+alt+down",
         "when": "editorTextFocus && vim.active && !inDebugRepl"
     },
     {
         "key": "alt+cmd+up",
         "command": "-extension.vim_cmd+alt+up",
         "when": "editorTextFocus && vim.active && !inDebugRepl"
     },
     {
         "key": "cmd+c",
         "command": "-extension.vim_cmd+c",
         "when": "editorTextFocus && vim.active && vim.overrideCopy && vim.use<D-c> && !inDebugRepl"
     },
     {
         "key": "cmd+v",
         "command": "-extension.vim_cmd+v",
         "when": "editorTextFocus && vim.active && vim.use<D-v> && vim.mode == ''CommandlineInProgress' !inDebugRepl' || editorTextFocus && vim.active && vim.use<D-v> && !inDebugRepl && vim.mode == 'SearchInProgressMode'"
     },
     {
         "key": "cmd+d",
         "command": "-extension.vim_cmd+d",
         "when": "editorTextFocus && vim.active && vim.use<D-d> && !inDebugRepl"
     },
     {
         "key": "cmd+left",
         "command": "-extension.vim_cmd+left",
         "when": "editorTextFocus && vim.active && vim.use<D-left> && !inDebugRepl && vim.mode != 'Insert'"
     },
     {
         "key": "cmd+right",
         "command": "-extension.vim_cmd+right",
         "when": "editorTextFocus && vim.active && vim.use<D-right> && !inDebugRepl && vim.mode != 'Insert'"
     },
     // --- 取消或更改一些vscode键位
     // cmd+a全选功能在非INSERT模式下不生效
     {
         "key": "cmd+a",
         "command": "editor.action.selectAll",
         "when": "vim.mode != 'Normal' && vim.mode != 'Visual' && vim.mode != 'VisualLine' && vim.mode != 'VisualBlock' && vim.mode != 'CommandlineInProgress'"
     },
     {
         "key": "cmd+a",
         "command": "-editor.action.selectAll"
     },
     // cmd+c或者cmd+v功能在非INSERT模式下不生效
     {
         "key": "cmd+c",
         "command": "-editor.action.clipboardCopyAction"
     },
     {
         "key": "cmd+v",
         "command": "-editor.action.clipboardPasteAction"
     },
     {
         "key": "cmd+c",
         "command": "-execCopy"
     },
     {
         "key": "cmd+c",
         "command": "execCopy",
         "when": "vim.mode != 'Normal' && vim.mode != 'Visual' && vim.mode != 'VisualLine' && vim.mode != 'VisualBlock' && vim.mode != 'CommandlineInProgress'"
     },
     {
         "key": "cmd+v",
         "command": "-execPaste",
     },
     {
         "key": "cmd+v",
         "command": "execPaste",
         "when": "vim.mode != 'Normal' && vim.mode != 'Visual' && vim.mode != 'VisualLine' && vim.mode != 'VisualBlock' && vim.mode != 'CommandlineInProgress'"
     },
 ]

```

## Z.10. **资源管理配置**

默认的资源管理配置只包含了上下左右移动等基础命令，所以我们需要手动添加新增、删除、剪切、刷新等操作命令，它们仅在资源管理器中生效：

```
 j ： 向下移动
 k ： 向上移动
 space ： 打开文件或目录
 ​
 // 手动新增：
 ​
 i ： 新增文件
 o ： 新增目录
 r ： 刷新目录
 a ： 重命名文件或目录
 d ： 删除文件或目录
 x ： 剪切文件或目录
 y ： 复制文件或目录
 p ： 粘贴文件或目录

```

在 keybindings.json 文件中加入以下配置项：

```
     // --- 资源管理器中对文件或目录的操作
     // 新建文件
     {
         "key": "i",
         "command": "explorer.newFile",
         "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
     },
     // 新建目录
     {
         "key": "o",
         "command": "explorer.newFolder",
         "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
     },
     // 刷新资源管理器
     {
         "key": "r",
         "command": "workbench.files.action.refreshFilesExplorer",
         "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
     },
     // 重命名文件或目录
     {
         "key": "a",
         "command": "renameFile",
         "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
     },
     // 删除文件或目录
     {
         "key": "d",
         "command": "deleteFile",
         "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
     },
     // 剪切文件或目录
     {
         "key": "x",
         "command": "filesExplorer.cut",
         "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
     },
     // 复制文件或目录
     {
         "key": "y",
         "command": "filesExplorer.copy",
         "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
     },
     // 粘贴文件或目录
     {
         "key": "p",
         "command": "filesExplorer.paste",
         "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceReadonly && !inputFocus"
     },

```

## Z.11. **输入法切换**

如果你在 INSERT 模式下使用中文输入法进行编辑，当 ESC 到 NORMAL 模式下后，它将依然保持中文输入法，这会使我们需要频繁的使用 ctrl+shift 或者 cmd+space 进行输入法切换，非常麻烦。

为了解决这个问题，你必须先在你的计算机上安装一个 [im-select](https://link.zhihu.com/?target=https%3A//github.com/daipeihust/im-select) 脚本（根据官方文档来看，貌似只有 mac 和 windows 平台下存在这个问题）：

```
 $ curl -Ls https://raw.githubusercontent.com/daipeihust/im-select/master/install_mac.sh | sh

```

这个脚本有 2 个作用，当你输入 im-select 后它将获取当前输入法，当你输入 im-select xxx 后它将切换至 xxx 输入法。

首先你需要先切换到英文输入法中到终端执行 im-select 命令，并把结果保存下来：

```
 $ im-select
 com.apple.keylayout.ABC

```

然后再到 settings.json 中加入以下配置项即可完成输入法在 INSERT 模式以及 NORMAL 模式下的自动切换：

```
   // 自动切换输入法
   "vim.autoSwitchInputMethod.enable": true,
   "vim.autoSwitchInputMethod.defaultIM": "com.apple.keylayout.ABC",  // 这里输入你刚刚获得的英文输入法名称
   "vim.autoSwitchInputMethod.obtainIMCmd": "/usr/local/bin/im-select",
   "vim.autoSwitchInputMethod.switchIMCmd": "/usr/local/bin/im-select {im}"

```

## Z.12. 内置插件

vsocde-vim 中内置了很多插件，使用它们可以快速的进行某一些操作。

1）vim-esaymotion 插件，使用它之前你必须在 settings.json 中加入下面这一行：

```
 "vim.easymotion": true,

```

它的作用是通过以下的按键组合，你可以快速的定位到任何你想修改的行中：

```
 <leader><leader>s<char>

```

2）vim-surround 插件，如果你想修改、或者删除单引号和双引号，它带给你的体验将是无与伦比的，以下是它的语法：

```
 ds<existing>
 cs<existing><desired>

```

示例如下：

```
 # 删除以下的[]
 [1, 2, 3] -> ds[
 ​
 # 将以下的[]修改为()
 [1, 2, 3] -> cs[(

```

3）vim-commentary 插件，该插件能够快速的利用键盘进行行或者块的注释，它内部其实是调用了 vscode 的注释 API：

```
 gcc ：行注释
 gCC ：块注释

```

## Z.13. 便捷操作

除此之外，vscode-vim 插件也额外提供了一些非常多的快捷键用于编辑操作：

```
 gd ： 跳转到函数定义或引用处，搭配cmd+i/cmd+o查看源码很方便
 gh ： 触发帮助提示
 gb ： 开启多光标模式，选中和当前单词相同的单词

```

## Z.14. 推荐插件

有一些朋友可能和我一样安装了 [google-translate](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dhancel.google-translate) 插件或者 [comment-translate](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dintellsmi.comment-translate) 插件来查看源代码注释的翻译结果，这个时候你将会遇到一些问题。

如一次性选择翻译的文本太长，vscode 的 hover 无法支持 scroll 的快捷键滚动操作，你只能通过鼠标滚轮进行 hover 窗口的滚动：

![](https://pic1.zhimg.com/v2-22dae510a107e6ef88fbe7166cde63c8_b.gif)

该问题在 vscode 的 github 上多次被提到，这对全键盘操作用户来说是非常不友好的，可以参见 [#69836](https://link.zhihu.com/?target=https%3A//github.com/microsoft/vscode/issues/69836)。

对此有一个折中的解决方案，安装一个 [Doc View](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dbierner.docs-view) 插件，将翻译结果放在侧边栏中，这样我们就有足够的空间来显示翻译结果了：

![](https://pic2.zhimg.com/v2-7947085a0019c36937def19eb824c7a5_r.jpg)

另外一个问题就是关于 Error 的提示信息，你可以自定义一些热键来快速查看 Error，或者跟我一样安装一个 [Error Lens](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dusernamehw.errorlens) 插件。

如下图所示，有了该插件我们就能快速的查看到一些问题的提示信息了：

![](https://pic2.zhimg.com/v2-14465a061fa548859a04423dc1d0e9d5_r.jpg)

配合上面定义的 g[或者 g] 热键，就可以快速的定位到某个错误并进行修改。

## Z.15. 写在后面

为什么不选择使用 vim 来搭建一个 IDE 呢？

* 太麻烦、懒得折腾，vscode 足够强大…

为什么不选择使用 vscode neovim 插件呢？

*   visual 模式不是 vscode 的真正选择，多端同步比 vscode-vim 麻烦是我没选择它的主要原因

vim 真的很好用吗？

* 使用 vim 能治好你的 vim 崇拜症，但是 vim 并不是必须的

此外，网上搜了很多资料无一例外都是比较浅显的介绍了一下 vsocode-vim 插件就完了，但是真正让你能够搭配出一套全键盘使用方案的文章少之又少，所以这里就将我的折腾历程发了出来，很显然它比单纯的折腾 vim 要快很多。

## Z.16. 参考文档

参考文档：

*   [vscode 官方文档 按键](https://link.zhihu.com/?target=https%3A//code.visualstudio.com/docs/getstarted/keybindings%23_keyboard-shortcuts-editor)
*   [vscode 官方文档 命令](https://link.zhihu.com/?target=https%3A//code.visualstudio.com/api/references/commands)
*   [vscode-vim 官方文档](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dvscodevim.vim)
*   [vscode-nvim 官方文档](https://link.zhihu.com/?target=https%3A//marketplace.visualstudio.com/items%3FitemName%3Dasvetliakov.vscode-neovim)
*   [spacevim 官方文档](https://link.zhihu.com/?target=https%3A//spacevim.org/cn/documentation/)

## Z.17. Windows 热键

我在 windows 上进行了尝试，它令我感到惊叹。

vim 插件不知为何在 mac 和 linux 上都有些许卡顿，但是 windows 上异常顺滑，下面是我的配置方案：

```
[
    // --- 全局命令
    // 显示命令面板
    {
        "key": "ctrl+g c",
        "command": "workbench.action.showCommands"
    },
    // 打开设置页面
    {
        "key": "ctrl+g s",
        "command": "workbench.action.openSettings"
    },
    // 打开热键映射
    {
        "key": "ctrl+g k",
        "command": "workbench.action.openGlobalKeybindings"
    },
    // 打开一个目录
    {
        "key": "ctrl+g d",
        "command": "workbench.action.files.openFolder"
    },
    // 打开一个文件
    {
        "key": "ctrl+g f",
        "command": "workbench.action.files.openFile"
    },
    // 打开最近记录
    {
        "key": "ctrl+g h",
        "command": "workbench.action.openRecent"
    },
    // 新建vscode实例
    {
        "key": "ctrl+g n",
        "command": "workbench.action.newWindow"
    },
    // 关闭vscode实例
    {
        "key": "ctrl+g q",
        "command": "workbench.action.closeWindow"
    },
    // --- 文件命令
    // 新建文件
    {
        "key": "ctrl+f n",
        "command": "welcome.showNewFileEntries",
    },
    // 打开文件
    {
        "key": "ctrl+f o",
        "command": "workbench.action.files.openFileFolder"
    },
    // 另存为文件
    {
        "key": "ctrl+f e",
        "command": "workbench.action.files.saveAs"
    },
    // 保存文件
    {
        "key": "ctrl+f s",
        "command": "workbench.action.files.save"
    },
    // 保存所有文件
    {
        "key": "ctrl+f w",
        "command": "workbench.action.files.saveAll"
    },
    // 关闭文件
    {
        "key": "ctrl+f q",
        "command": "workbench.action.closeActiveEditor"
    },
    // 关闭所有文件
    {
        "key": "ctrl+f a",
        "command": "workbench.action.closeAllEditors"
    },
    // -- 侧边栏命令
    // 切换侧边栏显示状态
    {
        "key": "ctrl+n [",
        "command": "workbench.action.toggleSidebarVisibility"
    },
    // 显示文件资源管理器
    {
        "key": "ctrl+n 1",
        "command": "workbench.files.action.focusFilesExplorer"
    },
    // 显示TODO Tree
    {
        "key": "ctrl+n 2",
        "command": "todo-tree-view.focus"
    },
    // 显示全局搜索
    {
        "key": "ctrl+n 3",
        "command": "workbench.action.replaceInFiles",
    },
    // 显示debug
    {
        "key": "ctrl+n 4",
        "command": "workbench.view.debug",
        "when": "viewContainer.workbench.view.debug.enabled"
    },
    // 显示版本控制
    {
        "key": "ctrl+n 5",
        "command": "workbench.view.scm",
        "when": "workbench.scm.active"
    },
    // 显示SQL Tools
    {
        "key": "ctrl+n 6",
        "command": "workbench.view.extension.sqltoolsActivityBarContainer"
    },
    // 显示Docker
    {
        "key": "ctrl+n 7",
        "command": "workbench.view.extension.dockerView"
    },
    // 显示测试
    {
        "key": "ctrl+n 8",
        "command": "workbench.view.testing.focus"
    },
    // 显示插件商店
    {
        "key": "ctrl+n 9",
        "command": "workbench.view.extensions",
        "when": "viewContainer.workbench.view.extensions.enabled"
    },
    // --- 面板命令
    // 切换面板显示状态
    {
        "key": "ctrl+p [",
        "command": "workbench.action.togglePanel"
    },
    // 显示问题
    {
        "key": "ctrl+p 1",
        "command": "workbench.panel.markers.view.focus"
    },
    // 显示输出
    {
        "key": "ctrl+p 2",
        "command": "workbench.action.output.toggleOutput",
        "when": "workbench.panel.output.active"
    },
    // 显示终端
    {
        "key": "ctrl+p 3",
        "command": "workbench.action.terminal.toggleTerminal",
        "when": "terminal.active"
    },
    // 显示调试控制台
    {
        "key": "ctrl+p 4",
        "command": "workbench.debug.action.toggleRepl",
        "when": "workbench.panel.repl.view.active"
    },
    // 显示SQL CONSOLE
    {
        "key": "ctrl+p 5",
        "command": "workbench.view.extension.sqltoolsPanelContainer"
    },
    // --- 编辑区命令
    // 关闭当前选项卡或分屏
    {
        "key": "ctrl+q",
        "command": "workbench.action.closeActiveEditor"
    },
    // 聚集在第一个选项卡中
    {
        "key": "ctrl+e",
        "command": "workbench.action.focusFirstEditorGroup"
    },
    // 切换到上一个选项卡
    {
        "key": "ctrl+,",
        "command": "workbench.action.previousEditor"
    },
    // 切换到下一个选项卡
    {
        "key": "ctrl+.",
        "command": "workbench.action.nextEditor",
    },
    {
        "key": "ctrl+w s",
        "command": "workbench.action.splitEditorDown"
    },
    // 拆分一个左右分屏
    {
        "key": "ctrl+w v",
        "command": "workbench.action.splitEditor"
    },
    // 将光标向上动1屏
    {
        "key": "ctrl+w k",
        "command": "workbench.action.focusAboveGroup"
    },
    // 将光标向下动1屏
    {
        "key": "ctrl+w j",
        "command": "workbench.action.focusBelowGroup"
    },
    // 将光标向左移动1屏
    {
        "key": "ctrl+w h",
        "command": "workbench.action.focusLeftGroup"
    },
    // 将光标向右移动1屏
    {
        "key": "ctrl+w l",
        "command": "workbench.action.focusRightGroup"
    },
    // --- 代码编辑命令
    // 触发帮助提示
    {
        "key": "ctrl+h",
        "command": "editor.action.showHover",
        "when": "editorTextFocus"
    },
    // 触发参数提示
    {
        "key": "ctrl+j",
        "command": "editor.action.triggerParameterHints",
        "when": "editorHasSignatureHelpProvider && editorTextFocus"
    },
    {
        "key": "ctrl+j",
        "command": "closeParameterHints",
        "when": "editorFocus && parameterHintsVisible"
    },
    // 触发建议提示
    {
        "key": "ctrl+k",
        "command": "editor.action.triggerSuggest",
        "when": "editorHasCompletionItemProvider && textInputFocus && !editorReadonly"
    },
    {
        "key": "ctrl+k",
        "command": "hideSuggestWidget",
        "when": "suggestWidgetVisible && textInputFocus"
    },
    // 移动到下一个建议
    {
        "key": "ctrl+n",
        "command": "selectNextSuggestion",
        "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
    },
    // 移动到上一个建议
    {
        "key": "ctrl+p",
        "command": "selectPrevSuggestion",
        "when": "suggestWidgetMultipleSuggestions && suggestWidgetVisible && textInputFocus"
    },
    // 打开快速修复
    {
        "key": "ctrl+m",
        "command": "editor.action.quickFix",
        "when": "editorHasCodeActionsProvider && editorTextFocus && !editorReadonly"
    },
    // 格式化代码
    {
        "key": "ctrl+alt+l",
        "command": "editor.action.formatDocument",
        "when": "editorHasDocumentFormattingProvider && editorTextFocus && !editorReadonly && !inCompositeEditor"
    },
    // 放大字体
    {
        "key": "ctrl+=",
        "command": "editor.action.fontZoomIn"
    },
    // 缩小字体
    {
        "key": "ctrl+-",
        "command": "editor.action.fontZoomOut"
    },
    // --- 资源管理器中对文件或目录的操作
    // 新建文件
    {
        "key": "i",
        "command": "explorer.newFile",
        "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
    },
    // 新建目录
    {
        "key": "o",
        "command": "explorer.newFolder",
        "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
    },
    // 刷新资源管理器
    {
        "key": "r",
        "command": "workbench.files.action.refreshFilesExplorer",
        "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
    },
    // 重命名文件或目录
    {
        "key": "a",
        "command": "renameFile",
        "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
    },
    // 删除文件或目录
    {
        "key": "d",
        "command": "deleteFile",
        "when": " explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus "
    },
    // 剪切文件或目录
    {
        "key": "x",
        "command": "filesExplorer.cut",
        "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !explorerResourceReadonly && !inputFocus"
    },
    // 复制文件或目录
    {
        "key": "y",
        "command": "filesExplorer.copy",
        "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceIsRoot && !inputFocus"
    },
    // 粘贴文件或目录
    {
        "key": "p",
        "command": "filesExplorer.paste",
        "when": "explorerViewletVisible && filesExplorerFocus && !explorerResourceReadonly && !inputFocus"
    },
]

```