---
title: "marker_series::write_alert 方法 | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert 方法"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_alert 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将警报写入并发可视化工具跟踪文件。  
  
## 语法  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### 参数  
 `_Format`  
 一个包含与零个或多个格式项混合的文本的复合格式字符串，这些格式项与变量列表中的对象相对应  
  
## 要求  
 **页眉：**cvmarkersobj.h  
  
 **命名空间:** Concurrency::diagnostic。  
  
## 请参阅  
 [marker\_series 类](../profiling/marker-series-class.md)