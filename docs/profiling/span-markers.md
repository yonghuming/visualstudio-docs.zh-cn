---
title: "范围标记 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.span"
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 范围标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

范围标记表示应用程序的有意义阶段。  例如，可以使用大小表示期间特定工作项处理的时间间隔。  其长度表示相应的应用程序阶段的持续时间。  下图显示并发可视化工具的一个范围：  
  
 ![并发可视化工具中的范围标记](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
并发可视化工具中的范围标记  
  
## 范围类别  
 范围标记会以五种不同颜色之一显示，具体取决于其类别。  如果具有超过5个类别则颜色会重复。  类别可以是任意整数。  此图显示五种可能的颜色：  
  
 ![不同类别中的 5 个范围](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
前面五范围类别的颜色  
  
## 聚合标记范围  
 有时并发可视化工具的范围标记发生的过于接近以至于它们不能单独绘制。  发生这种情况时，表示显示基础范围的 灰色*范围聚合标记*。  当将鼠标停在这些图标之一上时，工具提示显示表示基础范围的数量。  若要显示范围，请放大。  如果始终放大和仍获取范围标记聚合，可以在 [标记报告](../profiling/markers-report.md)的基础范围标记。  此图显示一个范围聚合标记：  
  
 ![并发可视化工具中的聚合范围](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
聚合标记范围  
  
## 请参阅  
 [并发可视化工具标记](../profiling/concurrency-visualizer-markers.md)   
 [并发可视化工具 SDK](../profiling/concurrency-visualizer-sdk.md)