---
title: "调试多线程应用程序使用线程窗口 |Microsoft 文档"
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
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
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4469f2f70bececca258fe4ea1a98d753f8349f87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debug-a-multithreaded-application-in-visual-studio-using-the-threads-window"></a>演练： 调试多线程应用程序在 Visual Studio 中使用线程窗口
Visual Studio 提供**线程**窗口和其他用户界面元素，以帮助你调试多线程应用程序。 本教程演示如何使用**线程**窗口和**调试位置**工具栏。 有关其他工具的信息，请参阅[开始调试多线程应用程序](../debugger/get-started-debugging-multithreaded-apps.md)。 本教程只需几分钟，但完成它将使您熟悉用于调试多线程应用程序的功能。   
  
若要开始本教程，你需要一个多线程应用程序项目。 请按照下面列出的步骤创建该项目。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>若要创建多线程应用程序项目  
  
1.  上**文件**菜单上，选择**新建**，然后单击**项目**。  
  
     此时将出现 “新建项目” 对话框。  
  
2.  在**项目类型**s 框中，单击你选择的语言： **Visual Basic**， **Visual C#**，或**Visual c + +**。  
  
3.  在**模板**框中，选择**控制台应用程序**。  
  
4.  在**名称**框中，键入名称 MyThreadWalkthroughApp。  
  
5.  单击“确定”。  
  
     新的控制台项目随即显示。 创建该项目后，将显示源文件。 根据所选的语言，源文件的名称可能是 Module1.vb、Program.cs 或 MyThreadWalkthroughApp.cpp  
  
6.  删除显示在源文件中的代码并将其显示在"创建线程"主题的部分中的示例代码替换[创建线程并在启动时传递数据](/dotnet/standard/threading/creating-threads-and-passing-data-at-start-time)。  
  
7.  上**文件**菜单上，单击**保存所有**。  
  
#### <a name="to-begin-the-tutorial"></a>若要开始使用本教程  
  
-   在源代码编辑器中，查找以下代码：  
  
    ```VB  
    Thread.Sleep(3000)   
    Console.WriteLine(  
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
  
#### <a name="to-start-debugging"></a>开始调试  
  
1.  单击左滚动条槽中`Console.WriteLine`用于插入新断点的语句。  
  
     在源代码编辑器左侧槽中，将显示一个红色圆圈。 这表示现在已在该位置设置了一个断点。  
  
2.  上**调试**菜单上，单击**启动调试**(**F5**)。  
  
     调试开始，您的控制台应用程序开始运行，随后在断点处停止。  
  
3.  如果此时控制台应用程序窗口具有焦点，请在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 窗口中单击以使焦点返回到 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
4.  在源代码编辑器中，找到包含以下代码行：  
  
    ```VB  
    Thread.Sleep(5000)   
    ```  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```
  
#### <a name="to-discover-the-thread-marker"></a>发现线程标记  

1.  在调试工具栏中，单击**在源中显示线程**按钮![在源中显示线程](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")。 
  
2.  查看窗口左侧的滚动条槽。 在这行内容，你将看到*线程标记*图标![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，类似于两根细线。 线程标记指示线程在此位置停止。  
  
3.  将指针悬停在线程标记上。 屏幕上显示数据提示。 数据提示将告诉您每个已停止线程的名称和线程 ID 号。 在此情况下，只有一个线程，其名称可能是 `<noname>`。  

    > [!TIP]
    > 你可能会发现有助于通过重命名它们识别无名称的线程。 在线程窗口中，选择**重命名**上右键单击后**名称**线程行中的列。
  
4.  右键单击要查看的快捷菜单上的可用选项的线程标记。 
    
  
## <a name="flagging-and-unflagging-threads"></a>标记线程和取消标记线程  
您可以标记要格外关注的线程。 标记线程是一种好的方法来跟踪重要线程并忽略您不关心的线程。  
  
#### <a name="to-flag-threads"></a>标记线程   

1.  上**视图**菜单上，指向**工具栏**。  
  
    请确保**调试位置**选择工具栏。

2.  转到**调试位置**工具栏，然后单击**线程**列表。  
  
    > [!NOTE]
    >  你可以通过三个突出显示的列表中识别此工具栏：**过程**，**线程**，和**堆栈帧**。  
  
3.  请注意列表中显示的线程数目。  
  
4.  返回到源代码编辑器并右击线程标记![线程标记](../debugger/media/dbg-thread-marker.png "ThreadMarker")试。  
  
5.  在快捷菜单上，指向**标志**，然后单击线程名称和 ID 号。  
  
6.  返回到**调试位置**工具栏和查找**仅显示标记的线程**图标![显示标记的线程](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")到右侧的**线程**列表。  
  
    按钮上的标志图标之前灰显。 现在，它是活动的按钮。  
  
7.  单击**仅显示标记的线程**图标。  
  
    现在只有标记的线程显示在该列表中。 (你可以单击单个标记按钮切换回**显示所有线程**模式。)

8. 线程窗口打开，请选择**调试 > Windows > 线程**。

    ![线程窗口](../debugger/media/dbg-threads-window.png "ThreadsWindow")  
  
    在**线程**窗口中，标记的线程已附加到它以突出显示红色标志图标。

    > [!TIP]
    > 当你具有标记的一些线程时，可以右键单击代码编辑器中的代码行，然后选择**运行到光标处的标记线程**（请确保你选择的所有标记的线程的代码将到达）。 这将暂停代码，使其变得更容易控制的执行顺序的选定行上的线程[冻结和解冻线程](#bkmk_freeze)。
  
11. 在源代码编辑器中，再次右键单击线程标记。  
  
     请注意此时快捷菜单上提供的选项。 而不是**标志**，你现在请参阅**取消标记**。 不要单击**取消标记**。  

     若要了解如何取消标记线程，请转到下一个过程。  
  
#### <a name="to-unflag-threads"></a>取消标记线程  
  
1.  在**线程**窗口中，右键单击标记的线程与对应的行。  
  
     一个快捷菜单随即显示。 其中包括选项**取消标记**和**取消标志所有线程**。  
  
2.  若要取消标记线程，请单击**取消标记**。  

    查看**调试位置**再次工具栏。 **仅显示标记的线程**按钮再次灰显。 这是因为您已取消标记唯一的已标记线程。 由于没有任何已标记的线程，工具栏已将返回到**显示所有线程**模式。 单击**线程**列出并验证你可以看到所有线程。  
  
5.  返回到**线程**窗口并检查信息列。  
  
    在第一列中，你将注意到线程列表的每一行中的标志大纲图标。 （大纲情况意味着线程已取消标记）。  
  
6.  单击两个线程、 第二个和第三从列表底部的标志大纲图标。 

    标记图标变为纯红色，而非空心边框。  
  
7.  单击该标记列顶部的按钮。  
  
    单击该按钮时，线程列表的顺序将会改变。 此时，线程列表的排序形式为标记的线程位于顶部。  
  
8.  再次单击该标记列顶部的按钮。  
  
    排序顺序再次改变。  
  
## <a name="more-about-the-threads-window"></a>有关“线程”窗口的更多信息  
  
#### <a name="to-learn-more-about-the-threads-window"></a>了解有关“线程”窗口的更多信息  
  
1.  在**线程**窗口中，检查从左侧起第三个列。 在此列顶部的按钮**ID**。  
  
2.  单击**ID**。  
  
     此时，线程列表按照线程 ID 号排序。  
  
3.  右击列表中的任意线程。 在快捷菜单上，单击**十六进制显示**。  
  
     线程 ID 号的格式将会改变。  
  
4.  将鼠标指针悬停**位置**列列表中的任何线程。  
  
     经过短暂的延迟后，将会出现数据提示。 其中显示线程的部分调用堆栈。

     > [!TIP]
     > 有关线程的调用堆栈的图形视图中，打开[并行堆栈](../debugger/using-the-parallel-stacks-window.md)窗口 (调试时，选择**调试 / Windows / 并行堆栈**)。  
  
5.  从左侧，该列标记为查看第四个列**类别**。 线程按类别分类。  
  
     进程中创建的第一个线程称为主线程。 请在线程列表中找到它。  
  
6.  右击主线程，然后单击**切换到线程**。  
  
     A**中断模式**窗口随即显示。 它告诉你调试器当前正在不执行任何代码，它可以显示 （因为它是主线程）。   
  
7.  查看**调用堆栈**窗口和**调试位置**工具栏。  
  
     内容**调用堆栈**窗口已更改。 

## <a name="bkmk_freeze"></a>冻结和解冻线程执行 

你可以冻结和解冻 （挂起和恢复） 线程控制，线程执行工作的顺序。 这可以帮助你解决并发问题，例如死锁和争用条件。

> [!TIP]
> 如果你想要按照单个线程冻结其他线程 （也一种常见调试方案），请参阅[开始调试多线程应用程序](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread)。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>冻结和解冻线程  
  
1.  在**线程**窗口中，右击任何线程，然后单击**冻结**。  
  
2.  查看第二个列 （当前线程列）。 暂停图标现在显示存在。 这些暂停图标指示该线程已冻结。  
  
3.  显示**挂起项计数**列中选择该**列**列表。

    此时线程的挂起计数是 1。  
  
4.  右击冻结的线程，然后单击**解冻**。  
  
     当前线程列与**挂起项计数**列发生更改。 
  
## <a name="switching-the-to-another-thread"></a>切换到另一个线程 
  
#### <a name="to-switch-threads"></a>切换线程  
  
1.  在**线程**窗口中，检查从左侧 （当前线程列） 的第二个列。 此列顶部的按钮上没有文本或图标。
  
2.  查看当前的线程列，并会看到一个线程带有黄色箭头。 黄色箭头指示此线程是当前线程 （这是执行指针的当前位置）。
  
    记下的线程 ID 号，你看到的当前线程图标。 会将当前线程图标移动到另一个线程，但是必须先将其放回完成后。 
  
3.  右键单击另一个线程，然后单击**切换到线程**。  
  
4.  查看**调用堆栈**在源代码编辑器的窗口。 其内容已经更改。  
  
5.  查看**调试位置**工具栏。 当前线程图标太已更改。  
  
6.  转到**调试位置**工具栏。 选择与不同的线程**线程**列表。  
  
7.  查看**线程**窗口。 当前线程图标已更改。  
  
8. 在源代码编辑器中，右击线程标记。 在快捷菜单上，指向**切换到线程**，再单击线程名称 /ID 号。  
  
     您现在已经了解将当前线程图标更改为另一个线程的三种方式： 使用**线程**窗口中，**线程**列入**调试位置**工具栏上，与在源代码编辑器中的线程标记。  
  
     与线程标记中，你只能切换到在特定位置停止的线程。 通过使用**线程**窗口和**调试位置**工具栏上，你可以切换到任何线程。   
  
## <a name="see-also"></a>另请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在调试时切换到另一个线程](../debugger/how-to-switch-to-another-thread-while-debugging.md)