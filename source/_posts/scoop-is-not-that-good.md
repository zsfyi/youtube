---
title: Scoop 并没有那么好
date: 2019-12-27 19:53:59
tags:
  - Scoop
  - 利器
  - 软件
---

了解过 Scoop 的想必在不少网站上看过介绍它的文章，其中「少数派」就有三篇。但是，这些文章几乎都是赞美，很少有指出其缺点的。

<!-- more -->

在 Linux 上有 APT、Yum、Pacman 等，macOS 上有 Homebrew，而 Windows 上一直缺少一个像样的包管理器。正如 Scoop 的 slogan 所讲「A command-line installer for Windows」，它在很大程度上确实扛起了这一重担，通过命令行这种 cool & sexy 方式就可以完成软件的搜索、安装、升级、卸载，甚至可以在软件的不同版本之间切换。

很多时候，尤其是跟开发有关的，我不仅需要安装一个软件，还需要一个工具帮我管理 path。也就是说，当涉及到需要 path 或环境变量的时候，我会非常乐于使用 Scoop 去做，它提供了一套自动化的方法来帮我们完成这项乏味的工作，这是 Scoop 带给我们最大的价值。

但，我觉得它还是不够好。

下面就我通过 Scoop 安装的软件，挑出一些来讲在哪些方面存在缺点。

首先是 7-Zip，这应该算是 Scoop 上除了 aria2、git 之外必装的软件，毕竟都需要解压这一过程。那通过 Scoop 安装的 7-Zip 与手动安装的有什么区别呢？首先先明确，因为 Scoop 不会写入注册表，所以 7-Zip 的一些常用快捷功能如提取和压缩文件不会自动集成到鼠标右键，需要打开软件进行手动设置。这番操作下来，像这种小软件，我还不如直接手动下载安装文件进行安装。

再来说说 vscode（Visual Studio Code）。同样是因为不写注册表（似乎有点成也萧何败也萧何的感觉了），在 Scoop 中安装完 vscode 后不会自动关联 `.py`、`.js`、`.go`、`.md` 等文件类型。当你想要打开如 `demo.py` 时，如果之前没有用 vscode 打开过 Python 文件，不好意思先得选择用哪个软件打开，而且很有可能还得一层层找到 vscode 的安装目录才行。虽然这些都是一次性的工作，但这样下来 Scoop 似乎并没有带来多大的幸福感。

其次再来说说 R 和 RStudio，后者的使用是要基于前者的。~~通过 Scoop 安装的 R 由于安装目录并没有在预设的「标准目录」，所以当启动 RStudio 时它会很困惑，你说你已经安装了 R 可是为啥我找不到哩……于是，我们又得手动为它指定 R 的安装目录。~~<mark>更正</mark>：其实使用 Scoop 安装更简单，直接 `scoop install rstudio` 便会依次为你安装 R 和 RStudio，rtools 也可以用 Scoop 安装。

这算是我目前使用不长的时间内发现的槽点，它为我们省去了一些工作，但同时又把一些原本软件安装过程中可以自动完成的事非让我们手动来做。我觉得 Scoop 适合用来安装像 aria2、curl、sudo 等工具，其他的像 Docker 等需要 UAC 提权或者需要写注册表的软件和许多 GUI 程序都不太适合（7-Zip 我觉得也要手动再安装一个，或者其他解压缩软件）。

再谈到它的 slogan，Scoop 其实只是一个 installer，我们不应把它当成像 pacman 一样的包管理器，用于掌管万物。根据自己的使用习惯，将其用来维护一些开发工具和小众软件（如 pandoc 这类没有自动更新功能的工具，以及另一些只能提示更新但不能自动更新的软件）即可。或许，可以将两者结合起来，一个 `scoop home [软件名]` 如 `scoop home 7zip` 轻松唤起浏览器并打开软件主页，手动下载安装完事，Scoop 深藏功与名。