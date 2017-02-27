---
title: "如何：在调试时切换到另一个线程 | Microsoft Docs"
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
helpviewer_keywords: 
  - "线程, 切换 [调试]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：在调试时切换到另一个线程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在调试多线程应用程序时，您可以使用若干方法中的任何一种，将上下文从正在处理的线程切换到另一个线程。  
  
### 切换至“线程”窗口中显示的任何线程  
  
-   双击线程。  
  
### 切换至源窗口中的线程  
  
-   在左滚动条槽中，右击线程指示符，指向**“切换到”**，然后单击要切换到的线程的名称。  快捷菜单仅显示该特定位置的线程。  
  
     如果未显示任何指示符，请在**“线程”**窗口中右击，然后验证是否选中**“在源中显示线程”**。  
  
### 切换到“调试位置”工具栏中的线程  
  
1.  在**“调试位置”**工具栏上，单击**“线程”**框。  
  
2.  在列表中，单击要切换到的线程。  
  
## 请参阅  
 [调试多线程应用程序](../debugger/debug-multithreaded-applications-in-visual-studio.md)