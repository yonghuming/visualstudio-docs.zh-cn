---
title: "Visual Studio 中的分析工具 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 0d129b4820944f5717c63243cb8550bc4fed3385
ms.openlocfilehash: 380b65540d8f5c6ea6d8a8adf1f3c5575f5dd9dc
ms.lasthandoff: 03/20/2017

---
# <a name="profiling-tools"></a>分析工具
分析和诊断工具有助于诊断内存和 CPU 使用率以及其他应用程序级别问题。 这些工具可用于累积一段时间内在调试器中运行应用程序的数据（例如变量值、函数调用和事件）。 可以查看代码执行期间不同点的应用程序状态。  
  
 查看底部的摘要，了解项目类型（例如，桌面、UWP、ASP.NET）可以使用的工具。  
  
 可通过“调试”/“Windows”/“显示诊断工具”访问分析工具以在调试会话期间使用这些工具，或者可使用其他一些方法进行事后分析。  请参阅[运行带或不带调试器的分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)了解不同方法的详细信息。
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")
  
 有关此版本中的新增功能，请参阅[分析工具中的新增功能](../profiling/what-s-new-in-profiling-tools.md)。
  
 以下各节介绍了可以在 Visual Studio 中使用的不同性能工具。
  
## <a name="memory-usage"></a>内存使用率  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 使用“内存使用率”  工具进行调试时可查找内存泄漏和低效内存。 该工具可以拍摄托管和本机内存堆的快照。 此工具可用于桌面应用、Windows 通用应用和 ASP.NET 应用。 “内存使用率”  工具可以在调试时从“诊断工具”  窗口运行（“调试”/“Windows”/“显示诊断工具”），也可以在调试器外部运行（“调试”/“性能探查器...”）。 有关详细信息，请参阅[内存使用情况](../profiling/memory-usage.md)和[不调试情况下的内存使用情况](../profiling/Memory-Usage-without-Debugging2.md)。  
  
## <a name="cpu-usage"></a>CPU 使用率  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **CPU 使用率** 工具可为你显示 CPU 耗用时间执行 C + +、C# / VB 和 JavaScript 代码的位置。  此工具可用于桌面应用和 Windows 通用应用以及 ASP.NET 和 Azure 应用服务应用。 “CPU 使用率”  工具可以在调试时从“诊断工具”  窗口运行（“调试”/“Windows”/“显示诊断工具”），也可以在调试器外部运行（“调试”/“性能探查器...”）。 有关详细信息，请参阅[性能分析初学者指南](../profiling/beginners-guide-to-performance-profiling.md)和 [CPU 使用情况](../profiling/cpu-usage.md)。
  
## <a name="gpu-usage"></a>GPU 使用情况  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 使用 [GPU 使用情况](../debugger/gpu-usage.md)工具可以更好地了解 Direct3D 应用的高级硬件利用率。 此工具可用于桌面和 Windows 通用应用，但不可用于 ASP.NET 应用。 可以在调试器外部运行“GPU 使用情况”工具（“调试/性能探查器...”）。  
  
## <a name="application-timeline"></a>应用程序时间线  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [应用程序时间线](../profiling/application-timeline.md)工具提供应用程序资源使用情况的详细视图，可帮助提高 XAML 应用程序的性能。 “应用程序时间线”  工具可用于桌面和 Windows 通用应用，但不可用于 ASP.NET 应用。 可以在调试器外部运行“应用程序时间线”工具（“调试/性能探查器...”）。
  
## <a name="perftips"></a>性能提示  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 调试器在断点或单步执行操作中停止执行时，中断与上一个断点之间经过的时间会显示为在编辑器窗口中的提示。 这些[性能提示](../profiling/perftips.md)有助于在调试期间监视和分析应用的性能。 可以在桌面应用、Windows 通用应用和 ASP.NET 应用中查看“性能提示”  。

## <a name="performance-explorer"></a>性能资源管理器  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 “性能资源管理器”  （“调试”/“探查器”/“性能资源管理器”）允许使用各种不同的工具，例如“CPU 采样” 、“检测”  、“.NET 内存分配” 和“资源争用” 。 性能资源管理器工具可用于桌面应用和 ASP.NET 应用，但不可用于 Windows 通用应用。 有关更多信息，请参见[性能资源管理器](../profiling/performance-explorer.md)。

 > [!NOTE]
 > 除非要执行检测等特殊任务，否则请使用“内存使用情况”和“CPU 使用情况”等诊断工具，而不要使用“性能资源管理器”（现已是旧版工具）。
  
## <a name="javascript-memory"></a>“JavaScript 内存”  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 通过 [JavaScript 内存](../profiling/javascript-memory.md)工具可在应用中查找内存泄漏和低效内存使用情况。 该工具让你可以拍摄 JavaScript 堆的快照。 此工具可用于 Windows 通用 HTML 应用。 可以在调试器外部运行“JavaScript 内存”工具（“调试/性能探查器...”）。  
  
## <a name="html-ui-responsiveness"></a>HTML UI 响应能力  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI 响应能力](../profiling/html-ui-responsiveness.md)工具有助于隔离应用中的性能问题，包括响应能力不足、加载时间缓慢以及视觉对象更新频率小于预期。 此工具可用于 Windows 通用 HTML 应用。 可以在调试器外部运行“HTML UI 响应能力”工具（“调试/性能探查器...”）。  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) 可以记录特定事件、检查调试器事件和函数调用期间“局部变量”窗口中的数据以及调试难以再现的问题。  IntelliTrace 主要是一个调试工具，但它还可以提供可用于性能调查的信息。 此工具仅可在 Visual Studio Enterprise 中与桌面应用、Windows 通用应用和 C# ASP.NET 应用结合使用。 调试时可以在“诊断工具”  窗口找到 IntelliTrace（“调试”/“Windows”/“显示诊断工具”）。  
  
## <a name="profiling-in-production"></a>在生产中分析  
 在生产中进行分析的推荐方法是从[使用 vsperf.exe 的命令行](../profiling/using-the-profiling-tools-from-the-command-line.md)分析，以收集 CPU 配置文件。 有关 Azure App Service 中的远程分析支持，请参阅 [服务器资源管理器或 Kudu 门户](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/)。  
  
## <a name="which-tool-should-i-use"></a>应使用哪一种工具？  
 下表列出了 Visual Studio 提供的不同工具以及适用的不同项目类型：  
  
|性能工具|Windows 桌面|Windows 通用/应用商店|ASP.NET/ASP.NET Core|  
|----------------------|---------------------|------------------------------|-------------|  
|[内存使用率](../profiling/memory-usage.md)|是|是|是|  
|[CPU 使用率](../profiling/cpu-usage.md)|是|是|是|  
|[GPU 使用情况](../debugger/gpu-usage.md)|是|是|no|  
|[应用程序时间线](../profiling/application-timeline.md)|是|是|no|  
|[PerfTips](../profiling/perftips.md)|是|XAML 适用，HTML 不适用|是|  
|[性能资源管理器](../profiling/performance-explorer.md)|是|no|是（不适用于 ASP.NET Core）|  
|[IntelliTrace](../debugger/intellitrace.md)|仅限 .NET Enterprise|仅限 .NET Enterprise|仅限 .NET Enterprise|
|[网络使用情况](../profiling/network-usage.md)|no|是|no| 
|[HTML UI 响应能力](../profiling/html-ui-responsiveness.md)|no|HTML 适用，XAML 不适用|no|  
|[JavaScript 内存](../profiling/javascript-memory.md)|no|HTML 适用，XAML 不适用|no|  
  
## <a name="see-also"></a>另请参阅  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
