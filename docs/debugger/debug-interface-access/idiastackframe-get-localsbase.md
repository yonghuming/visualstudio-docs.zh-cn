---
title: "IDiaStackFrame::get_localsBase | Microsoft Docs"
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
  - "IDiaStackFrame::get_localsBase 方法"
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackFrame::get_localsBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索局部变量的基址帧的。  
  
## 语法  
  
```cpp#  
HRESULT get_localsBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回局部变量的基址。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果该属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)