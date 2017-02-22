---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
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
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters 方法"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建方法的参数的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### 参数  
 `ppParams`  
 \[out\] 返回表示参数的列表。 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象传递给方法;否则，; 如果没有参数，返回空值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有参数。  否则，返回错误代码。  
  
## 备注  
 每个元素是表示参数的不同类型 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  对每个对象的 [GetKind](../Topic/IDebugField::GetKind.md) 方法准确确定哪些类型的参数对象表示。  
  
 参数包含其变量名及其类型。  为类方法的第一个参数通常是 “this”指针。  
  
 如果参数类型的是必需的，请调用 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 方法。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)