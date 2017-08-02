---
title: "使用针对 Visual Studio 的 R 工具进行调试 | Microsoft Docs"
ms.custom: 
ms.date: 5/1/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb5fe5f8-03bc-42bf-8346-c845036a9c6c
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 01bc916eb656cb8e24279498b7b0236fb8eb0e80
ms.contentlocale: zh-cn
ms.lasthandoff: 05/12/2017

---


# <a name="debugging-r-in-visual-studio"></a>在 Visual Studio 中调试 R

针对 Visual Studio 的 R 工具 (RTVS) 与 Visual Studio 的完整调试体验（请参阅 [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md)（在 Visual Studio 中调试））集成，包括断点、附加至运行的进程、检查并监视变量、检查调用堆栈等。 本主题随后探讨了 R 和 RTVS 独有的调试属性。

在 R 项目中启动 R 启动文件的调试器与启动其它项目类型的调试器相同：使用“调试”>“启动调试”，按 F5 键，或选择调试工具栏上的“源化启动文件”，如下所示。 要更改启动文件，请右键单击解决方案资源管理器中的文件，并选择“设置为启动 R 脚本”。

![R 的调试器启动按钮](~/rtvs/media/debugger-start-button.png)

在所有情况下，启动调试器都会在交互窗口中“源化”文件，这意味在该处加载并运行文件。 实际上，在开始调试后，可以在交互窗口中看到如下所示的输出：

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

可以看到，使用的是 `rtvs::debug_source` 函数来源化脚本。 必须进行此操作，因为 RTVS 需要修改代码，为调试做准备。 如果要使用任意 RTVS 命令（例如，通过右键单击解决方案资源管理器中的某个文件，运行“源化选定的文件”命令），并且已附加调试器，调用将自动重定向到 `rtvs::debug_source`。

也可以使用“R 工具”>“会话”>“附加调试器”命令、“调试”>“附加到 R 交互”命令或交互窗口的工具栏中的“附加调试器”命令，直接从交互窗口附加调试器。 进行此操作后，需要由你来源化要调试的文件。 如果要手动源化文件，请务必在 R 中使用 `rtvs::debug_source` 而非常规的 `source` 命令。在_某些_情况下，此命令可以起作用，但我们无法保证调试在所有情况下都成功，除非使用 `rtvs::debug_source` 命令。

调试器与交互窗口之间的此连接简化了使用不同参数值调用（和调试）函数等操作。 例如，假设源化文件中有如下所示的函数（意味着文件已加载到会话中）：

```R
add <- function(x, y) {
    return(x + y)
}
```

然后，在 `return` 语句中设置一个断点。 现在，在交互窗口中，如果输入 `add(4,5)`，则将看到调试器在断点处停止。


## <a name="environment-browser-in-the-interactive-window"></a>交互窗口中的环境浏览器

在调试器中停止时，还会在[交互窗口](interactive-repl.md)中的环境浏览器提示符处停止。 提示符显示为 `Browse[n]>`，其中 n 是一个数字。

环境浏览器支持若干特殊命令：

| 命令 | 描述 | 
| --- | --- |
| n | 下一个：运行代码文件中的下一个语句（与逐步执行相同）。 |
| 秒 | 单步执行：运行代码文件中的下一个语句，如果下个一语句是函数调用，则单步执行函数范围。 | 
| f | 完成：运行当前函数范围的剩余部分，并返回到调用方（与跳出相同）。 |
| c, cont | 继续：运行程序，直至到达下一个断点。 | 
| Q | 退出：结束调试会话。 |
| 其中 | 显示堆栈：在交互窗口中显示调用堆栈。 |
| 帮助 | 显示帮助：在交互窗口中显示可用命令。 |
| &lt;expr&gt; | 在 expr 中计算表达式。 |

![交互窗口中的环境浏览器](~/rtvs/media/debugger-environment-browser.png)

