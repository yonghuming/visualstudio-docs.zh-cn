---
title: "IDebugGenericParamField::GetNameOfFormalParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField::GetNameOfFormalParam"
  - "GetNameOfFormalParam"
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetNameOfFormalParam
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索此泛型参数的名称。  
  
## 语法  
  
```cpp#  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### 参数  
 `pbstrName`  
 \[out\] 此泛型参数的名称。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 接口的 **CDebugGenericParamFieldType** 对象的方法。  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrName;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );  
    return hr;  
}  
```  
  
## 请参阅  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)