---
title: "IDiaEnumFrameData::Next | Microsoft Docs"
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
  - "IDiaEnumFrameData::Next 方法"
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索框架元素指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 框架元素数在枚举数将检索。  
  
 rgelt  
 \[out\] 数组使用请求的框架元素将由填充的 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 对象。  
  
 pceltFetched  
 \[out\] 返回框架元素数在枚举中获取的枚举器。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的记录，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)