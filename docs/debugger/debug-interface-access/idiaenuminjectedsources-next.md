---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Next 方法"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索插入的源指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 插入的源数在枚举数将检索。  
  
 rgelt  
 \[out\] 返回表示预期插入的源的数组 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 对象。  
  
 pceltFetched  
 \[out\] 返回插入的源结果中的位。获取的枚举器。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的插入的源，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)