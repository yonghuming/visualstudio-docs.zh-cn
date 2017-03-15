---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses 方法"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

此类创建嵌套类的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回表示嵌套类的列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  ; 如果没有嵌套类，则返回 null 值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有嵌套类。  否则，返回错误代码。  
  
## 备注  
 枚举的每个元素是一个描述嵌套类的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。  
  
 嵌套类是类中定义在其他类中。  例如：  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 枚举将包含表示 `NestedClass` 类的对象。  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)