---
title: "IDiaEnumLineNumbers::Next | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Next 方法"
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索行号指定数目的枚举序列的。  
  
## 语法  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### 参数  
 凯尔特人  
 \[in\] 行号数在枚举数将检索。  
  
 rgelt  
 \[out\] 返回一个数组表示预期行号的 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) 对象。  
  
 pceltFetched  
 \[out\] 返回行号结果中的位。获取的枚举器。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果没有更多的行号，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)