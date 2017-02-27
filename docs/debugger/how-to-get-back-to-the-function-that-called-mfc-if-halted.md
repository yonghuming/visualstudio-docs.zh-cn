---
title: "如何：返回到在中断时调用了 MFC 的函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "“中断”命令"
  - "调试 [MFC], 函数"
  - "调试 [MFC], 返回到调用函数"
  - "函数调用, 返回到调用函数"
  - "函数 [C++], 调试"
  - "函数 [调试器]"
  - "程序, 暂停"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：返回到在中断时调用了 MFC 的函数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中描述的不同，具体取决于您的现有设置或版本。  若要更改设置，请在“工具”菜单上选择“导入和导出设置”。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 如果您使用了**“调试”**菜单上的**“中断”**命令来暂停程序，结果结束在 MFC 上，而且您可以确认问题在代码中，则可以使用“调用堆栈”窗口来向后定位到函数。  有关详细信息，请参阅[如何：使用“调用堆栈”窗口](../debugger/how-to-use-the-call-stack-window.md)。  
  
 有时，代码可能在消息泵中中断。  在这种情况下，调用堆栈中没有用户代码。  若要避免此问题，可以使用断点（也许加上条件和命中次数）而非**中断**命令。  有关更多信息，请参见 [Breakpoints and Tracepoints](http://msdn.microsoft.com/zh-cn/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
### 若要定位调用 MFC 的函数  
  
-   使用**“调用堆栈”**窗口。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)