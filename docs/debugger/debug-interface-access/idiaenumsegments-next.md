---
title: "IDiaEnumSegments::Next | Microsoft Docs"
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
  - "IDiaEnumSegments::Next 方法"
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索段指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 长的射线在枚举数将检索。  
  
 rgelt  
 \[out\] 将由所需 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 填充的对象表示段的数组。  
  
 pceltFetched  
 \[out\] 返回段结果中的位。获取的枚举器。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的段，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)