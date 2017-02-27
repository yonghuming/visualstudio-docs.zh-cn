---
title: "IDiaSectionContrib::get_compiland | Microsoft Docs"
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
  - "IDiaSectionContrib::get_compiland 方法"
ms.assetid: c0496f6f-f8f2-435f-8674-6c32db6c5934
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSectionContrib::get_compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索对提供本节的编译符号。  
  
## 语法  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回表示提供本节的 compiland 中 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果此属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)