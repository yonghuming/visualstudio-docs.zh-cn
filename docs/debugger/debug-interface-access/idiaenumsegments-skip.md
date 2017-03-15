---
title: "IDiaEnumSegments::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments::Skip 方法"
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

跳过段指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 长的射线在跳过的枚举序列的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，因此，如果不再有要跳过，的非段返回 `S_FALSE` 。  
  
## 请参阅  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)