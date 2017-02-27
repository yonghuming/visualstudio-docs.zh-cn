---
title: "“资源详细信息”视图 - 探查器争用数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "“资源详细信息”视图"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# “资源详细信息”视图 - 探查器争用数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“资源详细信息”视图针对因所选资源争用而导致的阻塞事件提供一个时间线图。  因另一个线程锁定了对资源的访问而迫使线程暂停执行时，即发生阻塞事件。  
  
 此视图以水平条的形式显示每个线程的执行时间线，并在线程时间线上以垂直条的形式表示每个阻塞事件。  必要时，可以放大时间线的一部分来查看单独的事件。  若要查看导致事件的函数的执行路径（调用堆栈），请单击事件条。  此时将在**“调用堆栈”**窗口中显示这些函数。  获得函数的源代码后，可以单击该函数名，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的界面中编辑源文件。  
  
## 过程  
  
#### 放大时间线的片段  
  
-   在时间线的某个区域上方拖动鼠标指针。  
  
     释放鼠标按钮后，视图将缩放到所选的时间段。  可重复此过程进一步放大片段。  时间滚动条上的滚动框表示视图中显示的时间段的相对大小。  
  
#### 缩小时间线  
  
-   执行以下步骤之一：  
  
    -   单击**“缩小”**返回上一个缩放级别。  
  
    -   单击**“缩放重置”**在视图中显示整个时间线。  
  
#### 查看事件的调用堆栈  
  
-   在时间线图中，单击事件条。  
  
#### 查看或编辑调用堆栈中某个函数的源代码  
  
-   在**“调用堆栈”**窗口中，单击该函数名。  
  
 函数源代码必须是当前项目的一部分。  
  
#### 查看资源的争用事件的调用树  
  
-   在时间线图中，单击**“总计”**。  
  
     此时将显示资源的“争用”视图。  有关更多信息，请参见[“资源争用”视图](../profiling/resource-contentions-view-contention-data.md)  
  
#### 查看线程的所有争用事件  
  
-   在时间线图中，单击该线程的名称或 ID。  
  
     此时将显示所选线程的“线程详细信息”视图。  有关更多信息，请参见 [“线程详细信息”视图](../profiling/thread-details-view-contention-data.md)。