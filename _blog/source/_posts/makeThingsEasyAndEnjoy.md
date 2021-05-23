---
title: Make things easy and enjoy
date: 2016-10-08 16:58:56
modified: 2018-11-19 18:53:59
category: 杂谈
tags: 杂谈
slug: 
---
# 命令行的简便生活 💦🤣


---

## find 文件查找
今天(2018年12月12日，17点08分)在众多文件里找一个文件的时候… 想到`find`命令。不过之前没有怎么了解过，所以…
我居然用了`tree | grep filename.filetype`来找东西。 结果路径太深——就最多确认了此文件的存在性。
随后，才知道`find`要加`-name`参数。 emm...不过对于`find`多功能来说也说得过去。  随后便有了以下这个命令:
```shell
find . -name "cifar.py" -exec vim {} \;
```
没错~，查找之后并编辑——😄
除此之外，当然可能用于 `rm`、`grep`等去替换`vim`进行操作。
其中，`{}`自然时代表匹配文件的路径。 如果不止一个那么…就： vim为例，会关闭一个窗口再打开另一个😓
另外，配合`grep`查找文本内容的时候，需要在最后面加`-print`否则只有匹配文本，不显示文件路径。

# Windows 转换磁盘分区格式
## 方法/步骤 

1
1.U盘引导，进入PE系统

2
 用pe进去，找到运行输入cmd   

3
输入”Diskpart”(不用输入引号，下同)，并按回车，进入操作界面

4
输入：”list disk”，查看磁盘信息。一般会出现两个选项，一个是你的硬盘，一个是U盘，要注意区分。

5
输入：”select disk 0”，选择disk 0为当前操作的磁盘（也就是电脑的 硬盘）

6
输入：”Clean”，清空当前磁盘分区

7
输入：”convert mbr”，转换为MBR分区。

8
OK，搞定，可以安装WIN7了


### Windows远程桌面 
    mstsc
    # WIn自带应用，不过用的时候得关闭防火墙就很伤
### Windows 输入法故障
    ctfmon.exe     win+R 执行此，重启输入法
### Win 安装Ubuntu
    #在powerShell中管理员运行
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-
Windows-Subsystem-Linux

#### Windows 自启动项目录
`C:\Users\Administrator\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`

在此目录下添加入快捷方式则在系统启动之后自动加载，但会有一些延时，不同于直接定义的自启动项，算是<font color=#ffff00>优先级最落后</font>的项目吧

#### Windows 查看电池使用情况
    powercfg /BatteryReport
    # 适用于Win8+

## Python Pip
    pip install -r *.txt
    # 从*.txt 文件读取需要安装的插件列表

---
---

# win Ubuntu 时间不一致
    timedatectl set-local-rtc true 
    #采用本地时间          推荐

---
---

### Ubuntu  升级系统
    sudo update-manager -c -d
    #会检测是否有系统更新，
    #如果都更新完毕，
    #则提醒有新版本系统是否更新
### Windows 更新系统错误
<font color=#ff00ff>dism++ 你值得拥有</font>

另外：
<font color=#800008>无法连接到更新服务。我们将稍后再试，你也可以立即进行检查。如果问题仍然存在，请确保你已连接到 Internet。</font>   
可能是
<font color=#808808>本地组策略中的windows更新的“指定Intranet Microsoft更新服务位置”被更改过</font>

解决办法为

* 1. gpedit.msc
* 2. 打开“本地组策略编辑器”展开“计算机配置”—“管理模版”—“Windows组件”—“Windows 更新”（专业版称为Windows Update）
* 3. "指定Intranet Microsoft更新服务位置”，点击“未配置"
    
### Ubuntu 桌面显示问题
卸载 ibus 输入法，会出现桌面显示不完全的情况，任务栏显示，启动栏消失，键盘快捷键无法使用。解决办法是重新安装 Unity 之后启动Unity 就会重新打开桌面环境…其实是又重新安装了 ibus  嗯………
### Vim 设置Tab空格数
    :set tabstop=4
    #添加至用户vim配置文件： .vimrc 下即可

# 正则表达式
作为短小精悍的东西嘞，今天在限制密码类型和长度的时候尝尽了甜头。但在分类时…不好分，应该单独写一个笔记的，但短小精悍嘛，所以就放在命令行这里了。

    import re    # 好吧，其实无所谓的，因为下面并没有用到Python正则模块
        a = QtCore.QRegExp("[A-Za-z]{0,5}[1-9][0-9]{0,5}")
        a = QtCore.QRegExp("[a-zA-Z0-9]{0,12}$")
        a = QtCore.QRegExp("[a-zA-Z0-9]+$")
    a = QtCore.QRegExp("[a-zA-Z0-9\,\.\\\!\?\#\$\%\^\&\*\(\)\)_\_\=\`\+]+$")

这里的`[]`中内容是输入范围，`{}`中的则是长度限制，而`+`就是不限长度 与` * `类似。 `$ `是结尾标志。 over。

## 闲的没事找事记：
    安装了一个美国版的windows 10 pro N 结果字体缺失，系统默认编码方式是Ascii不是utf……导致程序中的输出中文都出现问题。结果在这些不构成生产力的份儿上浪费时间，真是闲的没事找事…
        
## Vim
    查看编码格式 `:set fenc`   
    设置文件格式`:set fileformat=unix`或者`:set fileformat=dos` 
        ——针对于换行符
`set tabstop=4`、`set expandtab`前者是一个`tab`的长度，后者是tab换为空格…






# GoodApps
#### Nitrux、Flatabulous-master：
主题，图标 用来美化很漂亮，图例样式可以参看这两者的Github。

---

#### GoldenDict：
一款词典，其可以添加网络翻译源，还可以自行下载本地翻译文件，本地内容我下载的含有：日汉、汉日、英牛津，朗道，还有本本草纲目……没错，确实还有科普类的翻译源。各种奇异翻译本都有。

---

#### Xware：
一款迅雷的替代，网络远程下载，完全能当一个没有广告的迅雷来使。 只不过需要账户密码，还有，在安装完毕之后，需要预先设置一番，将Xware托管改为用户态upstar，或者简单的自动启动。否则会显示ETM 没有链接，不能使用。另外将挂载，实际作用是下载保存位置，也设置一下。这么长时间了，英文路径应该养成习惯……

---

#### MyPaint：
画图工具，很好使。

---

#### Chrome:
这个浏览器不用说，这里介绍的是关于它修改hosts文件之后可能仍然无法使用谷歌搜索的问题。

1.因为，默认的是http，故显示已被重定向啊，啥的。只要在地址栏前输入https就可以正常访问了。
2.当然，这样的话无法使用网页里的按钮“使用谷歌搜索”，所以需要修改其默认。可以在Chrome://net-internals/ 中，找见HSTS选项卡，Domain中输入想要默认强制使用https的网址。（PS：因为我的使用google自动跳转谷歌香港，所以这里用google.com还是不行的，得加上.hk的后缀。）
3.以上修改方法应该只能设置一个默认网址呢，不过一个google搜索就够了…… 嗯，我要求比较低。 至于其他浏览器，大概是默认https的，因为可以直接访问嘛。
自然还有很好的别的稍微专业的工具，这个会在之后持续更新出来，用学习笔记的形式（而且，等我学会在文章里添加链接啊，图片啊之后）。以上入门级、常用级的也会持续更新的～ 下载链接我以及之后都不会贴出来，嗯，毕竟没有永远保存的，链接经常失效。自行搜索总是好的，还能顺便了解一下这块软件的使用方法，以及类似替代软件的出现。

---

#### Nethack：
終端運行的一款地牢遊戲，相當高的自由度和隨機程度，除卻一切怪物和地圖都是用符號來代替，戰鬥過程就是用文字信息來描述，在創造和思索方面簡直一流。以後有空閒肯定要玩一玩～

---

#### Virbox ：
	sudo mount /dev/cdrom // ^^^目標地^^^ //掛載光盤 
	sudo mount -t vboxsf //^^Name^^ ^^^目標地^^^ //掛載虛擬機共享文件

---

### 下面是其他软件的学习笔记：（等待更新——）

---

#### Linux：
嗯，这是个软件…详见《Linuxのノート》

---

#### Pelican :
静态网页编辑生成工具。 keywords：Python、markdown

---

#### Blender：
開源建模，動畫軟件。 
###### 快捷鍵記錄：
	N、T	//編輯欄呼出、隱藏 
	T	//側重物體，N側重編輯窗口 
	B	//選擇 
	Tab	//模式切換
	Ctrl+U	//用戶界面保存 
	Z	//物體顯示樣式切換 線框、透視 
	H	//刪除 
	G	//移動 
#### musicbox：
Linux 命令行下的 網易雲音樂 。夠精簡夠豐富，實爲經驗驚豔。
##### 基於Python：
	>https://github.com/darknessomi/musicbox

---

#### xSwipe：
多指触控软件。通过将触控板手势映射成快捷键，可以支持甚至五指操作，还有侧边功能。在github中搜索`xSwipe`即可，其中有详细安装说明。之后可以在.conf文件中查看和修改映射快捷键。另最后如果不能运行，可能需要注销重启电脑方可。
运行 `perl xSwipe.pl`即可执行。

---

#### OpenCV：
开源计算机视觉库。  简单记录一下编译过程：(其實沒啥用的，自己爬官網找安裝教程去，基本沒用。)

##### 1. 解决依赖，编译工具
	sudo apt-get install build-essential
	sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
	sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev`
##### 2. github 下载源程序
	git clone https://github.com/opencv/opencv.git
##### 3. Building OpenCV from Source Using CMake, Using the Command Line
	cd ~/opencv
	mkdir release
	cd release
	cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
##### 4.
	make
	sudo make install
	all from >http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_install/linux_install.html
	// (或許安裝過程就這句有用 23333)

	Thanks for your teaching.

---

#### Simplenote:
	一款笔记软件，支持markdown编辑，很轻量、只能记录文字有点儿伤。不过有Linux版就很爽。而且同步速度、启动速度都很迅速。界面简单到不行。手机一次不幸刷机之后，有道云笔记懒得装，之后就用此软件吧…

#### scp
`server copy`? 这个简写不晓得，不过确实是适用于远程连接传输文件的…  
```shell 
    scp ian@123.123.41.3(😀):/home/ian/nihou.txt ./files
    scp ./files ian@123.123.41.3(😀):/home/ian/nihou.txt 
```
#### 删除Win系统服务
```shell
sc delete serverName
```

### tmux
丰富纯文字终端窗口，可以创建终端副本(反正也是我取得名字)—--类似于`win`的多桌面。也可以分割终端(界面类似vim分割)l--这便是类似于`win`的多窗口了。 (官方翻译: '窗格'？)

- 进入: `tmux`
- 退出: `exit`
- 类似于`vim`命令模式： `ctrl+b`以下简写为`CL_B`。
- 创建多桌面: CL_B + c
- 查看全部窗口，类似`win+Tab`: CL_B + s    使用窗口号切换桌面: CL_B + NUM    
- 关闭当前窗口: CL_B + &,emm直接`exit`...
- 创建多窗口: CL_B + " (垂直上下)、CL_B + % (水平左右)   调整窗口位置、大小 CL_B + space (默认布局轮换)
- 显示窗口编号: CL_B + q    暂时最大化当前窗格: CL_B + z   切换到下一个窗格: CL_B + o
- 对换窗格位置: CL_B + CL_O(ctrl + o)

### Termux
类似于`WIN`端的`Subsystem`——其实更像Ubuntu下的虚拟终端。 不过这东西功能强大，除了将安卓里的Linux发挥出来。还有`Termux API`来调用手机的底层接口。

#### ssh与手机连接
其实应该放在`ssh`的操作里面？ emm，还是就这儿吧。

##### *pc
**电脑生成密匙,无视密码设置全部回车
```bash
ssh-keygen -t rsa
```
**电脑开启sshd服务,用于手机的ssh连接到电脑拷贝id_rsa.pub内容
```bash
systemctl start sshd
```
然而我用的是win子系统所以：sshd re-exec requires execution with an absolute path
##### phone
**手机连接拷贝
```bash
$HOME/.ssh/authorized_keys -> 不管用什么复制，然后放到这个路径就好。
```
**查看手机的用户名
```bash
whoami
```
**开启服务
```bash
sshd -p 9000
```

##### *pc
连接到手机
```bash
ssh u0_222@192.168.1.14 -p 9000
```

Over, 其余问题查看文件权限？  不过还是自建文件`.ssh`出错率为0吧。

2018年12月4日11点27分,当我反过来操作的时候…  嗯，果然在权限这里出问题了…
另外，电脑端开启`sshd`的时候用的绝对地址… 因为是Syb？

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```
    😓

#### 快捷键(有用的音量键？)
显示扩展功能按键

方法一:
- 从左向右滑动,显示隐藏式导航栏,长按左下角的KEYBOARD.

方法二:
- 使用Termux快捷键:音量++Q键

常用快捷键
- Ctrl键是终端用户常用的按键 – 但大多数触摸键盘都没有这个按键。为此，Termux使用音量减小按钮来模拟Ctrl键。在触摸键盘上按音量减小+ L发送与在硬件键盘上按Ctrl + L相同的输入。
- Ctrl+A -> 将光标移动到行首
- Ctrl+C -> 中止当前进程
- Ctrl+D -> 注销终端会话
- Ctrl+E -> 将光标移动到行尾
- Ctrl+K -> 从光标删除到行尾
- Ctrl+L -> 清除终端
- Ctrl+Z -> 挂起（发送SIGTSTP到）当前进程

音量加键也可以作为产生特定输入的特殊键.
- 音量加+E -> Esc键
- 音量加+T -> Tab键
- 音量加+1 -> F1（和音量增加+ 2→F2等）
- 音量加+0 -> F10
- 音量加+B -> Alt + B，使用readline时返回一个单词
- 音量加+F -> Alt + F，使用readline时转发一个单词
- 音量加+X -> Alt+X
- 音量加+W -> 向上箭头键
- 音量加+A -> 向左箭头键
- 音量加+S -> 向下箭头键
- 音量加+D -> 向右箭头键
- 音量加+L -> | （管道字符）
- 音量加+H -> 〜（波浪号字符）
- 音量加+U -> _ (下划线字符)
- 音量加+P -> 上一页
- 音量加+N -> 下一页
- 音量加+. -> Ctrl + \（SIGQUIT）
- 音量加+V -> 显示音量控制
- 音量加+Q -> 显示额外的按键视图

## Rdfind
### 替代方案
`Rdfind`是命令行的, `DuplicatePhotoFinder1.6.3`是有UI的, 可以展示出内容, 不过很傻, 不能多选一次删除, 只能一个一个删除.....
所以我做了一个托管鼠标点击器. 如下

使用`Rdfind` 进行重复文件查询, 然后删了, 节省磁盘空间.
> 不过我准备自己做一个, 更方便删减图片, 所以以后应该会用自己做的, 这个就留下参考吧. 
[^_^]:
    2021-04-22
### 查询重复
```drfind /Image/`, 结果报表存于当前目录`results.txt```
### 终端输出
```rdfind -dryrun true /Image```
### 删除空文件和重复文件
```rdfind -deleteduplicates true -ignoreempty false /Image```
### 删除重复文件
```rdfind -deleteduplicates true /Image```


## 鼠标自动点击
选择点, 不到1s一点, 终端无法立即实时中断, 估计要用上`Listener`不过现在这样也可以啦.

```py
import time
from datetime import date, datetime

from pynput import mouse
from pynput.mouse import Button, Controller

mouse = Controller()

sign_start = False
print("请将鼠标移动到指定位置, 输入`r`开始.")

str_input = None
position_loop = None
while 1:
    str_input = str_input or input()
    if str_input == 'r':
        position_loop = position_loop or mouse.position
        mouse.position = position_loop
        # mouse.move(position_loop[0], position_loop[-1])
        mouse.press(Button.left)
        time.sleep(0.2)
        mouse.release(Button.left)
        print(f"{datetime.now()} - clicked - {position_loop}.")
        time.sleep(0.4)
    else:
        print("输入错误, 程序结束.")
        break
```
