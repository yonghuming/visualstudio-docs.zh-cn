---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
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
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass 方法"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取包含此类的类。  
  
## 语法  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### 参数  
 `ppClassField`  
 \[out\] 返回表示封闭类的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。  ; 如果没有封闭类，则返回 null 值。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 如果此 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象表示的类是嵌套类，则 `ppClassField` 参数返回表示封闭类的 `IDebugClassField` 对象。  例如命名此类定义:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 对表示 `NestedClass` 类的 `IDebugClassField` 对象的 `GetEnclosingClass` 方法返回表示类 `RootClass`的 `IDebugClassField` 对象。  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)