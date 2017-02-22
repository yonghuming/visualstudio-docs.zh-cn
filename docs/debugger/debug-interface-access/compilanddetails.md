---
title: "CompilandDetails | Microsoft Docs"
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
  - "CompilandDetails 符号"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

编译信息拆分在与 `SymTagCompiland` 标记 \(低详细信息\) 和 `SymTagCompilandDetails` 标记 \(高详细信息\) 的字符之间。  `SymTagCompilandDetails` 需要加载的其他符号。  但是，它提供有关如何 `SymTagCompiland` 符号不可用编译的大部分信息。  
  
## 属性  
 下表显示此符号类型有效的任何属性。  
  
|属性|数据类型|说明|  
|--------|----------|--------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|编译器后端的生成号。|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|编译器后端的主版本号。|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|编译器后端的次版本号。|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|导致此编译编译器的名称 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE` ，如果 " 编辑并继续 " 后启用了生成。|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|编译器前端的生成号。|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|编译器前端的主版本号。|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|编译器前端的次版本号。|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|`TRUE` ，则此编译具有调试信息 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` ，则此编译包含托管代码 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` ，如果编译生成了 [\/GS（缓冲区安全检查）](/visual-cpp/build/reference/gs-buffer-security-check) 编译器开关 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` ，如果编译来自公共中间语言代码 \(CIL\)转换为本机代码。|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` ，如果用户定义的类型 \(UDT\)对齐到某个指定的内存边界 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|`TRUE` ，如果编译生成了 [\/hotpatch（创建可热修补的映像）](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) 编译器开关 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` ，如果编译生成了 [\/LTCG（链接时代码生成）](/visual-cpp/build/reference/ltcg-link-time-code-generation) 编译器开关 \(仅在 DIA SDK V8.0 或更高版本\)。|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|则为 true，则编译为 Microsoft 中间语言 \(msil\) 模块 \(仅在 DIA SDK v8.0 或更高版本\)。|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|源代码语言。|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|编译符号。|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号的 ID。|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|编译生成的平台 \(其中一个 [CV\_CPU\_TYPE\_e 枚举](../../debugger/debug-interface-access/cv-cpu-type-e.md) 值\)。|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引符号 ID。|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|返回 `SymTagCompilandDetails` \(其中一个 [SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md) 值\)。|  
  
## 备注  
 编译器通常将称为的一个两阶段的编译器形式;在某些编译器版本中，每个按单独的程序。  这些称为的前端和后端编译器，因此，单个符号属性后端和前端版本号的。  
  
## 请参阅  
 [编译单位](../../debugger/debug-interface-access/compiland.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)