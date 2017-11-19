---
title: "演练： 调试并行应用程序 |Microsoft 文档"
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
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a532c2e238528ea32492aae22b001ab0955f8c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-parallel-application-in-visual-studio"></a>演练： 调试并行应用程序在 Visual Studio 中
本演练演示如何使用**并行任务**和**并行堆栈**窗口调试并行应用程序。 这些 windows 帮助你了解和验证使用的代码的运行时行为[任务并行库 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或[并发运行时](/cpp/parallel/concrt/concurrency-runtime)。 本演练提供了具有内置断点的代码示例。 代码中断后，本演练演示如何使用**并行任务**和**并行堆栈**windows 来对其进行检查。  
  
 本演练介绍了以下任务：  
  
-   如何在一个视图中查看所有线程的调用堆栈。  
  
-   如何查看在应用程序中创建的 `System.Threading.Tasks.Task` 实例的列表。  
  
-   如何查看任务（而不是线程）的实际调用堆栈。  
  
-   如何导航到代码从**并行任务**和**并行堆栈**windows。  
  
-   窗口如何通过分组、缩放和其他相关功能来处理缩放。  
  
## <a name="prerequisites"></a>先决条件  
 本演练假定**仅我的代码**启用 （默认情况下，在较新版本的 Visual Studio 中已启用）。 上**工具**菜单上，单击**选项**，展开**调试**节点中，选择**常规**，然后选择**启用仅我 （仅限托管） 的代码**。 如果未设置此功能，您仍可以使用本演练，但结果可能会与以下各图不同。  
  
## <a name="c-sample"></a>C# 示例  
 如果使用 C# 示例，本演练还将假定外部代码处于隐藏状态。 若要切换是否显示外部代码，请右键单击**名称**表标题**调用堆栈**窗口中，然后选中或清除**显示外部代码**。 如果未设置此功能，您仍可以使用本演练，但结果可能会与以下各图不同。  
  
## <a name="c-sample"></a>C++ 示例  
 如果使用 C++ 示例，则可以忽略本主题中对外部代码的引用。 外部代码仅适用于 C# 示例。  
  
## <a name="illustrations"></a>图示  
 本主题中的图示是在运行 C# 示例的四核计算机上记录的。 您也可以使用其他配置完成本演练，但您的计算机上显示的内容可能与这些图示不同。  
  
## <a name="creating-the-sample-project"></a>创建示例项目  
 本演练中的代码示例适用于不执行任何操作的应用程序。 其目的仅在于理解如何使用工具窗口调试并行应用程序。  
  
#### <a name="to-create-the-sample-project"></a>创建示例项目  
  
1.  在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。  
  
2.  在**已安装的模板**窗格中，选择 Visual C#、 Visual Basic 或 Visual c + +。 对于托管语言，请确保 [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] 显示在框架框中。  
  
3.  选择**控制台应用程序**，然后单击**确定**。 保留默认的调试配置。  
  
4.  在项目中打开 .cpp、.cs 或 .vb 代码文件。 删除其内容以创建一个空代码文件。  
  
5.  将所选语言的以下代码粘贴到上述空代码文件中。  
  
 [!code-csharp[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  上**文件**菜单上，单击**保存所有**。  
  
2.  上**生成**菜单上，单击**重新生成解决方案**。  
  
     请注意，有四个对 `Debugger.Break`（在 C++ 示例中为 `DebugBreak`）的调用。因此，您无需插入断点；您只需运行应用程序即可使其四次中断调试器。  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>使用“并行堆栈”窗口：“线程”视图  
 在“调试”菜单上，单击“启动调试”。 等待命中第一个断点。  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>查看一个线程的调用堆栈  
  
1.  上**调试**菜单上，指向**Windows** ，然后单击**线程**。 停靠**线程**窗口底部的 Visual Studio。  
  
2.  上**调试**菜单上，指向**Windows** ，然后单击**调用堆栈**。 停靠**调用堆栈**窗口 Visual Studio 底部。  
  
3.  在双击线程，**线程**窗口以使其作为当前。 当前线程具有一个黄色箭头。 当你更改当前线程时，其调用堆栈会显示在**调用堆栈**窗口。  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>查看“并行堆栈”窗口  
  
1.  上**调试**菜单上，指向**Windows** ，然后单击**并行堆栈**。 请确保**线程**在左上角的框中选择。  
  
     通过使用**并行堆栈**窗口中，你可以在一个视图中同时查看多个调用堆栈。 下图显示**并行堆栈**窗口上面**调用堆栈**窗口。  
  
     ![线程并行堆栈窗口中的视图](../debugger/media/pdb_walkthrough_1.png "PDB_Walkthrough_1")  
  
     主线程的调用堆栈显示在一个框中，其他四个线程的调用堆栈则划分到另一个框中。 将这四个线程划分在一起是因为其堆栈帧共享相同的方法上下文；也就是说，它们处于相同的方法中：`A`、`B` 和 `C`。 到视图的线程 Id 和名称的线程的同一框中，将鼠标悬停在标头 (**4 个线程**)。 当前线程显示为粗体，如下图所示。  
  
     ![显示线程 Id 和名称的工具提示](../debugger/media/pdb_walkthrough_1a.png "PDB_Walkthrough_1A")  
  
     黄色箭头指示当前线程的活动堆栈帧。 若要获取更多信息，请将鼠标指针悬停在堆栈帧上。  
  
     ![活动堆栈帧上的工具提示](../debugger/media/pdb_walkthrough_1b.png "PDB_Walkthrough_1B")  
  
     你可以设置要显示堆栈帧的多少细节 (**模块名称**，**参数类型**，**参数名称**，**参数值**，**行号**和**字节偏移量**) 中右键单击**调用堆栈**窗口。  
  
     方框周围的蓝色突出显示指示当前线程是该框的一部分。 工具提示中的粗体堆栈帧也可指示当前线程。 如果双击线程窗口中的主线程，则可以观察中的蓝色突出显示**并行堆栈**窗口将相应移动。  
  
     ![突出显示并行堆栈窗口中的主线程](../debugger/media/pdb_walkthrough_1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>继续执行到第二个断点  
  
1.  若要继续执行到命中第二个断点，请在**调试**菜单上，单击**继续**。 下图所示为第二个断点处的线程树。  
  
     ![显示多个分支的并行堆栈窗口](../debugger/media/pdb_walkthrough_2.png "PDB_Walkthrough_2")  
  
     在第一个断点处，所有四个线程均从 S.A 执行到 S.B 再到 S.C 方法。 验证信息是否仍会显示在**并行堆栈**窗口中，但是这四个线程已进一步。 其中一个线程继续执行到 S.D 再到 S.E。 另一个线程继续执行到 S.F、S.G 和 S.H。 其余两个线程继续执行到 S.I 和 S.J，其中一个线程从此方法执行到 S.K，而另一个线程继续执行到非用户外部代码。  
  
     你可以将鼠标悬停在框标题，例如， **1 个线程**或**2 个线程**以查看线程的线程的 Id。 将鼠标指针悬停在堆栈帧上可以查看线程 ID 和其他帧详细信息。 蓝色突出显示指示当前线程，黄色箭头指示当前线程的活动堆栈帧。  
  
     细线图标（重叠的蓝色和红色波浪线）指示非当前线程的活动堆栈帧。 在**调用堆栈**窗口中，双击 S.B 可以切换帧。 **并行堆栈**窗口通过使用绿色的曲线的箭头图标来指示当前线程的当前堆栈帧。  
  
     在**线程**窗口中，在线程间切换，并观察中的视图**并行堆栈**窗口将进行更新。  
  
     通过使用中的快捷菜单，可以切换到另一个线程或另一个线程的另一个帧**并行堆栈**窗口。 例如，右击 S.J，指向**切换到帧**，然后单击命令。  
  
     ![并行堆栈执行路径](../debugger/media/pdb_walkthrough_2b.png "PDB_Walkthrough_2B")  
  
     右击 S.C，指向**切换到帧**。 其中一个带有选中标记的命令指示当前线程的堆栈帧。 您可以切换到相同线程的上述帧（将仅移动绿色箭头），也可以切换到其他线程（将同时移动蓝色突出显示）。 下图所示为子菜单。  
  
     ![有两个选项时 J 为当前的 C 上的堆栈菜单](../debugger/media/pdb_walkthrough_3.png "PDB_Walkthrough_3")  
  
     与一个堆栈帧关联方法上下文时，框标题将显示**1 个线程**并且可通过双击切换到它。 如果双击关联有一个以上的帧的方法上下文，则会自动弹出该菜单。 将鼠标指针悬停在方法上下文上时，请注意右侧的黑色三角形。 单击该三角形也可以显示该快捷菜单。  
  
     对于具有多个线程的大型应用程序，您可能只希望关注某个线程子集。 **并行堆栈**窗口可以显示标记的线程调用堆栈。 在工具栏上，单击**仅显示已标记项**列表框旁边的按钮。  
  
     ![空并行堆栈窗口和工具提示](../debugger/media/pdb_walkthrough_3a.png "PDB_Walkthrough_3A")  
  
     接下来，在**线程**窗口中，标记线程，以查看调用堆栈中的显示方式**并行堆栈**窗口。 若要标记线程，请使用快捷菜单或线程的第一个单元格。 单击**仅显示已标记项**工具栏按钮再次以显示所有线程。  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>继续执行到第三个断点  
  
1.  若要继续执行到命中第三个断点，请在**调试**菜单上，单击**继续**。  
  
     如果有多个线程位于同一方法中，但该方法不在调用堆栈开头，则会在不同框中显示该方法。 当前断点处的一个示例是 S.L，它包含三个线程并在三个框中显示这三个线程。 双击 S.L。  
  
     ![并行堆栈窗口中的执行路径](../debugger/media/pdb_walkthrough_3b.png "PDB_Walkthrough_3B")  
  
     请注意，S.L 在其他两个框中为粗体，这样您可以看到 S.L 的其他显示位置。 如果你想要查看的帧 s.l 的调用和调用的帧，请单击**切换方法视图**工具栏上的按钮。 下图显示的方法视图**并行堆栈**窗口。  
  
     ![并行堆栈窗口中的方法视图](../debugger/media/pdw_walkthrough_4.png "PDW_Walkthrough_4")  
  
     请注意以上关系图以所选方法为中心并将其单独放在视图中间的方框中。 被调用方和调用方分别显示在顶部和底部。 单击**切换方法视图**按钮再次以退出此模式。  
  
     快捷菜单**并行堆栈**窗口还包括以下其他项。  
  
    -   **十六进制显示**用于切换在十进制和十六进制之间工具提示中的数字。  
  
    -   **符号加载信息**和**符号设置**打开相应的对话框。  
  
    -   **转到源代码**和**转到反汇编**所选方法编辑器中导航。  
  
    -   **显示外部代码**即使它们不在用户代码中显示所有帧。 使用此项可查看展开的关系图，其中包含其他帧（这些帧可能因没有相应符号而灰显）。  
  
     如果关系图较大，当单步执行到下一断点时，您可能希望视图自动滚动到当前线程的活动堆栈帧；即第一个命中该断点的线程。 在**并行堆栈**窗口中，请确保**自动滚动到当前堆栈帧**已启用工具栏上的按钮。  
  
     ![并行堆栈窗口中的自动滚动](../debugger/media/pdb_walkthrough_4a.png "PDB_Walkthrough_4A")  
  
2.  在继续之前**并行堆栈**窗口中，滚动到左侧和一直向下的所有方式。  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>继续执行到第四个断点  
  
1.  若要继续执行到命中第四个断点，请在**调试**菜单上，单击**继续**。  
  
     请注意视图如何自动滚动到位。 在中切换线程**线程**窗口或交换机堆栈帧中**调用堆栈**窗口，请注意如何视图一直自动滚动到正确的帧。 关闭**自动滚动到当前工具帧**选项并查看差异。  
  
     **鸟瞰**在大型关系图还有助于**并行堆栈**窗口。 你可以看到**鸟瞰**通过单击窗口右下角的滚动条之间的按钮，如下图中所示。  
  
     ![鸟瞰 &#45; 在并行堆栈窗口中查看的眼睛](../debugger/media/pdb_walkthrough_5.png "PDB_Walkthrough_5")  
  
     移动矩形可以快速移动到关系图的任何位置。  
  
     朝任意方向移动此关系图的另一种方法是：单击此关系图的空白区域并将其拖动到所需位置。  
  
     若要放大和缩小此关系图，请按住 Ctrl 并移动鼠标滚轮。 或者，也可以单击工具栏上的“缩放”按钮并使用缩放工具。  
  
     ![放大并行堆栈窗口中的堆栈](../debugger/media/pdb_walkthrough_5a.png "PDB_Walkthrough_5A")  
  
     你还可以查看堆栈按自上而下的方向而不是自下而上，通过单击**工具**菜单上，单击**选项**，然后选择或清除下方的选项**调试**节点。  
  
2.  在继续之前**调试**菜单上，单击**停止调试**以结束执行。  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>使用“并行任务”窗口和“并行堆栈”窗口的任务视图  
 继续之前，建议您先完成前面的过程。  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>重新启动应用程序，直到命中第一个断点  
  
1.  上**调试**菜单上，单击**启动调试**并等待命中第一个断点。  
  
2.  上**调试**菜单上，指向**Windows** ，然后单击**线程**。 停靠**线程**窗口底部的 Visual Studio。  
  
3.  上**调试**菜单上，指向**Windows**单击**调用堆栈**。 停靠**调用堆栈**窗口 Visual Studio 底部。  
  
4.  在双击线程，**线程**窗口将其作为当前。 当前线程具有一个黄色箭头。 更改当前线程时，将更新其他窗口。 接着，我们将查看任务。  
  
5.  上**调试**菜单上，指向**Windows** ，然后单击**并行任务**。 下图显示**任务**窗口。  
  
     ![在任务窗口中运行的四个任务](../debugger/media/pdw_walkthrough_6.png "PDW_Walkthrough_6")  
  
     对于运行的每一项任务，你可以读取其 ID（由名称相同的属性返回）、运行该任务的线程的 ID 和名称以及任务位置（悬停以显示具有整个调用堆栈的工具提示）。 此外，在**任务**列中，您可以看到已传递到该任务的方法; 换而言之，起始点。  
  
     可以对任何列进行排序。 请注意指示排序列和方向的排序标志符号。 您还可以通过向左或向右拖动列来对列重新排序。  
  
     黄色箭头指示当前任务。 通过双击某一任务或使用快捷菜单可以切换任务。 切换任务时，基础线程即成为当前线程并更新其他窗口。  
  
     在不同任务之间进行手动切换时，黄色箭头将相应移动，而白色箭头仍显示导致调试器中断的任务。  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>继续执行到第二个断点  
  
1.  若要继续执行到命中第二个断点，请在**调试**菜单上，单击**继续**。  
  
     以前，**状态**列以前将所有任务都显示为正在运行，但现在两个任务处于等待状态。 任务可能因多种不同原因而被阻止。 在**状态**列中，将鼠标悬停在正在等待的任务以了解其阻止原因。 例如，在下图中，任务 3 正在等待任务 4。  
  
     ![在任务窗口中的两个等待任务](../debugger/media/pdb_walkthrough_7.png "PDB_Walkthrough_7")  
  
     任务 4 又在等待分配给任务 2 的线程所拥有的监视器。  
  
     ![等待任务和任务窗口中的工具提示](../debugger/media/pdb_walkthrough_7a.png "PDB_Walkthrough_7A")  
  
     你可以对任务进行标记通过单击中的第一列的标志**任务**窗口。  
  
     你可以使用标记功能可以跟踪同一调试会话中的不同断点之间的任务或筛选的任务中显示其调用堆栈所**并行堆栈**窗口。  
  
     使用时**并行堆栈**窗口更早版本，你已查看了应用程序线程。 视图**并行堆栈**窗口再次，但这次查看应用程序任务。 执行此操作通过选择**任务**在左上方的框中。 下图所示为任务视图。  
  
     ![线程并行堆栈窗口中的视图](../debugger/media/pdb_walkthrough_8.png "PDB_Walkthrough_8")  
  
     当前未在执行任务的线程不会显示的任务视图中**并行堆栈**窗口。 此外，对于执行任务的线程，某些与任务无关的堆栈帧将从堆栈的顶部和底部筛选掉。  
  
     视图**任务**再次窗口。 右击任何列标题可以查看该列的快捷菜单。  
  
     ![任务窗口中的快捷视图菜单](../debugger/media/pdb_walkthrough_8a.png "PDB_Walkthrough_8A")  
  
     您可以使用此快捷菜单添加或移除列。 例如，AppDomain 列未处于选中状态；因此，不会在列表中显示它。 单击**父**。 **父**列出现没有任何任务的四个任务的值。  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>继续执行到第三个断点  
  
1.  若要继续执行到命中第三个断点，请在**调试**菜单上，单击**继续**。  
  
     此时，新任务（即任务 5）正在运行，而任务 4 则处于等待状态。 你可以通过查看其原因将鼠标悬停在正在等待的任务中**状态**窗口。 在**父**列，您会发现该任务 4 是任务 5 的父级。  
  
     要更好地直观地显示父-子关系，请右键单击**父**列标题并单击**父子视图**。 您应看到以下图示。  
  
     ![父 &#45; 子任务窗口中查看](../debugger/media/pdb_walkthrough_9.png "PDB_Walkthrough_9")  
  
     请注意，任务 4 和任务 5 正在同一线程上运行。 此信息不会显示在**线程**窗口中; 在它下面另一个好处的**任务**窗口。 若要确认这一点，查看**并行堆栈**窗口。 请确保你正在查看**任务**。 通过双击它们中查找任务 4 和 5**任务**窗口。 在执行操作时，蓝色突出显示**并行堆栈**窗口将进行更新。 你可以通过上扫描的工具提示来查找任务 4 和 5**并行堆栈**窗口。  
  
     ![任务并行堆栈窗口中的视图](../debugger/media/pdb_walkthrough_9a.png "PDB_Walkthrough_9A")  
  
     在**并行堆栈**窗口中，右击 S.P，，然后单击**转至线程**。 此时，窗口将切换到线程视图，并显示相应帧。 你可以在同一线程上查看两个任务。  
  
     ![突出显示在线程视图中的线程](../debugger/media/pdb_walkthrough_9b.png "PDB_Walkthrough_9B")  
  
     这是中的任务视图的另一个好处**并行堆栈**窗口，相对于**线程**窗口。  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>继续执行到第四个断点  
  
1.  若要继续执行到命中第三个断点，请在**调试**菜单上，单击**继续**。 单击**ID**列标题以按 id。 您应看到以下图示。  
  
     ![在并行堆栈窗口的状态的 4 种任务](../debugger/media/pdb_walkthrough_10.png "PDB_Walkthrough_10")  
  
     由于任务 5 已完成，因此不再显示该任务。 如果您的计算机上并非如此并且未显示死锁，请通过按 F11 单步执行一次。  
  
     此时，任务 3 和任务 4 正在相互等待，且处于死锁状态。 此外，还存在 5 个作为任务 2 的子级的新任务，目前已计划这些任务。 已计划任务是已在代码中启动但尚未运行的任务。 因此，其**位置**和**线程分配**列为空。  
  
     视图**并行堆栈**再次窗口。 每个框的标题都具有一个显示线程 ID 和名称的工具提示。 切换到任务视图中**并行堆栈**窗口。 将鼠标指针悬停在标题上可以查看任务 ID 和名称以及任务状态，如下图所示。  
  
     ![在并行堆栈窗口的标题工具提示](../debugger/media/pdb_walkthrough_11.png "PDB_Walkthrough_11")  
  
     可以按列对任务进行分组。 在**任务**窗口中，右键单击**状态**列标题并单击**按状态分组**。 下图显示**任务**窗口按状态分组。  
  
     ![分组任务窗口中的任务](../debugger/media/pdb_walkthrough_12.png "PDB_Walkthrough_12")  
  
     此外，还可以按其他列进行分组。 通过对任务进行分组，您可以关注某个任务子集。 每个可折叠的组都包含一个分组在一起的项的计数。 你可以通过单击来快速标记该组中的所有项**都标志**右侧的按钮**折叠**按钮。  
  
     ![分组并行堆栈窗口中的堆栈](../debugger/media/pdb_walkthrough_12a.png "PDB_Walkthrough_12A")  
  
     最后一个功能**任务**窗口，检查是右击任务时，将显示的快捷菜单。  
  
     ![在任务窗口的快捷菜单](../debugger/media/pdb_walkthrough_12b.png "PDB_Walkthrough_12B")  
  
     快捷菜单根据任务状态显示不同的命令。 这些命令可能包括**复制**，**选择所有**，**十六进制显示**，**切换到任务**，**冻结分配线程**，**冻结所有线程，但这**，和**解冻分配的线程**，和**标志**。  
  
     你可以冻结一个或多个任务的基础线程，也可以冻结除指定线程外的所有线程。 冻结的线程都在**任务**窗口，因为它处于**线程**窗口中的，由蓝色*暂停*图标。  
  
## <a name="summary"></a>摘要  
 本演练演示了**并行任务**和**并行堆栈**调试器窗口。 请在采用多线程代码的实际项目中使用这些窗口。 可以检查用 C++、C# 或 Visual Basic 编写的并行代码。  
  
## <a name="see-also"></a>另请参阅  
 [调试多线程应用程序](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Debugger Basics](../debugger/debugger-basics.md) （调试器基础知识）  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) （调试托管代码）  
 [并行编程](/dotnet/standard/parallel-programming/index)   
 [并发运行时](/cpp/parallel/concrt/concurrency-runtime)   
 [使用并行堆栈窗口](../debugger/using-the-parallel-stacks-window.md)   
 [使用“任务”窗口](../debugger/using-the-tasks-window.md)