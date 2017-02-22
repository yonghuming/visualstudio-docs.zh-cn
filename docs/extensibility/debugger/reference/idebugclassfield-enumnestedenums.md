---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
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
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedEnums 方法"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

创建此类的嵌套枚举的枚举数。  
  
## 语法  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 参数  
 `ppEnum`  
 \[out\] 返回表示嵌套的枚举列表 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  ; 如果没有嵌套的枚举，返回空值。  
  
## 返回值  
 如果成功，则返回 S\_OK 或返回 S\_FALSE，如果没有嵌套的枚举器。  否则，返回错误代码。  
  
## 备注  
 枚举的每个元素是一个描述嵌套的枚举的 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) 对象。  
  
 枚举声明在类中称为 " 嵌套的枚举。  例如，给定：  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums` 方法将返回一 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) 对象表示 `NestedEnum` 枚举的 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 对象。  
  
## 请参阅  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)