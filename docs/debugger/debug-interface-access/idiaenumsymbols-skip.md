---
title: "IDiaEnumSymbols::Skip | Microsoft Docs"
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
  - "IDiaEnumSymbols::Skip 方法"
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

跳过符号指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 符号数在跳过的枚举序列的。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，因此，如果不再有要跳过，的无符号返回 `S_FALSE` 。  
  
## 请参阅  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)