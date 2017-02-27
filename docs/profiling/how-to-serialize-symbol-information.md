---
title: "如何：序列化符号信息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "分析工具, 序列化符号信息"
  - "性能工具, 序列化符号信息"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 如何：序列化符号信息
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以序列化分析应用程序所需的符号。  符号序列化的作用是将符号添加到 .vsp 文件中。  通过向 .vsp 文件添加符号信息，其他人可以在没有原始符号访问权限的情况下分析性能报告。  如果没有序列化符号，则需要有原始的检测 .exe 和 .pdb 文件才能分析 .vsp 文件。  
  
### 自动序列化符号信息  
  
1.  在**“工具”**菜单上，单击**“选项”**。  
  
     随即出现**“选项”**对话框。  
  
2.  单击**“性能工具”**。  
  
3.  在**“常规设置”**下，选择**“自动序列化符号信息”**。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [如何：引用 Windows 符号信息](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/zh-cn/0340ddde-caf4-48ac-8af3-d15dcdade556)