---
title: "“进程”视图 - 探查器争用数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“进程”视图"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “进程”视图 - 探查器争用数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“进程”视图显示在分析运行期间执行的进程和线程的争用数据。  
  
 当符号可用时，进程按名称列出。  当符号不可用时，进程按其内存地址（十六进制格式）列出。  线程作为创建它们的进程的子进程列出。  
  
 下表介绍“进程”视图表中各列的值。  
  
|列|说明|  
|-------|--------|  
|**开始时间**|从分析开始到进程或线程开始所经历的毫秒数或处理器周期数。|  
|**阻塞的时间**|阻止进程或线程的各个函数执行的总时间。|  
|**阻塞的时间百分比**|阻止进程或线程的各个函数执行的时间占进程或线程生存期的百分比。|  
|**争用数**|阻止进程或线程的各个函数执行的次数。|  
|**争用数百分比**|进程或线程的争用数占分析运行期间所有争用数的百分比。|  
|**结束时间**|从分析开始到进程或线程结束所经历的毫秒数或处理器周期数。|  
|**ID**|系统为进程或线程生成的标识符。|  
|**生存时间**|从进程或线程开始到进程或线程结束或分析结束所经历的毫秒数或处理器周期数。|  
|**类型**|行的类型，进程或线程。<br /><br /> 仅用于 **VSReport** 命令行报告。  有关更多信息，请参见 [VSPerfReport](../profiling/vsperfreport.md)。|  
|**名称**|进程或线程的名称。|  
|**唯一 ID**|探查器生成的标识符，每个进程或线程都有一个唯一的标识符。|  
  
## 请参阅  
 [如何：自定义报告视图列](../profiling/how-to-customize-report-view-columns.md)   
 [“进程”视图](../profiling/process-view.md)