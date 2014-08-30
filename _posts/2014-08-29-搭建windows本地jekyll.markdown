---
layout: post
title:  "搭建windows本地jekyll"
date:   2014-08-29 08:42:45
categories: IT
---
jekyll可以运行在github page上，理论上不需要在本地搭建jekyll。做这样的事是为了调试方便（也就是折腾）。

这个过程在windows下有些繁琐。下面写一下步骤：

首先在官网下载ruby2.0.0版本。安装时主义要选上“add Ruby executables to your PATH”，以便可以在命令行里运行ruby命令。

其次在官网下载DevKit-mingw64，这是对应于ruby2.0.0的Ruby Devkit。别问我这是什么东西，我不懂。。下载下来是个解压缩包，双击解压到一个任意位置都可以。比如C:\RubyDevKit\
然后我们打开一种命令行（比如cmd或者git bash），依次执行：
{%highlight bat %}
cd C:\RubyDevKit\
ruby dk.rb init
ruby dk.rb install
{%endhighlight%}
然后不出意外的话，ruby这边就安装好了。

然后通过ruby gem安装jekyll，代码如下：
{%highlight bat %}
gem install jekyll
{%endhighlight%}

ok 然后问题就出现了，你会发现敲完这段代码，你等半天，结果却很可能是下载失败。这就是我国的特色了，你懂的~好在淘宝是大好人，去[这个网站](http://ruby.taobao.org/)上看看，就知道怎么解决了~

然后我们要安装高亮代码的东西pygments。可恶，这东西是用python写的，所以我们必须安装python。到官网去下载，注意不要下载3.x，要下载2.x。我下载的是v2.7吧。安装时同样不要忘了选择把它加进Path。然后下载get-pip.py，在[这里](https://pip.pypa.io/en/latest/installing.html) 。比如把它放到C:\pip\

然后我们执行
{%highlight bat %}
cd C:\pip
python get-pip.py
python -m pip install Pygments
{%endhighlight%}
就安装好了。

但是这时使用jekyll还是会报错，会提示yajl调用失败，这个问题可能是windows的原因。[这个](https://github.com/Gentoo-zh/todo/issues/1)和[这个](https://github.com/brianmario/yajl-ruby/issues/116)就是讨论这个问题的。我们按照这里提供的方法来解决：
首先卸载已有的yajl-ruby
{%highlight bat %}
gem uninstall yajl-ruby
{%endhighlight%}
如果给了你好几个版本，问你卸载哪个，就选全卸载。

然后执行下面代码，重新安装指定版本的yajl-ruby:
{%highlight bat%}
gem install yajl-ruby -v 1.1.0 --platform=ruby
{%endhighlight%}

这样的话就安装好了，虽然使用jekyll时会有警告，但是应该不影响使用。

然后下面列一份相关的网址资料，挺有用的觉得：

[http://www.360doc.com/content/12/0421/09/1016783_205350218.shtml](http://www.360doc.com/content/12/0421/09/1016783_205350218.shtml)这里有很多资源
[http://havee.me/internet/2013-08/support-pygments-in-jekyll.html](http://havee.me/internet/2013-08/support-pygments-in-jekyll.html)这里介绍了关于语法高亮显示的东西
[http://pygments.org/docs/lexers/](http://pygments.org/docs/lexers/)这里是pygments官网提供的语言缩写

[http://jekyllcn.com/](http://jekyllcn.com/)jekyll官网中文版

大概就这样吧~

