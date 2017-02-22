---
title: "分析工具使用规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 分析工具使用规则
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

分析工具使用类别中的性能规则为使用探查器最有效地收集数据提供指导。  
  
|||  
|-|-|  
|[DA0002：缺少 VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|命令行分析可能包含 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 二进制文件的不完整数据。  这可能是由于未设置正确的环境变量所致。|  
|[DA0003：大量内核样本](../profiling/da0003-many-kernel-samples.md)|记录了许多在目标二进制文件执行外发生的分析样本。  若要收集更准确的数据，请考虑使用检测方法。|  
|[DA0004：处理器使用率很高](../profiling/da0004-high-processor-usage.md)|分析数据表明，您的处理器在分析运行期间始终很忙。  若要收集更准确的数据，请考虑使用采样方法。|  
|[DA0008：收集的样本过少](../profiling/da0008-few-samples-collected.md)|分析运行中收集的样本数不够高，无法进行统计分析。  请考虑重新进行分析，并运行应用程序更长一段时间。  您还可考虑使用检测方法来收集数据。|  
|[DA0026：处理过程的内核 CPU 时间过长](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|处理器内核模式中分析运行用了大量的时间。  考虑将系统调用作为指标而不是将时间作为指标进行采样。|  
|[DA0029：不支持的 CLR 版本](../profiling/da0029-unsupported-clr-version.md)|分析的二进制文件使用的 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本不受探查器支持。  探查器报告无法解析符号名称。|  
|[DA0030：收集数据库项目的层交互测量值](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|收集到了对 <xref:System.Data?displayProperty=fullName> 命名空间中的方法的大量调用。  若要包含有关数据库调用的数据，请考虑在分析运行中收集层交互数据。|