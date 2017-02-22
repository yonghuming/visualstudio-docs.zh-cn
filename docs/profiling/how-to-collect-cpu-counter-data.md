---
title: "如何：使用检测方法收集 CPU 计数器数据 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "分析工具, 使用可迁移的 CPU 计数器"
  - "性能工具, 可迁移的 CPU 计数器"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用检测方法收集 CPU 计数器数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CPU 事件计数器用于收集特定于硬件的性能数据。  本主题演示当您使用检测分析方法时，如何收集事件计数器数据  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 发生了两种类型的 CPU 计数器事件：  
  
-   可移植事件 – 可收集的、与特定 CPU 无关的 CPU 事件。  
  
-   平台事件 – 与特定 CPU 关联的 CPU 事件。  
  
 可移植事件包括常规事件（如 Instructions Retired 和 Non Halted Cycles）、CPU 缓冲事件、分支事件以及 L2 缓存事件。  可用的平台事件计数器由处理器制造商决定。  
  
 事件类别可以在可移植计数器与平台计数器之间共享。  例如，以下数据类别通常是这两种类型所共有的：  
  
-   内存事件。  
  
-   前端事件。  
  
-   分支事件。  
  
 在探查器中可以采用两种方式收集性能计数器数据：  
  
-   通过检测进行分析时，从一个或多个计数器中收集数据。  
  
-   通过采样进行分析时将一个计数器事件指定为采样间隔。  有关详细信息，请参阅[如何：选择采样事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)。  
  
### 通过检测进行分析时收集 CPU 性能计数器数据  
  
1.  在性能会话**“属性页”**上，单击**“CPU 计数器”**。  
  
2.  选中**“收集 CPU 计数器”**复选框。  
  
3.  展开**“可用的性能计数器”**树，直到找到要收集的样本事件。  
  
4.  对于要收集的每个事件，选择该事件，然后单击右箭头将该事件添加到**“选定的计数器”**列表中。  
  
    > [!NOTE]
    >  只有选中了**“收集 CPU 计数器”**复选框时，才会启用**“可用的性能计数器”**。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [性能会话属性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 计数器](../profiling/cpu-and-windows-counters.md)   
 [如何：选择采样事件](../Topic/How%20to:%20Choose%20Sampling%20Events.md)