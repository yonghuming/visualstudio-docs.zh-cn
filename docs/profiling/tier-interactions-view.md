---
title: "“层交互”视图 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "“层交互”视图"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “层交互”视图
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

层交互分析提供有关多层应用程序的函数中的执行时间的其他信息，这些应用程序通过 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] 与数据库通信。  收集的数据仅用于同步函数调用。  
  
 **要求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 交互视图在两个窗格中显示层交互数据：  
  
-   主窗格是一个层次结构树。  顶级行包含 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 页或进程的数据库连接聚合数据。  子节点包含父级的数据库连接的聚合数据。  
  
-   当在主窗格中单击某个数据库调用节点时，该数据库调用的实例的数据会显示在细节窗格中。  
  
 时间以毫秒数或 CPU 时钟计时周期数的形式显示。  若要更改显示的时间单位，请单击**“工具”**菜单，单击**“选项”**，然后选择**“将时间值显示为”**选项之一。  
  
## 主窗格  
  
|列|说明|  
|-------|--------|  
|**名称**|-   对于顶级行，为分析的进程或网页的名称。<br />-   对于数据库连接行，为承载数据库的服务器的名称。|  
|**数据库**|数据库的名称（仅限数据库连接行）。|  
|**计数**|此进程、网站或数据库连接所生成的请求总数。|  
|**总运行时间**|执行来自此进程、网站或数据库连接的任何一个请求所花费的时间总计。|  
|**最大运行时间**|执行来自进程、网站或数据库连接的任何一个请求所花费的最大时间。|  
|**最小运行时间**|执行来自进程、网站或数据库连接的任何一个请求所花费的最小时间。|  
|**平均运行时间**|执行来自进程、Web 页面或数据库连接的每个请求所花费的平均时间。|  
  
## “数据库连接详细信息”窗格  
  
|列|说明|  
|-------|--------|  
|**命令文本**|请求的 SQL 查询。|  
|**查询计数**|运行查询的次数。|  
|**总运行时间**|执行查询实例所花费的时间总计。|  
|**最大运行时间**|执行任何一个查询实例所花费的最大时间。|  
|**最小运行时间**|执行任何一个查询实例所花费的最小时间。|  
|**平均运行时间**|执行每个查询实例所花费的平均时间。|