---
title: "标记报告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 标记报告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

标记报表列出了显示时间框架里的标记。平移或传输或隐藏通道，可能导致路由标记显示或消失。  报表中包含有关各个标记的此信息：  
  
-   当它开始时，相对于跟踪的开头。  
  
-   持续时间。  持续时间的标志和消息为零因为它们表示即时。  
  
-   生成它的线程ID  
  
-   生成它的 Windows \(ETW\) 事件跟踪提供程序的。  
  
-   写入标记的序列。  
  
-   它所属的事件类别。  
  
-   其重要程度。  
  
-   其类型 \(大小、标志或消息\)。  
  
-   它表示的深入说明。  
  
 选择 导出 按钮保存标记报告作为 CSV 文件。  可以使用其他应用程序或工具的 CSV 文件中的数据。  
  
> [!NOTE]
>  标记报表可显示 1,000 个标记。  若要查看全部标记，导出报告全文到 CSV 文件。