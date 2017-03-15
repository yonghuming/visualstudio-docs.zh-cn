---
title: "IDebugGenericParamField::GetFlags | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetFlags"
  - "IDebugGenericParamField::GetFlags"
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetFlags
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索此泛型参数的标志。  
  
## 语法  
  
```cpp#  
HRESULT GetFlags(  
   DWORD* pdwFlags  
);  
```  
  
```c#  
int GetFlags(  
   ref uint pdwFlags  
);  
```  
  
#### 参数  
 `pdwFlags`  
 \[out\] 返回此泛型参数的标志。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 这些标志包含有关各种特殊约束的信息。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 接口的 **CDebugGenericParamFieldType** 对象的方法。  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );  
  
    IfFalseGo( pdwFlags, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pdwFlags = m_dwFlags;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );  
    return hr;  
}  
```  
  
## 请参阅  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)