---
title: "衡量 Visual Studio 中 Python 代码的性能 | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 2511f1076450848dfc75584edc97950fd4279c7b
ms.lasthandoff: 03/10/2017

---

# <a name="profiling-python-code"></a>分析 Python 代码

使用基于 CPython 的解释器时，Visual Studio 支持分析 Python 应用程序。

通过“分析”>“启动 Python 分析”菜单命令（这将打开配置对话框）开始分析：

![分析配置对话框](media/profiling-start.png)

选择“确定”后，探查器将运行并打开性能报告，通过此报告可以了解在应用程序中所用的时间：

![分析性能报告](media/profiling-results.png)

有关概述，请参阅以下内容

有关演练演示，请参阅[使用针对 Visual Studio 的 Python 工具进行分析](http://www.youtube.com/watch?v=K-KqkFkp55k)视频（8 分&52; 秒）。

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>IronPython 的分析

由于 IronPython 不是基于 CPython 的解释器，因此上述分析功能不会正常运行。

请通过直接启动 `ipy.exe` 作为目标应用程序并使用适当的参数来启动你的启动脚本，从而改用 Visual Studio.NET 探查器。 在命令行上包含 `-X:Debug`，强制所有 Python 代码可进行调试和分析。 这会生成一个性能报告，其中包括在 IronPython 运行时和代码中所用的时间。 代码使用重整名称进行标识。

另外，IronPython 本身内置某些分析功能，但目前没有适合的可视化工具。 请参阅 [IronPython 探查器](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx)（MSDN 博客）查看可用内容。
