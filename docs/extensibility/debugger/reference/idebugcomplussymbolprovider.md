---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider 接口"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用特定于托管代码的方法表示 COM\+ 符号提供程序。  
  
## 语法  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## 实现者说明  
 虽然不在为表达式计算器 \(EE\)是有用应该由调试引擎 \(DE\)使用，以下方法只可能会 interest DE developers 的接口以及之间的分离:AreSymbolsLoaded、 GetAddressesInModuleFromPosition、 GetEntryPoint、 GetFunctionLineOffset、 GetLocalVariableLayout、 IsFunctionStale、 LoadSymbols、 LoadSymbolsFromStream、 ReplaceSymbols、 UnloadSymbols 和 UpdateSymbols。  
  
## 方法  
 除了在 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 接口的方法之外，此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|确定调试符号是否为给定的指定模块加载应用程序域标识符。|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|创建从指定的基元类型的类型。|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|映射中指定的模块的文档位置为数组调试地址。|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|检索有关提供的指定数组的类型信息其调试地址。|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|检索生成的程序集的名称其模块和应用程序域。|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|检索在这种特定编程语言实现具有指定属性的类。|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|检索具有指定属性的类在特定模块。|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|检索应用程序的入口点。|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|检索在表示特定行偏移量的函数中的地址。|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|检索局部变量格式的方法。|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|返回该名称与给定的指定标记其元数据对象。|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|检索与特定父属性的调试符号指定模块的。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|检索非托管代码的符号读取器。|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|检索对符号给定的类型其调试地址。|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|确定在中指定的函数是否调试地址被删除。|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|确定在中指定的函数是否调试地址被视为已过时。|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|确定指定的调试器地址的代码是否为隐藏的。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|加载指定的调试内存中的符号。|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|加载调试给定的符号数据流。|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|替换当前调试与这些符号在指定的数据流。|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|卸载指定模块的调试符号从内存。|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|更新内存中的调试符号与指定的数据流。|  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll