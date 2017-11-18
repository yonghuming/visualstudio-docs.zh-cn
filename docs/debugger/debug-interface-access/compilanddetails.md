---
title: "CompilandDetails |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bfbb1e05dadb18e9357e38d6ed660c248dccec4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="compilanddetails"></a>CompilandDetails
编译单位信息拆分之间具有符号`SymTagCompiland`标记 （低详细信息） 和一个`SymTagCompilandDetails`标记 （高详细信息）。 `SymTagCompilandDetails`需要加载其他符号。 但是，它提供了丰富的信息不适用于编译单位`SymTagCompiland`符号。  
  
## <a name="properties"></a>属性  
 下表显示可用于此符号类型的属性。  
  
|属性|数据类型|描述|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|编译器后端内部版本号。|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|后端的主要版本号编译器。|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|后端次版本号的编译器。|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|生成此编译单位 （仅在 DIA SDK V8.0 或更高版本） 的编译器的名称。|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`如果在编译已启用编辑并继续。|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|编译器前端生成号。|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|前端主要编译器的版本号。|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|前端次版本号的编译器。|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE`如果此编译单位具有调试信息 （仅在 DIA SDK V8.0 或更高版本）。|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`如果此编译单位包含托管的代码 （仅在 DIA SDK v8.0 或更高版本）。|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`如果编译单位用编译[/GS （缓冲区安全检查）](/cpp/build/reference/gs-buffer-security-check)编译器开关 （仅在 DIA SDK V8.0 或更高版本）。|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`如果编译单位从公共中间语言 (CIL) 代码转换为本机代码。|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`如果用户定义的类型 (UDT) 具有符合某些指定内存边界 （仅在 DIA SDK V8.0 或更高版本）。|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE`如果编译单位用编译[/hotpatch （创建可热修补的映像）](/cpp/build/reference/hotpatch-create-hotpatchable-image)编译器开关 （仅在 DIA SDK v8.0 或更高版本）。|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`如果编译单位用编译[/LTCG （链接时间代码生成）](/cpp/build/reference/ltcg-link-time-code-generation)编译器开关 （仅在 DIA SDK V8.0 或更高版本）。|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|如果编译单位是一个 Microsoft 中间语言 (MSIL) 模块 （仅在 DIA SDK v8.0 或更高版本），则为 TRUE。|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|源代码语言。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|编译单位符号。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|词法父符号 ID。|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|平台编译编译单位 (之一[CV_CPU_TYPE_e 枚举](../../debugger/debug-interface-access/cv-cpu-type-e.md)值)。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|索引 ID 的符号。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返回`SymTagCompilandDetails`(之一[SymTagEnum 枚举](../../debugger/debug-interface-access/symtagenum.md)值)。|  
  
## <a name="remarks"></a>备注  
 编译器通常出现在窗体中称为双步编译器;在某些版本的编译器，由一个单独的程序处理每个传递。 这些被称为前端和后端编译器，分别，因此后端和前端版本号的符号属性。  
  
## <a name="see-also"></a>另请参阅  
 [编译单位](../../debugger/debug-interface-access/compiland.md)   
 [符号类型的词法层次结构](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)