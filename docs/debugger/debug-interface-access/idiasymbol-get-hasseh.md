---
title: "IDiaSymbol::get_hasSEH | Microsoft Docs"
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
  - "IDiaSymbol::get_hasSEH 方法"
ms.assetid: 1a709ded-22c8-464c-97be-eba5e464210c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_hasSEH
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指定的标志函数是否包含任何 [结构化异常处理](/visual-cpp/cpp/structured-exception-handling-c-cpp) \(例如， \_\_try\/\_\_except 块\)。  
  
## 语法  
  
```cpp#  
HRESULT get_hasSEH(  
   BOOL *pFlag  
);  
```  
  
#### 参数  
 `pFlag`  
 \[out\] ，如果函数有任何结构化异常处理块，则返回; `TRUE` 否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v8.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [结构化异常处理](/visual-cpp/cpp/structured-exception-handling-c-cpp)