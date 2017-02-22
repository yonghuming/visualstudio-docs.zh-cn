---
title: "IDiaSymbol::findChildrenExByVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::findChildrenExByVA"
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索有效在指定的虚拟地址符号的子级。  
  
## 语法  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 参数  
 `symtag`  
 \[in\] 指定要检索的子级的符号标记，对于 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)定义。  设置为所有子级的 `SymTagNull` 可以进行检索。  
  
 `name`  
 \[in\] 指定子元素的名称将检索。  设置为所有子级的 `NULL` 可以进行检索。  
  
 `compareFlags`  
 \[in\] 指定要应用的比较选项。名称匹配。  从 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md) 枚举的值既可以单独使用或在组合。  
  
 `address`  
 \[in\] 指定虚拟地址。  
  
 `ppResult`  
 \[out\] 返回包含检索的子符号列表的 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 对象。  
  
## 返回值  
 返回 `S_OK` ，如果找到符号的至少一个子级，或者返回 `S_FALSE` ，如果未找到子项;否则，返回错误代码。  
  
## 备注  
 返回的本地符号包括活动范围信息。  
  
## 要求  
 标题:Dia2.h  
  
 库:diaguids.lib  
  
 DLL:msdia100.dll  
  
## 请参阅  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)