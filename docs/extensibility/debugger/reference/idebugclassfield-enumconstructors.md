---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
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
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors 方法"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建构造函数的枚举数此类的。  
  
## 语法  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 参数  
 `cMatch`  
 \[in\] 从构造函数中指定的类型设置为枚举的 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 枚举的值。  
  
 `ppEnum`  
 \[out\] 返回表示构造函数的列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  ; 如果没有构造函数，返回空值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有构造函数。  否则，返回错误代码。  
  
## 备注  
 枚举的每个元素都是描述构造函数方法的 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 对象。  
  
 构造函数列表通常不包括编译器提供的默认构造函数。  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)