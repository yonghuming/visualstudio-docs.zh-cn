---
title: "IDebugSymbolProviderDirect | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect 接口"
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示具有直接访问元数据和内核符号接口的符号提供程序。  
  
## 语法  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## 方法  
 此接口执行以下方法:  
  
|方法|说明|  
|--------|--------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|检索给定的应用程序域标识符调试地址。|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|检索有关模块的符号信息在组中。|  
|[GetCurrentModulesState](../Topic/IDebugSymbolProviderDirect::GetCurrentModulesState.md)|检索有关符号提供程序是成员的符号组的信息。|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|检索元数据导入信息。|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|检索有关指定的方法的信息调试地址。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|检索非托管代码的一个符号读取器。|  
  
## 备注  
 此接口可以使用而不是大多数其他符号提供程序接口。  它提供了直接访问元数据和 `CorSym` 接口。  
  
## 要求  
 标题:Sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll