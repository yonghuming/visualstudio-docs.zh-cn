---
title: "“性能资源管理器”窗口 | Microsoft Docs"
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
  - "vs.performanceexplorer"
  - "vs.performance.explorer"
helpviewer_keywords: 
  - "性能工具, 性能资源管理器"
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “性能资源管理器”窗口
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通过 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(IDE\) 中的**“性能资源管理器”**窗口，您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具来配置和启动性能会话。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## 性能资源管理器工具栏  
 **“性能资源管理器”**工具栏中提供了以下选项：  
  
-   **启动性能向导** \- 显示“性能向导”，以便向“性能资源管理器”窗口中添加新的性能会话。  
  
-   **新建性能会话** \- 向“性能资源管理器”窗口中添加空的性能会话。  
  
-   **启动** \- 利用**“启动”**命令按钮列表，可以启动启用立即分析（**“启动并启用分析功能”**）或暂停分析（**“启动并暂停分析”**）的目标应用程序。  
  
-   **方法** \- 指定会话的分析方法是采样还是检测。  
  
-   **停止** \- 立即退出目标应用程序和探查器。  
  
-   **附加\/分离** \- 显示**“将探查器附加到进程”**对话框，以选择要附加探查器且正在运行的进程。  
  
## “性能资源管理器”窗口  
 **“性能资源管理器”**窗口包含一个树控件，该控件显示一个或多个性能会话的二进制文件和报告数据文件。  
  
-   **会话名称** \- 树控件的根包含会话的名称。  右击会话名称可设置会话属性或启动目标应用程序和探查器。  
  
-   **目标** \- 显示要在会话中分析的二进制文件的名称。  右击**“目标”**可添加或移除二进制文件、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 项目或网站。  右击目标名称可设置单个二进制文件的属性。  
  
-   **报告** \- 显示为会话生成的探查器数据文件的名称。  右击**“报告”**可添加一个现有报告或比较两个探查器数据文件。  右击某个报告名称可打开、移除或导出一个探查器数据文件。  
  
## 请参阅  
 [概述](../profiling/overviews-performance-tools.md)   
 [配置性能会话](../profiling/configuring-performance-sessions.md)   
 [控制数据收集](../profiling/controlling-data-collection.md)