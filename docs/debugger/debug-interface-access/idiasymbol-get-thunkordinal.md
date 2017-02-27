---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "IDiaSymbol::get_thunkOrdinal 方法"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索功能的 thunk 类型。  
  
## 语法  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 返回从指定函数的 thunk 类型的 [THUNK\_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md) 枚举的值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 此属性有效，仅当符号为 `SymTagThunk`的 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值。  
  
 “thunk”是将 32 位内存地址空间代码中 \(也称为简单地址空间\) 和 16 位地址空间 \(称为分段的地址空间\)。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK\_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)