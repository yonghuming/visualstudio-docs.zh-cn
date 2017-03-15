---
title: "使用率导航器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.performance.utilizationnavigator"
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用率导航器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用并发可视化工具中的利用导航器来选择跟踪的时间间隔。  并发可视化工具显示目标进程一段时间内 的CPU 内核使用率。  这样便于检查 CPU 使用率模式并可以启用在利用数据和其他视图的数据之间的比较。  使用率导航器显示在并发可视化工具的每个视图的顶部。  下图显示利用导航器。  
  
 ![显示选定时间范围的利用率导航器](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
利用率导航器和一个选定时间的框架。  
  
 在图中，选择的时间由一个红色矩形定义的，即 *Thumb控件*。  
  
 这儿显示如何使用这些利用率操作导航器来操作显示时间的范围：  
  
-   可以通过拖动Thumb控件向左或向右来平移。\(键盘：将焦点移动到 Thumb控件 然后按下向左或向右箭头键。\)  
  
-   通过拖动其中一个图柄来更改间隔的程度。\(键盘：将焦点移动到 一个图柄 然后按下向右或向左箭头键。\)  
  
 如果使用另一种并发可视化工具缩放控件来更改间隔，则使用率导航器会更新以反射更改。