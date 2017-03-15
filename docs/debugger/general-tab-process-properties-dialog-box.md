---
title: "“进程属性”对话框 -&gt;“常规”选项卡 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows NT 的进程属性"
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# “进程属性”对话框 -&gt;“常规”选项卡
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用“常规”选项卡可以查找有关特定进程的更多信息。  若要显示[“进程属性”对话框](../debugger/process-properties-dialog-box.md)，请将焦点移动到[进程视图](../debugger/processes-view.md)窗口。  在树中选择任何进程节点，然后从“视图”菜单中选择“属性”。  
  
 “常规”选项卡上提供了下列设置：  
  
|Entry|说明|  
|-----------|--------|  
|**模块名**|模块的名称。|  
|**进程 ID**|此进程的唯一 ID。  进程 ID 号会重复使用，所以它们只在进程的生存期中标识该进程。  在程序运行时，将创建进程对象类型。  进程中的所有线程共享同一地址空间并有权访问相同的数据。|  
|**优先级基数**|此进程的当前基本优先级。  进程中的线程可以相对于进程的基本优先级，提升和降低它们自己的基本优先级。|  
|**线程**|此进程中当前处于活动状态的线程数量。|  
|**CPU 时间**|在此进程及其线程上花费的总 CPU 时间。  等于用户时间与特权时间之和。|  
|**用户时间**|此进程的线程以用户模式，在非空闲线程中执行代码所花费的累计运行时间。  应用程序以用户模式执行，窗口管理器和图形引擎等子系统也是如此。|  
|**特权时间**|此进程以特权模式在非空闲线程中运行的总时间。  服务层、执行例程和内核以特权模式执行。  大多数设备（除图形适配器和打印机外）的设备驱动程序也以特权模式执行。  除特权时间外，Windows 为应用程序执行的某些工作可能显示在其他子系统进程中。|  
|**运行时间**|此进程已运行的总时间。|