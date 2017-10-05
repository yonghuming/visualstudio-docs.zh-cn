---
title: "开始调试多线程应用程序 |Microsoft 文档"
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
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
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: 3ffb550707280d76756cbd144ed03f4143ce144b
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="get-started-debugging-a-multithreaded-application-in-visual-studio"></a>开始调试 Visual Studio 中的多线程应用程序
Visual Studio 提供的若干工具和用户界面元素，以帮助你调试多线程应用程序。 本教程演示如何使用线程标记**并行堆栈**窗口中，**并行监视**窗口中，条件断点，并筛选器断点。 本教程只需几分钟，但完成它将使您熟悉用于调试多线程应用程序的功能。

|         |         |
|---------|---------|
| ![观看视频](../install/media/video-icon.png "WatchVideo") | [观看视频](#video)上展示类似的步骤的多线程调试。 |

其他主题提供有关使用其他多线程调试工具的其他信息：

- 有关演示如何使用某个类似主题**调试位置**工具栏和**线程**窗口中，请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

- 与使用的示例类似主题<xref:System.Threading.Tasks.Task>（托管代码） 和并发运行时 （c + +），请参阅[演练： 调试并行应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)。 有关适用于最多线程应用程序类型的常规调试技巧，阅读本主题和链接的主题。
  
若要开始本教程，你需要一个多线程应用程序项目。 请按照下面列出的步骤创建该项目。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>若要创建多线程应用程序项目  
  
1.  上**文件**菜单上，选择**新建**，然后单击**项目**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  在**项目类型**s 框中，单击你选择的语言： **Visual C#**， **Visual c + +**，或**Visual Basic**。  
  
3.  在**模板**框中，选择**控制台应用程序**。  
  
4.  在**名称**框中，键入名称 MyThreadWalkthroughApp。  
  
5.  单击“确定”。  
  
     新的控制台项目随即显示。 创建该项目后，将显示源文件。 具体取决于你选择的语言，源文件可能 Program.cs、 MyThreadWalkthroughApp.cpp 或 Module1.vb 调用。  
  
6.  删除显示在源文件中的代码并将其替换为此处所示的示例代码。

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  上**文件**菜单上，单击**保存所有**。  
  
#### <a name="to-begin-the-tutorial"></a>若要开始使用本教程  
  
-   在源代码编辑器中，查找以下代码： 
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>开始调试  
  
1.  单击左滚动条槽中`Thread.Sleep`或`Thread::Sleep`用于插入新断点的语句。  
  
     在源代码编辑器左侧槽中，将显示一个红色圆圈。 这表示现在已在该位置设置了一个断点。 
  
2.  上**调试**菜单上，单击**启动调试**(**F5**)。  
  
     Visual Studio 生成该解决方案、 启动附带调试器，运行该应用程序和应用程序然后在断点处停止。  
  
    > [!NOTE]
    > 如果你将焦点切换到控制台窗口中，单击在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]窗口以使焦点返回到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
4.  在源代码编辑器中，找到包含断点的行：  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>若要发现线程标记  

1.  在调试工具栏中，单击**在源中显示线程**按钮![在源中显示线程](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。

2. 按**F11**一次向前移动代码的调试器一个行。
  
3.  查看窗口左侧的滚动条槽。 在这行内容，你将看到*线程标记*图标![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，类似于两根细线。 线程标记指示线程在此位置停止。

    请注意可能断点部分隐藏线程标记。 
  
4.  将指针悬停在线程标记上。 屏幕上显示数据提示。 数据提示将告诉您每个已停止线程的名称和线程 ID 号。 名称在这种情况下，可能是`<noname>`。 
  
5.  右键单击要查看的快捷菜单上的可用选项的线程标记。
    
## <a name="ParallelStacks"></a>查看线程的位置

在**并行堆栈**窗口中，你可以切换任务视图，并在视图间切换线程和 （对于基于任务的编程） 可以查看每个线程的调用堆栈信息。 在此应用中，我们可以使用线程视图。

1. 打开**并行堆栈**通过选择窗口**调试 > Windows > 并行堆栈**。 您应看到类似于以下内容 （的准确信息将当前位置的每个线程、 你的硬件和您的编程语言而异）。

    ![并行堆栈窗口](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    在此示例中，从左到右我们获取此信息：
    
    - 主线程 （左侧） 已停止上`Thread.Start`(停止点由线程标记图标表示![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker"))。
    - 两个线程已进入`ServerClass.InstanceMethod`，其中之一是当前线程 （黄色箭头），而另一个线程已停止在`Thread.Sleep`。
    - 此外启动新线程 （右侧） (上停止`ThreadHelper.ThreadStart`)。

2.  右键单击中的条目**并行堆栈**窗口来查看快捷菜单上的可用选项。

    你可以执行各种操作从这些右键单击菜单中，但对于本教程，我们将演示多个这些详细信息中**并行监视**窗口 （下一节）。

    > [!NOTE]
    > 如果你更感兴趣的列表，查看有关每个线程的信息，请使用**线程**窗口相反。 请参阅[演练： 调试多线程应用程序](../debugger/how-to-use-the-threads-window.md)。

## <a name="set-a-watch-on-a-variable"></a>在变量上设置监视

1. 打开**并行监视**通过选择窗口**调试 > Windows > 并行监视 > 并行监视 1**。

2. 单击单元格所在`<Add Watch>`文本 （或第四个列中的空标题单元格） 类型`data`，然后按 Enter。

    在窗口中显示每个线程数据变量的值。

3. 再次单击单元格所在`<Add Watch>`文本 （或第五个列中的空标题单元格） 类型`count`，然后按 Enter。

    在窗口中显示每个线程的计数变量的值。 （如果看不到尚未这么多信息，请尝试按 F11 几次向前移动在调试器中的线程的执行。）

    ![并行监视窗口](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 右键单击某个窗口以查看可用选项中的行。

## <a name="flagging-and-unflagging-threads"></a>标记线程和取消标记线程  
您可以标记要格外关注的线程。 标记线程是一种好的方法来跟踪重要线程并忽略您不关心的线程。  
  
#### <a name="to-flag-threads"></a>标记线程  

1. 在**并行监视**窗口中，按住 SHIFT 键并选择多个行。

2. 右键单击并选择**标志**。

    现在，所有选定的线程会将标记。 现在，你可以筛选，以仅显示已标记的线程。
  
3.  在**并行监视**窗口中，查找**仅显示标记的线程**按钮![显示标记的线程](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")。  
  
4.  单击**仅显示标记的线程**按钮。  
  
    现在只有标记的线程显示在该列表中。

    > [!TIP]
    > 当你具有标记的一些线程时，可以右键单击代码编辑器中的代码行，然后选择**运行到光标处的标记线程**（请确保你选择的所有标记的线程的代码将到达）。 这将暂停代码，使其更容易地控制的执行顺序的选定行上的线程[冻结和解冻线程](#bkmk_freeze)。

5.  单击**仅显示标记的线程**按钮切换回**显示所有线程**模式。
    
#### <a name="to-unflag-threads"></a>取消标记线程

若要取消标记线程，可以右键单击一个或多个标记的线程中**并行监视**窗口，然后选择**取消标记**。

## <a name="bkmk_freeze"></a>冻结和解冻线程执行 

> [!TIP]
> 你可以冻结和解冻 （挂起和恢复） 线程控制，线程执行工作的顺序。 这可以帮助你解决并发问题，例如死锁和争用条件。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>冻结和解冻线程  
  
1.  在**并行监视**窗口中，所有选定的行，右键单击并选择并**冻结**。

    在第二列中，暂停图标现在显示为每个行。 暂停图标指示该线程已冻结。

2.  通过单击对应的一行，取消选中行。

3.  右键单击某一行，然后选择**解冻**。

    在此行，指示已不再被冻结线程上的暂停图标将消失。

4.  切换到代码编辑器中，单击**F11**。 仅在未冻结的线程运行。

    应用程序还可以实例化某些新线程。 请注意，任何新线程是未标记，并且未被冻结。

## <a name="bkmk_follow_a_thread"></a>通过使用条件断点按照单线程

有时，它可以帮助执行在调试器中单个线程。 你可以执行该操作的一种方法是通过冻结你不感兴趣的线程，但在某些情况下，你可能希望按照单个线程冻结其他线程 （与特定 bug，例如重现）。 若要遵循的线程不冻结其他线程的情况下，必须避免破坏到除你感兴趣的线程上的代码。 你可以执行此操作通过设置[条件断点](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。

你可以设置断点，在不同情况下，例如线程名称或线程 id。 可能会有所帮助的另一种方法是在你知道将是唯一的每个线程的数据设置的条件。 这是常见的调试方案中，您是对更感兴趣比任何特定的线程中的一些特定的数据值。

#### <a name="to-follow-a-single-thread"></a>若要遵循的单个线程

1. 右键单击先前创建的断点并选择**条件**。

2. 在**断点设置**窗口中，键入`data == 5`条件表达式。

    ![条件断点](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 如果要对更感兴趣的特定线程，然后使用线程名称或线程 ID，此条件。 若要执行此操作在**断点设置**窗口中，选择**筛选器**而不是**条件表达式**，并按照筛选器提示。 你可能想要将应用程序代码中的线程命名 （因为线程 Id 进行更改时重新启动调试器）。

3. 关闭**断点设置**窗口。

4. 单击重新启动![重新启动应用](../debugger/media/dbg-tour-restart.png "RestartApp")按钮以重新启动调试会话。

    你将中断为其数据变量为 5 的线程上的代码。 在中查找的黄色箭头 （当前调试器上下文）**并行监视**窗口，以确认。

5. 现在，你可以单步执行代码 (F10) 和单步执行代码 (F11) 并遵循单个线程的执行。

    只要断点条件是唯一的线程，并且调试器不会命中 （可能需要禁用它们） 其他线程上的任何其他断点，可以单步执行代码并单步执行代码，而无需切换到其他线程。

    > [!NOTE]
    > 当你继续调试器时，将运行所有线程。 但是，调试器不会中断其他线程上的代码，除非有其他线程命中断点。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>有关多线程调试窗口的详细信息 

#### <a name="to-switch-to-another-thread"></a>若要切换到另一个线程 

- 若要切换到另一个线程，请参阅[How to： 切换到另一个线程中调试时](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

## <a name="video"></a>观看视频多线程调试

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171" frameborder="0" allowfullscreen></iframe>
</div>

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>若要了解有关并行堆栈和并行监视窗口  
  
- 请参阅[如何： 使用并行堆栈窗口](../debugger/using-the-parallel-stacks-window.md) 

- 请参阅[如何： 使用并行监视窗口](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>另请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)

