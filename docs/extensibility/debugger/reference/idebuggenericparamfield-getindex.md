---
title: "IDebugGenericParamField::GetIndex | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField::GetIndex"
ms.assetid: 8e0bdb26-1247-44d9-8d80-ec6e35187fb4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugGenericParamField::GetIndex
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

检索此泛型参数索引。  
  
## 语法  
  
```cpp#  
HRESULT GetIndex(  
   DWORD* pIndex  
);  
```  
  
```c#  
int GetIndex(  
   out uint pIndex  
);  
```  
  
#### 参数  
 `pIndex`  
 \[out\] 此泛型参数的索引值。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 例如，对于字典 \(K， Hyper\-v\)， K 是索引 0， V 是索引 1。  
  
## 示例  
 下面的示例演示如何执行显示 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) 接口的 **CDebugGenericParamFieldType** 对象的方法。  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetIndex(DWORD* pIndex)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetIndex );  
  
    IfFalseGo(pIndex, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    *pIndex = m_index;  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetIndex, hr );  
    return hr;  
}  
```  
  
## 请参阅  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)