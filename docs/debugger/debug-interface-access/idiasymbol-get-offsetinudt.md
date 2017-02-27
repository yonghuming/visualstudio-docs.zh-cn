---
title: "IDiaSymbol::get_offsetInUdt | Microsoft Docs"
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
  - "IDiaSymbol::get_offsetInUdt 方法"
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_offsetInUdt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索对一个成员的用户定义的类型的开头的偏移 \(UDT\)量 UDT 的。  
  
## 语法  
  
```cpp#  
HRESULT get_offsetInUdt(   
   DWORD* pRetVal)  
);  
```  
  
#### 参数  
 `pRetVal`  
 \[out\] 在符号位置的字节数组返回偏移量。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回 `S_FALSE` 或错误代码。  
  
> [!NOTE]
>  `S_FALSE` 的返回值表示该属性用于符号不可用。  
  
## 备注  
 此功能在优化生成的本地记录只使用。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia100.dll  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)