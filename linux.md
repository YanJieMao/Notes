

# 1.Linux简介

> 什么是Linux?

Linux是目前应用最广泛的服务器操作系统，基于Unix，开源免费，由于系统的稳定性和安全性，市场占有率很高，几乎成为程序代码运行的最佳系统环境。

Linux不仅可以长时间的运行我们编写的程序代码，还可以安装在各种计算机硬件设备中，如手机、路由器等，Android程序最底层就是运行在Linux系统上的。

## 1.1linux的目录结构

![img](/img/linux1.png)

以下是对这些目录的解释：
- /bin： bin是Binary的缩写, 这个目录存放着最经常使用的命令。
- /boot： 这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。（不
要动）
- /dev ： dev是Device(设备)的缩写, 存放的是Linux的外部设备，在Linux中访问设备的方式和访问
文件的方式是相同的。
- /etc： 这个目录用来存放所有的系统管理所需要的配置文件和子目录。
- /home：用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账
号命名的。
- /lib： 这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。
（不要动）
- /lost+found： 这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。（存放
突然关机的一些文件）
- /media：linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备
挂载到这个目录下。
- /mnt：系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，
然后进入该目录就可以查看光驱里的内容了。（我们后面会把一些本地文件挂载在这个目录下）
- /opt：这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个
目录下。默认是空的。
- /proc： 这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获
取系统信息。（不用管）
- /root：该目录为系统管理员，也称作超级权限者的用户主目录。
- /sbin：s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。
- /srv：该目录存放一些服务启动之后需要提取的数据。
- /sys：这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统
sysfs 。
- /tmp：这个目录是用来存放一些临时文件的。用完即丢的文件，可以放在这个目录下，安装包！
ls /
- /usr：这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows
下的program files目录。
- /usr/bin： 系统用户使用的应用程序。
- /usr/sbin： 超级用户使用的比较高级的管理程序和系统守护程序。Super
- /usr/src： 内核源代码默认的放置目录。
- /var：这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录
下。包括各种日志文件。
- /run：是一个临时文件系统，存储系统启动以来的信息。当系统重启时，这个目录下的文件应该被
删掉或清除。
- /www：存放服务器网站相关的资源，环境，网站的项目

# 2.linux常用命令

## 2.1学会使用命令帮助

在linux终端，面对命令不知道怎么用，或不记得命令的拼写及参数时，我们需要求助于系统的帮助文档； linux系统内置的帮助文档很详细，通常能解决我们的问题，我们需要掌握如何正确的去使用它们；

- 在只记得部分命令关键字的场合，我们可通过man -k来搜索；
- 需要知道某个命令的简要说明，可以使用whatis；而更详细的介绍，则可用info命令；
- 查看命令在哪个位置，我们需要使用which；
- 而对于命令的具体参数及使用方法，我们需要用到强大的man；

> 使用man 查询命令的说明文档

```
eg: man ls
```

在man的帮助手册中，将帮助文档分为了9个类别，对于有的关键字可能存在多个类别中， 我们就需要指定特定的类别来查看；（一般我们查询bash命令，归类在1类中）；

man页面所属的分类标识(常用的是分类1和分类3)

```
(1)、用户可以操作的命令或者是可执行文件
(2)、系统核心可调用的函数与工具等
(3)、一些常用的函数与数据库
(4)、设备文件的说明
(5)、设置文件或者某些文件的格式
(6)、游戏
(7)、惯例与协议等。例如Linux标准文件系统、网络协议、ASCⅡ，码等说明内容
(8)、系统管理员可用的管理条令
(9)、与内核有关的文件
```

使用whatis会显示命令所在的具体的文档类别，我们学习如何使用它

```
eg:
$whatis printf
printf               (1)  - format and print data
printf               (1p)  - write formatted output
printf               (3)  - formatted output conversion
printf               (3p)  - print formatted output
printf [builtins]    (1)  - bash built-in commands, see bash(1)
```

我们看到printf在分类1和分类3中都有；分类1中的页面是命令操作及可执行文件的帮助；而3是常用函数库说明；如果我们想看的是C语言中printf的用法，可以指定查看分类3的帮助：

```
$man 3 printf

$man -k keyword
```

查询关键字 根据命令中部分关键字来查询命令，适用于只记住部分命令的场合；

eg：查找GNOME的config配置工具命令:

```
$man -k GNOME config| grep 1
```

> 查看路径

查看程序的binary文件所在路径:

```
$which command
```

eg:查找make程序安装路径:

```
$which make
/opt/app/openav/soft/bin/make install
```

查看程序的搜索路径:

```
$whereis command
```

当系统中安装了同一软件的多个版本时，不确定使用的是哪个版本时，这个命令就能派上用场；