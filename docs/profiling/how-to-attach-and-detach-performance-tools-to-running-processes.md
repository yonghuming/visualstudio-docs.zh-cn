---
title: "如何：在正在运行的进程中附加和分离探查器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.attach"
helpviewer_keywords: 
  - "性能工具, 附加进程"
  - "分析工具, 分离进程"
  - "分析工具, 附加进程"
  - "性能工具, 分离进程"
  - "探查器"
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：在正在运行的进程中附加和分离探查器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

探查器可用于附加到正在运行的进程，或从正在运行的进程分离，从而简化性能数据的采样和收集。  如果您要避免收集有关应用程序加载时间的数据，或在进程达到某个特定状态时监视进程的性能，您可以使用此方法来分析进程。  
  
> [!NOTE]
>  下面的步骤适用于在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 集成开发环境 \(IDE\) 内附加和分离进程。  有关如何使用命令行工具的信息，请参见 [通过命令行进行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)。  有关如何分析服务的信息，请参见[分析服务](../profiling/command-line-profiling-of-services.md)。  
  
 可用于分析的进程取决于计算机管理员设置的用户访问权限。  例如，用户帐户可能具有以下操作的权限：  
  
-   高级分析功能（当管理员设置了要启动的驱动程序和服务时）。  
  
-   仅限采样分析（域用户）。  
  
-   拒绝向每个人提供分析的访问权。  
  
 有关更多信息，请参见[分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)和 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 选项。  
  
### 附加到正在运行的进程  
  
1.  在**“分析”**菜单上，指向**“探查器”**，然后单击**“附加\/分离”**。  
  
     \- 或 \-  
  
     在**“性能资源管理器”**中，右击性能会话，然后单击**“附加\/分离”**。  
  
     将出现**“将探查器附加到进程”**对话框。  
  
2.  单击要附加到的进程的名称。  
  
3.  单击**“附加”**。  
  
### 从正在运行的进程分离  
  
1.  在**“分析”**菜单上，指向**“探查器”**，然后单击**“附加\/分离”**。  
  
     \- 或 \-  
  
     在**“性能资源管理器”**中，右击性能会话，然后单击**“附加\/分离”**。  
  
     将出现**“将探查器附加到进程”**对话框。  
  
2.  单击要分离的映像名称。  
  
3.  单击**“分离”**。  
  
## 请参阅  
 [控制数据收集](../profiling/controlling-data-collection.md)   
 [性能会话概述](../profiling/performance-session-overview.md)   
 [如何：启动和结束分析](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [分析和 Windows Vista 安全性](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)