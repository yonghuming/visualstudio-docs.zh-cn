---
title: "查看调试器中的 GPU 线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23bb4ee4550f70681152fc14cc66a642597125ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-gpu-threads-window"></a>如何：使用“GPU 线程”窗口
在“GPU 线程”窗口中，可以检查和使用在要调试的应用程序中的 GPU 上运行的线程。 有关在 GPU 运行的应用程序的详细信息，请参阅[c + + AMP 概述](/cpp/parallel/amp/cpp-amp-overview)。  
  
 “GPU 线程”窗口包含一个表，其中，每个行均表示一组在所有列中具有相同值的 GPU 线程。 您可以对列中的项进行排序、重新排序、移除和分组操作。 您可以在“GPU 线程”窗口中标记、取消标记、冻结（禁止显示）和解冻（恢复）线程。 下面的列将显示在“GPU 线程”窗口中：  
  
-   标记列，可在其中标记要特别注意的线程。  
  
-   当前线程列，在其中一个黄色箭头指示当前线程。  
  
-   **线程计数**列，在同一位置中显示的线程数。  
  
-   **行**列，显示的每组线程所在的代码行。  
  
-   **地址**列，显示每组线程所在的指令地址。 默认情况下，此列被隐藏。  
  
-   **位置**列，该列中的源代码的位置。  
  
-   **状态**列，显示线程是活动、 阻止、 未启动或完成。  
  
-   **磁贴**列，显示线程的平铺索引行中。  
  
 表的标头显示将显示的平铺和线程。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-display-the-gpu-threads-window"></a>显示“GPU 线程”窗口  
  
1.  在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。  
  
2.  在**属性页**对于项目，窗口下**配置属性**，选择**调试**。  
  
3.  在**要启动的调试器**列表中，选择**本地 Windows 调试器**。 在**调试器类型**列表中，选择**仅限 GPU**。 必须选择此调试器以便在 GPU 上运行的代码的断点处中断。  
  
4.  选择“确定”  按钮。  
  
5.  在 GPU 代码中设置断点。  
  
6.  在菜单栏上，选择**调试**，**启动调试**。 等待应用程序到达断点。  
  
7.  菜单栏上，选择**调试**， **Windows**， **GPU 线程**。  
  
### <a name="to-switch-to-a-different-thread"></a>若要切换到另一个线程  
  
-   双击该列。 （键盘：选择行，然后选择 Enter。）  
  
### <a name="to-display-a-particular-tile-and-thread"></a>显示特定平铺和线程  
  
1.  选择**展开线程切换器**GPU 线程窗口中的按钮。  
  
2.  在文本框中输入平铺值和线程值。  
  
3.  选择其上带箭头的按钮。  
  
### <a name="to-display-or-hide-a-column"></a>显示或隐藏列  
  
-   打开 GPU 线程窗口的快捷菜单，选择**列**，然后选择你想要显示或隐藏的列。  
  
### <a name="to-sort-by-a-column"></a>按列排序  
  
-   选择列标题。  
  
### <a name="to-group-threads"></a>分组线程  
  
-   打开 GPU 线程窗口的快捷菜单，选择**Group By**，然后选择显示的列名称之一。 选择**无**取消线程。  
  
### <a name="to-freeze-or-thaw-a-row-of-threads"></a>冻结或解冻线程的某个行  
  
-   打开行的快捷菜单，然后选择**冻结**或**解冻**。  
  
### <a name="to-flag-or-unflag-a-row-of-threads"></a>标记或取消标记线程的某个行  
  
-   选择该线程的标记列或打开线程的快捷菜单并选择**标志**或**取消标记**。  
  
### <a name="to-display-only-flagged-threads"></a>仅显示标记的线程  
  
-   在“GPU 线程”窗口中选择标记按钮。  
  
## <a name="see-also"></a>另请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何： 使用并行监视窗口](../debugger/how-to-use-the-parallel-watch-window.md)   
 [演练：调试 C++ AMP 应用程序](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)