---
title: "IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider::GetClassTypeByName"
helpviewer_keywords: 
  - "IDebugSymbolProvider::GetClassTypeByName 方法"
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugSymbolProvider::GetClassTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此方法获取表示一个完全限定类名的类字段类型。  
  
## 语法  
  
```cpp#  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```c#  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### 参数  
 `pszClassName`  
 \[in\] 类名。  
  
 `nameMatch`  
 \[in\] 选择匹配的类型，例如，区分大小写。  [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md) 枚举中的一个值。  
  
 `ppField`  
 \[out\] 返回类类型 \(如由 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 请参阅  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)