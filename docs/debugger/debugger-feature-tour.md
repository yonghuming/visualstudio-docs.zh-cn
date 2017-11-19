---
title: "调试器功能教程 |Microsoft 文档"
ms.custom: H1HackMay2017
ms.date: 05/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7edb1428d3dedbbe6341427e28964559d9750b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="feature-tour-of-the-visual-studio-debugger"></a>Visual Studio 调试器的功能教程

本主题介绍 Visual Studio 调试器的功能。 如果你想要遵循通过在 Visual Studio 中打开你自己的应用，你可以这样做，或者你可以遵循示例应用程序使用[初学者指南](../debugger/getting-started-with-the-debugger.md)。

此处描述的功能都适用于 C#、 c + +、 Visual Basic、 JavaScript 和其他语言支持的 Visual Studio （除指明外）。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>设置断点并启动调试器

若要调试，需要使用调试程序附加到应用程序进程中启动您的应用程序。 F5 (**调试 > 启动调试**) 是执行该操作的最常见方法。 但是，现在你可能未设置任何断点，以检查你的应用程序代码，因此我们将执行此操作，它首先，然后开始调试。

如果你已在代码编辑器中打开文件，你可以通过在某个代码行的左边距中单击设置断点。

![设置断点](../debugger/media/dbg-tour-set-a-breakpoint.gif "设置断点")

按 F5 (**调试 > 启动调试**) 和调试器会运行到它所遇到的第一个断点。 如果应用程序尚未运行，F5 启动调试器，并在第一个断点处停止。

当你知道代码的行或你想要检查详细信息中的部分时，断点是代码的一个有用的功能。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>导航代码在调试器中使用步骤命令

因为它们使你的应用程序代码的导航速度更快，我们会为大多数命令提供的键盘快捷方式。 （如菜单命令显示在括号中命令的等效项。）

若要启动附有调试器的应用程序，请按 F11 (**调试 > 单步执行**)。 F11 是**单步执行**命令，并向前移动一次的应用程序执行一个语句。 当你开始与 F11 的应用程序时，调试器将在获取执行的第一个语句处中断。

![F11 单步执行](../debugger/media/dbg-tour-f11.png "F11 单步执行")

黄色箭头表示在其暂停调试器，它还将在同一时刻 （此语句具有尚未执行） 暂停应用程序执行的语句。

F11 是要检查的大多数详细信息中的执行流的好方法。 （若要通过代码更快地移动，我们展示其他一些选项。）默认情况下，调试器跳过非用户代码 (如果你希望更多详细信息，请参阅[仅我的代码](../debugger/just-my-code.md))。

>[!NOTE]
> 在托管代码中，你将看到一个询问你是否想要自动逐过程执行属性和运算符 （默认行为） 时通知对话框。 如果你想要更改设置更高版本，禁用**逐过程执行属性和运算符**中设置**工具 > 选项**下的菜单**调试**。

## <a name="step-over-code-to-skip-functions"></a>单步执行代码，以跳过函数

当所使用的是一个函数或方法调用的代码行时，你可以按 F10 (**调试 > 逐过程**) 而不是 F11。

F10 使调试器，而无需单步执行函数或应用程序代码 （仍执行的代码） 中的方法。 按 F10，你可以跳过你不感兴趣的代码。 这样一来，你可以快速访问你更感兴趣的代码。

## <a name="step-into-a-property"></a>单步执行属性

如前所述，默认情况下，调试器跳过托管的属性和字段，但**单步执行特定**命令允许你重写此行为。

右键单击某个属性或字段，然后选择**单步执行特定**，然后选择可用的选项之一。

![单步执行特定](../debugger/media/dbg-tour-step-into-specific.png "单步执行特定")

在此示例中，**单步执行特定**我们到达的代码`Path.set`。

![单步执行特定](../debugger/media/dbg-tour-step-into-specific-2.png "单步执行特定")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>运行到在你代码中快速使用鼠标的点

在调试器中，将鼠标悬停在一行代码之前**运行到单击**（运行执行到此处） 按钮![运行到单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")显示在左侧。

![运行到单击](../debugger/media/dbg-tour-run-to-click-2.png "到单击运行")

>  [!NOTE] 
> **运行到单击**是中新增功能 （运行执行到此处） 按钮[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

单击**运行到单击**（运行执行到此处） 按钮。 调试器将进入第的代码行您单击的位置。

使用此按钮是类似于设置临时断点。 此命令也是便于快速绕过应用程序代码的可见区域内。 你可以使用**运行到单击**中任何打开的文件。

## <a name="advance-the-debugger-out-of-the-current-function"></a>向前移动跳出当前函数调试器

有时，你可能想要继续调试会话但前移一直到当前函数调试器。

按下 Shift + F11 (或**调试 > 跳出**)。

此命令恢复应用程序执行 （和使调试器） 直到当前函数返回。

## <a name="run-to-cursor"></a>运行到光标处

停止了调试器，通过按**停止调试**的红色按钮![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")或 Shift + F5。

右键单击你的应用程序中的代码行，然后选择**运行到光标处**。 此命令将开始调试，并在当前代码行上设置一个临时断点。

![运行到光标处](../debugger/media/dbg-tour-run-to-cursor.png "运行到光标处")

如果设置断点时，调试器将暂停上抵达第一个断点。

按 F5，直到到达的代码行到选择的其中**运行到光标处**。

当你编辑代码，并想要快速设置临时断点，然后启动调试器时，此命令非常有用。


> [!NOTE]
> 你可以使用**运行到光标处**中**调用堆栈**窗口进行调试时。

## <a name="restart-your-app-quickly"></a>快速重新启动您的应用程序

单击**重新启动**![重新启动应用](../debugger/media/dbg-tour-restart.png "重新启动应用")中调试工具栏按钮 (**Ctrl + Shift + F5**)。

当你按**重新启动**，从而节省了时间而不是停止应用并重新启动调试器。 在第一个命中通过执行代码的断点处暂停调试器。

如果您想要停止了调试器，并返回到代码编辑器中，你可以按红色停止![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")按钮而不是**重新启动**。

## <a name="inspect-variables-with-data-tips"></a>检查与数据提示的变量

现在，你有点知道你采用相反的方法，你可以开始检查使用调试程序时你应用程序的状态 （变量） 的最佳时机。 允许你检查变量的功能是一些最有用的功能的调试器，并通过不同的方式来完成此操作。 通常情况下，当你尝试调试问题，您试图从中找出变量是否存储您希望他们能够在特定应用程序的状态中的值。

在暂停时在调试器中，将鼠标悬停在用鼠标的对象，并查看其默认属性值 (在此示例中，文件名`market 031.jpg`是默认属性值)。

![查看数据提示](../debugger/media/dbg-tour-data-tips.gif "查看数据提示")

展开要查看其属性的对象 (如`FullPath`在此示例中的属性)。

通常情况下，在调试时，你需要一种快速的方式来检查对象的属性值和数据提示是一种好方法，以执行此操作。

> [!TIP]
> 在最受支持的语言中，你可以编辑在调试会话过程的代码。 有关详细信息，请参阅[编辑并继续](../debugger/edit-and-continue.md)。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>检查与自动和局部变量窗口的变量

调试时，查看**自动**底部的代码编辑器窗口。

![自动窗口](../debugger/media/dbg-tour-autos-window.png "自动窗口")

在**自动**窗口中，你将看到沿其当前值和它们的类型的变量。 **自动**窗口将显示在当前行或前面的行上使用的所有变量 （在 c + + 中，窗口将都显示变量中的代码的前面三行。 查看文档，了解特定于语言的行为）。

> [!NOTE]
> 在 JavaScript 中，**局部变量**但不是支持窗口**自动**窗口。

接下来，查看**局部变量**窗口。 **局部变量**窗口显示当前位于范围内的变量。

![局部变量窗口](../debugger/media/dbg-tour-locals-window.png "局部变量窗口")

在此示例中，`this`对象和对象`f`作用域中。 有关详细信息，请参阅[自动和局部变量窗口中检查变量](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>设置监视

你可以使用**监视**窗口上指定一个变量 （或表达式），你想要跟踪。

调试时，右键单击某个对象，然后选择**添加监视**。

![监视窗口](../debugger/media/dbg-tour-watch-window.png "监视窗口")

在此示例中，必须在上设置监视`File`对象，也可以查看当你移动通过调试器时更改其值。 与其他变量窗口中，不同**监视**windows 始终显示的变量正在监视 （它们灰显时超出范围）。

有关详细信息，请参阅[设置使用监视和快速监视窗口监视](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>检查调用堆栈

单击**调用堆栈**这是默认情况下在较低的右窗格中打开的窗口在调试过程。

![检查调用堆栈](../debugger/media/dbg-tour-call-stack.png "检查调用堆栈")

**调用堆栈**窗口将显示在其中调用方法和函数获取的顺序。 顶部行显示当前函数 (`Update`在此示例中的方法)。 第二行显示`Update`从进行了调用`Path.set`属性，依次类推。 调用堆栈是一种好方法，以检查并了解应用程序的执行流。

> [!NOTE]
> **调用堆栈**在 Eclipse 如某些 Ide 窗口是类似于调试透视。

你可以双击要打算看看该源代码的代码行，并还更改正在检查由调试器当前作用域。 这不提升调试器。

你还可以使用从右击菜单**调用堆栈**窗口来执行其他操作。 例如，可以插入到特定函数的断点，重新启动你的应用使用**运行到光标处**，并转检查源代码。 请参阅[如何： 检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="examine-an-exception"></a>检查异常

当你的应用程序引发了异常时，则调试器将会引发异常的代码的行。
     
![异常帮助器](../debugger/media/dbg-tour-exception-helper.png "异常帮助器")

在此示例中，**异常帮助器**演示`System.Argument`异常和错误消息，指出该路径不是合法的窗体。 因此，我们知道该错误出现在方法或函数的自变量。

在此示例中，`DirectoryInfo`调用上中存储的空字符串提供错误`value`变量。

异常帮助程序是一项强大功能，可帮助你调试错误。 你可以执行诸如查看错误详细信息，并从异常帮助器添加监视。 或者，如果需要你可以更改引发特定异常的条件。

>  [!NOTE] 
> 异常帮助器替换异常助手中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

展开**异常设置**节点以查看更多选项如何处理这种异常类型，但你无需更改为本教程的任何内容 ！

## <a name="more-features-to-look-at"></a>要查看的多个功能

-   [调试器提示和技巧](../debugger/debugger-tips-and-tricks.md)了解如何使用调试器提高生产率。

-   [编辑并继续](../debugger/edit-and-continue.md)对于语言 (C#、 c + +、 Visual Basic) 的一个子集，编辑并继续功能允许你编辑在调试会话过程的代码。

-   [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)描述如何调试多线程应用程序。 

-   [远程调试](../debugger/remote-debugging.md)描述如何调试在其他计算机或设备上运行的应用。 
  
-   [IntelliTrace](../debugger/intellitrace.md)介绍 Visual Studio Enterprise 中的 IntelliTrace 功能。 你可以使用该记录和跟踪你代码的执行历史记录。

-   [网络使用情况](../profiling/network-usage.md)描述可用于调试 web 服务和其他网络资源在通用 Windows 应用 (UWP) 的分析工具。 该工具用于检查有效负载。

-   [调试接口访问 SDK](../debugger/debug-interface-access/debug-interface-access-sdk.md)描述 Microsoft 调试接口访问软件开发工具包 (DIA SDK)。 DIA SDK 提供对存储在由 Microsoft 后置编译器工具生成的程序数据库 (.pdb) 文件中的调试信息的访问。  

## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)
