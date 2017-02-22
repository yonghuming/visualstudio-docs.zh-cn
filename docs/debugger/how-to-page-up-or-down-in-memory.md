---
title: "如何：在内存中向上或向下翻页 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器，在内存中向上或向下分页"
  - "内存，向上或向下分页"
  - "反汇编窗口，查看内存空间"
  - "内存窗口，在内存中向上或向下分页"
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：在内存中向上或向下翻页
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在**“内存”**窗口或**“反汇编”**窗口中查看内存内容时，可以使用垂直滚动条在内存空间中上下移动。  
  
### 在内存中向上或向下翻页  
  
1.  若要向下翻页（移动到较高的内存地址），请单击滚动框下方的垂直滚动条。  
  
2.  若要向上翻页（移动到较低的内存地址），请单击滚动块上方的垂直滚动条。  
  
 您还将注意到垂直滚动条以非标准方式工作。  如今的计算机地址空间非常大，抓取滚动条滚动块并将其移动到任意位置，就容易找不到地址。  为此，滚动块就像“装了弹簧”，总是保持在滚动条的中心。  在本机代码应用程序中，可以向上或向下翻页，但不能随便滚动。  
  
 在托管应用程序中，反汇编限于一个函数，因而您可以正常滚动。  
  
 可以注意到，较高的地址出现在窗口的底部。  若要查看较高的地址，必须向下移动而不是向上移动。  
  
#### 向上或向下移动一个指令  
  
-   单击垂直滚动条顶部或底部的箭头。  
  
## 请参阅  
 [“内存”窗口](../debugger/memory-windows.md)   
 [如何：使用“反汇编”窗口](../debugger/how-to-use-the-disassembly-window.md)   
 [查看调试器中的数据](../debugger/viewing-data-in-the-debugger.md)