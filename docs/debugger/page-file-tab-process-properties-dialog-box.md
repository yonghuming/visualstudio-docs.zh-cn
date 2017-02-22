---
title: "“进程属性”对话框 -&gt;“页文件”选项卡 | Microsoft Docs"
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
  - "Windows NT 的进程属性"
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “进程属性”对话框 -&gt;“页文件”选项卡
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用“页文件”选项卡可以检查进程的页面文件。  若要显示[“进程属性”对话框](../debugger/process-properties-dialog-box.md)，请将焦点移动到[进程视图](../debugger/processes-view.md)窗口。  在树中选择任何进程节点，然后从“视图”菜单中选择“属性”。  
  
 “页文件”选项卡上提供了下列设置：  
  
|Entry|说明|  
|-----------|--------|  
|**页文件字节**|进程在页面文件中使用的页的当前数目。  页面文件存储进程使用的、但其他文件中未包含的数据的页。  页面文件由所有进程使用，如果页面文件缺少空间，则可能会导致在其他进程运行时出错。|  
|**峰值页文件字节**|进程已在页面文件中使用的最大页数。|  
|**页面错误**|由进程中正在执行的线程导致的页面错误数。  如果线程引用的虚拟内存页面不在其位于主内存的工作集中，会出现页面错误。  因此，如果页面位于备用列表中因而已位于主内存中，或者如果页面正由与之共享该页面的其他进程使用，则不会从磁盘检索该页面。|