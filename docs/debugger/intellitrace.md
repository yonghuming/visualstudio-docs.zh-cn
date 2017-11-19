---
title: "IntelliTrace |Microsoft 文档"
ms.custom: 
ms.date: 07/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: "135"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f009abffb1c956a0f7c57315181234fbea2fc1c
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2017
---
# <a name="intellitrace"></a>IntelliTrace
使用 IntelliTrace 记录和跟踪代码的执行历史记录时，可缩短调试应用程序所用的时间。 你可以更轻松地发现 Bug，因为 IntelliTrace 让你能够：  
  
-   记录特定事件  
  
     检查相关的代码、 中所显示数据**局部变量**窗口期间调试器事件和函数调用信息  
  
-   调试难以重现或在部署中出现的错误  
  
 可以在 Visual Studio Enterprise 版（但不可在 Professional 或 Community 版）中使用 IntelliTrace。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么？  
  
|||  
|-|-|  
|**调试我的应用程序使用 IntelliTrace:**<br /><br /> -我想查看以前事件。<br />-显示我调用以前事件的信息。<br />-保存我的 IntelliTrace 会话。<br />控制 IntelliTrace 收集的数据。|-   [演练： 使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace 功能](../debugger/intellitrace-features.md)<br />-   [历史调试](../debugger/historical-debugging.md)<br />-   [使用 IntelliTrace 步骤后的视图快照](../debugger/how-to-use-intellitrace-step-back.md)|  
|**测试管理器中的测试会话期间收集 IntelliTrace 数据**|-   [收集在手动测试中的更多诊断数据](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)|  
|**从已部署应用程序收集 IntelliTrace 数据**|-   [使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**开始从 IntelliTrace 日志文件 （.iTrace 文件） 调试。**|-   [使用保存的 IntelliTrace 数据](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a>哪些应用可以使用 IntelliTrace 进行调试？  
  
|||  
|-|-|  
|**支持**|的使用.NET Framework 2.0 或更高版本 Visual Basic 和 Visual C# 应用程序。<br />     你可以调试大多数应用程序，包括 ASP.NET、Microsoft Azure、Windows 窗体、WCF、WPF、Windows 工作流、SharePoint 2010、SharePoint 2013 和 64 位应用。<br />     若要调试 SharePoint 应用程序使用 IntelliTrace，请参阅[演练： 调试 SharePoint 应用程序通过使用 IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)。<br />     若要调试 intellitrace 的 Microsoft Azure 应用程序，请参阅[调试使用 IntelliTrace 和 Visual Studio 发布云服务](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services)。|  
|**有限的支持**|.NET 核心和 ASP.NET Core 应用仅支持事件<br />的实验证明 F # 应用程序<br />Windows 应用商店应用程序仅支持事件|  
|**不支持**|C + +、 其他语言和脚本<br />-Windows 服务、 Silverlight、 Xbox 或[!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)]应用|  
  
> [!NOTE]
>  如果你想要调试的进程已在运行，你可以仅收集 IntelliTrace 事件 （没有调用信息）。 你可以附加到本地计算机上的 32 位或 64 位进程。 未收集发生之前附加到进程的事件。
  
##  <a name="IntelliTraceVSTraditional"></a>为何使用 IntelliTrace 进行调试？  
 传统或*实时*调试仅显示你的应用程序的当前状态，提供有关过去事件的有限数据。 要么必须根据应用程序的当前状态推断这些事件，要么必须通过重新运行应用程序以重新生成这些事件。  
  
 IntelliTrace 通过记录特定事件和这些时间点的数据，扩展此传统调试体验。 这让你能够不重启应用程序即可查看应用程序中发生了什么，特别是在单步执行到 Bug 处时。 IntelliTrace 在传统调试期间会默认启用，并以不可见的方式自动收集数据。 这样，你即可轻松地在传统调试和 IntelliTrace 调试之间进行切换来查看该记录信息。 请参阅[IntelliTrace 功能](../debugger/intellitrace-features.md)和[IntelliTrace 收集哪些数据？](#WhatData)  
  
 IntelliTrace 还可帮助你调试难以重现或在部署时出现的错误。 可以收集 IntelliTrace 数据并将其保存为 IntelliTrace 日志文件（.iTrace 文件）。 .iTrace 文件包含有关异常、性能事件、Web 请求、测试数据、线程、模块和其他系统信息的详细信息。 可以在 Visual Studio Enterprise 中打开此文件、选择一个项，然后使用 IntelliTrace 开始调试。 这让你能够转到文件中的任何事件并查看该时间点上有关应用程序的特定详细信息。  
  
 你可以从这些源中保存 IntelliTrace 数据：  
  
-   中 Visual Studio 自 2017 年 1 Enterprise、 Visual Studio 2015 Enterprise、 或以前版本的 Visual Studio 旗舰版的 IntelliTrace 会话。  
  
-   Microsoft 测试管理器中的测试会话  
  
-   IIS 上托管的 ASP.NET Web 应用程序，或使用 Microsoft Monitoring Agent（单独使用或与 System Center 2012 一起使用）时在部署中运行的 SharePoint 2010 和 SharePoint 2013 应用程序。 请参阅[使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)和[使用 Microsoft Monitoring Agent 进行监视](http://technet.microsoft.com/library/dn465153.aspx)。  
  
 下面是一些示例，说明 IntelliTrace 如何帮助你进行调试：  
  
-   你的应用程序损坏了一个数据文件，但是你不知道此事件的发生位置。  
  
     如果不使用 IntelliTrace，则必须浏览代码以查找所有可能的文件访问，在这些访问上放置断点，并重新运行应用程序以查找出现问题的位置。 如果使用 IntelliTrace，则在每个事件发生时，可以查看收集的所有文件访问事件和有关应用程序的特定详细信息。  
  
-   发生异常。  
  
     如果不使用 IntelliTrace，获得有关异常的消息，但你没有多有关的事件的引发异常的信息。 你可以检查调用堆栈，以了解的一系列调用引发异常，但不是能看到这些调用过程中发生的事件的顺序。 如果使用 IntelliTrace，你可以检查在异常之前发生的事件。  
  
-   你的应用程序在测试计算机上崩溃，但在开发计算机上成功运行。  
  
     可以从 Microsoft 测试管理器中收集 IntelliTrace 数据，将该数据保存到 .iTrace 文件，并将此文件附加到 Team Foundation Server 工作项以备以后调查使用。 请参阅[收集在手动测试中的更多诊断数据](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)和[使用保存的 IntelliTrace 数据](../debugger/using-saved-intellitrace-data.md)。  
  
-   在已部署的应用程序中发生 Bug 或崩溃。  
  
     对于基于 Microsoft Azure 的应用，在发布应用程序之前，可以配置 IntelliTrace 数据收集。 应用程序运行时，IntelliTrace 会将数据保存到 .iTrace 文件。 请参阅[调试已发布的云服务使用 IntelliTrace 和 Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248)。  
  
     对于 IIS 7.0、7.5 和 8.0 上托管的 ASP.NET Web 应用程序，以及 SharePoint 2010 或 SharePoint 2013 应用程序，请使用 Microsoft Monitoring Agent（单独使用或与 System Center 2012 一起使用），以备将 IntelliTrace 数据保存到 .iTrace 文件中。  
  
     当你需要诊断部署中的应用程序的问题时，这会很有用。 请参阅[使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)。  
  
##  <a name="WhatData"></a>IntelliTrace 收集哪些数据？  
 **收集事件信息**  
  
 默认情况下，IntelliTrace 仅记录 IntelliTrace 事件：调试程序事件、异常、.NET Framework 事件以及可帮助进行调试的其他系统事件。 你可以选择想要收集的 IntelliTrace 事件的类型（始终收集的调试器事件和异常除外）。 请参阅[IntelliTrace 功能](../debugger/intellitrace-features.md)。  
  
-   **调试器事件**  
  
     IntelliTrace 始终记录 Visual Studio 调试器中发生的事件。 例如，启动应用程序是一个调试程序事件。 其他调试程序事件包括会导致应用程序中断执行的停止事件。 例如，你的程序命中断点、 命中跟踪点，或执行**步骤**命令。  

     默认情况下，为了帮助提高性能，IntelliTrace 不记录调试器事件的每个可能值。 而是记录以下值：  
  
    -   中的值**局部变量**窗口。 保留**局部变量**窗口处于打开状态以查看这些值。  
  
    -   中的值**自动**窗口才**自动**窗口处于打开状态  
  
    -   在将鼠标指针移到源窗口中的变量的上方以查看其值时显示的数据提示中的值。 IntelliTrace 不收集固定数据提示中的值。  

    启用 IntelliTrace 事件和快照模式后，IntelliTrace 将快照应用程序的过程在每个调试器**断点**和**步骤**事件。 这将记录中的值**局部变量**，**自动**，和**监视**windows，而不考虑 windows 的是否是打开。 此外会收集任何固定的数据提示中的值。 
  
-   **异常**  
  
     IntelliTrace 会记录异常类型和以下各类异常的消息：  
  
    -   已处理的异常（已引发并捕获异常）  
  
    -   未经处理的异常  
  
-   **.NET framework 事件**  
  
     默认情况下，IntelliTrace 记录最常见的 .NET Framework 事件。 例如:   
  
    -   对于选中复选框事件，IntelliTrace 将收集复选框状态和文本。  
  
-   **SharePoint 2010 和 SharePoint 2013 应用程序事件**  
  
     你可以为在 Visual Studio 外运行的 SharePoint 2010 和 2013 应用程序记录用户配置文件事件以及一部分统一日志记录系统 (ULS) 事件。 你可以将这些事件保存到 .iTrace 文件中。 需要 Visual Studio Enterprise 2017、 Visual Studio Enterprise 2015、 以前版本的 Visual Studio Ultimate 或[Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384)中运行**跟踪**模式。  
  
     打开 .iTrace 文件时，输入 SharePoint 相关 ID 以查找其匹配的 Web 请求，查看记录事件，并从特定事件开始调试。 如果文件包含未经处理的异常，可以选择相关 ID，开始调试异常。  
  
     请参阅：  
  
    -   [使用 IntelliTrace 独立收集器](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [使用保存的 IntelliTrace 数据](../debugger/using-saved-intellitrace-data.md)  
  
    -   [演练：使用 IntelliTrace 调试 SharePoint 应用程序](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)  
 
 **捕获快照**
 
 你可以配置 IntelliTrace 以捕获每个断点处的快照和调试器步骤事件。 IntelliTrace 记录的每个快照，允许你查看复杂变量并计算表达式的完整的应用程序状态。

 请参阅[查看快照使用 IntelliTrace 步骤回](../debugger/how-to-use-intellitrace-step-back.md)。

 **收集函数调用信息**  
  
 可以配置 IntelliTrace 以收集函数的调用信息。 此信息使你可以查看调用堆栈历史记录，并能在代码中向后移动和向前移动调用。 对于每个函数调用，IntelliTrace 将记录此数据：  
  
-   函数名  
  
-   在函数入口点作为参数传递并在函数退出点返回的基元数据类型的值  
  
-   读取或更改自动属性时该属性的值  
  
-   指向第一级子对象的指针，而不是它们的值，除非它们为 null  
  
> [!NOTE]
>  IntelliTrace 仅收集数组中的头 256 个对象和字符串的头 256 个字符。  
  
 请参阅[检查你的应用使用历史调试](../debugger/historical-debugging-inspect-app.md)。
  
 **收集模块信息**  
  
 若要控制 IntelliTrace 收集的调用信息量，请仅指定你关注的模块。 这有助于在收集期间提高应用程序的性能。 请参阅明[控制 IntelliTrace 收集的信息量](../debugger/intellitrace-features.md#ControlCallData)IntelliTrace 功能中。  
  
##  <a name="AffectPerformance"></a>IntelliTrace 将减慢我的应用程序？  
 默认情况下，IntelliTrace 仅收集所选 IntelliTrace 事件的数据。 这可能会让应用程序的速度变慢，也可能不会，具体取决于代码的结构和组织。 例如，如果 IntelliTrace 经常记录某个事件，则这可能会让应用程序的速度变慢。 它还可能会让你考虑重构应用程序。  
  
 收集调用信息可能会让应用程序的速度显著变慢。 它还可能增加您保存到磁盘的任何 IntelliTrace 日志文件（.iTrace 文件）的大小。 若要尽可能减少这些影响，请仅收集你关注的模块的调用信息。  若要更改.iTrace 文件的最大大小，请转到**工具**，**选项**， **IntelliTrace**，**高级**。 
  
## <a name="in-this-section"></a>本节内容  
 [IntelliTrace 功能](../debugger/intellitrace-features.md)  
  
 [包括的难以重现的 Bug 的诊断跟踪数据](/devops-test-docs/test_notintoc/including-diagnostic-trace-data-with-bugs-that-are-difficult-to-reproduce)  
  
 [诊断部署后出现的问题](../debugger/diagnose-problems-after-deployment.md)  
  
 [使用保存的 IntelliTrace 数据](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>博客  
 [Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>论坛  
 [Visual Studio 诊断](http://go.microsoft.com/fwlink/?LinkId=262263)