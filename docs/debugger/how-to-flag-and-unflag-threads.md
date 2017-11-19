---
title: "如何： 标记线程和取消标记线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
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
helpviewer_keywords: treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4ff3c0d06d7f668ad3d61f785320def8b9ddd0e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-flag-and-unflag-threads"></a>如何：标记线程和取消标记线程
你可以标记一个线程你想要通过将其标记为图标中为提供特别注意**线程**，**并行堆栈**（线程视图），**并行监视**，和**GPU 线程**windows。 此图标有助于您和其他人将标记的线程与其他线程区别开来。  
  
标记的线程还得到特殊处理中的**线程**列表上**调试位置**工具栏和其他多线程调试窗口中。 你可以显示所有线程或仅在标记的线程**线程**列表或在其他窗口。
  
### <a name="to-flag-or-unflag-a-thread"></a>标记或取消标记线程 
  
-   在**线程**或**并行监视**窗口中，找到你感兴趣的线程，然后单击标志图标可选择或清除标志。 
-   在**并行堆栈**窗口中，右击线程或线程并选择的组**标志 / <thread>** 或**取消标记 / <thread>** 。
  
### <a name="to-unflag-all-threads"></a>取消标记所有线程  
  
-   在**线程**窗口中，右击任何线程，然后单击**取消标志所有线程**。
-   在**并行监视**窗口中，选择所有标记的线程，然后右键单击并选择**取消标记**。  
  
### <a name="to-display-only-flagged-threads"></a>仅显示标记的线程  
  
-   选择**仅显示标记的线程的线程**一个多线程调试窗口中的按钮。  
  
### <a name="to-flag-just-my-code"></a>标记“仅我的代码”  
  
1.  在顶部的工具栏上**线程**窗口中，单击标志图标。  
  
2.  在下拉列表中，单击**标记 ' 仅我的代码**。  
  
### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>标记与选定模块关联的线程  
  
1.  在工具栏上的**线程**窗口中，单击标志图标。  
  
2.  在下拉列表中，单击**标志自定义模块选择**。  
  
3.  在**选择模块**对话框框中，选择所需的模块。  
  
4.  （可选）在**搜索**框中，键入要搜索特定模块的字符串。  
  
5.  单击“确定”。  
  
## <a name="see-also"></a>另请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [开始调试多线程应用程序](../debugger/get-started-debugging-multithreaded-apps.md)  
 [演练： 调试多线程应用程序使用线程窗口](../debugger/how-to-use-the-threads-window.md)