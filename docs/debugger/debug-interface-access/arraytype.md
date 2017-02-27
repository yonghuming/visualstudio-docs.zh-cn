---
title: "ArrayType | Microsoft Docs"
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
  - "ArrayType 符号"
ms.assetid: 1d973a3a-2bde-46df-8625-85d519bb3cc9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ArrayType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

数组是由 `SymTagArray` 符号标识。  
  
## 属性  
 下表显示该符号类型的其他活动的属性。  
  
|属性|数据类型|说明|  
|--------|----------|--------|  
|[IDiaSymbol::get\_arrayIndexType](../Topic/IDiaSymbol::get_arrayIndexType.md)|`IDiaSymbol*`|数组索引类型的符号。|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|`DWORD`|数组索引类型符号的 ID。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` ，如果数组标记为 const。|  
|[IDiaSymbol::get\_count](../Topic/IDiaSymbol::get_count.md)|`DWORD`|项目的数字数组中。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|在字节数组，该数组大小，。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封闭编译的符号。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号的 ID。|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|`DWORD`|编写多维数组的级别。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagArray` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|数组元素类型的符号。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|数组元素类型符号的 ID。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ，如果数组为对齐的|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ，如果数组被标记为变量。|  
  
## 请参阅  
 [符号类型的类层次结构](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [维度](../../debugger/debug-interface-access/dimension.md)