---
title: "使用针对 Visual Studio 的 Python 工具进行混合模式调试的符号 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>安装用于 Python 解释器的调试符号

若要提供完整的调试体验，针对 Visual Studio 的 Python 工具 (PTVS) 中的[混合模式调试器](debugging-mixed-mode.md)需要分析正在使用的 Python 解释器内的大量内部数据结构。 这需要解释器本身的调试符号。 例如，python27.dll 对应的符号文件是 python27.pdb。

当 PTVS 检测到它需要符号时，它会提示你指向包含符号文件的文件夹或下载它们：

![混合模式调试过程中的符号提示](media/mixed-mode-debugging-symbols-required.png) 

如下所述，可从[正式分发](#official-distribution)或 [Enthought Canopy](#enthought-canopy) 下载符号文件。 如果使用 ActiveState Python 等第三方 Python 分发，你需要联系该分发的作者并请求他们为你提供符号。 （但是，WinPython 采用了未做更改的标准 Python 器，因此请使用正式分发的符号来表示相应的版本号。）

如下所示，获得解释器的 .pdb 文件后，你将使 PTVS 注意到它们，以便在启动调试会话时自动加载它们：

1. 选择“工具”>“选项”菜单命令，然后导航至“调试”>“符号”：

![混合模式调试器符号选项](media/mixed-mode-debugging-symbols.png)

1. 选择工具栏上的“添加”按钮（如上所示最左侧的按钮，位于 ！ 图标 右侧），导航到包含 .pdb 文件的文件夹，然后选择“确定”。


## <a name="official-distribution"></a>正式分发

使用 Python 3.5 及更高版本时，可以通过安装程序（通过新的安装或修改现有安装）包括调试符号。 选择“自定义安装”，选择“下一步”以转到“高级选项”，然后选择“下载调试符号”**复选框，然后选择“下载调试二进制文件”**：

![Python 3.x 安装程序包含调试符号](media/mixed-mode-debugging-symbols-installer35.png)

对于 Python 3.4.x 和早期版本，符号均以可下载的 .zip 文件提供。 下载后，请将这些文件提取到文件夹，然后安装上一节中的说明注册到 PTVS。

| Python 版本 | 下载 | 
| --- | --- | 
| 3.4.4 | [32 位](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 位](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 位](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 位](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 位](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 位](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 位](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 位](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 位](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 位](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 位](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 位](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 位](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 位](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 位](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 位](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 位](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 位](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 位](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 位](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 位](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 位](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 位](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 位](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 位](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 位](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 位](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 位](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 位](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 位](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 位](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 位](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 位](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 位](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 位](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 位](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 位](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 位](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 位](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy provides 从版本 1.2 开始为其二进制文件提供符号。 如之前所述，这些符号将自动与分发一起安装，但你仍需向符号路径手动添加包含这些符号的文件夹。 若 Canopy 采用典型的按用户安装，对于 64 位版本，符号位于 `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts`，对于 32 位版本，符号位于 `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts`。

Enthought Canopy 1.1 及早期版本，以及 Enthought Python 分发 (EPD) 不提供解释器符号，因此不兼容混合模式调试。
