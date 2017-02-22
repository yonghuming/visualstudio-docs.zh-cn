---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
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
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty 方法"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取可返回此对象表示的属性的字段或变量 \(如果有\)。  
  
## 语法  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### 参数  
 `ppObject`  
 \[out\] 描述支持字段的 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 对象以获取表示托管代码类属性，也就是说，方法和\/或 set 访问器。  此属性通常需要一个变量包含属性操作的值。  此变量称为支持字段。  如果没有对象的支持字段，请确保返回空值:某些调用方不能注意返回值，但是查找查看 null 值是否在 `ppObject`返回。  
  
## 请参阅  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)