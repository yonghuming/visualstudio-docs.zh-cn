---
title: "marker_series::write_flag 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag 方法"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_series::write_flag 方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

将标志写入并发可视化工具跟踪文件。  
  
## 语法  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### 参数  
 `_Format`  
 一个包含与零个或多个格式项混合的文本的复合格式字符串，这些格式项与变量列表中的对象相对应  
  
 `_Importance`  
 重要程度。  
  
 `_Category`  
 分类  
  
## 要求  
 **页眉：**cvmarkersobj.h  
  
 **命名空间:** Concurrency::diagnostic。  
  
## 请参阅  
 [marker\_series 类](../profiling/marker-series-class.md)