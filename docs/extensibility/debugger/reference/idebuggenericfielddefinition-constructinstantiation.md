---
title: "IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstructInstantiation"
  - "IDebugGenericFieldDefinition::ConstructInstantiation"
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

构造给定的域实例一组类型参数。  
  
## 语法  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```c#  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### 参数  
 `cArgs`  
 \[in\] 参数的数量。 `ppArgs` 数组。  
  
 `ppArgs`  
 \[in\] 对包含类型参数。  该类型参数必须是封闭类型 \(非泛型或完全实例化的泛型\)。  
  
 `ppConstructedField`  
 \[out\] 返回表示新字段的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 接口。  
  
## 返回值  
 如果成功，则返回; `S_OK`否则，返回错误代码。  
  
## 备注  
 约束不会检查。  
  
## 请参阅  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)