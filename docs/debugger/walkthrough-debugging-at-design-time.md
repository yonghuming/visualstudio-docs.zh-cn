---
title: "演练： 在设计时调试 |Microsoft 文档"
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
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d497535f8511c3f9e6c55e80157507ed36184b0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>演练：在设计时调试
你可以使用 Visual Studio**即时**窗口在你的应用程序未运行时执行函数或子例程。 如果函数或子例程包含断点，Visual Studio 会在合适的点处中断执行。 然后可以使用调试器窗口来检查程序状态。 此功能称为在设计时调试。  
  
 下面的过程演示如何使用此功能。  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>要进行命中断点，从即时窗口  
  
1.  将以下代码粘贴到 Visual Basic 控制台应用程序：  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  在读取时，行上设置断点`s="Add BreakPoint Here"`。  
  
3.  键入以下内容中的**即时**窗口：`?MyFunction<enter>`  
  
4.  验证该断点被命中，以及调用堆栈准确。  
  
5.  上**调试**菜单上，单击**继续**，然后验证是否仍然处于设计模式。  
  
6.  键入以下内容中的**即时**窗口：`?MyFunction<enter>`  
  
7.  键入以下内容中的**即时**窗口：`?MySub<enter>`  
  
8.  验证你命中了断点，并检查的静态变量的值`i`中**局部变量**窗口。 它应具有的值为 3。  
  
9. 验证调用堆栈准确。  
  
10. 上**调试**菜单上，单击**继续**，然后验证是否仍然处于设计模式。  
  
## <a name="see-also"></a>另请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器基础知识](../debugger/debugger-basics.md)