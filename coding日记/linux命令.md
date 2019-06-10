

#### Linux最常用的20条命令https://blog.csdn.net/ljianhui/article/details/11100625

##### linux命令会出现[],<>,|等符号，它们的含义如下： 

[] 表示是可选的; 
<> 表示是可变化的; 
x|y|z 表示只能选择一个; 
-abc 表示三个参数(或任何二个)的混合使用

| -moveFromLocal | -moveFromLocal <多个linux上的文件> <hdfs路径>                | 从本地移动     |
| -------------- | ------------------------------------------------------------ | -------------- |
| -getmerge      | -getmerge <源路径> <linux路径>                               | 合并到本地     |
| -cat           | -cat <hdfs路径>                                              | 查看文件内容   |
| -text          | -text <hdfs路径>                                             | 查看文件内容   |
| -copyToLocal   | -copyToLocal [-ignoreCrc] [-crc] [hdfs源路径] [linux目的路径] | 从本地复制     |
| -moveToLocal   | -moveToLocal [-crc] <hdfs源路径> <linux目的路径>             | 从本地移动     |
| -mkdir         | -mkdir <hdfs路径>                                            | 创建空白文件夹 |

#### Linux权限和权限的修改 :

 **chmod     [{ugoa}{+-=}{rwx}]      [文件或目录]**

  **chmod   -R    [mode=421]     [文件或目录]**

详情：https://blog.csdn.net/jerrytomcat/article/details/81744860

Linux如何查看端口

1、lsof -i:端口号 用于查看某一端口的占用情况，比如查看8000端口使用情况，lsof -i:8000

netstat -tunlp 

netstat -tunlp |grep 端口号，用于查看指定的端口号的进程情况，如查看8000端口的情况，netstat -tunlp |grep 8000

**netstat -nltp|grep 9000查看9000端口是否处于监听状态**



进程

 ps -ef    ps -aux

 kill -s 9 1827 -

其中-s 9 制定了传递给进程的信号是９，即强制、尽快终止进程。各个终止信号及其作用见附录。

使用pgrep：

一看到pgrep首先会想到什么？没错，grep！pgrep的p表明了这个命令是专门用于进程查询的grep。

$ pgrep firefox
1827

看到了什么？没错火狐的PID，接下来又要打字了：



linux软件的安装与下载： http://www.cnblogs.com/shijiaqi1066/p/3843955.html

Linux分两个系列：

一般来说著名的 Linux 系统基本上分两大类：

1. RedHat 系列：Redhat、Centos、Fedora 等
2. Debian 系列：Debian、Ubuntu 等

Dpkg (Debian系)：Ubuntu 
RPM (Red Hat系)：CentOS、Fedora

|      | RedHat 系列                                                  | Debian 系列                                                  |
| ---- | :----------------------------------------------------------- | ------------------------------------------------------------ |
|      | rpm（麻烦不用，用下面的）                                    | dpkg(alien 可处理.deb、.rpm、.slp、.tgz 等档案格式, 进行转档或安装. 于Debian安装非Debian套件时,可使用alien进行安装. 安装alien套件: apt-get install alien) |
|      | **yum**；**就用这个**  YUM客户端基于RPM包进行管理，可以通过HTTP服务器下载、FTP服务器下载、本地软件池的等方式获得软件包，可以从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系。YUM在安装RPM时，会从服务器下载相应包，且缓存在本地。使用YUM进行RPM包的管理，非常简单方便。 | **apt-get(现在流行apt)**                                     |
|      |                                                              |                                                              |

​          

```
Yum（全称为 Yellow dog Updater, Modified）是一个在Fedora和RedHat以及SUSE中的Shell前端软件包管理器。
基於RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软体包，无须繁琐地一次次下载、安装。简言之个人觉得yum比较好用。
```

（1）wget不是安装方式 他是一种下载软件类似与迅雷 如果要下载一个软件 我们可以直接 wget 下载地址。

（2）apt-get是ubuntu下的一个软件安装方式，它是基于debain。

（3）yum是redhat、centos下的一个软件安装方式，它是基于Linux的。

二、（1）wget 类似于迅雷，是一种下载工具，通过HTTP、HTTPS、FTP三个最常见的TCP/IP协议下载，并可以使用HTTP代理名字是World Wide Web”与“get”的结合。
（2）yum: 是redhat, centos 系统下的软件安装方式，基于Linux，全称为 Yellow dog Updater, Modified，是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。
（3）rpm:  软件管理;   redhat的软件格式 rpm     r=redhat  p=package   m=management；用于安装 卸载 .rpm软件
（4）串联下：
   使用wget下载一个 rpm包, 然后用 rpm -ivh  xxx.rpm  安装这个软件，嫌麻烦的话，就
   可以直接用  yum  install  sqoop   来自动下载和安装依赖的rpm软件。

   ap-get是ubuntu下的一个软件安装方式，它是基于debain。

yum可以用于运作rpm包，例如在Fedora系统上对某个软件的管理：
安装：yum install <package_name>
卸载：yum remove <package_name>
更新：yum update <package_name>
apt-get可以用于运作deb包，例如在[Ubuntu系统](https://www.baidu.com/s?wd=Ubuntu%E7%B3%BB%E7%BB%9F&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)上对某个软件的管理：
安装：apt-get install <package_name>
卸载：apt-get remove <package_name>
更新：apt-get update <package_name>



#### 软件安装 ./configure 、make、make install

./configure是源代码安装的第一步，主要的作用是对即将安装的软件进行配置，检查当前的环境是否满足要安装软件的依赖关系，但并不是所有的tar包都是源代码的包，楼主可以ls看看有没有configure这个文件，也许你下的是二进制的包，如果是二进制的包，解压后直接就能使用

你先ls，看有没有configure或者makefile文件。
如果有configure，就./configure，有很多参数。如果系统环境合适，就会生成makefile，否则会报错。
如果有makefile，就直接make，然后make install。
**你还可以用rpm或者deb包来安装。而且现在的发行版都有自己的包管理器，比如apt或yum，一个命令就可以从源下载软件，还可以自动解决依赖问题。**

yum --help 

yum search java | grep jdk