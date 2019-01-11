
### Termux初始配置

首先，在Termux中从左向右滑动左边屏幕，出现白色侧栏，长按下方keyboard唤出特殊键。将出现的特殊键一栏向左滑，开启中文输入(严格来说是以词为单位的输入)。

然后把man装上……

```shell
pkg up; pkg in man
```

Bash来自GNU project，是大多数Linux发行版和Termux的默认Shell。也就是你正在使用的shell(应该是这样:D)

查看一下bash的使用手册

```shell
man bash
```
按`q`可以退出。

你可能意识到了，Linux的传统是将手册和应用包打包在一起。用man可以阅读用户手册。

```shell
man -k editor
#从所有手册中查找简介中有editor这个词的手册
---------------------
emacs(1) - GNU project Emacs editor
sed(1) - stream editor for filtering and transforming text
zshzle(1) - zsh command line editor
----------------------
```

这里的(1)是man手册的章节编号。假如我要阅读emacs(1)，我应该
```shell
man 1 emacs
```
不同章节的主题不同。
```
(1) -用户命令
(2) -系统调用
(5) -配置文件
……… #略过部分章节
(6) -游戏 #基本没有:D
(8) -系统命令与服务器
```

但有时我们只想简单的查看一下命令行选项，例如怎么都记不住选项的`tar`。那么`cheat`可以帮到你。

```shell
pkg in python -y
pip install cheat
```

运行一下试试看吧！

```shell
cheat tar | less
#依然按q退出
```

再也不用为tar发愁喽！

然而，有些工具，例如`termux-create-package`，它没有自带的man手册。别急，让我们执行一条命令。

```shell
pkg sh termux-create-package

---------------------------
Package: termux-create-package
Version: 0.7
Maintainer: Fredrik Fornwall @fornwall
Installed-Size: 36.9 kB
Depends: python
Homepage: https://github.com/termux/termux-create-package
Download-Size: 2880 B
APT-Sources: https://termux.net stable/main all Packages
Description: Utility to create Termux packages
-----------------------------
#快看，有homepage!
```

有homepage就有帮助可看了!

```shell
pkg sh termux-create-package 2> /dev/null | grep Homepage | awk '{print $2}' | xargs -I'{}' termux-open-url '{}'
```

浏览器将打开`termux-create-package`的[homepage](https://github.com/termux/termux-create-package)，看完你会发现，这是一个打包用的帮助脚本。

如果你想查看任意命令的帮助,例如ps(process scanner)，运行

```shell
ps -h

#或者
ps --help

#总有一个是对的
```
texinfo是另一个文档系统.

```
pkg in texinfo -y
```

```
info emacs
```

github,stackoverflow,Archwiki,termuxwiki都是很好的文档查找地点。搜索引擎尽可能使用google(把cookie关上)，当然也有很多地方可以找到在线帮助。

### 更换Zsh

```shell
pkg in git make -y
git clone https://github.com/myfreess/Tzim \
	~/Tzim
cd ~/Tzim
make zim
```

zsh拥有众多强大的特性，例如补全、Dirstack等，不过,read -p在zsh上无用，还有zsh的中文文档太少。

### Emacs与vi

```shell
pkg in vim emacs -y
```

`vi`是Unix上的传统文本编辑器,很多人是vi的狂热粉丝，但显而易见，一般Termux用户平时也用不上几次。所以别为vi配置头疼了，快来用`micro`吧。

Emacs就有意思多了，它是用`EmacsLisp`和`C`编写的，那些键绑定对应的是一个个ELisp函数,而配置文件压根就是个EmacsLisp脚本。也就是说，要学会使用Emacs，必须学会ELisp。

建议:

+ 对尚未学习过CLI的Termux用户来说，Termux很不好用。若你并没有使用过Linux发行版，你可能会需要几份简明的帮助手册.

e.g

https://i.linuxtoy.org/docs/guide/ch17.html

http://billie66.github.io/TLCL/book

https://github.com/me115/linuxtools_rst

+ 这里有一本大而全的中文Linux手册:http://cn.linux.vbird.org/

+ Bash常见陷阱:

