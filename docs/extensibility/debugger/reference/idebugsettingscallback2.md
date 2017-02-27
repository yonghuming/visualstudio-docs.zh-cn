---
title: "IDebugSettingsCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2 接口"
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

启用调试引擎远程读取指标设置。  
  
## 语法  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## 实现者说明  
 此接口由该会话的事件回调实现调试管理器，并使用调试引擎。  它还可以使用本地而不是 Dbgmetric \[\] d .lib。  
  
## 方法  
 下表显示 `IDebugSettingsCallback2`方法。  
  
|方法|说明|  
|--------|--------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|枚举提供的表达式计算器为语言和供应商标识符。|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|检索给定的表达式计算器本地对象指标。|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|检索对应于指定的指标表达式计算器的值。|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|检索给定的表达式计算器指标文件名称或指标。|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|检索命名的表达式计算器指标的唯一标识符其名称。|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|检索命名值的字符串表达式计算器指标其名称。|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|检索命名值的指标其名称。|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|检索命名的唯一标识符指标其名称。|  
|[GetMetricString](../Topic/IDebugSettingsCallback2::GetMetricString.md)|检索命名值的字符串指标其名称。|  
  
## 要求  
 标题:Msdbg.h  
  
 命名空间:Microsoft.VisualStudio.Debugger.Interop  
  
 程序集:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 示例  
 下面的示例演示获取 **IDebugSettingsCallback2** 对象作为参数的函数。  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```