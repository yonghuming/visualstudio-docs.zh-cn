---
title: "调试器入门 |Microsoft 文档"
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords: debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f6bcc75341297ad20d66514c92f92513ef44d2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="get-started-with-the-visual-studio-debugger"></a>要开始使用 Visual Studio 调试器

本主题介绍中的分步演练的 Visual Studio 调试器的功能。 如果你想调试器功能的更高级别的视图，请参阅[调试器功能教程](../debugger/debugger-feature-tour.md)。

你可以既读取沿若要查看的调试器功能，或可以下载功能教程中使用的完整示例，并请按照用户的步骤。 若要下载示例并遵循，请转到[照片查看器演示](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

|         |         |
|---------|---------|
| ![观看视频](../install/media/video-icon.png "WatchVideo") | [观看视频](#video)调试显示类似的步骤。 |

尽管演示应用程序是 C#，但功能都适用于 c + +、 Visual Basic、 JavaScript 和其他语言支持的 Visual Studio （除指明外）。

## <a name="start-the-debugger"></a>启动调试器 ！

1. 若要执行沿 Visual Studio 中的以下步骤，下载示例[此页上](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a)。

    > [!IMPORTANT]
    > 你需要安装 Visual Studio 与运行演示中我们将使用的应用的.NET 桌面开发工作负荷。

2. 相关项目进行解压缩。

3. 打开 Visual Studio 并选择**文件 > 打开**菜单命令，然后选择**项目/解决方案**，然后打开下载项目的文件夹中。

     ![打开示例项目](../debugger/media/dbg-tour-open-project.png "打开项目")

3. 打开 WPF 照片查看器演示 > C# 文件夹，选择 photoapp.sln 文件中，并选择**打开**。

     在 Visual Studio 中打开该项目。 解决方案资源管理器右窗格中的显示所有项目文件。

    ![解决方案资源管理器文件](../debugger/media/dbg-tour-solution-explorer.png "解决方案资源管理器")

4. 按 F5 (**调试 > 启动调试**或**启动调试**按钮![启动调试](../debugger/media/dbg-tour-start-debugging.png "启动调试")调试工具栏中)。

     ![照片查看器应用](../debugger/media/dbg-tour-wpf-app.png "照片查看器应用程序")

     F5 启动调试器附加到应用程序过程中，但右，现在我们尚未添加任何断点或进行任何特殊操作便可检查代码的应用程序。 因此应用程序只需加载并查看照片映像。

     在此教程中，我们需要进一步查看此应用程序中使用调试器，看一看调试器功能。

5. 停止了调试器，通过按红色停止![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")按钮。

## <a name="set-a-breakpoint-and-start-the-debugger"></a>设置断点并启动调试器

若要调试，需要使用调试程序附加到应用程序进程中启动您的应用程序。

1. 在`MainWindow`构造函数的 MainWindow.xaml.cs，通过单击左边的距的第一行代码来设置断点。

     ![设置断点](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

6. 按 F5 或**启动调试**按钮，应用将启动，然后调试器会运行的代码行到你在其中设置断点。

    黄色箭头表示在其暂停调试器，它还将在同一时刻 （此语句具有尚未执行） 暂停应用程序执行的语句。

    F5 继续运行到下一个断点的应用程序。 （如果应用程序尚未运行，F5 启动调试器并在第一个断点处停止。）

    当你知道代码的行或你想要检查详细信息中的部分时，断点是代码的一个有用的功能。

## <a name="restart-your-app-quickly"></a>快速重新启动您的应用程序

1. 单击**重新启动**![重新启动应用](../debugger/media/dbg-tour-restart.png "RestartApp") （Ctrl + Shift + F5） 的调试工具栏中的按钮。

    当你按**重新启动**，从而节省了时间而不是停止应用并重新启动调试器。 在第一个命中通过执行代码的断点处暂停调试器。

    调试器中设置的断点处再次停止`MainWindow`构造函数。

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>导航代码在调试器中使用步骤命令

大多数情况下，我们使用键盘快捷方式在这里，因为它是一种好的方法来获取快速在调试器 （等效命令如菜单命令显示在括号中） 中执行你的应用程序。

1. 按 F11 (**调试 > 单步执行**) 两次以转到应用的执行`InitializeComponent()`函数。

     ![使用 F11 单步执行代码到](../debugger/media/dbg-tour-f11.png "F11 单步执行")

     F11 是**单步执行**命令，并向前移动一次的应用程序执行一个语句。 F11 是要检查的大多数详细信息中的执行流的好方法。 （若要通过代码更快地移动，我们展示一些其他选项也。）默认情况下，调试器跳过非用户代码 (如果你希望更多详细信息，请参阅[仅我的代码](../debugger/just-my-code.md))。

     >[!NOTE]
     > 在托管代码中，你将看到一个询问你是否想要自动逐过程执行属性和运算符 （默认行为） 时通知对话框。 如果你想要更改设置更高版本，禁用**逐过程执行属性和运算符**中设置**工具 > 选项**下的菜单**调试**。

2. 按 F10 (**调试 > 逐过程**) 几次，直到在第一行中的代码，调试器将停止`OnApplicationStartup`事件处理程序。

     ![逐过程代码中使用 F10](../debugger/media/dbg-tour-f10-step-over.png "F10 逐过程")

     F10 使调试器，而无需单步执行函数或应用程序代码 （仍执行的代码） 中的方法。 按 F10`InitializeComponent`方法调用 （而不是 F11)，我们跳过的实现代码`InitializeComponent`(我们不感兴趣稍后再试哪些 maybe)。

## <a name="step-into-a-property"></a>单步执行属性

1. 使用调试程序在此代码行上暂停：

    ````
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    右键单击代码行，然后选择**单步执行特定**，然后**SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![使用单步执行特定功能](../debugger/media/dbg-tour-step-into-specific.png "单步执行特定")

    如前所述，默认情况下，调试器跳过托管的属性和字段，但**单步执行特定**命令允许你重写此行为。 现在，我们想要查看会发生什么情况时`Path.set`属性 setter 运行。 **单步执行特定**获取我们到`Path.set`此处的代码。

     ![单步执行特定的结果](../debugger/media/dbg-tour-step-into-specific-2.png "单步执行特定")

     `Update`方法在此代码看起来可能是有趣，现在，让我们使用调试器检查近视该代码。

5. 将鼠标悬停在`Update`方法直到绿色**运行到单击**按钮![运行到单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")显示在左侧。

     ![使用运行到单击功能](../debugger/media/dbg-tour-run-to-click-2.png "到单击运行")

    >  [!NOTE] 
    > **运行到单击**按钮是中的新增功能[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。 如果看不到绿色箭头按钮，改用 F11 在此示例中向前移动调试器。

6. 单击**运行到单击**按钮![运行到单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

    使用此按钮是类似于设置临时断点。 **运行到单击**适用于快速绕过 （您可以在任何打开的文件内单击的） 的应用程序代码的可见区域内。

    调试器将进入第`Update`方法实现。

7. 按 f11 键进入并单步执行`Update`方法。

     ![单步执行更新方法的结果](../debugger/media/dbg-tour-update-method.png "步骤到 Update 方法")

    我们在这里找到看起来很有趣; 一些更多代码该应用将获取所有 *.jpg 文件驻留在一个特定的目录，然后再创建一个用于每个文件的照片对象。 此代码为我们提供了启动检查使用调试程序时你应用程序的状态 （变量） 的最佳时机。

    允许你检查变量的功能是的调试程序时，最有用的功能之一，通过不同的方式来完成此操作。 通常情况下，当你尝试调试问题，您试图从中找出变量是否存储您希望他们能够在特定时间的值。

## <a name="inspect-variables-with-data-tips"></a>检查与数据提示的变量

1. 若要在暂停调试器`Add`方法调用，将鼠标悬停在`Add`方法调用，并单击**到单击运行**按钮![运行到单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")。

2. 现在，将鼠标悬停在文件对象 (`f`)，你将看到其默认属性值的文件名称`market 031.jpg`。

     ![查看数据提示](../debugger/media/dbg-tour-data-tips.gif "查看数据提示")

3. 展开的对象，若要查看所有属性，如`FullPath`属性。

    通常情况下，在调试时，你需要一种快速的方式来检查对象的属性值和数据提示是一种好方法，以执行此操作。

    > [!TIP]
    > 在最受支持的语言中，你可以编辑调试器会话期间的代码，如果你找到想要更改的内容。 有关详细信息，请参阅[编辑并继续](../debugger/edit-and-continue.md)。 若要在此应用程序中使用该功能，但是，我们将首先需要更新的.NET framework 的应用程序的版本。

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>检查与自动和局部变量窗口的变量

1. 查看**自动**底部的代码编辑器窗口。

     ![检查自动窗口中的变量](../debugger/media/dbg-tour-autos-window.png "自动窗口")

    在**自动**窗口中，请参阅变量和其当前值。 **自动**窗口将显示在当前行或前面的行上使用的所有变量 （在 c + + 中，窗口将都显示变量中的代码的前面三行。 查看文档，了解特定于语言的行为）。

    > [!NOTE]
    > 在 JavaScript 中，**局部变量**但不是支持窗口**自动**窗口。

2. 接下来，查看**局部变量**窗口。

    **局部变量**窗口显示当前作用域中的变量。

    ![检查局部变量窗口中的变量](../debugger/media/dbg-tour-locals-window.png "局部变量窗口")

    目前，`this`对象和文件对象 (`f`) 的当前作用域中。 有关详细信息，请参阅[自动和局部变量窗口中检查变量](../debugger/autos-and-locals-windows.md)。

## <a name="set-a-watch"></a>设置监视

1. 在主代码编辑器窗口中，右键单击文件对象 (`f`)，然后选择**添加监视**。

    你可以使用**监视**窗口上指定一个变量 （或表达式），你想要跟踪。

    现在，你必须在上设置监视`File`对象，也可以查看当你移动通过调试器时更改其值。 与其他变量窗口中，不同**监视**窗口始终显示的变量正在监视 （它们灰显时超出范围）。

2. 上`Add`方法中，单击绿色![运行到单击](../debugger/media/dbg-tour-run-to-click.png "RunToClick")再次按钮 （或按 F11 几次） 以前进到`foreach`循环。

    ![在变量上设置监视](../debugger/media/dbg-tour-watch-window.png "监视窗口")

    你可能还会看到添加到正在运行的主窗口第一张图片示例应用，但这发生在不同的应用程序线程，因此映像可能不可见尚未。

    有关详细信息，请参阅[设置使用监视和快速监视窗口监视](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>检查调用堆栈

1. 单击**调用堆栈**窗口中，这是默认情况下在较低的右窗格中打开。

     ![检查调用堆栈](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

    **调用堆栈**窗口将显示在其中调用方法和函数获取的顺序。 顶部行显示当前函数 (`Update`教程应用程序中的方法)。 第二行显示`Update`从进行了调用`Path.set`属性，依次类推。

    >  [!NOTE]
    > **调用堆栈**在 Eclipse 如某些 Ide 窗口是类似于调试透视。

    调用堆栈是一种好方法，以检查并了解应用程序的执行流。

    你可以双击要打算看看该源代码的代码行，并还更改正在检查由调试器当前作用域。 此操作不提升调试器。

    你还可以使用从右击菜单**调用堆栈**窗口来执行其他操作。 例如，可以将断点插入到指定的函数、 向前移动使用调试器**运行到光标处**，并转检查源代码。 有关详细信息，请参阅[如何： 检查调用堆栈](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="change-the-execution-flow"></a>更改执行流

1. 使用调试程序上暂停`Add`方法调用时，使用鼠标左侧获取黄色箭头 （执行指针），并移动的黄色箭头上移一行到`foreach`循环。

     ![执行将指针移动到](../debugger/media/dbg-tour-move-the-execution-pointer.gif "执行将指针移动到")

    通过更改执行流，你可以执行某些操作，如测试不同的代码执行路径，或重新运行代码，无需重新启动调试器。

2. 现在，按 F5。

    你可以看到添加到应用程序窗口的映像。 由于正在重新运行中的代码`foreach`已两次添加循环，探讨了 ！
    
    > [!WARNING]
    > 通常，您需要小心使用此功能，并查看工具提示中的某个警告。 你可能会太看到其他警告。 将指针移无法还原到较早的应用程序状态的应用程序。

## <a name="run-to-cursor"></a>运行到光标处

1. 选择**停止调试**的红色按钮![停止调试](../debugger/media/dbg-tour-stop-debugging.png "停止调试")或 Shift + F5。

2. 在`Update`方法中，右键单击`Add`方法调用，并选择**运行到光标处**。 此命令将开始调试，并在当前代码行上设置一个临时断点。

     ![使用运行到光标功能](../debugger/media/dbg-tour-run-to-cursor.png "运行到光标处")

    你应在中的断点处暂停`MainWindow`（因为它是第一个断点。

3. 按 f5 键以前进到`Add`其中所选的方法**运行到光标处**。

    当你编辑代码，并想要快速设置临时断点，然后启动调试器时，此命令非常有用。

## <a name="step-out"></a>跳出

假设你已完成检查`Update`方法中 Data.cs，并且你想要获取跳出函数，但仍在调试器中。 你可以执行此使用**单步跳出**命令。

1. 按下 Shift + F11 (或**调试 > 跳出**)。

     此命令恢复应用程序执行 （和使调试器） 直到当前函数返回。

     应返回`Update`Data.cs 中的方法调用。

2. 按 Shift + F11 试，并使调试器在调用堆栈中向上转回`OnApplicationStartup`事件处理程序。

3. 按 F5 以继续。

## <a name="examine-an-exception"></a>检查异常

1. 在正在运行的应用程序窗口中，删除中的文本**路径**输入的框，然后选择**更改**按钮。

     ![导致异常引发](../debugger/media/dbg-tour-cause-an-exception.png "会导致异常")

     应用程序引发异常，，调试器会打开的引发异常的代码行。
     
     ![异常帮助器](../debugger/media/dbg-tour-exception-helper.png "异常帮助器")

     在这里，**异常帮助器**演示`System.ArgumentException`和一条错误消息，指出该路径不是合法的窗体。 因此，我们知道该错误出现在方法或函数的自变量。

     在此示例中，`DirectoryInfo`调用上中存储的空字符串提供错误`value`变量。 (将鼠标悬停在`value`若要查看的空字符串。)

     异常帮助程序是一项强大功能，可帮助你调试错误。 你可以执行诸如查看错误详细信息，并从异常帮助器添加监视。 或者，如果需要你可以更改引发特定异常的条件。

    >  [!NOTE] 
    > 异常帮助器替换异常助手中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。

2. 展开**异常设置**节点以查看更多选项如何处理这种异常类型，但你无需更改为本教程的任何内容 ！

3. 按 F5 以继续应用程序。

若要了解有关调试器的功能的详细信息，请参阅[调试器提示和技巧](../debugger/debugger-tips-and-tricks.md)。

## <a name="video"></a>观看视频调试

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171" frameborder="0" allowfullscreen></iframe>
</div>

## <a name="see-also"></a>另请参阅  
 [在 Visual Studio 中进行调试](../debugger/index.md)  
 [调试器功能简介](../debugger/debugger-feature-tour.md)
