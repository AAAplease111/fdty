# 复旦体育理论考试-自动答题机器 ![收录题目总数](https://img.shields.io/badge/收录题目总数-5752-green.svg) ![最后更新时间](https://img.shields.io/badge/最后更新时间-2018/12/9-blue.svg)

## 项目说明
本项目基于```体育理论考试精灵```题库和在线收集的题库，只是一个技术实验（获取网页信息、数据库中智能匹配、修改网页表单项）。
本项目仅限技术交流，完全开源，无任何盈利行为。也请同学们重视体育理论考试，好好准备体育理论考试。

* 方便易用，基于Chrome，兼容所有操作系统，无需安装任何软件。
* 自动读取网页、匹配题库，瞬间出答案、自动勾选，节省时间。
* 支持是非题与单选题。
* 截止到2018年12月9日，总共有5206道不重复的是非题、546道不重复的单选题。
* 智能容错，若发现题目是数据库中某题修改了几个字，会提醒用户判断。

## 一张图体会一下
![show](screenshots/show.png?2017-5-22)
不光自动匹配，还会帮您自动勾选上！

所以，按照下面的【使用方法】做一遍，然后点交卷，基本就能满分了。

一分钟搞定体育理论考试。

## 使用方法

### 1. 使用 **Chrome** 打开考试界面
要打开【考试界面】哦！就是做题界面，点“开始考试”按钮后，能看到50道题目的那个界面。

随便玩，点“开始考试”没有后果的，考到一半不想交了，关闭窗口即可（2016年5月26日亲测）。

一定要较新版本的Chrome！别的浏览器没试过，尽量不要用！

### 2. 在考试界面中，打开开发者工具里的控制台
确保考试界面是激活状态的（不是灰的），然后在该界面按：

| 操作系统    | 快捷键                                      |
| ------- | ---------------------------------------- |
| Windows | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>J</kbd> |
| Mac     | <kbd>Command</kbd>+<kbd>Option</kbd>+<kbd>J</kbd> |

### 3. 修改左上角下拉菜单的值
![show](screenshots/1.png?2017-5-22)

调整为 ```paper(stexampaperV1.aspx)```

### 4. 复制以下代码，粘贴、运行
![show](screenshots/2.png?2017-5-22)

	var fdty_src="http://kevinwang.cc/fdty/fdty.js";var f_sl = document.createElement("script");f_sl.type = "text/javascript";console.info('正在加载自动答题脚本');f_sl.src = fdty_src + '?' + (+new Date());document.getElementsByTagName("head")[0].appendChild(f_sl);


### 5. 检查试卷、补充数据库中没有的题目的答案、交卷
![show](screenshots/3.png?2017-5-22)
只要数据库中有答案的，本程序会帮您自动勾选，但您还是要检查一下试卷哦！

数据库中没答案的，就不会自动勾选，您需要百度一下，然后手动勾选。

### 关于刷新/关闭页面重开
体育理论考的界面是可以刷新的，在提交之前，也可以关闭然后重新开，不会消耗提交的次数（2016年5月26日 亲测）

体育理论考界面有代码防止学生刷新，所以按<kbd>F5</kbd>是没用的。但这个很容易绕过，在Chrome开发者工具中，按<kbd>Ctrl</kbd>+<kbd>R</kbd>刷新就行。

所以，如果哪次打开，发现有好几题没有匹配成功的，不妨刷新了重新匹配试试。刷新后，要回到第三步，重新做哦。

# PR请求

## 求完善题库（长期）

虽然题库已经比较全了，但体育部仍然会偶尔新加一些题、改一些题的。

如果您手上有新的题库，请[点击这个链接](https://github.com/KevinWang15/fdty/issues/3)分享给我。

（注意：分享单选题答案的时候，重要的是答案选项哦（A B C D），这是程序做自动勾选的依据，分享时一定要带上）

您也可以发Pull Request，

### 题库生成方法：

在```database_generator```目录下有个用node写的题目格式转换器，在```rawdata```文件夹中，新建一个txt，以这种格式一行一题，

	["获得和利用食物的综合过程称为营养。","true"],
	["合理的营养意味着机体能够摄入保持身体健康所必须的部分营养成分。","false"],
	...

（原始题库、转换题库成以上格式时用到的正则表达式也请记录一下哦）

然后运行```node generate.js```就行了，谢谢。
