---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv 方法"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检查两符号是否等效。  
  
## 语法  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### 参数  
 `symbolA`  
 \[in\] 用于比较的第一 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象。  
  
 `symbolB`  
 \[in\] 用于比较的第二 `IDiaSymbol` 对象。  
  
## 返回值  
 如果符号相等，则返回; `S_OK`否则，返回 `S_FALSE`，符号不是等效的。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)