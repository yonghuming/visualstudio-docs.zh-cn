---
title: "IDiaSymbol::get_code | Microsoft Docs"
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
  - "IDiaSymbol::get_code 方法"
ms.assetid: 5f425fa3-7ba6-4979-8b3e-0fcd06cbba73
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_code
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指定的标志符号是否引用一个代码地址。  
  
## 语法  
  
```cpp#  
HRESULT get_code (   
   BOOL* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回 `TRUE` ，如果符号是指一个代码地址，否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 要求  
  
|要求|说明|  
|--------|--------|  
|标题:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)