---
title: "Visual Studio 中的 Python 交互式 REPL | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ca444dbe9fea25b205ae2060d462f23957368496
ms.lasthandoff: 04/10/2017

---

# <a name="working-with-the-python-interactive-window"></a>使用 Python 交互窗口

Visual Studio 为每个 Python 环境提供交互式读取-评估-打印-循环 (REPL) 窗口，改进了在命令行中运行 `python.exe` 获得的 REPL。 在交互窗口中（使用“视图”>“其他窗口”>&lt;环境&gt;交互窗口菜单命令打开），可以输入任意 Python 代码，并查看即时结果，从而帮助学习和实验 API，还可以使用交互方式开发要包括在项目中的工作代码。

![Python 交互窗口](~/python/media/interactive-window.png)

Visual Studio 有大量 Python REPL 模式可供选择：

| REPL | 描述 | 编辑 | 调试 | 图像 |
| --- | --- | --- | --- | --- |
| 标准 | 默认 REPL，直接与 Python 通信 | 标准编辑（多行等）。 | 是，通过 `$attach` | No |
| 调试 | 默认 REPL，与已调试的 Python 进程通信 | 标准编辑 | 仅调试 | No |
| IPython | REPL 与 IPython 后端通信 | IPython 命令，Pylab 的便利 | No | 是，在 REPL 中内联 |
| 带 Pylab 的 IPython | REPL 与 IPython 后端通信 | 标准 IPython | No | 是，单独窗口 | 

本主题介绍**标准** REPL 模式和**调试** REPL 模式。 有关 IPython 模式的详细信息，请参阅[使用 IPython REPL](interactive-repl-ipython.md)。

有关 Python 交互窗口的介绍，请观看 [Visual Studio 中的 Python 入门，第 5 部分：交互式 REPL](https://youtu.be/yc2CROtTsC0?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)（youtube.com，2 分 51 秒）。

> [!VIDEO https://www.youtube.com/embed/yc2CROtTsC0]

## <a name="opening-an-interactive-window"></a>打开交互窗口

以下有几种方法可用于针对某个环境打开交互窗口。

方法一，切换到 Python 环境窗口（“视图”>“其他窗口”>“Python 环境”或 Ctrl-K、Ctrl-'），然后针对选定的环境，选择“打开交互窗口”命令或按钮。

![Python 环境窗口中的交互窗口链接](~/python/media/interactive-window-opening.png)

方法二，“视图”>“其他窗口”中针对每个环境都具有**交互窗口**命令，通常显示在菜单底部附近：

![“视图”>“其他窗口”中的交互窗口菜单项](~/python/media/interactive-window-menu.png)

方法三，可以通过选择“调试”>“在 Python 交互窗口中执行 [项目 | 文件]”菜单命令 (Shift+Alt+F5)，打开项目中启动文件的交互窗口，或独立文件的交互窗口：

![在 Python 交互菜单中执行项目](~/python/media/interactive-execute-project.png)

最后，可以选中文件中的代码，然后如下所述，使用“将代码发送到交互命令”[](#send-code-to-interactive-command)命令。

## <a name="interactive-window-options"></a>交互窗口选项

你可以通过 Python 环境窗口中的“配置交互窗口”，或者通过“工具”>“选项”>“Python 工具”>“交互窗口”，控制交互窗口的各个方面：

![Python 交互窗口选项](media/interactive-window-options.png)

请注意，此外还有用于“调试交互窗口”的单独选项集，可在调试会话期间用于控制行为：

![Python 交互窗口调试选项](media/interactive-window-debug-options.png)

## <a name="using-the-interactive-window"></a>使用交互窗口

交互窗口打开后，可以在 `>>>` 提示符处逐行输入代码。 交互窗口将执行输入的每一行代码，包括导入模块、定义变量等。 如下图中的前两行所示：

![Python 交互窗口](~/python/media/interactive-window.png)

语句以冒号结束的情况除外（如上述的 `for` 语句），因为交互窗口知道该语句需要其他代码行，才可以正确执行代码块。 在这种情况下，行提示符将更改为 `...`，以指示需要输入程序块的其他行，如上图中的第四和第五行所示。 在空行上按 Enter 键时，交互窗口将关闭程序块，并在解释器中执行该程序块。

> [!Tip]
> 交互窗口通过自动缩进属于周边范围的语句，改进常用 Python 命令行的 REPL 体验。 其历史记录（使用向上键重新调用）还提供多行项，而命令行 REPL 仅提供单行。

交互窗口非常适合用于试用新库。 你可以导入该库，检查子包、类和函数。  Python 可以通过其 `help()` 函数告诉你所有相关信息。  此外，Visual Studio 中的 Python 支持会基于其编辑器中使用的代码建模为你提供建议和文档，这个过程无需执行库。  当实际执行代码时，Visual Studio 将根据 Python 运行时中的信息改进这些建议。  

<a name="meta-commands"></a>交互窗口还支持多个元命令。 所有元命令都以 `$` 开头，你可以键入 `$help` 获得元命令和 `$help <command>` 的列表，以获取特定命令的使用情况详细信息。

| 元命令 | 说明 |
| --- | --- |
| `$$` | 插入注释，用于注释会话中的代码。 |
| `$attach` | 将 Visual Studio 调试器附加到 REPL 窗口进程以启用调试。 |
| `$cls`, `$clear` | 清除编辑器窗口的内容，使历史记录和执行上下文保持不变。 |
| `$help` | 显示命令列表，或有关特定命令的帮助。 |
| `$load` | 从文件加载命令并执行，直到完成。 |
| `$mod` | 将当前范围切换为指定模块名称。 |
| `$reset` | 将执行环境重置为初始状态，但保留历史记录。 |
| `$wait` | 至少等待指定的毫秒数。 |

这些命令也可通过 MEF (Managed Extensibility Framework for .NET) 进行扩展。

## <a name="switching-scopes"></a>切换范围

默认情况下，项目交互窗口的范围为项目的启动文件，就像从命令提示符处运行一样。 对于独立文件，其范围为该文件。 但是，可随时使用交互窗口顶部的下拉列表菜单在 REPL 会话期间更改范围：

![交互窗口的范围](~/python/media/interactive-scopes.png)

导入模块后（如键入 `import os`），下拉列表中将显示可切换到该模块任意范围的选项。 交互窗口中还将显示指示新范围的消息，以便追踪会话期间如何达到某个特定状态。

在某个范围中输入 `dir()` 将显示该范围的有效标识符，包括函数名称、类和变量。 例如，使用 `$mod importlib` 后跟 `dir()` 将显示以下内容：

![Importlib 范围中的交互窗口](~/python/media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>
## <a name="send-code-to-interactive-command"></a>将代码发送到交互命令

除了直接在交互窗口中处理代码，还可以在编辑器中选中代码，单击右键，并选择“发送到交互”：

![发送到交互式菜单命令](~/python/media/interactive-send-to.png)

这非常适用于迭代或演化代码开发，包括在开发时测试代码。 例如，将一段代码发送到交互窗口并显示其输出后，可以按向上键再次显示代码、对其进行修改，并通过按 Ctrl + Enter 快速测试。 （在输入结束时按 Enter 将执行它，但在输入过程中按 Enter 将插入新行。）如果有需要的代码，可以轻松将其复制回项目文件。

你还可以选中代码，单击右键，然后选择“发送到定义模块”，用于搜索交互过程，以查找与当前正在编辑的文件相匹配的模块。 如果该命令找到正确的模块，它将使用 `$mod` 元命令切换到该模块（该操作将成为交互窗口会话历史记录的一部分），并将所选内容粘贴到交互窗口进行评估。 这简化了在编辑器中复制代码、在交互窗口中切换范围以及手动粘贴的过程。

## <a name="intellisense-behavior"></a>IntelliSense 的行为

与代码编辑器中 IntelliSense 仅基于源代码分析不同，交互窗口中，IntelliSense 基于活动的对象。 这使得交互窗口中的建议正确率更高，尤其是在使用动态生成代码的情况下。 缺点是有副作用（如记录消息）的函数可能会影响开发体验。

如果这造成了困扰，请在“完成模式”组的“工具”>“选项”>“Python 工具”>“交互窗口”下更改设置：

- **永不评估表达式**：使用普通 IntelliSense 引擎提供建议。
- **永不评估包含调用的表达式**（默认）：评估简单表达式（如 `a.b`），但对于涉及调用的表达式（如 `a().b`）则使用普通引擎。
- **始终评估表达式**：执行完整的表达式以获取建议，无论其是否可能产生副作用。
