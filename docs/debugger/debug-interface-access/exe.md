---
title: "Exe | Microsoft Docs"
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
  - ".dll 文件"
  - "Exe 符号"
  - ".exe 文件"
  - "可执行文件, Exe 符号"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

，因为它表示 .exe 或 .dll 文件的全局范围，系统是唯一的符号不词法或类父级。  只能有 `SymTagExe` 标记的符号每个文件。  [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md) 方法返回符号。  
  
## 属性  
 下表显示此符号类型有效的任何属性。  
  
|属性|数据类型|说明|  
|--------|----------|--------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|可执行的年龄。|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|可执行的`GUID` 。|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` ，如果符号文件与此可执行文件包含 C 类型 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` ，如果私有符号从符号文件中去除与此可执行文件 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|指示目标 CPU \(之一的值 [CV\_CPU\_TYPE\_e 枚举](../../debugger/debug-interface-access/cv-cpu-type-e.md) 值\)。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|.exe 文件的名称。|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|签名可执行文件。|  
|[IDiaSymbol::get\_symbolsFileName](../Topic/IDiaSymbol::get_symbolsFileName.md)|`BSTR`|.exe 文件的 .pdb 或 .dbg 文件的完整路径。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagExe` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
  
## 请参阅  
 [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)