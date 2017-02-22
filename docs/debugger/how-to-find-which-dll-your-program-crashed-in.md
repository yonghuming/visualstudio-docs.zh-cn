---
title: "如何：查找导致程序崩溃的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dll"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "调试器, DLL 崩溃"
  - "调试 [Visual Studio], DLL 崩溃"
  - "DLL, 加载顺序"
  - "错误 [调试器], DLL 崩溃"
  - "“模块清单”对话框"
  - "“模块”窗口"
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：查找导致程序崩溃的 DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中描述的不同，具体取决于您的现有设置或版本。  若要更改设置，请在“工具”菜单上选择“导入和导出设置”。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 如果应用程序在调用系统 DLL 或别人的代码时出现崩溃，则需要找出在崩溃发生时哪个 DLL 是活动的。  如果在您自己的程序外部的 DLL 中出现崩溃，可以使用**“模块”**窗口标识该位置。  
  
### 使用“模块”窗口查找崩溃发生的位置  
  
1.  记下崩溃发生的地址。  
  
2.  在**“调试”**菜单上选择**“窗口”**，再单击**“模块”**。  
  
3.  在**“模块”**窗口中，查找**“地址”**列。  可能需要使用滚动条来查看。  
  
4.  单击**“地址”**按钮（在列顶部）按地址对 DLL 进行排序。  
  
5.  细查排序的列表，找到其地址包含崩溃位置的 DLL。  
  
6.  查看**“名称”**和**“路径”**列，查看 DLL 的名称和路径。  
  
## 请参阅  
 [如何：调试本机 DLL](../Topic/How%20to:%20Debug%20Native%20DLLs.md)   
 [如何：使用“模块”窗口](../debugger/how-to-use-the-modules-window.md)