---
title: "Visual Studio 性能分析初学者指南 | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
caps.latest.revision: 45
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
ms.sourcegitcommit: 5c28e68b89f6583dc35a91b275693c11e0259dfd
ms.openlocfilehash: 6e4094925eec3e4a8768219180e75fa9d1f1fa03
ms.contentlocale: zh-cn
ms.lasthandoff: 07/13/2017

---
# <a name="beginners-guide-to-performance-profiling"></a>性能分析初学者指南
可使用 Visual Studio 分析工具来分析应用程序中的性能问题。 此过程演示如何使用诊断工具的“CPU 使用率”选项卡获取应用的性能数据。 Visual Studio 中的 .NET 开发（包括 ASP.NET、和本机 /C++ 开发）支持此诊断工具。
  
调试中断时，**CPU 使用率**工具收集有关应用程序中正在执行的函数的信息。 该工具将列出执行工作的函数，并提供时间线图，可专用于采样会话的特定部分。

诊断中心提供了大量其他选项来运行和管理诊断会话。 如果**CPU 使用率**未提供所需数据，[其他分析工具](../profiling/Profiling-Tools.md)可提供可能有帮助的不同种类的信息。 在许多情况下，CPU 以外的因素可能会导致应用程序性能瓶颈，例如内存、呈现 UI 或网络请求时间。 诊断中心提供大量其他选项，可用于记录和分析此种数据。

还可[观看介绍诊断工具用法的视频](#video)，了解如何分析 CPU 使用率以及如何分析内存使用情况。

本主题讨论在普通调试工作流中分析 CPU 使用率。 还可以在不附加调试器的情况下或将运行中的应用作为目标来分析 CPU 使用率 - 有关详细信息，请参阅[在不调试的情况下运行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a>步骤 1：收集分析数据 
  
1.  打开要在 Visual Studio 中调试的项目，并在应用中设置检查 CPU 使用率的断点。

2.  在函数末尾或想要分析的代码区域中设置第二个断点。

    > [!TIP]
    > 通过设置两个断点，可将数据收集限制到想要分析的代码部分。
  
3.  将自动显示 **“诊断工具”** 窗口，除非你已将其关闭。 若要再次显示该窗口，请依次单击“调试”、“Windows”、“显示诊断工具”。

4.  可以使用工具栏上的“选择工具”设置，选择是否查看 **CPU 使用率**[内存使用](../profiling/Memory-Usage.md)或同时查看两者。 如果运行的是 Visual Studio Enterprise，则可依次选择“工具”、“选项”、“IntelliTrace”启用或禁用 IntelliTrace。

     ![显示诊断工具](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     我们将主要查看 CPU 使用率，因此请确保已启用**CPU 使用率**（默认情况下已启用）。

5.  依次单击“调试”、“启动调试”或单击工具栏上的“启动”或按 **F5**。

     当应用完成加载后，将显示诊断工具的“摘要”视图。

     ![诊断工具“摘要”选项卡](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     有关事件的详细信息，请参阅[搜索和筛选“诊断工具”窗口中的“事件”选项卡](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx)

6.  运行会触发第一个断点的方案。

7.  调试器暂停时，启用收集 CPU 使用率数据，然后打开“CPU 使用率”选项卡。

     ![诊断工具启用 CPU 分析](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     选择“启用 CPU 分析”时，Visual Studio 将开始记录函数和执行这些函数所用的时间。 应用程序在断点处中断时，仅可以查看此收集的数据。

8.  按 F5 将应用运行到第二个断点。

     现在将拥有应用程序特定于在两个断点间运行的代码区域的性能数据。

9.  选择希望在 CPU 时间线中进行分析的区域（必须是显示分析数据的区域）。

     ![诊断工具选择时间段](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     探查器开始准备线程数据。 等待其完成。

     ![诊断工具准备线程](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     CPU 使用率工具在“CPU 使用率”选项卡中显示报表。
  
     ![诊断工具“ CPU 使用率”选项卡](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     现在可以开始分析数据。

## <a name="Step2"></a>步骤 2：分析 CPU 使用率数据

建议通过检查 CPU 使用率下的函数列表开始分析数据，然后确定执行大部分工作的函数，最后仔细查看每一个函数。

1. 在函数列表中，检查执行大部分工作的函数。

    ![诊断工具 CPU 使用率函数列表](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 函数将按执行工作量从多到少排列（不按调用顺序）。 这有助于快速标识运行时间最长的函数。

2. 在函数列表中，双击一个执行大量工作的应用函数。

    双击该函数时，将在左侧窗格中打开“调用方/被调用方”视图。 

    ![诊断工具调用方和被调用方视图](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    在此视图中，所选函数显示在标题和“当前函数”框中（本例中为 GetNumber）。 调用当前函数的函数显示在左侧的“调用函数”中，当前函数调用的任何函数均显示在右侧的“被调用函数”框中。 （可选择其中一个框来更改当前函数。）

    此视图显示总时间及函数完成执行所用的总体应用运行时间的百分比。

    **函数体**还显示函数体中所用的时间总量（及百分比），其中不包括调用和被调用函数中所用的时间。 （在此示例中，共花费 3729 毫秒，函数体内花费 3713 毫秒，其余 16 毫秒花费在此函数调用的外部代码中）。

    > [!TIP]
    > **函数体**中的较高值可能指示函数自身内部的性能瓶颈。

3. 如果希望按调用函数的顺序来查看较高级别的视图，请在顶部窗格的下拉列表中选择“调用关系树”。
 
    图中每个带编号的区域都与过程中的一个步骤相关。
  
    ![诊断工具调用关系树](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![第 1 步](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 使用量调用关系树中的顶级节点是一个伪节点|  
|![第 2 步](../profiling/media/ProcGuid_2.png "ProcGuid_2")|在大多数应用中，当禁用 [“显示外部代码”](#BKMK_External_Code) 选项时，二级节点是 **[外部代码]** 节点，该节点包含系统和框架代码，它可以启动和停止应用、绘制 UI、控制线程计划以及向应用提供其他低级服务。|  
|![第 3 步](../profiling/media/ProcGuid_3.png "ProcGuid_3")|二级节点的子级为用户代码方法和异步例程，它们由二级系统和框架代码进行调用或创建。|
|![第 4 步](../profiling/media/ProcGuid_4.png "ProcGuid_4")|方法的子节点仅包含用于父方法调用的数据。 禁用“显示外部代码”  后，应用方法只能包含 **[外部代码]** 节点。|

下面是列值的详细信息：

- **总 CPU** 指示函数及由它调用的任何函数完成的工作量。 较高的总 CPU 值指向总体成本最高的函数。
  
- **自 CPU**指示函数体中的代码完成的工作量，不包括由它调用的函数完成的工作。 较高的**自 CPU** 值可能指示函数自身内部的性能瓶颈。

- **模块**包含函数的模块名或包含 [外部代码] 节点中的函数的模块数量。

## <a name="BKMK_External_Code"></a>查看外部代码

外部代码是你编写的代码执行的系统和框架组件中的函数。 外部代码包含函数，可启动和停止应用、绘制 UI、控制线程以及向应用提供其他低级别服务。 在大多数情况下，你不会对外部代码感兴趣，因此 CPU 使用率工具可将用户方法的外部函数收集到一个 [外部代码] 节点中。
  
若要查看外部代码的调用路径，请从“筛选器视图”列表中选择“显示外部代码”，然后选择“应用”。  
  
![选择“筛选器视图”，然后选择“显示外部代码”](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
请注意，许多外部代码调用链已深度嵌套，因此函数名列的宽度可能超过所有计算机监视器（最大的计算机监视器除外）的显示宽度。 发生这种情况时，函数名将显示为 […]。
  
使用搜索框找到要查找的节点，然后滑动水平滚动条将数据带入视图中。

> [!TIP]
> 如果分析调用 Windows 函数的外部代码，应确保具有最新的 .pdb 文件。 如果没有这些文件，报告视图将列出含义隐晦、难以理解的 Windows 函数名称。 有关如何确保具有所需文件的详细信息，请参阅[在调试器中指定符号 (.pdb) 和源文件](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="video"></a>观看介绍诊断工具用法的视频

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171" frameborder="0" allowfullscreen></iframe>
</div>
  
## <a name="see-also"></a>另请参阅  
 [[内存使用情况](../profiling/memory-usage.md) [CPU 使用率](../profiling/cpu-usage.md) [Visual Studio 中的分析](../profiling/index.md) [分析功能简介](../profiling/profiling-feature-tour.md)
