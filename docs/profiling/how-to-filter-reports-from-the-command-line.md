---
title: "如何：从命令行筛选报告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何：从命令行筛选报告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过使用 **VSPerfReport** 命令的选项，可以筛选报告中分析数据文件的特定时间段，或仅限一个或多个进程或线程的数据。  有关此命令的更多信息，请参见 [VSPerfReport](../profiling/vsperfreport.md)。  
  
|选项|说明|  
|--------|--------|  
|**StartTime:**\[*Value*\]|仅显示值（以毫秒为单位）后收集的信息。|  
|**EndTime:**\[*Value*\]|仅显示值（以毫秒为单位）前收集的信息。|  
|**FilterFile:** `VSPFFile`|指定从**“Visual Studio 性能报告”**窗口中生成的筛选器文件的位置。|  
|**MsFilter:**\[*StartTime,Duration*\]|仅显示从 `StartTime` 算起持续 `Duration`（以毫秒为单位）的数据。|  
|**Process:**\[*Pid*\]|仅显示指定进程的数据。|  
|**Thread:**\[*ThreadID*\]|仅显示指定线程的数据。|  
|**Thread:**\[*ThreadID,ProcessID*\]|仅显示与指定进程关联的指定线程中的数据。|