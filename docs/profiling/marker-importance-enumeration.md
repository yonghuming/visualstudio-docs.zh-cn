---
title: "marker_importance 枚举 | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance 枚举"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_importance 枚举
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示并发可视化工具标记的重要性级别。  
  
## 语法  
  
```  
enum marker_importance;  
```  
  
## 成员  
  
### 值  
  
|名称|说明|  
|--------|--------|  
|`critical_importance`|指定具有关键的重要性的标记。|  
|`high_importance`|指定具有高重要性的标记。|  
|`low_importance`|指定具有低重要性的标记。|  
|`normal_importance`|指定具有普通重要性的标记。|  
  
## 要求  
 **页眉：**cvmarkersobj.h  
  
 **命名空间:** Concurrency::diagnostic。  
  
## 请参阅  
 [diagnostic 命名空间](../profiling/diagnostic-namespace.md)