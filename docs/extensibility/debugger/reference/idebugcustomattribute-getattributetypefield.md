---
title: "IDebugCustomAttribute::GetAttributeTypeField | Microsoft Docs"
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
  - "IDebugCustomAttribute::GetAttributeTypeField"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetAttributeTypeField"
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

获取自定义特性类类型。  
  
## 语法  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```c#  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### 参数  
 `ppCAType`  
 \[out\] 返回表示类自定义特性的实例的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。  
  
## 返回值  
 如果成功，则返回 S\_OK;否则，返回错误代码。  
  
## 备注  
 自定义属性始终是类。  此方法提供对描述该类的 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 对象。  
  
## 请参阅  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)