---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "IDiaSession::findChildren 方法"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

检索与名称和符号类型指定的一个父标识符的所有子级。  
  
## 语法  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 参数  
 `parent`  
 \[in\] 表示父的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 对象。  如果此父符号是函数，模块，或块，则它的词法子项。 `ppResult`返回。  如果父符号的类型为，则其类子返回。  如果此参数是 `NULL`，则必须设置 `symtag` 到 `SymTagExe` 或 `SymTagNull`，返回全局范围 \(.exe 文件\)。  
  
 `symtag`  
 \[in\] 指定子元素的符号标记进行检索。  值从 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 枚举中采用。  设置为 `SymTagNull` 检索所有子级。  
  
 `name`  
 \[in\] 指定子元素的名称将检索。  设置为所有子级的 `NULL` 可以进行检索。  
  
 `compareFlags`  
 \[in\] 指定比较选项适用于名称匹配。  从 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md) 枚举的值既可以单独使用或在组合。  
  
 `ppResult`  
 \[out\] 返回包含子符号列表检索的 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 对象。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 示例  
 下面的示例演示如何查找与其名称 `szVarName`功能 `pFunc` 的局部变量。  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## 请参阅  
 [概述](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions 枚举](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)