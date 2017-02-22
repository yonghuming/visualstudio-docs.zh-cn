---
title: "如何：收集 Windows 计数器数据 | Microsoft Docs"
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
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "Windows 计数器"
  - "性能工具, 使用 Windows 计数器"
  - "分析工具, 使用 Windows 计数器"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：收集 Windows 计数器数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows 计数器是可以在分析过程中按设定的时间间隔收集的系统性能计数器。  在分析工具报告的“标记”视图中，对于每个收集时间间隔都有一个标记为**“AutoMark”**的行。  该行包含描述该时间间隔内的性能计数器值的列。  若要将分析限制在两个特定标记之间的时间段，请选择这些标记，在快捷菜单中右击并选择**“添加针对标记的筛选器”**\>。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增强安全功能需要在 Visual Studio 探查器收集这些平台上的数据的方式上的重大更改。  Windows 应用商店应用程序还需要新的集合技术。  请参见[分析 Windows 8 和 Windows Server 2012 应用程序](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
### 收集 Windows 计数器数据  
  
1.  在“性能资源管理器”中，右击要为其配置 Windows 计数器的会话，然后选择**“属性”**。  
  
2.  在**“属性页”**中，单击**“Windows 计数器”**。  
  
3.  选中**“收集 Windows 计数器”**复选框。  
  
4.  在**“收集间隔\(毫秒\)”**文本框中，键入一个时间间隔。  
  
5.  从**“计数器类别”**下拉列表中选择某种类别。  
  
6.  从**“实例”**下拉列表中选择一个实例。  
  
7.  选择分析应用程序时要使用的计数器。  
  
8.  单击**“应用”**。  
  
## 请参阅  
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [性能会话属性](../profiling/performance-session-properties.md)   
 [CPU 和 Windows 计数器](../profiling/cpu-and-windows-counters.md)