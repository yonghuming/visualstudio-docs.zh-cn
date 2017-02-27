---
title: "IDiaSymbol::get_framePointerPresent | Microsoft Docs"
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
  - "IDiaSymbol::get_framePointerPresent 方法"
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDiaSymbol::get_framePointerPresent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索指定的标志帧指针是否存在。  使用，在 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 设置为 `SymTagFunction`。  
  
## 语法  
  
```cpp#  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] ，如果帧指针存在，则返回; `TRUE` \]否则，返回 `FALSE`。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia100.dll  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)