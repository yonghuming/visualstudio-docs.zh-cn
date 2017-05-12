---
title: "DebugPropertyInfo 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo 结构"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo 结构
描述具有名称、类型和值分层性质的对象。  它用于描述局部变量调试属性、参数、监视变量与表达式和注册。  
  
## 语法  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## 成员  
 dwValidFields  
 使用的一个枚举数据类型指定哪些字段初始化。  
  
 bstrName  
 在上下文中的属性名称。  
  
 bstrType  
 属性类型，作为格式化的字符串。  
  
 bstrValue  
 属性值，作为格式化的字符串。  
  
 bstrFullName  
 特性的全名。  
  
 dwAttrib  
 为调试属性指定标志的枚举。  
  
 pDebugProp  
 所介绍的 `IDebugProperty` 本 `DebugPropertyInfo` 结构。  
  
## 请参阅  
 [IDebugProperty 接口](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)