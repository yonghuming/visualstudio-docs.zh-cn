---
title: "收集线程和进程并发数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "并发分析方法"
  - "分析工具, 并发方法"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 收集线程和进程并发数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]分析工具并发分析方法可以收集收集资源争用数据，该数据包含有关每个同步事件的信息，它会造成在配置文件分析应用程序中的函数等待访问资源。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 可以使用以下过程之一指定并发分析方法：  
  
-   在分析向导的第一页上，单击**Concurrency**。  
  
-   在性能会话的属性对话框的**常规**页上，单击**并发**。  
  
-   在**“性能资源管理器”**工具栏上的**“方法”**列表中，单击**“并发”**。  
  
## 常规任务  
 您可以在性能部分的*Performance Session* **属性页面**对话框中指定附加选项。  打开此对话框：  
  
-   在**“性能资源管理器”**中，右击性能会话名称，然后单击**“属性”**。  
  
 下表中的任务说明在使用并发方法进行分析时，可以在*性能会话Performance Session* **属性页** 对话框中指定选项。  
  
|任务|相关内容|  
|--------|----------|  
|在**“常规”**页上，指定生成的分析数据 \(.vsp\) 文件的命名详细信息。|-   [如何：设置分析数据文件名选项](../profiling/how-to-set-performance-data-file-name-options.md)|  
|在**“启动”**页上，指定代码解决方案中有多个 .exe 项目时要启动的应用程序。|-   [如何：指定要启动的二进制文件](../profiling/how-to-specify-the-binary-to-start.md)|  
|在**“层交互”**页上，向分析运行添加 ADO.NET 调用数据。|-   [收集层交互数据](../profiling/collecting-tier-interaction-data.md)|  
|在**“Windows 计数器”**页上，指定要作为标记添加到分析数据的一个或多个操作系统性能计数器。|-   [如何：收集 Windows 计数器数据](../profiling/how-to-collect-windows-counter-data.md)|  
|在**“高级”**页上，指定在应用程序模块使用多个 .NET Framework 运行时版本时，要分析的运行时版本。  默认情况下分析加载的第一个版本。|-   [如何：在并行方案中指定要分析的 .NET Framework 运行时](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|