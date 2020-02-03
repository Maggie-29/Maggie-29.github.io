# Anaconda安装教程

## 1. 到[anaconda官网](https://www.anaconda.com/distribution/)下载适配自己电脑系统的安装程序

![anaconda web page](/Users/test/Maggie-29.github.io/install anaconda/anaconda web page.png)

目前anaconda支持的系统有：windows、Mac OS、Linux

这里我们下载Python 3.7 version



https://link.jianshu.com/?t=https%3A%2F%2Fdocs.anaconda.com%2Fanaconda%2Finstall%2Fmac-os)



用户名不能是中文 如果是中文如何修改

浏览器 杀毒软件

zsh模式下装anaconda



2、路径配置

按官方教程安装好之后，Anaconda的路径已经被配置到了 `.bash_profile` 中，不过由于我使用的是 zsh，所以需要手动将 Anaconda 路径配置到 zsh 的配置文件中。

做法就是，将 Anaconda 的路径 export 到 .zshrc 文件中。这样每次启动 zsh 终端时候都会自动从 .zshrc 文件中读取配置信息。

![img](https:////upload-images.jianshu.io/upload_images/5214592-5c1b2320fdd58382.png?imageMogr2/auto-orient/strip|imageView2/2/w/762)

开发Web-APP需要使用python3，将Mac自带bash更新为oh my zsh之后，shell没有重启之前输入python3可以进入python，但是重启shell之后，输入“python3”，shell显示：

zsh: command not found: python3

[原链接](https://blog.csdn.net/liuhui_1211/article/details/79439137)
究其原因，认为是Anaconda的路径没有加入导致。

但事实上，在安装Anaconda时，该路径已经自动加上了。

但作为尝试，手动再次将该路径加入，输入：

echo 'export PATH="/Users/liuhui/anaconda3/bin:$PATH"'>>~/.zshrc #zsh

其中，/Users/liuhui/anaconda3/ 为安装anaconda3的绝对路径。

之后，在shell中输入

source ~/.zshrc #zsh