---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "IDebugMethodField::EnumArguments 方法"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建所需的每个参数的类型的枚举器调用方法。  
  
## 语法  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### 参数  
 `ppParams`  
 \[out\] 返回表示参数类型的列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  ; 如果没有参数，返回空值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有参数。  否则，返回错误代码。  
  
## 备注  
 每个元素是表示每个参数的类型 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  调用 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 方法来检索有关每个参数的类型的信息。  
  
 如果该参数的名称与类型一起是必需的，然后调用 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) 方法。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)