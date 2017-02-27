---
title: "IDebugMethodField::EnumStaticLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumStaticLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumStaticLocals 方法"
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建方法的静态局部变量的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 参数  
 `ppLocals`  
 \[out\] 返回表示静态局部的列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  ; 如果没有静态局部，返回空值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有静态局部。  否则，返回错误代码。  
  
## 备注  
 每个元素是表示静态局部不同类型的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 对象。  对每个对象的 [GetKind](../Topic/IDebugField::GetKind.md) 方法正确地确定哪种静态局部对象表示。  
  
## 请参阅  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)