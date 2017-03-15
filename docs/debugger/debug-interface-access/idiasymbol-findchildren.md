---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren 方法"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索符号的子级。  
  
## 语法  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 参数  
 `symtag`  
 \[in\] 指定要检索的子级的符号标记，对于 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)定义。  设置为所有子级的 `SymTagNull` 可以进行检索。  
  
 `name`  
 \[in\] 指定子元素的名称将检索。  设置为所有子级的 `NULL` 可以进行检索。  
  
 `compareFlags`  
 \[in\] 指定比较选项适用于名称匹配。  从 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md) 枚举的值既可以单独使用或在组合。  
  
 `ppResult`  
 \[out\] 返回包含检索的子符号列表的 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 对象。  
  
## 返回值  
 返回 `S_OK` ，如果找到符号的至少一个子级，或者返回 `S_FALSE` ，如果未找到子项;否则返回错误代码。  
  
## 备注  
 此方法的调用与该符号的 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) 方法相同的作为第一个参数。  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)