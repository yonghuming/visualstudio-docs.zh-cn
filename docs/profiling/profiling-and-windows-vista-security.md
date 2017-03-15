---
title: "分析和 Windows Vista 安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "分析工具, 安全性"
  - "性能工具, 安全性"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 分析和 Windows Vista 安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

根据计算机管理员提供的 [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] 用户访问权限设置，单个用户可能有在该计算机上分析进程的安全权限。  下面的示例演示了用户间可能存在的不同之处：  
  
-   管理员设置了要启动的驱动程序和服务后，某些用户可以访问高级分析功能。  
  
-   域用户仅能访问取样分析。  
  
-   某些用户可以拒绝向所有其他用户提供分析的访问权。  
  
 有关更多信息，请参见 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 选项。  
  
## 跨会话分析  
 跨会话分析能够分析在不同登录会话中运行的进程。  例如，大多数服务在会话 0 中运行，并且用户不能直接在会话 0 中运行。  使用“性能资源管理器”工具栏上的**“附加到进程”**按钮或 VSPerfCmd 命令行工具的 \/attach 选项，您可以分析不同登录会话中的大多数进程。  
  
 您可以通过设置跨进程分析可见性选项来查看可用的进程列表。  单击**“附加到进程”**时显示的**“附加到进程”**窗口中提供了以下选项：  
  
-   **显示所有用户的进程**  
  
     没有选择此选项时，列表仅显示当前用户拥有的进程。  选择**“显示所有用户的进程”**时，列表显示所有用户的进程。  
  
-   **显示所有会话中的进程**  
  
     没有选择此选项时，列表显示当前会话中的进程。  选择此选项时，列表显示所有会话中的进程。  
  
## 请参阅  
 [概述](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/zh-cn/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)