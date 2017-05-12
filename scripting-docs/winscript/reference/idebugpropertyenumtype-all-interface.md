---
title: "IDebugPropertyEnumType_All 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All 接口"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All 接口
`IDebugPropertyEnumType` 接口定义，以便它们的每个IIDs可作为筛选器。`IDebugProperty::EnumMembers`，当请求适当的枚举数时。  
  
## 语法  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|返回一个描述该名称的文本字符串|  
  
 下列接口从 `IDebugPropertyEnumType_All`继承，并且没有其他方法。  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## 请参阅  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)