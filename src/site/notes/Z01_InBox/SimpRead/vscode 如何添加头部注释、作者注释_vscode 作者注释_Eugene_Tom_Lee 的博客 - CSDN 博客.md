---
{"dg-publish":true,"aliases":[null],"tags":["4_Information"],"number headings":"auto, first-level 1, max 6, A.1.","url":"https://blog.csdn.net/weixin_42677762/article/details/109034890","title":"vscode 如何添加头部注释、作者注释_vscode 作者注释_Eugene.Tom.Lee 的博客 - CSDN 博客","summary":null,"Created-Date":"2023-09-24 15:53:10","Modified-Date":"2024-04-18 11:52:11","permalink":"/Z01_InBox/SimpRead/vscode 如何添加头部注释、作者注释_vscode 作者注释_Eugene_Tom_Lee 的博客 - CSDN 博客/","dgPassFrontmatter":true}
---

### Z.1.1. [vscode](https://so.csdn.net/so/search?q=vscode&spm=1001.2101.3001.7020) 如何添加头部注释、作者注释

Visual Studio Code 是微软开发的编辑器， 目前国内使用的用的人是越来越多。那么 vscode 如何添加头部注释，让你的代码有很明显的标识呢？  
第一步：  
打开 Visual Studio Code 编辑器。找到 vscode 右下角那个添加插件的按钮

![](https://img-blog.csdnimg.cn/20201012194306937.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

点击插件按钮后， 在输入框内输入 fileheader 回车，选择第一个。如第二图所示，点击 install（安装）按钮。

![](https://img-blog.csdnimg.cn/20201012194333565.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

  
左下角选择管理—设置—输入 "fileheader"—点击 " 在 setting.json 中编辑 "  

![](https://img-blog.csdnimg.cn/20201012194714648.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

把下面的代码放到 json 文件父对象中  

![](https://img-blog.csdnimg.cn/20201012195316838.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

然后记得改一下你的名字，我的英文名：Eugene.tom.lee 你也可以改成例如：K1101355 这样子的自己的工号。（对了，代码奉上。）

```
// 文件头部注释
    "fileheader.customMade": {
        "Descripttion":"",
        "version":"",
        "Author":"Eugene",
        "Date":"Do not edit",
        "LastEditors":"Andy",
        "LastEditTime":"Do not Edit"
    },
    //函数注释
    "fileheader.cursorMode": {
        "name":"",
        "msg":"",
        "param":"",
        "return":""
    },

```

最后检查一下，发现成功了，嘻嘻。

**快捷键：ctrl + alt + i 生成头部注释**  

![](https://img-blog.csdnimg.cn/20201012195719976.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

**快捷键：ctrl + alt + t 生成函数注释**  

![](https://img-blog.csdnimg.cn/20201012195950408.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjY3Nzc2Mg==,size_16,color_FFFFFF,t_70#pic_center)

### Z.1.2. 每天一句中文式外语

### Z.1.3. 俄语

```
парикмахерская (把里和马海勒斯嘎呀)
理发店
супермаркет (苏别勒马给特) 超市
базар (巴扎勒) 市场
чулки‚носки (丘俄给,拿丝给) 袜子
туфли (读富里) 鞋
брюки (不留给) 裤子
пальто (八里多) 大衣
костюм (嘎丝旧木) 西服
куртка (古勒特嘎) 夹克衫
шапка (沙铺嘎) 帽子
полотенце (把拉接恩采) 毛巾
мыло (美啦) 肥皂
зубная щётка (足不拿呀 笑特嘎) 牙刷
зубная паста (足不拿呀 八丝达) 牙膏
телевизор (节列为扎了) 电视机
магнитафон (马革尼达佛) 录音机
радио (辣椒) 广播,收音机
фотоаппарат (发达阿爸拉特) 照相机
господин‚мистер (嘎丝八井,米丝节了)
先生
госпожа (嘎丝八染) 女士
мадам (马达母) 夫人
девушка‚мисс (借物识嘎,密丝) 小姐
весна (为丝那) 春天
лето (列达) 夏天
осень (噢些你) 秋天
зима (贼吗) 冬天
жарко (热了嘎) 热
тепло (节朴劳) 暖和
холодно (火辣的那) 冷
прохладно (扑拉和拉得那) 凉
мороз (马骡死) 严寒
погода (八国打) 天气
климат (刻里马特) 气候
хорошая погода (哈罗杀呀 八国打)
好天气
снег (丝捏可) 雪
дождь (多洗) 雨
ветер (位接了) 风
песочная буря (憋缩其拿呀 不里呀)
沙尘暴
утром (无特拉木) 早上
днём (得鸟木) 白天
вечером (为切拉木) 晚上
ночью (挪其油) 夜里
сегодня (写我的你呀) 今天
вчера (复切拉) 昨天
завтра (扎复特拉) 明天
да (达) 是
нет (涅特) 不是
хорошо (哈拉烁) 好
плохо (朴罗哈) 不好
налево (拿列瓦) 向左
направо (拿朴拉瓦) 向右
прямо (扑里呀马) 直走

```

### Z.1.4. `任何一种进步的过程都是反人性的，甚至是痛苦的。所以我们要努力做到在快乐中学习与成长。首先要对世界产生强烈的好奇心，兴趣是自己最好的老师！`