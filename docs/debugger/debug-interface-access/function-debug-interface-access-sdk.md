---
title: "函数（调试接口访问 SDK） | Microsoft Docs"
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
  - "Function 符号"
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 函数（调试接口访问 SDK）
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

每个功能由 `SymTagFunction` 符号标识。  
  
## 属性  
 下表显示此符号类型有效的任何属性。  
  
|属性|`Data type`|说明|  
|--------|-----------------|--------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|一个 [CV\_access\_e 枚举](../../debugger/debug-interface-access/cv-access-e.md)的值，因此，如果函数是成员函数。|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|位置的偏移量部件;有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|位置的部分; 部件有关详细信息，请参见 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)。|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|类的符号，因此，如果函数是成员函数。|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|类父符号的 ID。|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` ，如果函数标记为常数。|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` ，如果该函数使用自定义调用约定 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` ，如果函数执行一返回 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasAlloca](../Topic/IDiaSymbol::get_hasAlloca.md)|`BOOL`|`TRUE` ，如果该函数使用分配的记忆函数 \(uinnder 仅 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` ，如果该函数包含 C\+\+ 样式的异常处理 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasEHa](../Topic/IDiaSymbol::get_hasEHa.md)|`BOOL`|`TRUE` ，如果该函数包含异步异常处理 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` ，如果该函数包含内联程序集 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` ，如果该函数包含 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) 调用 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` ，如果该函数包含安全检查 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` ，如果该函数包含 Win32 样式结构化异常处理 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` ，如果该函数包含 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) 调用 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` ，如果该函数具有从中断的一个返回 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` ，如果函数是虚拟的表示形式。|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` ，如果该函数标记用一 [inline、\_\_inline、\_\_forceinline](../../misc/inline-inline-forceinline.md) 属性。|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` ，如果函数标记为 [naked](/visual-cpp/cpp/naked-cpp) 属性 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` ，如果函数是静态的 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|字节数函数代码，从起始位置。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|封闭编译的符号。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号的 ID。|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|函数可以有静态或元数据位置;有关详细信息，请参见 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)。|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|函数的名称。|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` ，如果函数不是内联函数 \(n 仅 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` ，如果函数不可访问 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` ，如果函数不返回值 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_noStackOrdering](../Topic/IDiaSymbol::get_noStackOrdering.md)|`BOOL`|`TRUE` ，如果函数生成了缓冲区安全检查，但没有堆栈排序上执行。|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` ，如果代码具有调试优化代码的信息 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` ，如果函数是纯虚函数。|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|此函数的相对位置。它的模块中。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagFunction` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|元数据标记。功能。|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|函数签名的符号。|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|类型符号的 ID。|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` ，如果函数未对齐的。|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|函数名的修饰形式 \(仅在 DIA SDK v8.0 或更高版本\)|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|部分或全部函数名的修饰形式 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` ，如果虚函数。|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|此功能在的位置可执行 \(pe\) 映像中的。|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|如果虚函数，然后按虚函数表中。|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` ，如果函数标记为变量。|  
  
## 请参阅  
 [CV\_access\_e 枚举](../../debugger/debug-interface-access/cv-access-e.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType 枚举](../../debugger/debug-interface-access/locationtype.md)   
 [符号位置](../../debugger/debug-interface-access/symbol-locations.md)