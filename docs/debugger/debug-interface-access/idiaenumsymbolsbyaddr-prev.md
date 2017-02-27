---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev 方法"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由地址检索以前的符号按顺序。  
  
## 语法  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 符号数在枚举数将检索。  
  
 rgelt  
 \[out\] 将通过 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 填充的对象表示预期符号的数组。  
  
 pceltFetched  
 \[out\] 返回符号结果中的位。获取的枚举器。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ; 如果没有前面的符号，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 此方法由获取元素的数量更新枚举数位置。  
  
## 请参阅  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)