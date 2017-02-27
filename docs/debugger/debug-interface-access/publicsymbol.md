---
title: "PublicSymbol | Microsoft Docs"
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
  - "数据符号 [C++]"
  - "PublicSymbol 符号"
  - "全局函数 [C++], 作为公共符号"
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PublicSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当 .exe 文件之后， \(最少，每个全局函数和数据符号\) 为每个公共符号一 `SymTagPublicSymbol` 标记。  
  
## 属性  
 下表显示此符号类型有效的任何属性。  
  
|属性|数据类型|说明|  
|--------|----------|--------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位置的偏移量部件;有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|位置的部分; 部件有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` ，如果符号的位置在代码。|  
|[IDiaSymbol::get\_function](../Topic/IDiaSymbol::get_function.md)|`BOOL`|`TRUE` ，如果符号是功能。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|此符号字节长度。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|全局范围的符号。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号的 ID。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|公共符号具有静态位置;有关详细信息，请参见 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get\_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` ，如果符号的位置在托管代码。|  
|[IDiaSymbol::get\_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` ，如果符号的位置 Microsoft 中间语言 \(msil\) 代码。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|符号的完全修饰名。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|符号的相对位置在其块中。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagPublicSymbol` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|未修饰符号名称。|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|部分或全部未修饰符号名称。|  
  
## 请参阅  
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)   
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)