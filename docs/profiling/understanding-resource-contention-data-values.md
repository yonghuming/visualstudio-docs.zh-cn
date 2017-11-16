---
title: "了解资源争用数据值 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4e128fa9a557569eb737a2b0a70ce60687d0830
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="understanding-resource-contention-data-values"></a>了解资源争用数据值
资源争用分析将收集每次应用程序中的争用线程访问共享资源时被强制等待的详细调用堆栈信息。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 资源争用报告显示争用的总数，以及对于在其中发生等待的模块、函数、源代码行和指令，等待资源所用的总时间。  
  
-   非独占值显示资源争用迫使函数等待的争用总数以及函数等待的总时间。  非独占值包括函数调用的子函数导致的争用。  
  
-   独占值只显示迫使函数等待并且由函数体中的代码导致的争用数。 不包括子函数导致的争用。 函数的独占时间也只包括函数体中的语句导致的等待时间。  
  
 资源争用报告视图还包括显示一段时间内各个争用事件的时间线关系图，并显示创建特定事件的调用堆栈。 有关更多信息，请参见下列主题之一：  
  
-   [“线程详细信息”视图](../profiling/thread-details-view-contention-data.md)  
  
-   [“资源详细信息”视图](../profiling/resource-details-view-contention-data.md)  
  
 有关并发分析的第二个模式的详细信息，请参阅[并发可视化工具](../profiling/concurrency-visualizer.md)。