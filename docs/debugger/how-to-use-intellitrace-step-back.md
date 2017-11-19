---
title: "查看快照使用 IntelliTrace 步骤后的 Visual Studio |Microsoft 文档"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc7ad92e708666baf1ab0429c041ca9b7d2e0f95
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="view-snapshots-using-intellitrace-step-back"></a>使用 IntelliTrace 步骤后的视图快照
IntelliTrace 步骤后会自动编制的应用程序的每个断点和调试器快照步骤事件。 记录的快照，可以返回到上一个断点或步骤，并查看应用程序的状态，因为它在过去。 IntelliTrace 步骤后可以节省你时间： 如果您想要查看以前的应用程序状态，但不想重新启动调试或重新创建所需的应用程序的状态。

IntelliTrace 回步骤是在 Visual Studio Enterprise 2017 15.5 及更高版本，版本中开始提供，要求 Windows 10 周年 Update 或更高版本。 调试 ASP.NET、 WinForms、 WPF、 托管的控制台应用程序和托管的类库当前支持的功能。 当前不支持调试 ASP.NET Core、.NET 核心或 UWP 应用程序。 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>启用 IntelliTrace 事件和快照模式 
若要启用此功能，请转到**工具 > 选项 > IntelliTrace**设置，并选择选项**IntelliTrace 事件和快照**。 

![启用 IntelliTrace 事件和快照模式](../debugger/media/intellitrace-enable-snapshots.png "启用 IntelliTrace 事件和快照模式")

IntelliTrace 拍摄的快照应用程序的进程上每个调试器步骤和断点事件。 这些事件记录在**事件**选项卡中**诊断工具**窗口，同时还有其他 IntelliTrace 事件。 若要打开此窗口，请选择**调试 / Windows / 显示诊断工具**。

快照可提供的事件旁边会出现一个相机图标。 

![事件选项卡上使用快照](../debugger/media/intellitrace-events-tab-with-snapshots.png "与断点和步骤的快照的事件选项卡")

出于性能原因，快照不会采取单步执行时速度非常快。 如果该步骤旁不显示任何照相机图标，请尝试单步执行速度更慢。

## <a name="navigate-and-view-snapshots"></a>导航并查看快照

你可以使用事件之间导航**步骤向后**和**单步前进**中调试工具栏按钮。 这些按钮导航中显示的事件**事件**选项卡中**诊断工具窗口**。 单步执行向后翻或转发到的事件自动激活历史调试所选事件。

![向后移动和转发按钮](../debugger/media/intellitrace-step-back-icons-description.png "后退一步和单步前进按钮")

返回一步或单步前进，Visual Studio 将进入历史调试模式。 在此模式下，将调试器的上下文切换到所选的事件记录时的时间。 Visual Studio 还将指针移到相应的源窗口中的代码行。 

从此视图中，你可以检查中的值**调用堆栈**，**局部变量**，**自动**，和**监视**windows。 你还可以悬停在变量以查看数据提示并执行中的表达式计算**即时**窗口。 你看到的数据是进程的从应用程序在该点按时间的快照。

因此，举例来说，如果你已命中断点后，执行步骤 (**F10**)，则**步骤向后**按钮可使 Visual Studio 中的行处对应于断点的代码的历史模式。 

![使用快照执行事件正在激活历史模式](../debugger/media/intellitrace-historical-mode-with-snapshot.png "正在激活历史模式使用快照执行事件")

若要返回到实时执行，请选择**继续 (F5)**或单击**返回到实时调试**信息栏中的链接。 

你还可以查看从快照**事件**选项卡。选择具有快照的事件，然后单击**激活历史调试**。 你也可以单击相机图标以激活历史调试。

![事件激活历史调试](../debugger/media/intellitrace-activate-historical-debugging.png "事件激活历史调试")

与不同**设置下一语句**命令，查看快照不会重新运行你的代码; 它提供的静态视图状态的应用程序的点处发生在过去的时间。

![概述 IntelliTrace 步骤回](../debugger/media/intellitrace-step-back-overview.png "概述的 IntelliTrace 步骤回")

## <a name="next-steps"></a>后续步骤  
 若要了解如何检查 Visual Studio 中的变量，请参阅[调试器功能教程](../debugger/debugger-feature-tour.md)  
 有关历史调试的概述，请参阅[历史调试](../debugger/historical-debugging.md)。  

## <a name="frequently-asked-questions"></a>常见问题

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>是如何 IntelliTrace 回步骤不同于 IntelliTrace 事件的唯一模式？

事件仅模式中的 IntelliTrace 允许你以激活历史调试在调试器将单步和断点。 但是，IntelliTrace 只会捕获中的数据**局部变量**和**自动**windows 如果 windows 已打开，并且它仅捕获已展开的数据和视图中。 在事件仅模式下，你通常不具有的变量和复杂的对象的完整视图。 此外，表达式求值和查看数据中的**监视**窗口不支持。 

在事件和快照模式下，IntelliTrace 捕获整个快照应用程序的过程，包括复杂对象。 在代码的行，可以看到相同的信息，就像已在断点处停止 （和你以前已展开的信息是否并不重要）。 查看快照，则还支持表达式计算。  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>此功能的性能影响是什么？ 

单步执行的总体性能的影响取决于你的应用程序。 拍摄快照的开销是大约 30 ms。 时拍摄快照时，应用的过程派生并且分叉的副本会挂起。 当你查看快照时，则会将 Visual Studio 将附加到进程的分叉副本。 对于每个快照，Visual Studio 将复制仅的页表，并将页面设置到写入时复制。 如果堆上的对象更改之间关联的快照的调试器将单步，相应的页表是然后复制，导致最小内存开销。 如果 Visual Studio 检测到没有足够的内存来拍摄快照，它不使用其中一个。
 
## <a name="known-issues"></a>已知问题  
* 如果你在早于 Windows 10 秋季创建者更新 (RS3) 的 Windows 版本上使用 IntelliTrace 事件和快照模式，并且如果应用程序的调试平台目标设置为 x86，IntelliTrace 不拍摄快照。

    解决方法：
    * 安装或升级到 Windows 10 秋季创建者更新 (RS3)。 
    * 或者： 
        1. 用 Visual Studio 安装程序安装用于桌面的 VC++ 2015.3 v140 工具集组件 (x86, x64)。
        2. 生成目标应用程序。
        3. 从命令行中，使用 editbin 工具设置`Largeaddressaware`目标可执行文件的标志。 例如，你可以 （在更新的路径） 之后使用此命令:"C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe"/Largeaddressaware"C:\Path\To\Application\app.exe"。
        4. 若要开始调试时，按**F5**。 现在，调试器将单步和断点上拍摄快照。

        > [!Note]
        > `Largeaddressaware`标志必须设置每个使用更改重新生成可执行文件的时间。

* 当使用持久的内存映射文件的应用程序在拍摄应用程序的进程的快照时，快照的进程包含内存映射文件上的排他锁的 （即使父进程已发布它的锁定）。 其他进程将仍能够读取，但不是写入到内存映射文件。

    解决方法：
    * 通过结束调试会话中清除所有快照。 

* 保存的文件时**调试 > IntelliTrace > 保存 IntelliTrace 会话**在事件和快照模式下，附加的数据从快照捕获中不可用时.itrace 文件。 在断点并单步事件，你将看到相同的信息，就像已在 IntelliTrace 事件仅模式下保存文件。 