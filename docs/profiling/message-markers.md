---
title: "消息标记 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 消息标记
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

消息标记代表日志输出。  消息是特定线程按特定时间发出的字符串。  可以导出消息到文本文件,与其他工具一起使用。  可以将鼠标指针停在并发可视化工具的信息上来显示信息字符串。  您可以在 [标记报告](../profiling/markers-report.md)的所有消息标记。以下插图显示了消息标记。  
  
## 消息标记聚合  
 有时并发可视化工具的多个消息发生的过于接近以至于它们不能单独绘制。  发生这种情况时，表示显示基础消息的 *消息聚合标记*。  当将鼠标停在这些图标之一上时，工具提示显示表示基础消息的数量。  若要显示消息，请放大。如果始终放大并且仍获取聚合标记，您可在查看 [标记报告](../profiling/markers-report.md)的基础信息。  
  
## 请参阅  
 [并发可视化工具标记](../profiling/concurrency-visualizer-markers.md)   
 [并发可视化工具 SDK](../profiling/concurrency-visualizer-sdk.md)