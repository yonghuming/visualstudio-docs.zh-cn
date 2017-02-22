---
title: "内存和分页性能规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 内存和分页性能规则
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

内存和分页类别中的性能规则确定在分析运行中能影响应用程序性能和响应速度的分页活动。  
  
|||  
|-|-|  
|[DA0014：以分页方式将活动内存移到磁盘的发生率极高](../Topic/DA0014:%20Extremely%20high%20rates%20of%20paging%20active%20memory%20to%20disk.md)|在整个分析运行期间出现了超高比率的分页活动内存进出磁盘的情况。  这一级别的分页比率通常会影响应用程序的性能和响应速度。  请考虑通过修改算法来减少内存分配。  此外，还可能需考虑应用程序的内存要求。  在拥有更多内存的计算机上重新尝试运行分析。  当分页活动数超过规则 D0017 的上限阈值时，将激发此规则。|  
|[DA0017：以分页方式将活动内存移到磁盘的发生率高](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|在整个分析运行期间出现了相对高比率的分页活动内存进出磁盘的情况。  这一级别的分页比率通常会影响应用程序的性能和响应速度。  请考虑通过修改算法来减少内存分配。  此外，还可能需考虑应用程序的内存要求。  在拥有更多内存的计算机上重新尝试运行分析。|