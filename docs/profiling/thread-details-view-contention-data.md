---
title: "“线程详细信息”视图 - 探查器争用数据 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "“线程详细信息”视图"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# “线程详细信息”视图 - 探查器争用数据
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

“线程详细信息”视图针对分析运行的所选线程中因资源争用而导致的阻塞事件提供一个时间线图。  因另一个线程锁定了对资源的访问而迫使线程暂停执行时，即发生阻塞事件。  
  
 此视图以水平条的形式显示线程的执行时间线，并在线程的水平时间线上以垂直条的形式显示阻塞事件。  必要时，可以放大时间线的一部分来查看单独的事件。  若要查看导致事件的函数的执行路径，请单击事件条。  此时将在“调用堆栈”窗口中显示这些函数。  当函数的源代码可用时，可以单击该函数名，在 Visual Studio ID 中编辑源文件。  
  
## 在时间线中导航  
  
#### 放大时间线的片段  
  
-   单击并拖动鼠标指针选择时间线的某个区域。  
  
     释放鼠标后，视图将缩放到所选的时间段。  可重复此过程放大更多细节。  时间滚动条上的滚动框表示视图中显示的时间段的相对大小。  
  
#### 缩小时间线  
  
-   单击**“缩小”**返回上一个缩放级别。  
  
-   单击**“缩放重置”**在视图中显示整个时间线。  
  
#### 查看事件的调用堆栈  
  
-   在时间线图中，单击表示事件的垂直条。  
  
#### 查看或编辑调用堆栈中某个函数的源代码  
  
-   在“调用堆栈”窗口中，单击该函数名。  
  
 函数源代码必须是当前项目的一部分。  
  
#### 查看分析运行期间所有线程中对某项资源的争用事件  
  
-   在时间线图中，单击该资源的名称或 ID。  
  
     此时将显示所选资源的[“资源详细信息”视图](../profiling/resource-details-view-contention-data.md)。  
  
#### 在“进程”窗口中查看线程争用数据  
  
-   在时间线图中，单击**“总计”**。  
  
     此时将显示所选线程的[“进程”视图](../profiling/process-view-contention-data.md)。