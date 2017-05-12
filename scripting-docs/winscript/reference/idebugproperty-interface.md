---
title: "IDebugProperty 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty 接口"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty 接口
用于描述具有一个名称、类型和值正在调试的实体的任何分层属性。  通常，`IDebugProperty` 用于描述表达式计算、语句计算或注册计算的结果。  
  
## Vtable 顺序中的方法  
 下表显示 `IDebugProperty` 接口的方法。  
  
|方法|说明|  
|--------|--------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|获取描述此 `IDebugProperty``.`的 `DebugPropertyInfo`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|获取有关属性的扩展的信息。|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|设置属性的值从字符串的。|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|枚举属性的成员。|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|获取特性的父级。|  
  
## 要求  
 标头:dbgprop.h