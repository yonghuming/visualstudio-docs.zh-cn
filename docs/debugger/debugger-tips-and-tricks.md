---
title: "提示和技巧在 Visual Studio 调试器 |Microsoft 文档"
ms.custom: 
ms.date: 06/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26993da79249d1706dc8609cfcd5b0ceb66e1ec4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>了解 Visual Studio 中调试程序的工作效率提示和技巧

阅读本主题以了解 for Visual Studio 调试器的少量工作效率提示和技巧。 了解调试器的基本功能的信息，请参阅[调试器功能教程](../debugger/debugger-feature-tour.md)。 在本主题中，我们将介绍一些功能教程中未包括的区域。

## <a name="pin-data-tips"></a>固定数据提示

如果你经常将鼠标悬停在数据提示在调试时，你可能想要固定变量以便自己给快速访问的数据提示。 变量在重新启动后保持固定。 若要固定数据提示，请悬停时单击的图钉图标。 你可以将固定多个变量。

![固定数据提示](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>编辑你的代码并继续调试 （C#、 VB、 c + +）

在 Visual Studio 支持大多数语言中，可以编辑在调试会话中间代码，并继续调试。 若要使用此功能，请单击进入你代码的光标在暂停时，调试器，进行编辑，然后按**F5**， **F10**，或**F11**继续调试。

![编辑并继续调试](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

使用功能和功能限制的详细信息，请参阅[编辑并继续](../debugger/edit-and-continue.md)。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>调试难以重现的问题

如果却很难或花费大量时间来重新创建你的应用程序中的特定状态，请考虑是否可以帮助使用条件断点。 你可以使用[条件断点](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)和筛选器以避免中断到应用程序代码，直到应用程序进入 （例如状态变量将在其中存储错误数据） 所需的状态的断点。 你可以设置使用表达式、 筛选器、 命中的次数和等等的条件。

#### <a name="to-create-a-conditional-breakpoint"></a>若要创建条件断点

1. 右键单击断点图标 （红色球） 并选择**条件**。

2. 在**断点设置**窗口中，键入一个表达式。

    ![条件断点](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 如果你感兴趣的条件的另一个类型，选择**筛选器**而不是**条件表达式**中**断点设置**对话框中，然后按照筛选器的技巧。

## <a name="change-the-execution-flow"></a>更改执行流

使用调试程序时暂停的代码行上，使用鼠标来获取在左侧的黄色箭头指针。 将黄色箭头指针移动到的代码执行路径中的不同点。 然后使用 F5 或步骤命令继续运行应用程序。

![执行将指针移动到](../debugger/media/dbg-tour-move-the-execution-pointer.gif "执行将指针移动到")

通过更改执行流，你可以执行某些操作，如测试不同的代码执行路径，或重新运行代码，无需重新启动调试器。

> [!WARNING]
> 通常，您需要小心使用此功能，并查看工具提示中的某个警告。 你可能会太看到其他警告。 将指针移无法还原到较早的应用程序状态应用程序。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>跟踪范围扩展的对象 （C#、 Visual Basic）

很容易地查看变量使用之类的调试器窗口**监视**窗口。 但是，当变量超出范围中时才**监视**窗口中，你可能注意到，它将灰显。某些应用方案中，即使当变量超出范围，并且你可能想要密切监视可能会更改变量的值 （例如，变量可能会收到垃圾回收）。 你可以通过中为其创建一个对象 ID 跟踪变量**监视**窗口。

#### <a name="to-create-an-object-id"></a>若要创建的对象 ID

1.  设置接近您想要跟踪的变量断点。

2.  启动调试器 (**F5**) 并在断点处停止。

3. 查找中的变量**局部变量**窗口 (**调试 > Windows > 局部变量**)，右键单击该变量，然后选择**创建对象 ID**。

    ![创建对象 ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  应该会在“局部变量” **$** 窗口中看到 **$** 窗口中设置断点来中断调用函数返回到的指令或行处的执行。 此变量是对象 id。
  
5.  右键单击该对象 ID 变量，然后选择**添加监视**。

有关详细信息，请参阅[创建对象 ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>查看有关函数的返回值

若要查看您的函数的返回值，请查看显示在函数**自动**窗口时你逐句通过代码。 若要查看函数的返回值，请确保已执行您感兴趣的函数 (按**F10**一次，如果您当前已停止在函数调用)。 如果窗口已关闭，则使用**调试 > Windows > 自动**以打开**自动**窗口。

![自动窗口](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

此外，你可以输入中的函数**即时**窗口来查看返回值。 (打开它使用**调试 > Windows > 即时**。)

![即时窗口](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

你还可以使用[伪变量](../debugger/pseudovariables.md)中**监视**和**即时**窗口中，如`$ReturnValue`。

## <a name="string_visualizer"></a>检查在可视化工具中的字符串

在使用字符串，它可有助于查看整个带格式的字符串。 若要查看的纯文本、 XML、 HTML 或 JSON 字符串，请单击放大镜图标![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "可视化工具图标")当悬停在包含一个字符串值的变量。

![打开字符串可视化工具](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

字符串可视化工具可帮助你找出字符串是否为格式不正确，具体取决于字符串类型。 例如，空白**值**字段指示的可视化工具类型无法识别该字符串。 有关详细信息，请参阅[字符串可视化工具对话框](../debugger/string-visualizer-dialog-box.md)。

![JSON 字符串可视化工具](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

对于在调试器窗口中显示的 WPF 对象等的几个其他类型，你也可以打开可视化工具。

## <a name="break-into-code-on-handled-exceptions"></a>中断上处理的异常的代码

调试器将中断上未经处理的异常代码。 但是，处理异常 (如内出现的异常`try/catch`块) 也可以是 bug 的源，并且你可能想要调查发生时。 你可以配置调试器中断的处理的异常的代码通过配置中的选项**异常设置**对话框。 打开此对话框中，请选择**调试 > Windows > 异常设置**。

**异常设置**对话框中，你可以让调试器中断对特定异常的代码。 在下图中，调试器将中断代码每当`System.NullReferenceException`时发生。 有关详细信息，请参阅[管理异常](../debugger/managing-exceptions-with-the-debugger.md)。

![异常设置对话框](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>调试死锁和争用条件

如果需要进行调试的多线程应用是通用的问题，它通常有助于在调试时查看的线程的位置。 你可以轻松地使用**在源中显示线程**按钮。

#### <a name="to-show-threads-in-your-source-code"></a>若要显示在源代码中的线程

1.  调试时，单击**在源中显示线程**按钮![在源中显示线程](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")中**调试**工具栏。
  
2.  查看窗口左侧的滚动条槽。 在这行内容，你看到*线程标记*图标![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，类似于两根细线。 线程标记指示线程在此位置停止。

    请注意可能断点部分隐藏线程标记。
  
3.  将指针悬停在线程标记上。 屏幕上显示数据提示。 数据提示将告诉您每个已停止线程的名称和线程 ID 号。

    你还可以查看中的线程位置[并行堆栈窗口](../debugger/get-started-debugging-multithreaded-apps.md)。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>检查 web 服务和网络资源 (UWP) 的有效负载

在 UWP 应用中，你可以分析执行使用的网络操作`Windows.Web.Http`API。 可以使用此工具来帮助调试 web 服务和网络资源。 若要使用该工具，选择**调试 > 性能探查器结合**。 选择**网络**，然后选择**启动**。 在应用中，浏览使用 `Windows.Web.Http` 的应用场景，然后选择“停止收集”生成报表。

![网络使用情况分析工具](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

选择摘要视图中的操作以查看更多详细信息。

![详细信息中网络使用情况工具](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

有关详细信息，请参阅[网络使用情况](../profiling/network-usage.md)。

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>获取更熟悉如何将调试器附加到你的应用程序

若要附加到正在运行的应用，调试器将加载为完全相同生成尝试调试的应用生成的符号 (.pdb) 文件。 在某些情况下，了解符号文件的很有用。 你可以检查 Visual Studio 会使用的符号文件的加载**模块**窗口。

打开**模块**时通过选择调试窗口**调试 > Windows > 模块**。 **模块**窗口可以告知调试器将视为用户代码中，哪些模块或[*我的代码*](../debugger/just-my-code.md)，和符号加载模块的状态。 在大多数情况下，调试器自动查找符号文件，对于用户代码，但如果你想要单步执行 （或调试）.NET framework 代码、 系统代码或第三方库代码，需要额外的步骤来获取正确的符号文件。

![在模块窗口中查看符号信息](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

你可以加载符号信息直接从**模块**窗口中的右键单击并选择**加载符号**。

有时，应用程序开发人员没有匹配的符号文件 （若要减少内存占用），但保留一份匹配的符号文件生成，以便它们能够调试一个已发布的版本更高版本的情况下提供应用。

若要找出调试器将为用户代码的代码的分类，请参阅[仅我的代码](../debugger/just-my-code.md)。 若要了解有关符号文件的详细信息，请参阅[在 Visual Studio 调试器中指定符号 (.pdb) 和源文件](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="learn-more"></a>了解详细信息

有关更多的提示和技巧和更多详细的信息，请参阅以下博客帖子：

- [7 较小已知攻击的威胁的 Visual Studio 中调试](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 中的 7 隐藏的 gem](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>另请参阅
[键盘快捷键](../ide/tips-and-tricks-for-visual-studio.md)
