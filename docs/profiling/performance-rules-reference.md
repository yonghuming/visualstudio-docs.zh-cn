---
title: "性能规则参考 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec05a24a932816374766c107c1aab6f018e77cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="performance-rules-reference"></a>性能规则参考
分析工具的性能规则提供有关应用程序性能的其他警告和信息。 性能规则分析在分析运行中从源（如 Windows 和处理器性能计数器）收集的数据。 规则消息会出现在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 集成开发环境的“错误输出”窗口中。 这些消息使用以下规则级别之一列出：  
  
|||  
|-|-|  
|**错误**|极少规则会生成“错误”消息，因为很多性能问题不完全是错误。 “错误”消息可能指示收集分析数据失败。|  
|**警告**|“警告”指示可能成为性能问题来源或可能受益于优化的应用程序区域。|  
|**信息**|“信息”消息指示将规则条件的分析未达到生成“错误”消息的阈值，或消息中的信息很有用，但不反映性能问题。|  
  
## <a name="in-this-section"></a>本节内容  
 [按 ID 列出的性能规则](../profiling/performance-rules-by-id.md)  
  
 分析工具性能规则按四个类别进行组织：  
  
|||  
|-|-|  
|[.NET Framework 使用性能规则](../profiling/dotnet-framework-usage-performance-rules.md)|可帮助高效使用 .NET Framework 的规则。|  
|[内存和分页性能规则](../profiling/memory-and-paging-performance-rules.md)|分析应用程序的托管内存和分页行为的规则。|  
|[分析工具使用规则](../profiling/profiling-tools-usage-rules.md)|可帮助高效使用分析工具的规则。|  
|[资源监控性能规则](../profiling/resource-monitoring-performance-rules.md)|有关分析运行中的处理器和内存利用率的信息消息。|