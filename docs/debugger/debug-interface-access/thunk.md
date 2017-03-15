---
title: "Thunk | Microsoft Docs"
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
  - "thunk 属性 [DIA SDK]"
  - "thunk 符号"
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Thunk
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每 `thunk` 由 `SymTagThunk` 标记来标识。  
  
## 属性  
 下表显示此符号类型有效的任何属性。  
  
|属性|数据类型|说明|  
|--------|----------|--------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|访问修饰符属性，其中一个 [CV\_access\_e 枚举](../../debugger/debug-interface-access/cv-access-e.md) 值 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位置的偏移量部件;有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|位置的部分; 部件有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|将类父级，因此，如果任何 \(仅在 DIA SDK V8.0 或更高版本下\)。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|封闭类父符号的 ID \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|则为 true，则 thunk 标记为常数 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|则为 true，则 thunk 是介绍虚函数 \(仅在 DIA SDK V8.0 或更高版本\)|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|则为 true，则 thunk 被视为静态 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|中的字节数 thunk 的代码。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封闭编译符号，块或函数。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号的 ID。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|端点具有静态位置;有关详细信息，请参见 [符号位置](../../debugger/debug-interface-access/symbol-locations.md) 枚举。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|thunk 的名称。|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|则为 true，则 thunk 纯粹是虚拟的 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此 thunk 的相对位置在其模块中。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagThunk` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|thunk 目标位置的偏移量部件。|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../Topic/IDiaSymbol::get_targetRelativeVirtualAddress.md)|`DWORD`|thunk 目标的相对虚拟地址在其封闭块。|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|thunk 目标的部分部件。|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|thunk 目标的位置可执行映像。|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Thunk 类型的定义，是 [THUNK\_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|此 thunk 的类型 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|类型符号的 ID \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ，如果没有 thunk 对齐 \(仅在 DIA SDK V8.0 或更高版本\)，|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` ，如果 thunk 是虚拟的 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此 thunk 的位置在可执行 \(pe\) 映像中的。|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|按虚拟表中对此 thunk \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ，如果 thunk 标记为变量 \(仅在 DIA SDK V8.0 或更高版本\)。|  
  
## 请参阅  
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)   
 [THUNK\_ORDINAL 枚举](../../debugger/debug-interface-access/thunk-ordinal.md)