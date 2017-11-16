---
title: "“摘要”视图 - .NET 内存数据 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 968d46c4fe771229647282c719815982d81bf416
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="summary-view---net-memory-data"></a>“摘要”视图 - .NET 内存数据
“摘要”视图显示有关分配最多内存的 .NET 函数和类型以及在分析运行中创建次数最多的类型的信息。 有关详细信息（包括通知链接和报告列表的说明），请参阅[“摘要”视图](../profiling/summary-view.md)。  
  
## <a name="timeline-graph"></a>时间线关系图  
 “摘要”视图中的时间线关系图按分析的应用程序显示在进行分析的时间内的处理器 (CPU) 利用率。 可以使用时间线关系图将视图筛选到所选时间范围。 有关详细信息，请参阅[如何：从摘要时间线中筛选报告视图](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
## <a name="functions-allocating-most-memory"></a>分配最多内存的函数  
 列出在分析运行中分配了最大内存字节数的函数。  
  
|列|说明|  
|------------|-----------------|  
|**Name**|函数名。|  
|**字节数百分比**|由此函数或此函数调用的子函数分配的字节数占分析运行中分配的所有字节数的百分比。|  
  
## <a name="types-with-most-memory-allocated"></a>内存分配最多的类型  
 列出在分析运行中为其分配了最大内存字节数的类型。  
  
|列|说明|  
|------------|-----------------|  
|**Name**|类型的名称。|  
|**字节数百分比**|为此类型分配的字节数占分析运行中分配的所有字节数的百分比。|  
  
## <a name="types-with-most-instances"></a>实例最多的类型  
 列出在分析运行期间创建次数最多的类型。 具有  
  
|列|说明|  
|------------|-----------------|  
|**Name**|类型的名称。|  
|**实例数百分比**|属于此类型的实例的 .NET 对象数占分析运行中创建的 .NET 对象总数的百分比。|  
  
## <a name="see-also"></a>另请参阅  
 [“摘要”视图](../profiling/summary-view-sampling-data.md)   
 [“摘要”视图](../profiling/summary-view-instrumentation-data.md)