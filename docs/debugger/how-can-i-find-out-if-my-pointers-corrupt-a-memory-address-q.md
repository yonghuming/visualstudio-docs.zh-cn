---
title: "如何查明指针是否损坏了内存地址？ | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "地址, 造成内存地址损坏的指针"
  - "损坏的内存地址"
  - "调试 [C++], 内存损坏"
  - "指针造成的内存地址损坏"
  - "内存, 损坏"
  - "指针, 损坏内存地址"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何查明指针是否损坏了内存地址？
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 问题描述  
 我认为我的一个指针可能损坏了地址 0x00408000 处的内存。  如何查明该地址处所发生的情况？  
  
## 解决方案  
  
#### 检查堆损坏  
  
-   大多数内存损坏实际上是由堆损坏引起的。  尝试使用 Global Flags Utility \(gflags.exe\) 或 pageheap.exe。  请参阅 [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470)。  
  
#### 若要查找内存地址改变的位置  
  
1.  在 0x00408000 处设置一个数据断点。  请参阅[设置数据更改断点（仅限本机 C\+\+）](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_)。  
  
2.  当命中断点时，使用**“内存”**窗口查看从 0x00408000 开始的内存内容。  有关详细信息，请参阅[“内存”窗口](../debugger/memory-windows.md)。  
  
## 请参阅  
 [调试本机代码常见问题](../debugger/debugging-native-code-faqs.md)   
 [调试本机代码](../debugger/debugging-native-code.md)