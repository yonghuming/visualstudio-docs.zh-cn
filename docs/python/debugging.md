---
title: "在 Visual Studio 中调试 Python | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2192dc77-b5da-4332-b753-fa20f03f81e0
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: e15edc1f2739cad0960619aa6cb4b089589eebd8
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---

# <a name="debugging-your-python-code"></a>调试 Python 代码

Visual Studio 提供全面的 Python 调试体验，包括附加到正在运行的进程，在监视窗口和即时窗口中计算表达式，检查局部变量、断点、单步执行/单步跳出/单步跳过语句、设置下一语句等。 

有关调试概述，请参阅[PTVS 入门，第 4 部分：调试](https://youtu.be/bO7wpzgy74A?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)（youtube.com，3 分 30 秒）。

> [!VIDEO https://www.youtube.com/embed/bO7wpzgy74A]

在本主题中：

- [基础调试](#basic-debugging)
- [项目调试选项](#project-debugging-options)
- [调试交互窗口](#the-debug-interactive-window)

另请参阅以下情景特定的调试主题：

- [跨平台远程调试](debugging-cross-platform-remote.md)
- [Azure 远程调试](debugging-azure-remote.md)
- [Python/C++ 混合模式调试](debugging-mixed-mode.md)
- [混合模式调试的符号](debugging-symbols-for-mixed-mode.md)

<a name="debugging-without-a-project"</a>
> [!Tip]
> Visual Studio 中的 Python 支持不含项目进行调试。 打开独立的 Python 文件后，在编辑器中单击右键，选择“开始调试”，Visual Studio 将使用全局默认环境且不使用参数（请参阅 [Python 环境](python-environments.md)）启动脚本。 之后，你就获得完整的调试支持。
>
> 若要控制环境和参数，需要针对代码创建项目。 通过[基于现有的 Python 代码](python-projects.md#creating-a-project-from-existing-files)可轻松执行此操作。

<a name="debugging-with-a-project"</a>
## <a name="basic-debugging"></a>基础调试

基础调试工作流包括如以下各节中所述的设置断点、逐句通过代码、检查值以及处理异常。 有关 Visual Studio 调试器的完整详细信息，请参阅 [Visual Studio 中的调试](../debugger/debugging-in-visual-studio.md)。

使用“调试”>“开始调试”命令、工具栏上的“开始”按钮或 F5 键启动调试会话。 这将使用项目的活动环境和任意命令行参数或项目属性中已指定的搜索路径（请参阅[项目调试选项](#project-debugging-options)）来启动项目的启动文件（在解决方案资源管理器中以粗体显示）。 如果出于某种原因而未设置启动文件，则会看到 Python 输出窗口短暂出现并消失。 在此情况下，请右键单击相应文件，然后选择“设为启动文件”。

> [!Note]
> 调试器始终通过项目的活动 Python 环境启动。 若要更改环境，请如 [Python 环境](python-environments.md)中所述，将其他环境更改为活动状态。

### <a name="breakpoints"></a>断点

断点在标记的点处停止执行代码，便于检查程序状态。 单击代码编辑器的左边距或右键单击代码行，然后选择“断点”>“插入断点”可设置断点。 包含断点的每行上将出现一个红点。

![Visual Studio 中的断点](media/debugging-breakpoints.png)

单击红点或右键单击代码行，选择“断点”>“删除断点”可删除断点。 若不删除断点，也可以使用“断点”>“禁用断点”命令禁用断点。

> [!Note]
> Python 中的某些断点可能会令习惯使用其他语言的用户感到意外。 在 Python 中，由于整个文件都是可执行代码，因此在加载该文件来处理任何顶级类或函数定义时，Python 都可以运行该文件。 如果设置了断点，你可能会发现调试器通过一个类声明从中间断开。 即使有时令人意外，但这是正确的行为。

用户可以自定义触发断点的条件，如仅在变量达到特定值时中断。 若要设置条件，请右键单击断点的红点，选择“条件”，然后使用 Python 代码创建表达式。 有关 Visual Studio 中此功能的完整详细信息，请参阅[断点条件](../debugger/using-breakpoints.md#breakpoint-conditions)

设置条件时，还可以设置“操作”并创建一条消息以记录到输出窗口，从而选择性地继续自动执行。 这将直接创建一个所谓的*跟踪点*，而无需将日志记录代码引入应用程序：

![使用断点创建跟踪点](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>逐句通过代码

在断点处停止后，可使用多种方法逐句通过代码或在再次中断之前运行代码块。 多个位置和途径可以提供这些命令，包括顶部调试工具栏、“调试”菜单、通过右键单击代码编辑器中的上下文菜单，以及通过键盘快捷方式（但并非所有命令都可以在这些位置提供）：

| 功能 | 击键 | 说明 |
| --- | --- | --- |
| Continue | F5 | 运行代码，到达下一个断点时停止。 |
| 逐语句 | F11 | 运行下一语句并停止。 如果下一语句是对函数的调用，调试器将在调用函数的第一行处停止。 |
| 逐过程 | F10 | 运行下一语句，包括对函数进行调用（运行其所有代码）并应用任何返回值。 单步跳过允许轻松跳过不需要调试的函数。 |
| 跳出 | Shift+F11 | 运行代码，到达当前函数的结尾，然后执行调用语句。 不需要调试当前函数的其余部分时，可以使用此功能。 |
| 运行到光标处 | Ctrl+F10 | 运行代码，直到编辑器中的插入符号位置。 通过此功能可以轻松跳过不需要调试的代码段。 |
| 设置下一语句 | Ctrl+Shift+F10 | 将代码中的当前运行点更改为插入符号的位置。 此功能允许忽略运行某个代码段，例如，当已知此代码段出现故障或产生不良副作用时，可使用此功能。 |
| 显示下一语句 | Alt+Num * | 返回将要运行的下一个语句。 当已仔细查看代码但并不知道调试器实际停止的位置时，可以使用此功能。 |

### <a name="inspecting-and-modifying-values"></a>检查和修改值

在调试器中停止时，可检查和修改变量的值。 还可以使用监视窗口监视单个变量，以及自定义表达式。 （请参阅[检查变量](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows)，了解常规详细信息。）

若要使用数据提示查看值，只需将鼠标悬停在编辑器中的任何变量上即可。 可以单击值进行更改：

![调试器中的数据提示](media/debugging-quick-tips.png)

自动变量窗口（“调试”>“窗口”>“自动变量”）包含接近当前语句的变量和表达式。 可以在值列中双击或选择值并按 F2 来编辑值：

![调试器中的自动变量窗口](media/debugging-autos-window.png)

局部变量窗口（“调试”>“窗口”>“局部变量”）显示当前范围内所有可再次编辑的变量：

![调试器中的局部变量窗口](media/debugging-locals-window.png)

有关使用自动变量和局部变量的详细信息，请参阅[在自动变量窗口和局部变量窗口中检查变量](../debugger/autos-and-locals-windows.md)。

通过监视窗口（“调试”>“窗口”>“监视”>“监视 1-4”）可以输入任意 Python 表达式并查看结果。 每个步骤都重新计算了表达式：

![调试器中的监视窗口](media/debugging-watch-window.png)

有关使用监视的详细信息，请参阅[使用监视窗口和快速监视窗口对变量设置监视](../debugger/watch-and-quickwatch-windows.md)。

检查到字符串值（`str`、`unicode`、`bytes` 和 `bytearray` 均被视为用于此目的字符串）时，将在该值的右侧看到一个放大镜图标。 单击该图标将在弹出对话框中显示不带引号的字符串值，对话框具有换行和滚动功能，有助于显示长字符串。 此外，单击图标上的下拉箭头可选择纯文本、HTML、XML 和 JSON 可视化效果：

![字符串可视化工具](media/debugging-string-visualizers.png)

HTML、XML 和 JSON 可视化效果显示在单独的弹出窗口中，其中突出显示了语法并采用树状视图。

### <a name="exceptions"></a>异常

如果调试器时出错，但你没有相应的异常处理程序，调试器将在异常点处中断：

![异常弹出窗口](media/debugging-exception-popup.png)

此时，可以检查程序状态，包括调用堆栈。 但如果尝试逐句通过代码，将继续引发该异常，直到异常得以处理或程序退出为止。

“调试”>“窗口”>“异常设置”菜单命令将打开一个窗口，可在其中展开“Python 异常”：

![异常窗口](media/debugging-exception-settings.png)

每个异常的复选框控制引发该异常时调试器是否*始终*中断。 如果想要针对特定异常比较频繁地进行中断，应选中此框。

默认情况下，在源代码中找不到异常处理程序时，大多数异常将中断。 若要更改此行为，请右键单击任何异常并选中或取消选中“在用户代码中未经处理时继续”。 如果想要针对某异常较少地进行中断，应清除此框。

若要配置此列表中未出现的异常，请单击“添加”按钮进行添加。 名称必须与该异常的完整名称匹配。

## <a name="project-debugging-options"></a>项目调试选项

默认情况下，调试器使用标准 Python 启动器且不使用命令行参数和其他特殊路径或条件启动程序。 可通过右键单击解决方案资源管理器中的项目，选择“属性”，然后选择“调试”选项卡来访问该项目的调试属性，从而更改这些选项。

![项目调试属性](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>启动模式选项

“启动模式”选项允许在以下选项之间进行选择，从而启用不同的方案：

| 选项 | 描述 |
| --- | --- |
| 标准 Python 启动器 | 使用以可移植 Python（与 CPython、IronPython 和无堆栈 Python 等变量兼容）编写的调试代码。 它提供调试纯 Python 代码的最佳体验。 附加到正在运行的 `python.exe` 进程时，将使用此启动器。 此外，此启动器还提供针对 CPython 的[混合模式调试](debugging-mixed-mode.md)，可以无缝地在 C/C++ 代码和 Python 代码之间进行单步执行。 |
| Web 启动器 | 在启动时启动默认浏览器并启用模板调试。 请参阅[Web 模板调试](template-web.md#debugging)部分，了解详细信息。 |
| Django Web 启动器 | 相当于 Web 启动器，仅为了向后兼容性而显示。 |
| IronPython (.NET) 启动器 | 使用 .NET 调试器，它只适用于 IronPython，但允许在任何 .NET 语言项目（包括 C# 和 VB）之间进行单步执行。 如果附加到托管 IronPython 的正在运行的 .NET 进程，将使用此启动器。 |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>运行选项（搜索路径、启动参数和环境变量）

| 选项 | 描述 |
| --- | --- |
| 搜索路径 | 这些路径与解决方案资源管理器中项目的搜索路径节点中显示的路径匹配。 可以在此处修改该值，但使用解决方案资源管理器更简单，因为可以浏览文件夹和自动将路径转换为相对形式。 |
| 脚本参数 | 这些参数添加到用于启动脚本的命令中，并且显示在脚本的文件名后。 此处可供脚本使用的第一项为 `sys.argv[1]`，第二项为 `sys.argv[2]`以此类推。 |
| 解释器参数 | 这些参数添加到启动程序命令行中的脚本名称之前。 此处常见的参数有：用于控制警告的 `-W ...`、用于略微优化程序的 `-O` 和用于使用未缓冲 IO的 `-u`。 IronPython 用户可能会使用此字段来传递 `-X` 选项，例如 `-X:Frames` 或 `-X:MTA`。 |
| 解释器路径 | 替代与当前环境相关联的路径。 可能可用于通过非标准解释器启动脚本。 |
| 环境变量 | 在此多行文本框中，添加 `NAME=VALUE` 形式的条目。 除任何现有全局环境变量外，在根据搜索路径设置设定 `PYTHONPATH` 之后，最后应用此设置，因此可以将该设置用于手动替代任何设置。 |

<a name="the-debug-interactive-window"</a>
## <a name="immediate-and-interactive-windows"></a>即时窗口和交互窗口

调试会话期间可使用两个交互窗口：标准 Visual Studio 即时窗口和 Python 调试交互窗口。

即时窗口（“调试”>“窗口”>“即时”）用于快速计算 Python 表达式以及检查或分配正在运行的程序中的变量。 请参见常规[即时窗口](../ide/reference/immediate-window.md)主题，了解详细信息。

Python 调试交互窗口（“调试”>“窗口”>“Python 调试交互窗口”）更丰富，因为它可以在调试（包括编写和运行代码）时提供完整的[交互式 REPL](interactive-repl.md) 体验。 它会自动连接到使用标准 Python 启动器在调试器中启动的任何进程（包括通过连接*“调试”>“附加到进程”附加的进程）。 但使用 C/C++ 混合模式调试时，它不可用。

![Python 调试交互窗口](media/debugging-interactive.png)

除[标准 REPL 命令](interactive-repl.md#meta-commands)外，调试交互窗口还支持特殊元命令：

| 命令 | 参数 | 描述 |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | 从当前语句开始运行程序。 |
| `$down`, `$d` | 在堆栈跟踪中将当前帧下移一级。 |
| `$frame` | | 显示当前的帧 ID。
| `$frame` | 帧 ID | 将当前帧切换为指定帧 ID。
| `$load` | 从文件加载命令并执行，直到完成 |
| `$proc` |  | 显示当前的进程 ID。 |
| `$proc` | 进程 ID | 将当前进程切换为指定进程 ID。 |
| `$procs` | | 列出当前正在调试的进程。 |
| `$stepin`, `$step`, `$s` | 如果可能，单步执行下一个函数调用。 |
| `$stepout`, `$return`, `$r` | 跳出当前函数。 |
| `$stepover`, `$until`, `$unt` | 转到下一个函数调用。 |
| `$thread` | | 显示当前的线程 ID。 |
| `$thread` | 线程 ID | 将当前线程切换为指定线程 ID。 |
| `$threads` | | 列出当前正在调试的线程。 |
| `$up`, `$u` | | 在堆栈跟踪中将当前帧上移一级。 |
| `$where`, `$w`, `$bt` | 列出当前线程的帧。 |

请注意，标准调试器窗口（如进程、线程和调用堆栈）不与调试交互窗口同步。 这意味着在调试交互窗口中更改活动的进程、线程或帧不会影响其他调试器窗口，同样，在其他调试器窗口中更改活动的进程、线程或帧不会影响调试交互窗口。

调试交互窗口自身具有一组选项，可通过“工具”>“选项”>“Python 工具”>“调试交互窗口”进行访问。 与常规 Python 交互窗口（针对每个 Python 环境具有单独的实例）不同，该交互窗口只有一个调试交互窗口，并且它始终对正在调试的进程使用 Python 解释器。

![调试交互窗口选项](media/debugging-interactive-options.png)
