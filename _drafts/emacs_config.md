-------------------------------------------------------------------------------

## emacs初始化

1. 在用户文件夹下寻找.emacs文件并加载；
2. 如果没有找到，在~/.emacs.d/下寻找init.el并加载；

emacs继承了系统的环境变量，使用`M-x getenv PATH`可以获得系统的环境变量。

-------------------------------------------------------------------------------

## emacs的加载方式

一般来说，在网上下载了新的插件（即*.el文件）后，需要使用load进行加载，但是某些大型的插件甚至需要写更复杂的脚本才能够使用。而Emacs24以上都集成了一个插件管理器`elpa`，使用`M-x list-packages`可以查看已经被加载的了插件。

而`elpa`一般需要几个步骤：`load`，`require`，`autoload`等。

1. `load`：加载文件。即运行一个文件内部的Lisp代码（在load-path中），并将执行结果返回至Emacs环境中；
2. `feature`：功能。插件启动的结尾会有`provide 'feature_name`，提供一个可被使用的插件的名称；
3. `require`：包含。`require 'feature_name`查看功能列表中是否存在feature_name的功能，并包含到Emacs环境中。但是如果不存在列表中的话，Emacs会去寻找与其相同名称的文件，并且`load`该文件。如果文件也不存在的话，就会报错。

但是一次性将所有的文件全部加载好，并不是一个好的选择。这样每次打开Emacs的时候，都会执行过多的代码。所以可以使用`autoload`进行预加载。相当于告诉Emacs在某个地方存在这样一个函数，当需要使用的时候再去加载。

-------------------------------------------------------------------------------

## 参考文档

[从零开始——Emacs 安装配置使用教程 2015](http://www.jianshu.com/p/b4cf683c25f3)
