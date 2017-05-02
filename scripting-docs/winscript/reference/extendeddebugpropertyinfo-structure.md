---
title: "ExtendedDebugPropertyInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo 结构"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo 结构
扩展 `DebugPropertyInfo` 结构与其他成员分析该扩展属性。  
  
## 语法  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## 成员  
 `dwValidFields`  
 使用的一个枚举数据类型指定哪些字段初始化。  
  
 `bstrName`  
 在上下文中的属性名称。  
  
 `bstrType`  
 作为格式的字符串的属性类型。  
  
 `bstrValue`  
 属性值作为已格式化的字符串。  
  
 `bstrFullName`  
 特性的全名。  
  
 `dwAttrib`  
 为调试属性指定标志的枚举。  
  
 `pDebugProp`  
 与此 `ExtendedDebugPropertyInfo`对应的`IDebugProperty` 对象。  
  
 `nDISPID`  
 调度ID.  
  
 `nType`  
 扩展属性类型。  
  
 `varValue`  
 扩展属性值，则可能包含变量。  
  
 `plbValue`  
 属性值的实际数据字节。  
  
 `pDebugExtProp`  
 与此 `ExtendedDebugPropertyInfo`对应的`IDebugExtendedProperty` 对象。  
  
## 请参阅  
 [DebugPropertyInfo 结构](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 接口](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)