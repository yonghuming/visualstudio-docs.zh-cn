---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "IDebugSymbolProvider 接口"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此接口表示提供符号和类型的符号提供程序，返回它们作为字段。  
  
## 语法  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## 实现者说明  
 符号提供程序必须实现此接口提供符号和类型信息对表达式计算器。  
  
## 调用方的说明  
 此接口获取使用 COM 的 `CoCreateInstance` 函数 \(非托管符号提供程序\) 或通过将相应的托管代码程序集和实例化基于信息的符号提供程序在该程序集中找到。  调试引擎实例化符号提供程序与表达式计算器进行交互的方式。  为一个方法参见示例在运行时实例化此接口。  
  
## 方法按 Vtable 顺序  
 下表显示 `IDebugSymbolProvider`方法。  
  
|方法|说明|  
|--------|--------|  
|`Initialize`|已否决。  不要使用。|  
|`Uninitialize`|已否决。  不要使用。|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|获取包含调试地址的字段。|  
|`GetField`|已否决。  不要使用。|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|映射一个文档位置到数组调试地址。|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|映射到文档上下文设置为数组调试地址。|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|映射一个调试地址到文档上下文。|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|获取该语言用于生成代码在调试地址。|  
|`GetGlobalContainer`|已否决。  不要使用。|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|获取表示完全限定的方法名称的字段。|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|获取表示一个完全限定类名的类字段类型。|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|创建命名空间的枚举数与调试地址。|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|映射一个符号名到符号类型。|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|获取遵循给定的调试在方法的地址的调试地址。|  
  
## 备注  
 此接口映射文档位置到调试地址反之亦然。  
  
## 要求  
 标题:sh.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 示例  
 此示例演示如何实例化符号提供程序将其 GUID \(调试引擎必须知道此值\)。  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## 请参阅  
 [符号提供程序接口](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)