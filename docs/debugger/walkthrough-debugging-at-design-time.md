---
title: "演练：在设计时调试 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "断点, 设计时调试"
  - "调试 [Visual Studio], 设计时"
  - "设计时调试"
  - "即时窗口, 设计时调试"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 演练：在设计时调试
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 Visual Studio**“即时”**窗口在没有运行应用程序的情况下执行函数或子例程。  如果函数或子例程包含断点，Visual Studio 将在适当的点中断执行。  然后，您就可以使用调试器窗口检查您的程序状态。  此功能称为设计时调试。  
  
 下面的过程显示了如何使用此功能。  
  
### 从“即时”窗口命中断点  
  
1.  将下列代码粘贴到 Visual Basic 控制台应用程序中：  
  
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
  
2.  在 `s="Add BreakPoint Here"` 行上设置一个断点。  
  
3.  在“即时”窗口中键入以下内容：`?MyFunction<<enter>>`  
  
4.  确认是否命中了断点，以及调用堆栈是否准确。  
  
5.  在**“调试”**菜单上，单击**“继续”**，并确认是否仍处于设计模式。  
  
6.  在“即时”窗口中键入以下内容：`?MyFunction<<enter>>`  
  
7.  在“即时”窗口中键入以下内容：`?MySub<<enter>>`  
  
8.  确认是否命中了断点，并在**“局部变量”**窗口中检查静态变量 `i` 的值。  它的值应当为 3。  
  
9. 确认调用堆栈是否准确。  
  
10. 在**“调试”**菜单上，单击**“继续”**，并确认是否仍处于设计模式。  
  
## 请参阅  
 [调试器安全](../debugger/debugger-security.md)   
 [调试器基础知识](../debugger/debugger-basics.md)