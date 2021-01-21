



-------

记WSL中Vim与Windows剪切板通信的问题：

在WSL中的Vim中，其复制的内容在Vim的寄存器中，而不是在系统的剪切板上，所以在与Windows进行互相复制粘贴时很麻烦，那么我在搜索网络资料的过程中看到了一个[教程](https://blog.csdn.net/weixin_45901207/article/details/106659919)：

1. 首先查看本机中Vim是否支持剪切板

```vim
vim --version | grep clipboard
```

如果显示结果中 *clipboard* 前为 - ，则代表不支持，此时需要使用命令来安装，即：

```vim
sudo apt-get install vim-gtk
```

等待安装完毕后，再次检查就会发现 *clipboard* 前为 +。

由于在Windows中的复制和粘贴依赖于clip.exe和paste.exe，但系统中仅仅自带了clip.exe，此时需要[下载paste.exe](https://www.c3scripts.com/tutorials/msdos/paste.zip)，下载完毕后将其放置在路径为 **C:/Windows/System32** 目录下。

之后进入vimrc配置文件中配置映射：

```vim
map ;y :!/mnt/c/Windows/System32/clip.exe <cr>u                      
map ;p :read !/mnt/c/Windows/System32/paste.exe <cr>i<bs><esc>l      
map! ;p <esc>:read !/mnt/c/Windows/System32/paste.exe <cr>i<bs><esc>    l
```

配置完成后，使用 ;y 和 ;p 来进行复制和粘贴即可。