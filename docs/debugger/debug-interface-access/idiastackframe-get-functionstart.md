---
title: "IDiaStackFrame::get_functionStart | Microsoft Docs"
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
  - "IDiaStackFrame::get_functionStart"
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_functionStart
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指示的标志块是否包含入口点函数。  
  
## 语法  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] ，如果堆栈帧包含入口点函数，则返回; `TRUE` 否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回 `S_OK`。  ，如果该属性不受支持，返回 `S_FALSE` 。  否则，返回错误代码。  
  
## 请参阅  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)