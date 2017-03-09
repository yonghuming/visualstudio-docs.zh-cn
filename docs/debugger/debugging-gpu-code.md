---
title: "调试 GPU 代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 调试 GPU 代码
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以调试在图形处理单元 \(GPU\) 上运行的 C\+\+ 代码。  Visual Studio 中的 GPU 调试支持包括争用检测、启动进程并附加到进程以及集成到调试窗口中。  
  
## 受支持的平台  
 [!INCLUDE[win7](../debugger/includes/win7_md.md)]、[!INCLUDE[win8](../debugger/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] 和 [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] 上支持调试。  对于在软件模拟器上进行的调试，需要 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)]。  对于在硬件上进行的调试，您必须为图形卡安装驱动程序。  并非所有硬件供应商都实现所有调试器功能。  有关限制，请参阅供应商文档。  
  
> [!NOTE]
>  希望在 Visual Studio 中支持 GPU 调试的独立硬件供应商必须创建一个实现 VSD3DDebug 接口并面向其自己的驱动程序的 DLL。  
  
## 配置 GPU 调试  
 调试器无法同时在同一应用执行中的 CPU 代码和 GPU 代码处中断。  默认情况下，调试器在 CPU 代码处中断。  若要调试 GPU 代码，请使用以下两个步骤之一：  
  
-   在**“标准”**工具栏上的**“调试类型”**列表中，选择**“仅 GPU”**。  
  
-   在**“解决方案资源管理器”**中，在项目的快捷菜单上，选择**“属性”**。  在**“属性页”**对话框中，选择**“调试”**，然后在**“调试器类型”**列表中选择**“仅 GPU”**。  
  
## 启动并附加到应用程序  
 您可以使用 Visual Studio 调试命令来启动和停止 GPU 调试。  有关详细信息，请参阅[使用调试器浏览代码](../debugger/navigating-through-code-with-the-debugger.md)。  您还可以将 GPU 调试器附加到正在运行的进程，但仅在该进程执行 GPU 代码时才能这样做。  有关详细信息，请参阅[附加到运行的进程](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
## “将当前 Tile 运行到光标处”和“运行到光标处”  
 当您在 GPU 上进行调试时，您可以通过两个选项运行到光标位置。  代码编辑器的快捷菜单上提供了这两个选项的命令。  
  
1.  **“运行到光标处”**命令可运行您的应用程序，直到其达到光标位置，然后中断。  这并不表示当前线程运行到光标处；相反，这意味着第一个到达光标点的线程会触发中断。  请参阅[使用调试器浏览代码](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  **“将当前 Tile 运行到光标处”**命令可运行您的应用程序，直到当前 Tile 中的所有线程到达光标处，然后中断。  
  
## “调试”窗口  
 通过使用某些调试窗口，您可以检查、标记和冻结 GPU 线程。  有关详细信息，请参阅：  
  
-   [使用“并行堆栈”窗口](../debugger/using-the-parallel-stacks-window.md)  
  
-   [使用“任务”窗口](../debugger/using-the-tasks-window.md)  
  
-   [如何：使用“并行监视”窗口](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [调试线程和进程](../debugger/debug-threads-and-processes.md)（“调试位置”工具栏）  
  
-   [如何：使用“GPU 线程”窗口](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
  
## 数据同步异常  
 调试器可以在执行期间标识多个数据同步条件。  在检测条件时，调试器会进入中断状态。  您有两个选项：**“中断”**或**“继续”**。  通过使用**“异常”**对话框，您可以配置调试器是否检测这些条件以及它将在哪些条件下中断。  有关详细信息，请参阅[管理调试器的异常](../debugger/managing-exceptions-with-the-debugger.md)。  您还可以使用**“选项”**对话框来指定调试器应忽略异常（如果写入的数据不更改数据的值）。  有关详细信息，请参阅[“选项”对话框 \-\>“调试”\-\>“常规”](../debugger/general-debugging-options-dialog-box.md)。  
  
## 疑难解答  
  
### 指定加速器  
 如果代码在 [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) \(REF\) 加速器上运行，则仅命中 GPU 代码中的断点。  如果未指定代码中的加速器，则自动将 REF 加速器选作项目属性中的**“调试加速器类型”**。  如果您的代码显式选择加速器，则在调试期间将不会使用 REF 加速器，并且将不会命中断点，除非您的 GPU 硬件具有调试支持。  您可以通过编写代码来对此情况进行补救，以便在调试期间使用 REF 加速器。  有关详细信息，请参阅项目属性和[使用 accelerator 和 accelerator\_view 对象](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects)以及[C\+\+ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
### 条件断点  
 GPU 代码中的条件断点是受支持的，但并不能在设备上计算所有表达式。  当无法在设备上计算某个表达式时，将在调试器中计算该表达式。  调试器的运行速度比设备的运行速度慢得多。  
  
### 错误：选定的调试加速器类型存在配置问题。  
 当项目设置和您在其上进行调试的 PC 的配置之间存在不一致之处时，会发生此错误。  有关详细信息，请参阅 [C\+\+ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
### 错误：目标计算机上未安装选定的调试加速器类型的调试驱动程序。  
 如果在远程 PC 上进行调试，则会发生此错误。  调试器无法确定远程 PC 上是否安装了驱动程序，直到运行时。  可从图形卡的制造商处获得驱动程序。  
  
### 错误：必须在远程站点上禁用超时检测和恢复 \(TDR\)。  
 C\+\+ AMP 计算可能会超过由 Windows 超时检测和恢复进程 \(TDR\) 设置的默认时间间隔。  在这种情况下，计算将被取消，并且数据将丢失。  有关详细信息，请参阅[在 C\+\+ AMP 中处理 TDR](http://go.microsoft.com/fwlink/p/?LinkId=249154)。  
  
## 请参阅  
 [演练：调试 C\+\+ AMP 应用程序](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [C\+\+ 调试配置的项目设置](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [在 Visual Studio 中开始 GPU 调试](http://go.microsoft.com/fwlink/p/?LinkId=255381)