---
title: "比较性能数据文件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9a0b4dcb86aa4241d223dd4a1172267dd8ec20da

---
# <a name="comparing-performance-data-files"></a>比较性能数据文件
凭借分析工具数据文件比较功能，可以选择两个报表文件（.VSP 或 .VSP）文件，然后生成显示从一个分析会话到另一个分析会话出现的差异、性能回归和改进。  
  
 来自 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具中的数据文件比较报告将一个分析数据文件中的分析结果与另一个数据文件中的基线分析的结果进行比较。 必须已使用同一分析方法生成了这两个数据文件。 将所分析的比较的报告另存为 .vsps 文件。  
  
 比较报告视图呈现已更改数据的表视图。 该表呈现增量，或基线中的更改。 增量是通过确定旧值、基线值和新分析中的结果值之间的差异来计算的。  
  
 探查器数据的比较可基于代码中的函数、应用程序中的模块、行、指令指针 (IP) 和类型。  
  
 可用于比较的分析数据包括列中显示的信息。 有关这些列名称的定义，请参阅[性能报告视图](../profiling/performance-report-views.md)。  
  
 可设置阈值以降噪并筛选出未按指定量更改的行的比较表视图中的任何数据。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：比较性能数据文件](../profiling/how-to-compare-performance-data-files.md)


<!--HONumber=Feb17_HO4-->


