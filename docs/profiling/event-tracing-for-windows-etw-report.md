---
title: "Windows 事件跟踪 (ETW) 报告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW 分析支持"
  - "Windows 事件跟踪分析报告"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Windows 事件跟踪 (ETW) 报告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows 事件跟踪 \(ETW\) 报告列出 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的性能会话中所记录的 ETW 事件。  ETW 数据收集在二进制 \(.etl\) 文件中。  
  
> [!NOTE]
>  不能在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 界面中显示 ETW 报告。  
  
-   有关如何从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 界面中使用分析工具收集 ETW 的信息，请参见[如何：收集 Windows 事件跟踪 \(ETW\) 数据](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)。  
  
-   有关如何使用 [VSPerfCmd](../profiling/vsperfcmd.md) 命令行工具收集 ETW 数据的信息，请参见 [事件](../profiling/events-vsperfcmd.md)。  
  
-   您使用 **VSReport \/Summary:ETW** 命令生成 ETW 报告。  有关详细信息，请参阅[VSPerfReport](../profiling/vsperfreport.md)。  
  
|列|说明|  
|-------|--------|  
|**时间戳**|标识何时发生事件。|  
|**进程 ID**|标识生成事件的进程。|  
|**线程 ID**|标识生成事件的线程。|  
|**说明**|标识事件提供程序。|  
|**类型**|标识事件类型。|  
|**属性**|事件的属性。  每个事件都是一个括在方括号内的以逗号分隔的名称\/值对。|