---
title: "IDiaEnumSymbolsByAddr::Next | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSymbolsByAddr::Next 方法"
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

由地址检索下符号按顺序。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
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
 如果成功，则返回 `S_OK`。  ，如果没有更多的符号，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 备注  
 此方法由获取元素的数量更新枚举数位置。  
  
## 请参阅  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)