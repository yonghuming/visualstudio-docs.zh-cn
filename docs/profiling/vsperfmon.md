---
title: "VSPerfMon | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPerfMon 工具"
  - "命令行, 工具"
  - "命令行工具, VSPerfMon 工具"
  - "数据 [Visual Studio ALM], VSPerfMon 工具"
  - "性能数据, VSPerfMon 工具"
  - "性能工具, VSPerfMon 工具"
  - "分析工具, VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

可以使用 VSPerfMon 工具收集应用程序的性能数据；此工具通常由 VSPerfCmd.exe 启动。  VSPerfMon 会显示有关进程附加或分离的额外信息，使用 VSPerfCmd 工具时则没有这些信息。  若要查看此信息，请在单独的窗口中启动 VSPerfMon。  若要调用 VSPerfMon，请使用以下语法：  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 下表描述 VSPerfMon 工具选项：  
  
|选项|说明|  
|--------|--------|  
|**U**|重定向控制台的输出编写为 Unicode。这必须是指定的第一个选项。|  
|**OUTPUT:** `<` *file name* `>`|将输出重定向到指定的文件名。|  
|**TRACE**|为检测分析启动性能监视器。|  
|**SAMPLE**|为取样分析启动性能监视器。|  
|**COVERAGE**|为代码覆盖率收集启动性能监视器。|  
|**CONCURRENCY**|启动资源争用分析的性能监视器。|  
|**USER:** `[` *domain* `\]` *username*|允许客户端从指定帐户访问性能监视器。|  
|**CROSSSESSION**|启用跨会话分析。|  
|**COUNTER** `:cfg`|使用检测 \(TRACE\) 分析方法时，指定要在每个检测点收集的 CPU 计数器。  您可以通过指定多个计数器选项来收集多个计数器数据。<br /><br /> 使用以下语法指定计数器 \(*cfg*\) 数据：<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   “计数器名称”是由 VSPerfCmd\/QueryCounters 命令返回的计数器的名称。<br />-   重载是计数器事件采样间隔。  不要与检测方法一起使用 *Reload*。<br />-   指定了“友好名称”时，此名称将取代分析工具报告列名称中的“计数器名称”。|  
|**WINCOUNTER** `:path`|指定要包含标记数据的 Windows 性能计数器。  `path` 是 PDH 计数器路径格式的 Windows 性能计数器字符串。  例如：<br /><br /> \\Processor\(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|使用 \/WINCOUNTER 时指定自动标记之间的时间间隔（单位为毫秒）。  向上舍入到最接近的 500 毫秒。<br /><br /> 使用 0 可禁用自动标记。（如果没有指定，默认值为 500）|  
  
## 请参阅  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [分析工具报告视图](../profiling/performance-report-views.md)