# PA0

## Installing GNU/Linux







## First Exploration with GNU/Linux





## Installing Tools

​	在安装完操作系统后需要对网络的连通性进行一下测试，可以使用Ping操作测试是否与互联网连通。

```linux
ping mirrors.tuna.tsinghua.edu.cn -c 4
```

​	之后先给Linux配置清华源：

```linux
bash -c 'echo "deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stable main" > /etc/apt/sources.list'
```

​	从配置的清华源中更新资源：

```linux
apt-get update
```

​	下载ICS相关工具：

```linux
apt-get install build-essential    # build-essential packages, include binary utilities, gcc, make, and so on
apt-get install man                # on-line reference manual
apt-get install gdb                # GNU debugger
apt-get install git                # revision control system
apt-get install libreadline-dev    # a library to use compile the project later
apt-get install libsdl2-dev        # a library to use compile the project later
apt-get install libc6-dev-i386     # a library to use compile the project later
apt-get install qemu-system        # QEMU
```

## Configuring vim

​	在Ubuntu-20.04中，Vim是内置的，所以不需要进行安装，直接使用即可。对于Vim的基本使用，我参看了内置的***vimtutor***（可以看记录的vimtutor笔记），对着里面的例子进行了练习，算是入门了? 但我暂时还没感觉到Vim被成为“编辑器之神”的原因，可能后面就会感觉到了把...2333。

​	目前看来，vim留给我的感觉就是一个非图形化的编辑器，其可扩展性和自定义性比较强，感觉不需要鼠标的操作就可以完成文本的编辑。不过对于具体的使用，还需要慢慢的尝试和琢磨。

## More Exploration

​	对于这一小节，老师在Gitbook中写的很清楚。

> Learn to use ***man***, learn to use everything.

​	上面明确说了，对于man来说RTFM是STFW的长辈，man相当于一个官方文档，大部分linux的基本操作在其中都可以找到相关解释。

​	在这一小节中，我也在Ubuntu中装了tmux，它就是一个在linux下的多窗口工具，用起来比较方便。多数命令都可以在man中查到。

- **在WSL2中Ubuntu-20.04下的Vim与Windows剪切板通信的坑**

​	在WSL2下的Vim中，其复制的内容在Vim的寄存器中，而不是在系统的剪切板上，所以在与Windows进行互相复制粘贴时很麻烦，那么我在搜索网络资料的过程中看到了一个[教程](https://blog.csdn.net/weixin_45901207/article/details/106659919)：

​	首先查看本机中Vim是否支持剪切板

```vim
vim --version | grep clipboard
```

​	如果显示结果中 *clipboard* 前为 - ，则代表不支持，此时需要使用命令来安装，即：

```vim
sudo apt-get install vim-gtk
```

​	等待安装完毕后，再次检查就会发现 *clipboard* 前为 +。

​	由于在Windows中的复制和粘贴依赖于clip.exe和paste.exe，但系统中仅仅自带了clip.exe，此时需要[下载paste.exe](https://www.c3scripts.com/tutorials/msdos/paste.zip)，下载完毕后将其放置在路径为 **C:/Windows/System32** 目录下。

​	之后进入vimrc配置文件中配置映射：

```vim
map ;y :!/mnt/c/Windows/System32/clip.exe <cr>u                      
map ;p :read !/mnt/c/Windows/System32/paste.exe <cr>i<bs><esc>l      
map! ;p <esc>:read !/mnt/c/Windows/System32/paste.exe <cr>i<bs><esc>    l
```

​	配置完成后，使用 ;y 和 ;p 来进行复制和粘贴即可。

## Getting Source Code for PAs









